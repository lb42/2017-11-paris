
#STYLESHEET=/home/lou/Public/TEIslides/Remark/tei2md.xsl
STYLESHEET=../teislidy.xsl

# Makefile
# needs to be copied to and run from source directory 
# assumes that folders PDF and Diapos exist
ECHO=

HTMLSLIDES= \
	../programme \
    introductionXML \
	apparatCritique \
	transcriptionManuscrit \
	notesIndexations

EXERCISES= \
	ex01-analyse \
	ex02-oxygen \
	ex03-roma \
	ex05-header \
	ex06-msdesc \
	ex12-xslt

DIAPOS= \
	01-principes \
	richessesTEI \
	teiHeader \
	msdesc \
	xsltNuls \
	outils \
	teiCommunity

default: exercises htmlslides pdfslides

setup:
	mkdir ../PDF ../Diapos

# should empty dir if it exists
# need to copy js and themes to diapos

htmlslides: 
	for f in $(HTMLSLIDES); do echo $$f; \
	saxon -o:../Diapos/$$f.html $$f.xml $(STYLESHEET); \
	done; 


exercises:
	for i in $(EXERCISES) ; do \
		teitopdf $$i.xml ; \
		mv $$i.xml.pdf ../PDF/$$i.pdf; \
	done

slides: pdfslides 

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


validate:
	-for i in $(TALKS) ; do onvdl ../teitalks.nvdl `basename $$i .xml`.xml \
	 | grep -v ': error: unfinished element$$' \
	 | grep -v ': error: unfinished element .* required to finish the element$$'; done

driver:
	cp corpHeaderStart.txt driver.tei;\
		for f in *.xml ; do \
		echo "<xi:include href='$$f'/>" >> driver.tei; \
	done; echo "</teiCorpus>" >> driver.tei


