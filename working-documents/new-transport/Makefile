XML2RFC := xml2rfc
TARGET1 := draft-ietf-alto-new-transport
TARGET2 := draft-ietf-alto-new-transport-push
OPEN := gnome-open

all: $(TARGET1).txt $(TARGET2).txt 

$(TARGET1).txt: $(TARGET1).xml
	$(XML2RFC) -N $(TARGET1).xml

$(TARGET2).txt: $(TARGET2).xml
	$(XML2RFC) -N $(TARGET2).xml
	

clean:
	rm -f *.pdf *.dvi *.aux *.log *.bbl *.blg

