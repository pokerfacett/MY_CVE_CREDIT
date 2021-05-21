# Background
China Mobile An Lianbao WF-1 router is an AX1800 router based on Qualcomm's five-core processor. It adopts a new generation of 11AX technology, 2.4G and 5G dual-band concurrently, and can provide a wireless rate of 1800M, providing high-speed and stable WiFi coverage

# Description
China Mobile An Lianbao WF-1 router provide web interface /api/ZRUsb/pop_usb_device which receive parameters by POST request, and the parameter path has a command injection vulnerability, An attacker can use the vulnerability to execute remote commands

# Affect Versions
V1.0.1

# POC
![image](https://user-images.githubusercontent.com/13774458/119132354-2cc14f80-ba6d-11eb-8248-703927f5cb27.png)


Interface pop_usb_device recevice params from post request as follow：

![image](https://user-images.githubusercontent.com/13774458/119132401-38147b00-ba6d-11eb-854a-38336eab9602.png)


Cause command injection:
![image](https://user-images.githubusercontent.com/13774458/119132427-419de300-ba6d-11eb-9d57-c276fcd160b8.png)


result of POC is：
![image](https://user-images.githubusercontent.com/13774458/119132440-46fb2d80-ba6d-11eb-909f-cb0cdf80fd65.png)

# Acknowledgements
repoter :Lewei Qu and Dongxiang Ke

# References
https://www.cnvd.org.cn/flaw/show/CNVD-2021-03520

https://www.ebuy7.com/item/china-mobile-wireless-router-qualcomm-qiki-wifi6-routing-mesh-network-home-5g-dual-frequency-double-gigabit-port-wall-wall-high-speed-%E2%80%8B%E2%80%8Bhigh-power-enhanced-dormitory-students-an-lianbao-wf-1-628692180620

http://iot.10086.cn/?l=en-us
