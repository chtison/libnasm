.PHONY: all clean fclean re

NAME := libasm.a
OBJS := $(addprefix obj/ft_, $(addsuffix .o, \
			bzero  \
			cat    \
			memcpy \
			memset \
			puts   \
			strcat \
			strcpy \
			strdup \
			strlen \
		))
TSTS := $(OBJS:obj/%.o=tst/%.c)

all: $(NAME)

$(NAME): obj/ $(OBJS)
	ar -rc -- $@ $(OBJS)

obj/:
	@mkdir -p obj/

obj/%.o: src/%.s libasm.s
	nasm -f macho64 -Wall -o $@ $<

clean:
	rm -f -- $(NAME)

fclean: clean
	rm -rf -- obj/

re: fclean all

test: all
	for test in $(TSTS); do gcc $$test -Wall -Wextra -Werror -lasm -L. -I. && ./a.out ; rm -f -- a.out ; done
