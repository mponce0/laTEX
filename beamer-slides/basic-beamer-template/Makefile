NAME=lecture_wrapper
TARGET=$(NAME).pdf
SOURCE=$(NAME).tex
# name of the PDF file that will be generated
LECTURE="lecture_SLIDES.pdf"

# location of repository where to commit changes in main lecture
REPO="."

# files to clean up
JUNK=.aux .bbl .blg .brf .dvi .log .nav .out .ps .snm .vrb .tex.backup .tex.bak .toc Notes.bib .spl



.PHONY: clean

all: $(TARGET) #distribute clean 

$(TARGET): $(SOURCE) *tex 
	@pdflatex $(SOURCE)
	#@bibtex $(NAME)
	#@pdflatex $(SOURCE)
	@pdflatex $(SOURCE)

clean:
	@for ext in $(JUNK); do \
		rm -v $(NAME)$$ext; \
		rm -v texput.log; \
	done

hardclean:
	@for ext in $(JUNK) .pdf; do \
		rm -v $(NAME)$$ext; \
		rm -v texput.log; \
	done

distribute:
	cp -v $(TARGET) $(REPO)/$(LECTURE)
	cd $(REPO) && git add $(LECTURE) && git commit -m "Adding $(LECTURE)" && git push 
