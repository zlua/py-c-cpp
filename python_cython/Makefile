
Target = c1

SRC_C   := $(wildcard *.c)
OBJ_C   := $(patsubst %.c,%.o,$(SRC_C))

LIB = lib$(Target).a
ShareLib = lib$(Target).dll
ShareFlags = -DDL_EXPORT -s -shared -Wl,--subsystem,windows,--out-implib,$(LIB)

CFLAGS = -I"C:\\Python27\\include"
Python_LDFLAGS = -L"C:\\Python27\\libs"
Sharedlibs = -lpython27

share: $(ShareLib)

$(ShareLib): $(OBJ_C)
	gcc -shared $(ShareFlags) $(CFLAGS) $(Python_LDFLAGS) $(Sharedlibs)  $^ -o $@

$(obj)%.o:	%.c
	@echo "Compling: " $(addsuffix .c, $(basename $(notdir $@)))
	gcc $(CFLAGS) -c $< -o $@

clean:
	@echo "Cleaning..."
	$(RM) $(StaticLIB) $(LIB) $(OBJ_C) $(OBJ_CPP) $(LIB) $(ShareLib) *.bak *~ $(obj).depend *.o