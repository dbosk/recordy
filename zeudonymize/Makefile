.PHONY: all
all: zeudonymize.pdf

LATEXFLAGS+=	-shell-escape

zeudonymize.pdf: zeudonymize.tex zeudonymize.bib
zeudonymize.pdf: abstract.tex
zeudonymize.pdf: old_format.txt new_format.txt

zeudonymize.tex: zeudonymize.nw


.PHONY:
all: zeudonymize

zeudonymize.py: zeudonymize.nw
zeudonymize: zeudonymize.py
	cp $^ $@
	chmod +x $@


.PHONY: test
test: zeudonymize
	./zeudonymize -t old_format.txt -p OldStudent
	cat old_format-pseudonymized.txt
	./zeudonymize -t new_format.txt -p NewStudent
	cat new_format-pseudonymized.txt


.PHONY: clean
clean:
	${RM} zeudonymize zeudonymize.py zeudonymize.pdf zeudonymize.tex


PKG_NAME-main= 			zeudonymize
PKG_INSTALL_FILES-main=	zeudonymize
PKG_PREFIX-main?= 		/usr/local
PKG_INSTALL_DIR-main=	/bin
PKG_TARBALL_FILES-main= ${PKG_FILES-main} Makefile


INCLUDE_MAKEFILES=../makefiles
include ${INCLUDE_MAKEFILES}/tex.mk
include ${INCLUDE_MAKEFILES}/noweb.mk
include ${INCLUDE_MAKEFILES}/pkg.mk
