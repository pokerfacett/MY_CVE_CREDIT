## Background
Allwinner R818 SoC is made for smart speakers with a screen which is a processor for use in Android-based
It integrates quad-core 64-bit CortexTM-A53 CPU and Imagination PowerVR GE8300 GPU to ensure response rapidity and
running smoothness for daily application, such as on-line video, web browsing, and so on

## Description
There is a Integer Overflow in the ION driver "/dev/ion". An third-app could use the ioctl cmd "COMPAT_ION_IOC_SUNXI_FLUSH_RANGE"to cause a system crash.

## Affect Versions
Soc: Allwinner R818 
System: R818 Android Q 
SDK Version: V1.0 

## POC
The problem code is as follow:

![image](https://user-images.githubusercontent.com/13774458/129023290-3ca1b2b2-ef27-407b-92a3-4e5f1d62102f.png)

Here there is an integer overflow at size. If end <start, size will become a very large number, and start and end are user-mode controllable parameters. The structure is as follows:

```
typedef struct
{
    long    start;
    long    end;
} sunxi_cache_range;

```

Related question command words can be called in the following ways:

```
ret = ioctl(g_alloc_context->fd, ION_IOC_SUNXI_FLUSH_RANGE, &range);
```

After configuring the CONFIG_ARM64 compilation, the __dma_flush_range function will be called, if the CONFIG_ARM64 option is configured, the size will be passed into the __dma_flush_range function

![image](https://user-images.githubusercontent.com/13774458/129023602-2d450014-2954-4345-9e65-4e0d5224402e.png)

Will cause out-of-bounds, and there will be no problem if CONFIG_ARM64 is not configured

Here I borrow CdxIon.c in audio and video decoding:

![image](https://user-images.githubusercontent.com/13774458/129023687-a47f3222-d8f6-407b-afa8-109f67ccfaa9.png)


And CdxIonFlushCache1 is as follows:

![image](https://user-images.githubusercontent.com/13774458/129023748-84493cf0-67fb-4acf-9fe1-ac3a67c1c10c.png)

In fact, to verify the integer overflow, we run the POC and print through dmesg:

![image](https://user-images.githubusercontent.com/13774458/129023796-9fcad5a3-7c67-4855-a728-e079e62b6241.png)


The dmesg is as follows:

![image](https://user-images.githubusercontent.com/13774458/129023866-1e6a2a8a-f6dd-4510-8b98-cf594c2295ac.png)


## Patch
The patch of Allwinner is as follow:

![image](https://user-images.githubusercontent.com/13774458/129023971-66f2c282-8812-4ac7-9aa1-fb4dbad80cdd.png)


## References
https://www.cnvd.org.cn/flaw/show/CNVD-2021-49171

https://vul.wangan.com/a/CNVD-2021-49171

https://www.allwinnertech.com/index.php?c=product&a=index&id=92
