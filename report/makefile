MD_FILES=abstract domain-mismatch whiteners-library dicn evaluation results

all:
	for f in ${MD_FILES}; do pandoc $$f.md -o $$f.tex; done
	pdflatex src.tex

clean:
	for f in ${MD_FILES}; do rm $$f.tex; rm $$f.aux; done
	rm *.toc
