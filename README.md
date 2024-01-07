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
```
Building target: ch32v003.elf
Invoking: GNU RISC-V Cross C Linker
riscv-none-embed-gcc -msmall-data-limit=0 -msave-restore -march=rv32ec -mabi=ilp32e -O1 -fmessage-length=0 -fsigned-char -ffunction-sections -fdata-sections -fno-common -T "/home/alanfans/Desktop/elink/STM32/eclipse-workspaces/ch32v003/startup/Link.ld" -nostartfiles -Xlinker --gc-sections -Wl,-Map,"ch32v003.map" --specs=nano.specs --specs=nosys.specs -o "ch32v003.elf" ./system/src/Peripheral/ch32v00x_adc.o ./system/src/Peripheral/ch32v00x_dbgmcu.o ./system/src/Peripheral/ch32v00x_dma.o ./system/src/Peripheral/ch32v00x_exti.o ./system/src/Peripheral/ch32v00x_flash.o ./system/src/Peripheral/ch32v00x_gpio.o ./system/src/Peripheral/ch32v00x_i2c.o ./system/src/Peripheral/ch32v00x_iwdg.o ./system/src/Peripheral/ch32v00x_misc.o ./system/src/Peripheral/ch32v00x_opa.o ./system/src/Peripheral/ch32v00x_pwr.o ./system/src/Peripheral/ch32v00x_rcc.o ./system/src/Peripheral/ch32v00x_spi.o ./system/src/Peripheral/ch32v00x_tim.o ./system/src/Peripheral/ch32v00x_usart.o ./system/src/Peripheral/ch32v00x_wwdg.o  ./system/src/Core/core_riscv.o  ./startup/startup_ch32v00x.o  ./src/ch32v00x_it.o ./src/debug.o ./src/main.o ./src/system_ch32v00x.o   
Finished building target: ch32v003.elf
 
Invoking: GNU RISC-V Cross Create Flash Image
riscv-none-embed-objcopy -O ihex "ch32v003.elf"  "ch32v003.hex"
Invoking: GNU RISC-V Cross Print Size
riscv-none-embed-size --format=berkeley "ch32v003.elf"
Finished building: ch32v003.hex
   text	   data	    bss	    dec	    hex	filename
   7096	    152	    532	   7780	   1e64	ch32v003.elf
 
Finished building: ch32v003.siz
```

startup_ch32v00x.s结尾这个S要大写（外网关于eclipse单片机视频里看到up主这么改的，我不知道原因）且和ld文件放入同一个目录

Eclipse IDE for Embedded C/C++ Developers  used