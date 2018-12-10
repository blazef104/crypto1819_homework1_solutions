# -*- mode: Makefile -*-
SRC=homework1.tex
FILENAME=$(SRC:.tex=)
FMT=pdf
PDF=$(SRC:.tex=.pdf)
TOOL=rubber --pdf $(OPT)
TODOS=$(shell grep -i todo *.tex | grep -c -v newcommand)
DATETAG=$(shell date '+%Y_%m_%d_%H%M%S')


################################################################################


$(PDF):  $(SRC) $(DEPEND) TODOS
	@${TOOL} $(SRC) #%$(@:.pdf=.tex)
#	http://www.unix.com/shell-programming-and-scripting/55661-how-get-number-pages-pdf-file.html
	###########################
	@echo "The current PDF has $$(pdftk $(BUILDIR)/$(FILENAME).pdf dump_data output | grep NumberOfPages | cut -d ' ' -f 2) pages"

TODOS:
	@if [ $(TODOS) -eq "0" ]; then echo "++++ All TODOs fixed! ++++"; fi

	@echo "**** still $(TODOS) TODOs left to fix !!! ****"

clean:
	cd $(BUILDIR)/
	rm -f  *~ *.aux *.blg *.bbl *.log *.bin $PDF
	rm -f *.dvi *.ps *.aux *.log *.bbl *.blg *.bcf *~ *.out *.dia~ *.bak *.nlo
#	rm -f figures/*~
#	rm -f figures/*-eps-converted-to.pdf
#	rm -f paper_diff.* paper_old.*
# rm -f generate-*.tex


view:
	evince $(PDF) &

spellcheck:
	for file_tex in `ls *.tex`; do aspell check --lang=en_US $${file_tex}; done
