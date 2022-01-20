# Background
China Mobile An Lianbao WF-1 router is an AX1800 router based on Qualcomm's five-core processor. It adopts a new generation of 11AX technology, 2.4G and 5G dual-band concurrently, and can provide a wireless rate of 1800M, providing high-speed and stable WiFi coverage

# Description
China Mobile An Lianbao WF-1 router provide web interface /api/ZRMesh/set_ZRMesh which receive parameters by POST request, and the parameter mesh_enable and mesh_device has a command injection vulnerability, An attacker can use the vulnerability to execute remote commands

# Affect Versions
V1.0.1

# POC
![image](https://user-images.githubusercontent.com/13774458/119131687-5c238c80-ba6c-11eb-9d63-4b730a305b05.png)


Interface set_ZRMesh recevice params from post request as follow：

![image](https://user-images.githubusercontent.com/13774458/119131725-68a7e500-ba6c-11eb-82ca-827ab960af69.png)

![image](https://user-images.githubusercontent.com/13774458/119131736-6d6c9900-ba6c-11eb-997e-eccf65fe004f.png)


Cause command injection:

![image](https://user-images.githubusercontent.com/13774458/119131776-78272e00-ba6c-11eb-8663-870a9746d094.png)


result of POC is：

![image](https://user-images.githubusercontent.com/13774458/119131787-7c534b80-ba6c-11eb-9150-9bc91bb6dbcb.png)

# Acknowledgements
repoter :Lewei Qu and Dongxiang Ke

# References
https://www.cnvd.org.cn/flaw/show/CNVD-2021-03520

https://www.ebuy7.com/item/china-mobile-wireless-router-qualcomm-qiki-wifi6-routing-mesh-network-home-5g-dual-frequency-double-gigabit-port-wall-wall-high-speed-%E2%80%8B%E2%80%8Bhigh-power-enhanced-dormitory-students-an-lianbao-wf-1-628692180620

http://iot.10086.cn/?l=en-us
