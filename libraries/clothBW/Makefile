ifndef CLOTHBW
CLOTHBW=CLOTHBW

ifndef CLEANFOLDER
CLEANFOLDER=CLOTHBW
endif

R ?= ../..
include $(R)/Makefile-headers/Makefile-header

# the object files to be compiled for this library
CLOTHBW_OBJECTS=clothBW.o clothBWFromObjMesh.o

# the libraries this library depends on
CLOTHBW_LIBS=minivector objMesh sparseMatrix

# the headers in this library
CLOTHBW_HEADERS=clothBW.h clothBWFromObjMesh.h

CLOTHBW_OBJECTS_FILENAMES=$(addprefix $(L)/clothBW/, $(CLOTHBW_OBJECTS))
CLOTHBW_HEADER_FILENAMES=$(addprefix $(L)/clothBW/, $(CLOTHBW_HEADERS))
CLOTHBW_LIB_MAKEFILES=$(call GET_LIB_MAKEFILES, $(CLOTHBW_LIBS))
CLOTHBW_LIB_FILENAMES=$(call GET_LIB_FILENAMES, $(CLOTHBW_LIBS))

include $(CLOTHBW_LIB_MAKEFILES)

all: $(L)/clothBW/libclothBW.a

$(L)/clothBW/libclothBW.a: $(CLOTHBW_OBJECTS_FILENAMES)
	ar r $@ $^; cp $@ $(L)/lib; cp $(L)/clothBW/*.h $(L)/include

$(CLOTHBW_OBJECTS_FILENAMES): %.o: %.cpp $(CLOTHBW_LIB_FILENAMES) $(CLOTHBW_HEADER_FILENAMES)
	$(CXX) $(CXXFLAGS) -c $(TBB_INCLUDE) $(PARDISO_INCLUDE) $(INCLUDE) $< -o $@

ifeq ($(CLEANFOLDER), CLOTHBW)
clean: cleanclothBW
endif

deepclean: cleanclothBW

cleanclothBW:
	$(RM) $(CLOTHBW_OBJECTS_FILENAMES) $(L)/clothBW/libclothBW.a

endif

