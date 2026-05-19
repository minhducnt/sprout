MAIN = main
export PATH := /Library/TeX/texbin:$(PATH)
LATEX = xelatex
BIBTEX = bibtex
MMDC = npx --yes @mermaid-js/mermaid-cli@11
DIAGRAMS = diagrams/system-overview.mmd diagrams/user-flow.mmd
DIAGRAM_PNGS = images/system-overview.png images/user-flow.png

.PHONY: all pdf diagrams clean clean-all

all: pdf

diagrams: $(DIAGRAM_PNGS)

images/system-overview.png: diagrams/system-overview.mmd
	$(MMDC) -i $< -o $@ -b transparent

images/user-flow.png: diagrams/user-flow.mmd
	$(MMDC) -i $< -o $@ -b transparent

pdf: diagrams
	$(LATEX) -interaction=nonstopmode $(MAIN).tex
	$(BIBTEX) $(MAIN)
	$(LATEX) -interaction=nonstopmode $(MAIN).tex
	$(LATEX) -interaction=nonstopmode $(MAIN).tex

clean:
	rm -f $(MAIN).{aux,bbl,bcf,blg,log,out,toc,lof,lot,run.xml}

clean-all: clean
	rm -f $(DIAGRAM_PNGS)
