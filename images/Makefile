#===STRING MANIPULATIONS===
SVGS = $(shell find . -name '*.svg')
DIAS = $(shell find . -name '*.dia')
GIFS = $(shell find . -name '*.gif')
PGMS = $(shell find . -name '*.pgm')

SVGS2PDF = $(patsubst %.svg,%.pdf,$(SVGS))
DIAS2PDF = $(patsubst %.dia,%.pdf,$(DIAS))
GIFS2PDF = $(patsubst %.gif,%.png,$(GIFS))
PGMS2PDF = $(patsubst %.pgm,%.png,$(PGMS))

ALLIMAGES = $(DIAS2PDF) $(SVGS2PDF) $(GIFS2PDF) $(PGMS2PDF)
#==========================

#===CONVERSIONS===
%.png: %.gif
	convert $< $@

%.png: %.pgm
	convert $< $@

%.pdf: %.svg
	inkscape --without-gui --export-pdf=$@ $<

%.svg: %.dia
	dia -t svg $< -e $@
#=================

all: $(ALLIMAGES)

clean:
	rm -f $(ALLIMAGES)

.PHONY: all clean
