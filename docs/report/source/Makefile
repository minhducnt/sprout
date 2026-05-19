# Sprout internship report — from this directory:
#
#   make export     clean + build PDF + copy to ../exports/  (submission workflow)
#   make pdf        build main.pdf only (keeps aux files)
#   make diagrams   refresh Mermaid PNGs in images/
#   make clean      remove LaTeX build artefacts
#
# Equivalent to:
#   make clean && make pdf && cp main.pdf ../exports/sprout-internship-final-report.pdf
# is: make export

MAIN = main
export PATH := /Library/TeX/texbin:$(PATH)
LATEX = xelatex
BIBTEX = bibtex
MMDC = npx --yes @mermaid-js/mermaid-cli@11
DIAGRAMS = diagrams/system-overview.mmd diagrams/user-flow.mmd
DIAGRAM_PNGS = images/system-overview.png images/user-flow.png

EXPORT = ../exports/sprout-internship-final-report.pdf

.PHONY: all pdf export diagrams clean clean-all

all: export

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
	$(LATEX) -interaction=nonstopmode $(MAIN).tex

export: clean pdf
	@mkdir -p ../exports
	cp $(MAIN).pdf $(EXPORT)
	@echo "Exported: $(EXPORT)"

clean:
	rm -f $(MAIN).{aux,bbl,bcf,blg,log,out,toc,lof,lot,run.xml}

clean-all: clean
	rm -f $(DIAGRAM_PNGS)
