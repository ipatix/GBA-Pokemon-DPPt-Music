AS = arm-none-eabi-as
AR = arm-none-eabi-ar

S_FILES = $(sort $(wildcard *.s))
OBJ_FILES = $(S_FILES:.s=.o)

all: voice.a
	

.PHONY: clean
clean:
	rm -f *.o voice.a

%.o: %.s
	$(AS) $< -o $@

voice.a: $(OBJ_FILES)
	$(AR) rcs $@ $^
