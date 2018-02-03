CC = arm-none-eabi-gcc
LD = arm-none-eabi-ld
OCP = arm-none-eabi-objcopy
NM = arm-none-eabi-nm
MAKE = make

TARGET_OFFSET = 0x09001000

LD_FLAGS = --gc-sections --section-start=.rodata=$(TARGET_OFFSET)

BINARY = build.bin
OBJECT = build.o

MUSIC_AR = ../Music/music.a
SMPL_AR = ../Samples/sample.a
VOICE_AR = ../Voicegroup/voice.a
LIST_AR = ../SongTable/songlist.a


all: $(BINARY)
	

.PHONY: clean
clean:
	$(MAKE) -C $(dir $(MUSIC_AR)) clean
	$(MAKE) -C $(dir $(SMPL_AR)) clean
	$(MAKE) -C $(dir $(VOICE_AR)) clean
	$(MAKE) -C $(dir $(LIST_AR)) clean

.PHONY: $(MUSIC_AR)
$(MUSIC_AR):
	$(MAKE) -C $(dir $@) all

.PHONY: $(SMPL_AR)
$(SMPL_AR):
	$(MAKE) -C $(dir $@) all

.PHONY: $(VOICE_AR)
$(VOICE_AR):
	$(MAKE) -C $(dir $@) all

.PHONY: $(LIST_AR)
$(LIST_AR):
	$(MAKE) -C $(dir $@) all

$(BINARY): $(OBJECT)
	$(OCP) -O binary $< $@

$(OBJECT): $(LIST_AR) $(MUSIC_AR) $(SMPL_AR) $(VOICE_AR)
	$(LD) $(LD_FLAGS) -o $@ --start-group $^ --end-group
	$(NM) $@ -g > content.txt
