a.out: driver.o lex.yy.o errormsg.o util.o
	cc -g driver.o lex.yy.o errormsg.o util.o

driver.o: driver.c tokens.h errormsg.h util.h
	cc -g -c driver.c

errormsg.o: errormsg.c errormsg.h util.h
	cc -g -c errormsg.c

lex.yy.o: lex.yy.c tokens.h errormsg.h util.h
	cc -g -c lex.yy.c

lex.yy.c: tiger.lex
	lex tiger.lex

util.o: util.c util.h
	cc -g -c util.c

clean: 
	rm -f a.out *.o lex.yy.*

all-tests := $(addsuffix .test, $(notdir $(basename $(wildcard ../testcases/*.tig))))

test: $(all-tests)

%.test: ../testcases/%.tig
	mkdir -p testoutput
	./a.out $< > testoutput/$@
