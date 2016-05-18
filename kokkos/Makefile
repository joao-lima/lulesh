KOKKOS_PATH = ${HOME}/kokkos-tutorial/kokkos
KOKKOS_DEVICES = "Pthreads"
EXE_NAME = "lulesh2.0"

SRC = $(wildcard *.cc)

default: build
	echo "Start Build"


CXX = g++
EXE = ${EXE_NAME}.host
KOKKOS_ARCH = "SNB"

CXXFLAGS = -O2 -g -DUSE_MPI=0
LINK = ${CXX} 
LINKFLAGS =  -g

DEPFLAGS = -M

OBJ = $(SRC:.cc=.o)
LIB =

include $(KOKKOS_PATH)/Makefile.kokkos

build: $(EXE)

$(EXE): $(OBJ) $(KOKKOS_LINK_DEPENDS)
	$(LINK) $(KOKKOS_LDFLAGS) $(LINKFLAGS) $(EXTRA_PATH) $(OBJ) $(KOKKOS_LIBS) $(LIB) -o $(EXE)

clean: kokkos-clean 
	rm -f *.o *.cuda *.host

# Compilation rules

%.o:%.cc $(KOKKOS_CPP_DEPENDS)
	$(CXX) $(KOKKOS_CPPFLAGS) $(KOKKOS_CXXFLAGS) $(CXXFLAGS) $(EXTRA_INC) -c $<
