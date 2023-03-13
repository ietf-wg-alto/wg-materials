XML2RFC := xml2rfc
TARGET  := draft-yang-alto-multi-domain
VERSION := 00

all: $(TARGET)-$(VERSION).txt

$(TARGET)-$(VERSION).txt: $(TARGET).xml
	$(XML2RFC) -N $(TARGET).xml

clean:
	rm -f *.pdf *.dvi *.aux *.log *.bbl *.blg

