#
# Project-specific settings
#
VERBOSE=1
PROJECT = mbed_simple
OBJECTS = .\Microsoft.Zelig.Test.mbed.Simple_opt.o $(TARGET)\temporary_helper.o


#
# Paths and includes
# TODO: Make this algorithmic based on TARGET.
#

ifndef TARGET
	$(error TARGET is undefined. Pass in TARGET for desired board)
endif

ifeq ($(HARDFP),1)
	FLOAT_ABI = hard
else
	FLOAT_ABI = softfp
endif

# Common settings
GCC_BIN = ..\ARM_GCC\4.9\bin\\
MBED_ROOT = ..\mbed
LIBRARIES = -lmbed
LD_SYS_LIBS = -lstdc++ -lsupc++ -lm -lc -lgcc -lnosys

# LPC1768 settings
ifeq ($(TARGET),LPC1768)
	SYS_OBJECTS = $(MBED_ROOT)\TARGET_LPC1768\TOOLCHAIN_GCC_ARM\board.o $(MBED_ROOT)\TARGET_LPC1768\TOOLCHAIN_GCC_ARM\startup_LPC17xx.o $(MBED_ROOT)\TARGET_LPC1768\TOOLCHAIN_GCC_ARM\cmsis_nvic.o $(MBED_ROOT)\TARGET_LPC1768\TOOLCHAIN_GCC_ARM\retarget.o $(MBED_ROOT)\TARGET_LPC1768\TOOLCHAIN_GCC_ARM\system_LPC17xx.o
	INCLUDE_PATHS = -I. -I$(MBED_ROOT) -I$(MBED_ROOT)\TARGET_LPC1768 -I$(MBED_ROOT)\TARGET_LPC1768\TOOLCHAIN_GCC_ARM -I$(MBED_ROOT)\TARGET_LPC1768\TARGET_NXP -I$(MBED_ROOT)\TARGET_LPC1768\TARGET_NXP\TARGET_LPC176X -I$(MBED_ROOT)\TARGET_LPC1768\TARGET_NXP\TARGET_LPC176X\TARGET_MBED_LPC1768
	LIBRARY_PATHS = -L$(MBED_ROOT)\TARGET_LPC1768\TOOLCHAIN_GCC_ARM
	LINKER_SCRIPT = $(MBED_ROOT)\TARGET_LPC1768\TOOLCHAIN_GCC_ARM\LPC1768.ld
	
	# Build flags
	CPU = -mcpu=cortex-m3 -mthumb
	CC_FLAGS = $(CPU) -c -g -fno-common -fmessage-length=0 -Wall -fno-exceptions -ffunction-sections -fdata-sections -fomit-frame-pointer -MMD -MP
	CC_SYMBOLS = -DTARGET_LPC1768 -DTARGET_M3 -DTARGET_CORTEX_M -DTARGET_NXP -DTARGET_LPC176X -DTARGET_MBED_LPC1768 -DTOOLCHAIN_GCC_ARM -DTOOLCHAIN_GCC -D__CORTEX_M3 -DARM_MATH_CM3 -DMBED_BUILD_TIMESTAMP=1435185689.48 -D__MBED__=1
	LD_FLAGS = $(CPU) -Wl,--gc-sections --specs=nano.specs -u _printf_float -u _scanf_float -Wl,--wrap,main -Wl,-Map=$(TARGET)\$(PROJECT).map,--cref
	
# K64F settings
else ifeq ($(TARGET),K64F)
	SYS_OBJECTS = $(MBED_ROOT)/TARGET_K64F/TOOLCHAIN_GCC_ARM/mbed_overrides.o $(MBED_ROOT)/TARGET_K64F/TOOLCHAIN_GCC_ARM/system_MK64F12.o $(MBED_ROOT)/TARGET_K64F/TOOLCHAIN_GCC_ARM/startup_MK64F12.o $(MBED_ROOT)/TARGET_K64F/TOOLCHAIN_GCC_ARM/board.o $(MBED_ROOT)/TARGET_K64F/TOOLCHAIN_GCC_ARM/cmsis_nvic.o $(MBED_ROOT)/TARGET_K64F/TOOLCHAIN_GCC_ARM/retarget.o 
	INCLUDE_PATHS = -I. -I$(MBED_ROOT) -I$(MBED_ROOT)/TARGET_K64F -I$(MBED_ROOT)/TARGET_K64F/TOOLCHAIN_GCC_ARM -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_MCU_K64F -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_MCU_K64F/MK64F12 -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_MCU_K64F/device -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_MCU_K64F/device/MK64F12 -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_MCU_K64F/device/device -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_MCU_K64F/device/device/MK64F12 -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_MCU_K64F/TARGET_FRDM -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/common -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/common/phyksz8081 -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/lptmr -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/dac -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/gpio -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/port -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/llwu -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/sim -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/rcm -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/sdhc -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/can -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/mpu -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/smc -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/osc -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/flextimer -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/pdb -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/enet -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/i2c -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/uart -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/dspi -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/pit -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/lpuart -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/sai -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/rtc -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/mcg -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/edma -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/pmc -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/adc -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/wdog -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/hal/dmamux -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/utilities -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/drivers -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/drivers/enet -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/drivers/pit -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/drivers/pit/common -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/drivers/interrupt -I$(MBED_ROOT)/TARGET_K64F/TARGET_Freescale/TARGET_KPSDK_MCUS/TARGET_KPSDK_CODE/drivers/clock 
	LIBRARY_PATHS = -L$(MBED_ROOT)/TARGET_K64F/TOOLCHAIN_GCC_ARM 
	LINKER_SCRIPT = $(MBED_ROOT)/TARGET_K64F/TOOLCHAIN_GCC_ARM/K64FN1M0xxx12.ld
	
	# Build flags
	CPU = -mcpu=cortex-m4 -mthumb -mfpu=fpv4-sp-d16 -mfloat-abi=$(FLOAT_ABI) 
	CC_FLAGS = $(CPU) -c -g -fno-common -fmessage-length=0 -Wall -fno-exceptions -ffunction-sections -fdata-sections -fomit-frame-pointer -MMD -MP
	CC_SYMBOLS = -DTARGET_K64F -DTARGET_M4 -DTARGET_CORTEX_M -DTARGET_Freescale -DTARGET_KPSDK_MCUS -DTARGET_KPSDK_CODE -DTARGET_MCU_K64F -DTARGET_FRDM -DTOOLCHAIN_GCC_ARM -DTOOLCHAIN_GCC -D__CORTEX_M4 -DARM_MATH_CM4 -D__FPU_PRESENT=1 -DMBED_BUILD_TIMESTAMP=1435855534.71 -D__MBED__=1 -DCPU_MK64FN1M0VMD12 -DFSL_RTOS_MBED -DTARGET_FF_ARDUINO 
	LD_FLAGS = $(CPU) -Wl,--gc-sections --specs=nano.specs -u _printf_float -u _scanf_float -Wl,--wrap,main -Wl,-Map=$(TARGET)\$(PROJECT).map,--cref
else
	$(error TARGET is not recognized. Please check the value passed in)
endif

DEPS = $(OBJECTS:.o=.d)

#
# Build tools
#

AS      = "$(GCC_BIN)arm-none-eabi-as"
CC      = "$(GCC_BIN)arm-none-eabi-gcc"
CPP     = "$(GCC_BIN)arm-none-eabi-g++"
LD      = "$(GCC_BIN)arm-none-eabi-gcc"
OBJCOPY = "$(GCC_BIN)arm-none-eabi-objcopy"
OBJDUMP = "$(GCC_BIN)arm-none-eabi-objdump"
SIZE    = "$(GCC_BIN)arm-none-eabi-size"

ifeq ($(DEBUG), 1)
    CC_FLAGS += -DDEBUG -O0
else
    CC_FLAGS += -DNDEBUG -Os
endif

#
# Recipes
#

.PHONY: all clean lst size

all: ${TARGET} $(TARGET)\$(PROJECT).bin $(TARGET)\$(PROJECT).hex $(TARGET)\$(PROJECT).lst $(TARGET)\$(PROJECT).disasm size

# Conditionals (ifeq/ifneq) are bugged on Windows. Instead, we'll just ensure the directory exists and remove it unconditionally.
clean: ${TARGET}
	@rmdir /q /s $(TARGET)

# Ensures the target directory has been created.
${TARGET}:
	@mkdir $@

$(TARGET)\\%.o: %.s
	$(AS) $(CPU) -o $@ $<

$(TARGET)\\%.o: %.c
	$(CC) $(CC_FLAGS) $(CC_SYMBOLS) -std=gnu99 $(INCLUDE_PATHS) -o $@ $<

$(TARGET)\\%.o: %.cpp
	$(CPP) $(CC_FLAGS) $(CC_SYMBOLS) -std=gnu++98 -fno-rtti $(INCLUDE_PATHS) -o $@ $<

$(TARGET)\$(PROJECT).elf: $(OBJECTS) $(SYS_OBJECTS)
	$(LD) $(LD_FLAGS) -T$(LINKER_SCRIPT) $(LIBRARY_PATHS) -o $@ $^ $(LIBRARIES) $(LD_SYS_LIBS) $(LIBRARIES) $(LD_SYS_LIBS)

$(TARGET)\$(PROJECT).bin: $(TARGET)\$(PROJECT).elf
	$(OBJCOPY) -O binary $< $@

$(TARGET)\$(PROJECT).hex: $(TARGET)\$(PROJECT).elf
	@$(OBJCOPY) -O ihex $< $@

$(TARGET)\$(PROJECT).lst: $(TARGET)\$(PROJECT).elf
	@$(OBJDUMP) -Sdh $< > $@

$(TARGET)\$(PROJECT).disasm: $(TARGET)\$(PROJECT).elf
	@$(OBJDUMP) -D $< > $@

size: $(TARGET)\$(PROJECT).elf
	@echo Size report...
	$(SIZE) $<
