CC=x86_64-w64-mingw32-gcc
CXX=x86_64-w64-mingw32-g++
WINDRES=x86_64-w64-mingw32-windres

CFLAGS=-g -I ../../../imdisk/inc -municode -DUNICODE -D_UNICODE -DAIMAPI_EXPORTS
#CFLAGS=-I ../../../imdisk/inc -municode -DUNICODE -D_UNICODE -D__in -D__out -D__inout -D__deref
LFLAGS=-L../../API/aimapi/x64 -L../aimapi -laimapi -lntdll -lshell32 -lversion -lnewdev -lsetupapi -Bdynamic -limdisk


.PHONY: all
all: aim_ll.exe

.PHONY: clean
clean:
	rm -rf *.o *.exe

# ../aimapi/aimapi.o ../aimapi/debugmsg.o ../aimapi/drvsetup.o
aim_ll.exe: aimcmd.o drvsetup.o aimcmdres.o
	$(CXX) -o $@ $^ $(LFLAGS) $(CFLAGS)

%res.o: %.rc
	$(WINDRES) -o $@ $<

%.o: %.cpp
	$(CXX) -c -o $@ $< $(CFLAGS)

%.o: %.c
	$(CC) -c -o $@ $< $(CFLAGS)
