# CH32V003
由于不想下载MounRiver Studio，大佬都是用命令行，我不行，我已经有eclipse,所以ch32v003编译采用eclipseCDT

工具链用的MRS_Toolchain_Linux_x64_V1.80

工具链里的openocd 已经支持debug,配置文件在根目录wch-riscv.cfg

编译参数参考PlatformIO里的编译参数，-march=rv32ec -mabi=ilp32e

环境变量设置了：CH32V003x4

主要是配置头文件相关的库引用
``` 
"${workspace_loc:/${ProjName}/include}"
"${workspace_loc:/${ProjName}/system/include/Core}"
"${workspace_loc:/${ProjName}/system/include/Peripheral}"
```

其他参数也可以参考PlatformIO里的编译参数

startup_ch32v00x.s结尾这个S要大写（外网关于eclipse单片机视频里看到up主这么改的，我不知道原因）且和ld文件放入同一个目录

Eclipse IDE for Embedded C/C++ Developers  used