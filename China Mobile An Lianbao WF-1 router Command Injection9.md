# Background
China Mobile An Lianbao WF-1 router is an AX1800 router based on Qualcomm's five-core processor. It adopts a new generation of 11AX technology, 2.4G and 5G dual-band concurrently, and can provide a wireless rate of 1800M, providing high-speed and stable WiFi coverage

# Description
China Mobile An Lianbao WF-1 router provide web interface /api/ZRMacClone/mac_addr_clone which receive parameters by POST request, and the parameter MLD_PROXY_WAN_CONNECT has a command injection vulnerability, An attacker can use the vulnerability to execute remote commands

# Affect Versions
V1.0.1

# POC
![image](https://user-images.githubusercontent.com/13774458/119130627-0995a080-ba6b-11eb-921b-e4a6b3cdad19.png)

Interface mac_addr_clone recevice params from post request as follow：

![image](https://user-images.githubusercontent.com/13774458/119130694-1c0fda00-ba6b-11eb-9d91-9d454f78e1b2.png)

here will pass param macType to logger which cause command injection

![image](https://user-images.githubusercontent.com/13774458/119130811-46619780-ba6b-11eb-90c4-bcd969d76a99.png)

result of POC is：

![image](https://user-images.githubusercontent.com/13774458/119130870-5bd6c180-ba6b-11eb-89d9-a2506d62409d.png)


# Acknowledgements
repoter :Lewei Qu and Dongxiang Ke

# References
https://www.cnvd.org.cn/flaw/show/CNVD-2021-03520

https://www.ebuy7.com/item/china-mobile-wireless-router-qualcomm-qiki-wifi6-routing-mesh-network-home-5g-dual-frequency-double-gigabit-port-wall-wall-high-speed-%E2%80%8B%E2%80%8Bhigh-power-enhanced-dormitory-students-an-lianbao-wf-1-628692180620

http://iot.10086.cn/?l=en-us
