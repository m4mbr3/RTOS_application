# Testapplikation makefile
SO               :=libhwaccel_uc.so

.SUFFIXES : .cpp .o
.DEFAULT : $(SO)
.PHONY : clean

CPP  = g++
LIBS = 
INCLUDES = -I/usr/include -I.#-I/usr/src/linux/include -I/usr/src/include/linux -I/usr/include -I/usr/src/linux/include/linux
CXXFLAGS = $(INCLUDES) -g3 -fPIC -D__DEBUG__ -D_REENTRANT -fbounds-check -D CONFIG_SCHED_HET
RM = rm -f
CP = cp -f

SOURCES         := $(wildcard *.cpp)
HEADERS         := $(wildcard *.h)
OBJS            := $(patsubst %.cpp, %.o, $(SOURCES))


.PHONY: all all-before all-after clean clean-custom

all: all-before $(SO) all-after

$(SO): $(OBJS) $(HEADERS)
	$(CPP) -shared -Wl,-soname,$(SO) -o $(SO) $(OBJS)

clean: clean-custom
	${RM} $(OBJS) $(SO)

# Rest
%.o: %.cpp
	$(CPP) $(CXXFLAGS) -c $< -o $@

