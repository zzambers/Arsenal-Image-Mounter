CC=x86_64-w64-mingw32-gcc
CXX=x86_64-w64-mingw32-g++
WINDRES=x86_64-w64-mingw32-windres

CFLAGS=-g -I ../../../imdisk/inc -municode -DUNICODE -D_UNICODE -DAIMAPI_EXPORTS
# LFLAGS=-L../../../imdisk_source/cpl/amd64 -static-libgcc -static-libstdc++ -limdisk -lntdll -lshell32 -lversion -lnewdev -lsetupapi
LFLAGS=-L../../API/aimapi/x64  -Wl,-R,../../API/aimapi/x64 -lntdll -lshell32 -lversion -lnewdev -lsetupapi -Bdynamic -limdisk
# -D__in -D__out -D__inout -Dinout -D__in_opt -DAIMAPI_EXPORTS

.PHONY: all
all: aimapi.dll

.PHONY: clean
clean:
	rm -rf *.o *.dll *.a


aimapi.dll: aimapi.o debugmsg.o dllmain.o drvsetup.o stdafx.o aimapires.o
	$(CXX) -shared -o $@ $^ -Wl,--out-implib,aimapi.a $(LFLAGS) $(CFLAGS)

%res.o: %.rc
	$(WINDRES) -o $@ $<

%.o: %.cpp
	$(CXX) -c -o $@ $< $(CFLAGS)

%.o: %.c
	$(CC) -c -o $@ $< $(CFLAGS)
