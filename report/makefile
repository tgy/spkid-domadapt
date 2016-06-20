MD_FILES=abstract \
	 domain-mismatch \
	 compensation-techniques \
	 whiteners-library \
	 dicn \
	 evaluation \
	 results

all:
	for f in ${MD_FILES}; do pandoc $$f.md -o $$f.tex; done
	pdflatex src
	makeglossaries src
	bibtex src
	pdflatex src
	pdflatex src

clean:
	for f in ${MD_FILES}; do rm -f $$f.tex; rm -f $$f.aux; done
	rm -f *.toc *.aux *.gls *.glo *.glg *.alg *.acn *xdy *.log *.acr *.out *.blg *.bbl
