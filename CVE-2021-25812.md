# Background
China Mobile An Lianbao WF-1 router is an AX1800 router based on Qualcomm's five-core processor. It adopts a new generation of 11AX technology, 2.4G and 5G dual-band concurrently, and can provide a wireless rate of 1800M, providing high-speed and stable WiFi coverage

# Description
China Mobile An Lianbao WF-1 router provide web interface /api/ZRQos/set_online_client which receive parameters by POST request, and the parameter ip field has a command injection vulnerability, An attacker can use the vulnerability to execute remote commands

# Affect Versions
V1.0.1

# POC
![image](./picture/ZQos%20RCE.png)

problem code is in zrQos.lua which receive params from http request as follow：

![image](./picture/set_online_client1.png)

And param ip  not filtered and directly spliced into the command line parameters, causing command injection

![image](./picture/set_online_client.jpg)

result of POC is：

![image](./picture/result_command_injection1.png)

# Acknowledgements
repoter :Lewei Qu and Dongxiang Ke

# Video
https://drive.google.com/drive/folders/1Im_nxWnwEgRrs0u0QYWkJXR4E-f26qna

# References
https://www.cnvd.org.cn/flaw/show/CNVD-2021-03520

https://www.ebuy7.com/item/china-mobile-wireless-router-qualcomm-qiki-wifi6-routing-mesh-network-home-5g-dual-frequency-double-gigabit-port-wall-wall-high-speed-%E2%80%8B%E2%80%8Bhigh-power-enhanced-dormitory-students-an-lianbao-wf-1-628692180620

http://iot.10086.cn/?l=en-us
