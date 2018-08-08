# 参考Nordic官方例程修改，python3环境执行
> https://www.nordicsemi.com/eng/Products/Bluetooth-low-energy/nRF-Sniffer
> http://www.nordicsemi.com/eng/Products/Bluetooth-low-energy/nRF-Sniffer#Downloads

# 环境
    >=python3.5.4
    >=pyserial3.4
    >=wireshark2.4.5

# 测试环境
    win10
    nrf52832 DK板（P10040）
    （linux or osx 应该也没有问题）

# 配置
> 解压至".\Wireshark\extcap"

# 端口测试
> 命令行执行：nrf_sniffer.bat --extcap-interfaces

    extcap {version=2.0.0}{display=nRF Sniffer}{help=http://www.nordicsemi.com/eng/Products/Bluetooth-low-energy/nRF-Sniffer#Downloads}
    ('串口列表:', 'COM6')
    0
    ('串口列表:', 'COM6')
    control {number=0}{type=selector}{display=Device}{tooltip=Device list}
    control {number=1}{type=string}{display=Passkey / OOB key}{tooltip=6 digit temporary key or 16 byte Out-of-band (OOB) key in hexadecimal starting with '0x', big endian format. If the entered key is shorter than 16 bytes, it will be zero-padded in front'}{validation=\b^(([0-9]{6})|(0x[0-9a-fA-F]{1,32}))$\b}
    control {number=2}{type=string}{display=Adv Hop}{default=37,38,39}{tooltip=Advertising channel hop sequence. Change the order in which the siffer switches advertising channels. Valid channels are 37, 38 and 39 separated by comma.}{validation=^\s*((37|38|39)\s*,\s*){0,2}(37|38|39){1}\s*$}{required=true}
    control {number=3}{type=button}{role=help}{display=Help}{tooltip=Access user guide (launches browser)}
    control {number=4}{type=button}{role=restore}{display=Defaults}{tooltip=Resets the user interface and clears the log file}
    control {number=5}{type=button}{role=logger}{display=Log}{tooltip=Log per interface}
    value {control=0}{value= }{display=All advertising devices}{default=true}

# 运行
> 1，开发板烧录对应hex文件，如nrf52_DK板: ".\hex\sniffer_pca10040_51296aa"  
> 2，上电，等待3-5秒，串口稳定，打开wireshark，发现成功注册“nRF Sniffer COMx”信息，如果未出现，重做此步骤  
> 3，打开“nRF Sniffer COMx”，开始抓包，如果打开后没有信息输出，重做步骤2  
> 4，关机结束  

## 谢谢




