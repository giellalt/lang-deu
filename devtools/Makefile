all: test.xfst

check: test.pass.out test.fail.out

test.xfst: test.lexc
	printf "read lexc $^\n\
	        save stack $@\n\
	        quit\n" \
		| xfst

test.%.out: test.%.txt test.xfst
	cat $< | lookup test.xfst > $@

clean:
	rm -f *.xfst *.out
