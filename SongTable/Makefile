AS = arm-none-eabi-as
AR = arm-none-eabi-ar

S_FILES = $(sort $(wildcard *.s))
OBJ_FILES = $(S_FILES:.s=.o)

all: songlist.a
	

.PHONY: clean
clean:
	rm -f *.o songlist.a

%.o: %.s
	$(AS) $< -o $@

songlist.a: $(OBJ_FILES)
	$(AR) rcs $@ $^
