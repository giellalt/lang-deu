# ****************************************************************** #
# This is a makefile that builds the morphological parser for German #
# ****************************************************************** #

# The file builds a DEU parser based upon twolc.

# This is the ultimate goal (for the initial goal, read from the bottom of the file).


XFST = xfst #-utf8
LEXC = lexc #-utf8
TWOLC = twolc #-utf8

ifeq (victorio.uit.no, $(shell hostname))
XFST = /opt/sami/xerox/c-fsm/ix86-linux2.6-gcc3.4/bin/fst -utf8
LEXC = /opt/sami/xerox/bin/lexc -utf8
TWOLC = /opt/sami/xerox/bin/twolc -utf8
endif




# Here we build the final generator , an inverted transducer of the analyzer.
# It is dependent upon deu.save (and not upon deu.fst, we don't want to generate
# Was, only was.
# "invert net" means that all a:b are changed to b:a, which is what we want.
# usage for the resulting file: lookup -flags mbTT -utf8 bin/ideu.fst
# and then feed winken+V+Ind+Sg1 to get winke etc.

ideu.fst: ../bin/ideu.fst
../bin/ideu.fst: ../bin/deu.fst
	@echo
	@echo "*** Building the inverse ideu.fst ***"
	@echo
	@printf "load ../bin/deu.save \n\
	invert net \n\
	save stack ../bin/ideu.fst \n\
	quit \n" > ../../tmp/ideu-fst-script
	$(XFST) < ../../tmp/ideu-fst-script
	@rm -f ../../tmp/ideu-fst-script


# This goal is to build the final analyser. It depends, indirectly, on all the files.
# what we do is that we put the transducers after each other

deu.fst: ../bin/deu.fst
../bin/deu.fst: ../bin/deu.save ../bin/caseconv.fst ../bin/tok.fst 
	@echo
	@echo "*** Building deu.fst ***" ;
	@echo
	@printf "read regex [[@\"../bin/deu.save\"] .o. \
	[@\"../bin/caseconv.fst\"]] ; \n\
	save stack ../bin/deu.fst \n\
	quit \n" > ../../tmp/deu-fst-script
	$(XFST) < ../../tmp/deu-fst-script
	@rm -f ../../tmp/deu-fst-script


# This minor goal is to build the caseconv.fst file (for Was vs. was)
# It depends on case.regex, and only upon that.

caseconv.fst: ../bin/caseconv.fst
../bin/caseconv.fst: case.regex
	@echo
	@echo "*** Building caseconv.fst ***" ;
	@echo
	@printf "read regex < case.regex \n\
	save stack ../bin/caseconv.fst \n\
	quit \n" > ../../tmp/caseconv-script
	$(XFST) < ../../tmp/caseconv-script
	@rm -f ../../tmp/caseconv-script


# Another goal is to build a preprocessor (also known as tokenizer).
# This goal depends on tok.txt
# We actually don't use tok.fst so much, we use preprocess, but tok.txt
# is here, anyway, ready for use. Usage (standing in deu/):
# cat text.txt | tokenize bin/tok.fst | lookup ...
# Instead of
# cat text.txt | preprocess --abbr=bin/abbr.txt| lookup ...
# But then, we never made the german abbr list.

tok.fst: ../bin/tok.fst
../bin/tok.fst: tok.txt
	@echo
	@echo "*** Building the tokenizer tok.fst ***" ;
	@echo
	@printf "source tok.txt \n\
	save stack ../bin/tok.fst \n\
	quit \n" > ../../tmp/tok-script
	$(XFST) < ../../tmp/tok-script
	@rm -f ../../tmp/tok-script


# The next, or second, goal is to build deu.save
# This goal depends on a bunch of lexicon files and upon the twol file from
# the first goal below (twol-deu.bin, that is).

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
	$(LEXC) < ../../tmp/deu-lex-save-script
	rm -f ../../tmp/deu-lex-save-script

# The initial goal is to build twol-deu.bin
# This goal depends on twol-deu.txt


twol-deu.bin: ../bin/twol.deu.bin
../bin/twol-deu.bin: twol-deu.txt
	@echo
	@echo "*** Building twol-deu.bin ***" ;
	@echo
	@printf "read-grammar twol-deu.txt \n\
	compile \n\
	save-binary ../bin/twol-deu.bin \n\
	quit \n" > /tmp/twol-deu-script
	$(TWOLC) < /tmp/twol-deu-script
	@rm -f /tmp/twol-deu-script


clean:
	@rm -f ../bin/*.bin ../bin/*.fst ../bin/*.save


