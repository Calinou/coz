ROOT 		 := ..
TARGETS  := libcoz.so
LIBS     := dl rt pthread elf++ dwarf++
CXXFLAGS := --std=c++0x -g -O2 -fPIC -I$(ROOT)/include -I.

include $(ROOT)/common.mk

check:: libcoz.so
	printf "int main(int argc, char *argv[])\n{\nreturn (0);\n}\n" > x.c
	gcc -g -o x x.c || ( $(RM) x x.c ; exit 1)
	../coz run --- ./x
	if grep -q time= profile.coz; then echo success: coz profiler ran as it should.; fi
	$(RM) -f x.c x profile.coz
