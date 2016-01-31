THESIS = szablon_pracy_dyplomowej
SRC_FILES = 0_strona_tytulowa 1_wstep 2_teoria 3_technologie \
            4_badania 5_podsumowanie a_cd
STYLE = praca_dyplomowa.sty
BIBLIOGRAPHY = bibliografia
OTHER_FILES = Makefile korekta.sh images
WEB_SOURCES = web

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
		$(SRC_FILES:%=%.tex) $(STYLE) $(BIBLIOGRAPHY).bib \
	    $(OTHER_FILES)

web-sources:
	grep '\\url{.*}' $(BIBLIOGRAPHY).bib | sed 's/^.*\\url{\(.*\)}.*$$/\1/' | \
	wget --page-requisites --convert-links --adjust-extension --span-hosts \
		 --directory-prefix=$(WEB_SOURCES) --input-file=-

clean:
	rm -rf $(THESIS).aux
	rm -rf $(THESIS).bbl
	rm -rf $(THESIS).blg
	rm -rf $(THESIS).log
	rm -rf $(THESIS).out
	rm -rf $(THESIS).pdf
	rm -rf $(THESIS).toc
	rm -rf $(THESIS).lof
	rm -rf $(THESIS).lot
	rm -rf $(THESIS).lol
	rm -rf $(THESIS).tar.gz
	rm -rf texput.log
	rm -rf $(WEB_SOURCES)
