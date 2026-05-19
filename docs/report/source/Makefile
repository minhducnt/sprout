MAIN = main
export PATH := /Library/TeX/texbin:$(PATH)
LATEX = xelatex
BIBTEX = bibtex

.PHONY: all pdf clean

all: pdf

pdf:
	$(LATEX) -interaction=nonstopmode $(MAIN).tex
	$(BIBTEX) $(MAIN)
	$(LATEX) -interaction=nonstopmode $(MAIN).tex
	$(LATEX) -interaction=nonstopmode $(MAIN).tex

clean:
	rm -f $(MAIN).{aux,bbl,bcf,blg,log,out,toc,lof,lot,run.xml}
