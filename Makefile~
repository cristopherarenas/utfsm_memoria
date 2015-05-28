#NOMBRE=$(shell grep -H \\documentclass *.tex | cut -d: -f1 | cut -d. -f1)
NOMBRE=thesis
SHELL=/bin/bash

all: images $(NOMBRE).pdf

$(NOMBRE).pdf:$(NOMBRE).tex include/*.tex
	@echo "   Making pdf for first time..."
	pdflatex -halt-on-error $(NOMBRE).tex #> .my_log || (cat .my_log && rm .my_log && exit 1)
	echo "   Making bibtex..."
	bibtex $(NOMBRE)
	@echo "   Re-making dvi for satisfying references..."
	pdflatex $(NOMBRE).tex #&> /dev/null
	pdflatex $(NOMBRE).tex #&> /dev/null

clean:
	-rm -f $(NOMBRE).{aux,toc,log,tmp,dvi,idx,ilg,ind,out,bbl,blg,lol,lof,lot} .my_log include/*.aux

distclean: clean
	-make -C images clean
	-rm -f $(NOMBRE).pdf

images:
	-make -C images

.PHONY: all clean distclean images
