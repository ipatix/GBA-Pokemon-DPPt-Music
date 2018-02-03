AS = arm-none-eabi-as
AR = arm-none-eabi-ar

BIN_FILES = $(sort $(wildcard Collections/*.bin))
OBJ_FILES = $(addprefix OBJ/,$(notdir $(BIN_FILES:.bin=.o)))

all: sample.a
	

.PHONY: clean
clean:
	rm -f OBJ/*.o sample.a

S/%.s: Collections/%.bin
	BIN2ASM $< $@

OBJ/%.o: S/%.s
	$(AS) $< -o $@

sample.a: $(OBJ_FILES)
	$(AR) rcs $@ $^
