MD_FILES=abstract \
	 domain-mismatch \
	 compensation-techniques \
	 whiteners-library \
	 dicn \
	 evaluation \
	 results

all:
	for f in ${MD_FILES}; do pandoc $$f.md -o $$f.tex; done
	pdflatex src.tex
	makeglossaries src
	pdflatex src.tex

clean:
	for f in ${MD_FILES}; do rm -f $$f.tex; rm -f $$f.aux; done
	rm -f *.toc *.aux *.gls *.glo *.glg *.alg *.acn *xdy *.log *.acr *.out
