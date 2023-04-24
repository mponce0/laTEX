#####################################################################
#
#  Makefile for Latex compilation
#
#  Includes:
#	- auto-detection of BIBliography files and auto compilation.
#	- (soft) _clean_ rule to remove aux/intermediate files.
#	- _hardclean_ rule to removealdo PDF + aux/intermediate files.
#	- _distribute_ rule for copying/add-commit to repo.
#
#
#  Author: Marcelo Ponce
#
#####################################################################


NAME=myDocument
TARGET=$(NAME).pdf
SOURCE=$(NAME).tex
# name of the PDF file that will be generated
FinalDOC="FinalDoc.pdf"

LATEX=`which pdflatex`
BIBTEX=`which bibtex`

RM=/bin/rm -f

# location of repository where to commit changes in main lecture
REPO="."

# files to clean up
JUNK=.aux .bbl .blg .brf .dvi .log .nav .out .ps .snm .vrb .tex.backup .tex.bak .toc .spl 
AUXfiles=Notes.bib textup.log


.PHONY: clean

all: $(TARGET) #distribute clean 

$(TARGET): $(SOURCE) *tex 
	@$(LATEX) $(SOURCE)
	@$(LATEX) $(SOURCE)
	###
	# bibliography processing based on BIB file presence, instead of just using
	# @bibtex $(NAME)
	# check individual cases of bibliography files
	[[ -f refs.bib && -f biblio.bib ]] && $(BIBTEX) $(NAME) || echo "BIB file not found!"
	# check for any BIB file
	if [[ -f *.bib ]]; then \
		for i in *bib; do \
			if [[ -f $$i ]]; then	\
				 $(BIBTEX) $(NAME); \
			fi; \
		done ; \
	fi
	###
	@$(LATEX) $(SOURCE)

clean:
	@for ext in $(JUNK) ; do \
		if [[ -f $(NAME)$$ext ]]; then	\
			$(RM) $(NAME)$$ext ; \
		fi;	\
	done 
	echo "the end"

	#for file in $(AUXfiles); do \
	#	[[ -f $$file ]] && rm -v $$file; \
	#done

realclean: clean
	[[ -f $(NAME).pdf ]] && rm -v $(NAME).pdf
	#@for ext in $(JUNK) .pdf; do \
	#	rm -v $(NAME)$$ext; \
	#	rm -v texput.log; \
	#done

distribute:
	cp -v $(TARGET) $(REPO)/$(FinalDOC)
	cd $(REPO) && git add $(FinalDOC) && git commit -m "Adding/updating $(FinalDOC)" && git push 


#####################################################################
