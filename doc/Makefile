###############################################################################
#
# 	Makefile for jnuthesis
#
# 	Copyright (C) 2013-2015 Haixing Hu,
#   Department of Computer Science and Technology, Nanjing University.
#
#	Home Page of the Project: http://haixing-hu.github.io/nju-thesis/
#
###############################################################################

PACKAGE=jnuthesis
BST_FILE=gbt7714-2005-jnu.bst
BST_URL=https://raw.githubusercontent.com/Haixing-Hu/GBT7714-2005-BibTeX-Style/master/gbt7714-2005.bst
SOURCES=$(PACKAGE).dtx $(PACKAGE).ins
CLS=$(PACKAGE).cls $(PACKAGE).cfg dtx-style.sty dtklogos.sty
SAMPLE_D=phd
SAMPLE_M=master
SAMPLE_MB=master-blind
SAMPLE_MP=master-p
SAMPLE_MPB=master-p-blind
SAMPLE_B=bachelor
SAMPLE_BC=bachelor-coursework
SAMPLE_BD=bachelor-design
SAMPLE_BR=bachelor-related
SAMPLEBIB_D=$(SAMPLE_D).bib
SAMPLEBIB_M=$(SAMPLE_M).bib
SAMPLEBIB_MB=$(SAMPLE_M).bib
SAMPLEBIB_MP=$(SAMPLE_M).bib
SAMPLEBIB_MPB=$(SAMPLE_M).bib
SAMPLEBIB_B=$(SAMPLE_B).bib
PREAMBLE_M=$(SAMPLE_M)-preamble
CONTENTS_M=$(SAMPLE_M)-contents
COMMON_B=$(SAMPLE_B)-common
INSTITUTE_NAME=jnuname.eps jnuname.pdf
TEXMFLOCAL=$(shell get_texmf_dir.sh)

.PHONY: all clean cls doc phd master masterblind masterpro masterproblind bachelor bachelorcoursework bachelordesign bachelorrelated

all: bst cls doc phd master masterblind masterpro masterproblind bachelor bachelorcoursework bachelordesign bachelorrelated

###### update bst file
bst:  $(BST_FILE)

$(BST_FILE):
	curl $(BST_URL) -o $(BST_FILE)

###### generate cls/cfg
cls:  $(CLS)

$(CLS): $(SOURCES)
	latex $(PACKAGE).ins

###### generate doc

doc: $(PACKAGE).pdf

$(PACKAGE).pdf: $(CLS)
	xelatex $(PACKAGE).dtx
	makeindex -s gind.ist -o $(PACKAGE).ind $(PACKAGE).idx
	xelatex $(PACKAGE).dtx
	xelatex $(PACKAGE).dtx

###### for sample

phd:	 $(SAMPLE_D).pdf

$(SAMPLE_D).pdf: $(CLS) $(INSTITUTE_NAME) $(BST_FILE) $(SAMPLE_D).tex $(SAMPLEBIB_D)
	xelatex $(SAMPLE_D).tex
	bibtex $(SAMPLE_D)
	xelatex $(SAMPLE_D).tex
	xelatex $(SAMPLE_D).tex


master:	 $(SAMPLE_M).pdf

$(SAMPLE_M).pdf: $(CLS) $(INSTITUTE_NAME) $(BST_FILE) $(SAMPLE_M).tex $(PREAMBLE_M).tex $(CONTENTS_M).tex $(SAMPLEBIB_M)
	xelatex $(SAMPLE_M).tex
	bibtex $(SAMPLE_M)
	xelatex $(SAMPLE_M).tex
	xelatex $(SAMPLE_M).tex


masterblind:	 $(SAMPLE_MB).pdf

$(SAMPLE_MB).pdf: $(CLS) $(INSTITUTE_NAME) $(BST_FILE) $(SAMPLE_MB).tex $(PREAMBLE_M).tex $(CONTENTS_M).tex $(SAMPLEBIB_MB)
	xelatex $(SAMPLE_MB).tex
	bibtex $(SAMPLE_MB)
	xelatex $(SAMPLE_MB).tex
	xelatex $(SAMPLE_MB).tex


masterpro:	 $(SAMPLE_MP).pdf

$(SAMPLE_MP).pdf: $(CLS) $(INSTITUTE_NAME) $(BST_FILE) $(SAMPLE_MP).tex $(PREAMBLE_M).tex $(CONTENTS_M).tex $(SAMPLEBIB_MP)
	xelatex $(SAMPLE_MP).tex
	bibtex $(SAMPLE_MP)
	xelatex $(SAMPLE_MP).tex
	xelatex $(SAMPLE_MP).tex


masterproblind:	 $(SAMPLE_MPB).pdf

$(SAMPLE_MPB).pdf: $(CLS) $(INSTITUTE_NAME) $(BST_FILE) $(SAMPLE_MPB).tex $(PREAMBLE_M).tex $(CONTENTS_M).tex $(SAMPLEBIB_MP)
	xelatex $(SAMPLE_MPB).tex
	bibtex $(SAMPLE_MPB)
	xelatex $(SAMPLE_MPB).tex
	xelatex $(SAMPLE_MPB).tex


bachelor: $(SAMPLE_B).pdf

$(SAMPLE_B).pdf: $(CLS) $(INSTITUTE_NAME) $(BST_FILE) $(SAMPLE_B).tex $(COMMON_B).tex $(SAMPLEBIB_B)
	xelatex $(SAMPLE_B).tex
	bibtex $(SAMPLE_B)
	xelatex $(SAMPLE_B).tex
	xelatex $(SAMPLE_B).tex


bachelorcoursework: $(SAMPLE_BC).pdf

$(SAMPLE_BC).pdf: $(CLS) $(INSTITUTE_NAME) $(BST_FILE) $(SAMPLE_BC).tex $(COMMON_B).tex $(SAMPLEBIB_B)
	xelatex $(SAMPLE_BC).tex
	bibtex $(SAMPLE_B)
	xelatex $(SAMPLE_BC).tex
	xelatex $(SAMPLE_BC).tex


bachelordesign: $(SAMPLE_BD).pdf

$(SAMPLE_BD).pdf: $(CLS) $(INSTITUTE_NAME) $(BST_FILE) $(SAMPLE_BD).tex $(COMMON_B).tex $(SAMPLEBIB_B)
	xelatex $(SAMPLE_BD).tex
	bibtex $(SAMPLE_B)
	xelatex $(SAMPLE_BD).tex
	xelatex $(SAMPLE_BD).tex


bachelorrelated: $(SAMPLE_BR).pdf

$(SAMPLE_BR).pdf: $(CLS) $(INSTITUTE_NAME) $(BST_FILE) $(SAMPLE_BR).tex
	xelatex $(SAMPLE_BR).tex
	xelatex $(SAMPLE_BR).tex
	xelatex $(SAMPLE_BR).tex


###### install

install: $(SOURCE) $(CLS) $(INSTITUTE_NAME) $(BST_FILE) $(PACKAGE).pdf $(SAMPLE_D).pdf $(SAMPLE_M).pdf $(SAMPLE_MB).pdf $(SAMPLE_B).pdf
	mkdir -p $(TEXMFLOCAL)/tex/latex/jnuthesis
	cp -rvf $(SOURCES) $(CLS) $(INSTITUTE_NAME) $(TEXMFLOCAL)/tex/latex/jnuthesis/
	mkdir -p $(TEXMFLOCAL)/doc/latex/jnuthesis
	cp -rvf $(PACKAGE).pdf $(SAMPLE_D).pdf $(SAMPLE_M).pdf $(SAMPLE_MB).pdf $(SAMPLE_B).pdf $(TEXMFLOCAL)/doc/latex/jnuthesis/
	mkdir -p $(TEXMFLOCAL)/bibtex/bst
	cp -rvf $(BST_FILE) $(TEXMFLOCAL)/bibtex/bst/
	texhash

###### clean

clean:
	-@rm -f \
		*.aux \
		*.bak \
		*.bbl \
		*.blg \
		*.dvi \
		*.glo \
		*.gls \
		*.idx \
		*.ilg \
		*.ind \
		*.ist \
		*.log \
		*.out \
		*.ps \
		*.thm \
		*.toc \
		*.lof \
		*.lot \
		*.loe \
		*.cfg \
		*.cls \
		dtx-style.sty
