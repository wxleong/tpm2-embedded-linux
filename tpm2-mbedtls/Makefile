SRC := $(wildcard *.c */*.c)
OBJ := $(patsubst %.c,%.o,$(SRC))
DEP := $(SRC:.c=.d)

$(info Sources=$(SRC))
$(info Objects=$(OBJ))

CPPFLAGS := -MMD
CC := gcc
LDFLAGS := 
LDLIBS := -L~/tpm2-tss/cmake/ -ltpm2tss -L~/mbedtls/library/ -lmbedcrypto -lmbedtls -lmbedx509
CFLAGS := -Os -Wall -std=c99 -I~/tpm2-tss/include/ -I~/mbedtls/include/ -Itpm/ -DTCTI_NAME_CONF=\"device:/dev/tpmrm0\"

main: $(OBJ)

.PHONY: clean
clean:
	rm -f main $(OBJ) $(DEP)

-include $(DEP)
