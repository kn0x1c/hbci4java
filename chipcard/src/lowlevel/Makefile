
DEFINES  = -D__UNIX
INCLUDES = -I../include
WARNINGS = -Wall
# removed "-Werror -pedantic" because of dlsym() typecast problem

CC       = g++
AR       = ar
CFLAGS   = -fPIC $(DEFINES) $(INCLUDES) $(WARNINGS)

SOURCES = atr.cpp \
          bcs.cpp \
          ctapi-tools.cpp \
	  get_challenge.cpp \
	  get_keyinfo.cpp \
	  internal_authenticate.cpp \
	  put_data.cpp \
          read_binary.cpp \
          read_record.cpp \
          select_file.cpp \
          tools.cpp \
	  verify_pin.cpp \
	  modify_pin.cpp \
	  write_record.cpp

OBJECTS = ../../bin/atr.o \
          ../../bin/bcs.o \
          ../../bin/ctapi-tools.o \
	  ../../bin/get_challenge.o \
	  ../../bin/get_keyinfo.o \
	  ../../bin/internal_authenticate.o \
	  ../../bin/put_data.o \
          ../../bin/read_binary.o \
          ../../bin/read_record.o \
          ../../bin/select_file.o \
          ../../bin/tools.o \
	  ../../bin/verify_pin.o \
	  ../../bin/modify_pin.o \
	  ../../bin/write_record.o

.SUFFIXES: .cpp .o

../../bin/%.o: %.cpp
	$(CC) -c -o $@ $(CFLAGS) $<

all: depend ../../bin/libzkachip-lowlevel.a

depend: Makefile.depend

Makefile.depend: $(SOURCES)
	for file in $(SOURCES); do echo -n "../../bin/"; gcc $(CFLAGS) -MM $$file; done >Makefile.depend

../../bin/libzkachip-lowlevel.a: $(OBJECTS)
	$(AR) rcsv $@ $(OBJECTS)

include Makefile.depend
