FC = gfortran -ffixed-line-length-none
FFLAGS = -O -g
NR = nr/
CFLAGS = ${FFLAGS} -I$(NR)/include

SUBS = sacio.o fft.o Complex.o radiats.o radpmt.o butstsub.o grid3d.o
SRC_INV = cap

all: $(SRC_INV) fault
	rm *.o

$(SRC_INV): %:%.o $(SUBS)
	$(LINK.f) -o cap $@.o $(SUBS) $(FGCCLIB) -L$(NR)/lib -lnrc

fault: fault.c
	$(LINK.c) -o fault fault.c -lm

cap_dir.o: cap.c
	$(COMPILE.c) -DDIRECTIVITY -o $@ $<

#fmap: fmap.o
#	$(LINK.f) -o $@ $@.o $(FGCCLIB)

clean:
	rm *.o
