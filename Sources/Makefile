
#STYLESHEET=/home/lou/Public/TEIslides/Remark/tei2md.xsl
STYLESHEET=../teislidy.xsl

# Makefile
# needs to be run from Sources directory 
# assumes that folders Travaux and Diapos exist
ECHO=

HTMLSLIDES= \
	../programme \
	introductionXML \
	teiHeader \
	apparatCritique \
	transcriptionManuscrit \
	notesIndexations

EXERCISES= \
	ex01-analyse \
	ex02-oxygen \
	ex03-transcr 
#	ex03-roma \
#	ex05-header \
#	ex06-msdesc \
#	ex12-xslt


DIAPOS= \
	01-principes \
	richessesTEI \
	teiHeader \
	msdesc \
	xsltNuls \
	outils \
	teiCommunity

default: exercises htmlslides pdfslides


htmlslides: 
	for f in $(HTMLSLIDES); do echo $$f; \
	saxon -o:../Diapos/$$f.html $$f.xml $(STYLESHEET); \
	done; 


exercises:
	for i in $(EXERCISES) ; do \
		teitopdf $$i.xml ; \
		mv $$i.xml.pdf ../Travaux/$$i.pdf; \
	done

slides: pdfslides htmlslides

pdfslides:  
	for i in $(DIAPOS) ; do \
		teitoslides --profile=tei $$i.xml; \
		mv $$i.xml.slides ../Diapos/$$i.pdf; \
	done


clean:
	-rm -f *.aux
	-rm -f *.log
	-rm -f *.nav
	-rm -f *.out
	-rm -f *.snm
	-rm -f *.tex
	-rm -f *.toc
	-rm -f *.vrb
	-rm -f *.eps *.dvi
	-rm -f *.xhtml
	-rm -f *~


