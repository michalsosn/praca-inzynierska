THESIS = szablon_pracy_dyplomowej
SRC_FILES = 0_strona_tytulowa 1_wstep 2_teoria 3_nowa_teoria \
            5_badania 6_podsumowanie a_latex b_cd
STYLE = praca_dyplomowa.sty
BIBLIOGRAPHY = bibliografia
OTHER_FILES = Makefile korekta.sh

.PHONY: all clean zip

all: $(THESIS).pdf

zip: $(THESIS).tar.gz

$(THESIS).pdf: $(THESIS).tex  $(SRC_FILES:%=%.tex) $(STYLE) $(THESIS).bbl
	pdflatex $(THESIS).tex
	pdflatex $(THESIS).tex

$(THESIS).bbl: $(BIBLIOGRAPHY).bib
	pdflatex $(THESIS).tex
	bibtex $(THESIS)

$(THESIS).tar.gz: $(THESIS).pdf
	tar czf $(THESIS).tar.gz $(THESIS).pdf $(THESIS).tex \
		$(SRC_FILES:%=%.tex) $(STYLE) $(BIBLIOGRAPHY).bib $(OTHER_FILES)

clean:
	rm -rf $(THESIS).aux
	rm -rf $(THESIS).bbl
	rm -rf $(THESIS).blg
	rm -rf $(THESIS).log
	rm -rf $(THESIS).out
	rm -rf $(THESIS).pdf
	rm -rf $(THESIS).toc
	rm -rf $(THESIS).tar.gz
	rm -rf texput.log
