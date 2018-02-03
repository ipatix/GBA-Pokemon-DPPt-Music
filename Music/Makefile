AS = arm-none-eabi-as
AR = arm-none-eabi-ar
M_FLAGS = -V080 -E -P000 -R000
FIX_FLAGS = modscale=0,5

MID_FILES = $(sort $(wildcard MID/*.mid))
OBJ_FILES = $(addprefix OBJ/,$(notdir $(MID_FILES:.mid=.o)))

all: music.a
	

.PHONY: clean
clean:
	rm -f OBJ/*.o music.a

MID_FINAL/%.mid: MID/%.mid
	midfix4agb $< $@ $(FIX_FLAGS)

S_FINAL/%.s: MID_FINAL/%.mid
	mid2agb $< $@ $(M_FLAGS)

OBJ/%.o: S_FINAL/%.s
	$(AS) $< -o $@

music.a: $(OBJ_FILES)
	$(AR) rcs $@ $^
