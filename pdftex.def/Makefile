# $Id: Makefile,v 1.1 2004/09/07 13:14:57 oneiros Exp $

SOURCE		= pdftex
BIN		= $(SOURCE).def
LATEX		= latex
PDFLATEX	= pdflatex
MAKEINDEX	= makeindex

SRCS	= $(SOURCE).dtx $(SOURCE).ins
OBJS	= $(BIN)


##########################################################
# Rules

all : $(BIN)

$(BIN): $(SOURCE).ins $(SOURCE).dtx 
	$(LATEX) $(SOURCE).ins 

# --- auxillirary rules: ---

doc: dvi pdf

$(SOURCE).drv : $(SOURCE).ins $(SOURCE).dtx
	$(LATEX) $(SOURCE).ins 
    
dvi: $(SOURCE).dvi 
$(SOURCE).dvi: $(SOURCE).drv $(SOURCE).dtx
	$(LATEX) $(SOURCE).drv
	$(LATEX) $(SOURCE).drv
	$(MAKEINDEX) -s gind.ist -t $(SOURCE).ind.ilg $(SOURCE).idx
	$(MAKEINDEX) -s gglo.ist -t $(SOURCE).gls.ilg -o $(SOURCE).gls $(SOURCE).glo
	$(LATEX) $(SOURCE).drv

pdf: $(SOURCE).pdf
$(SOURCE).pdf: $(SOURCE).drv $(SOURCE).dtx
	$(PDFLATEX) $(SOURCE).drv
	$(PDFLATEX) $(SOURCE).drv
	$(MAKEINDEX) -s gind.ist -t $(SOURCE).ind.ilg $(SOURCE).idx
	$(MAKEINDEX) -s gglo.ist -t $(SOURCE).gls.ilg -o $(SOURCE).gls $(SOURCE).glo
	$(PDFLATEX) $(SOURCE).drv

clean:
	rm -f *.aux *.log *.ilg *.toc *.gls *.glo *.idx *.ind *.brf *.out *.tpt

realclean: clean
	rm -f *.tex *.drv *.dvi *.pdf

distrib: $(BIN)
