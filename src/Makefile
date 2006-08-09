# This is a makefile that builds the XXX morphological parser
# *****************************************************************
# This is a dummy file. DEU refers to the name of the language, deu to the 
# ISO code of the language, for use in file names.

# This is a preliminary file that builds a DEU parser based upon
# xfst and not twolc.

# Here we build the final generator , an inverted transducer of the analyzer.
# It is dependent upon deu.save



ideu.fst: ../bin/ideu.fst
../bin/ideu.fst: ../bin/deu.fst
	@echo
	@echo "*** Building the inverse ideu.fst ***"
	@echo
	@printf "load ../bin/deu.save \n\
	invert net \n\
	save stack ../bin/ideu.fst \n\
	quit \n" > ../../tmp/ideu-fst-script
	@xfst -utf8 < ../../tmp/ideu-fst-script
	@rm -f ../../tmp/ideu-fst-script


# This goal is to build the final analyser. It depends on all the files.

deu.fst: ../bin/deu.fst
../bin/deu.fst: ../bin/deu.save ../bin/caseconv.fst ../bin/tok.fst 
	@echo
	@echo "*** Building deu.fst ***" ;
	@echo
	@printf "read regex [[@\"../bin/deu.save\"] .o. \
	[@\"../bin/caseconv.fst\"]] ; \n\
	save stack ../bin/deu.fst \n\
	quit \n" > ../../tmp/deu-fst-script
	@xfst -utf8 < ../../tmp/deu-fst-script
	@rm -f ../../tmp/deu-fst-script


# The second goal is to build the caseconv.fst file
# This goal depends on case.regex

caseconv.fst: ../bin/caseconv.fst
../bin/caseconv.fst: case.regex
	@echo
	@echo "*** Building caseconv.fst ***" ;
	@echo
	@printf "read regex < case.regex \n\
	save stack ../bin/caseconv.fst \n\
	quit \n" > ../../tmp/caseconv-script
	@xfst -utf8 < ../../tmp/caseconv-script
	@rm -f ../../tmp/caseconv-script


# Another goal is to build a preprocessor.This goal depends on tok.txt

tok.fst: ../bin/tok.fst
../bin/tok.fst: tok.txt
	@echo
	@echo "*** Building the tokenizer tok.fst ***" ;
	@echo
	@printf "source tok.txt \n\
	save stack ../bin/tok.fst \n\
	quit \n" > ../../tmp/tok-script
	@xfst -utf8 < ../../tmp/tok-script
	@rm -f ../../tmp/tok-script


# The first goal is to build deu-save
# This goal depends on a bunch of lexicon files and upon twol

deu.save: ../bin/deu.save
../bin/deu.save: ../bin/twol-deu.bin deu-lex.txt noun-deu-morph.txt noun-deu-lex.txt \
        adj-deu-lex.txt adv-deu-lex.txt verb-deu-lex.txt verb-deu-morph.txt \
	pron-deu-lex.txt punct-deu-lex.txt numeral-deu-lex.txt \
	pp-deu-lex.txt cc-deu-lex.txt cs-deu-lex.txt interj-deu-lex.txt
	@echo
	@echo "*** Building deu-lex.save ***" ;
	@echo
	printf "compile-source deu-lex.txt noun-deu-morph.txt noun-deu-lex.txt \
        adj-deu-lex.txt adv-deu-lex.txt verb-deu-lex.txt verb-deu-morph.txt \
	pron-deu-lex.txt punct-deu-lex.txt numeral-deu-lex.txt \
	pp-deu-lex.txt cc-deu-lex.txt cs-deu-lex.txt interj-deu-lex.txt \n\
	read-rules ../bin/twol-deu.bin \n\
	compose-result \n\
	save-result ../bin/deu.save \n\
	quit \n" > ../../tmp/deu-lex-save-script
	@lexc -utf8 < ../../tmp/deu-lex-save-script
	rm -f ../../tmp/deu-lex-save-script

# The second goal is to build xfst-deu.bin
# This goal depends on xfst-deu.txt


twol-deu.bin: ../bin/twol.deu.bin
../bin/twol-deu.bin: twol-deu.txt
	@echo
	@echo "*** Building twol-deu.bin ***" ;
	@echo
	@printf "read-grammar twol-deu.txt \n\
	compile \n\
	save-binary ../bin/twol-deu.bin \n\
	quit \n" > /tmp/twol-deu-script
	@twolc -utf8 < /tmp/twol-deu-script
	@rm -f /tmp/twol-deu-script


clean:
	@rm -f ../bin/*.bin ../bin/*.fst ../bin/*.save


