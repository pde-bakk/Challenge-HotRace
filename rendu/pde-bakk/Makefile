NAME = hotrace

SHELL := /bin/bash

# COLORS
PINK = \x1b[35;01m
BLUE = \x1b[34;01m
YELLOW = \x1b[33;01m
GREEN = \x1b[32;01m
RED = \x1b[31;01m
WHITE = \x1b[31;37m
RESET = \x1b[0m

CXXFLAGS = -W -Wall -Werror -Wextra -pedantic -std=c++98
INCLUDE = -Iincludes -Ift_containers -Igetnextline/include

ifdef DEBUG
 CXXFLAGS += -g -fsanitize=address
else
 CXXFLAGS += -Ofast
endif
FILES = main.cpp
SRCS = $(addprefix srcs/, $(FILES))
OBJS = $(SRCS:.cpp=.o)

all: $(NAME)

$(NAME): getnextline.a $(OBJS)
	@echo -e "$(BLUE) @ is " $^ "$(RESET)"
	$(CXX) $(CXXFLAGS) $(INCLUDE) $(SRCS) getnextline/getnextline.a -o $@

%.a: %
	$(MAKE) -C $^

%.o: %.cpp
	$(CXX) -c $(CXXFLAGS) $(INCLUDE) $^ -o $@

clean:
	$(RM) $(OBJS)
	$(MAKE) clean -sC getnextline

fclean: clean
	$(RM) $(NAME)
	$(MAKE) fclean -sC getnextline

re: fclean all

test: $(NAME)
	cat ../../ressources/generated-1 | ./$< > myoutput1.txt

test_time: $(NAME)
	./test.sh

.PHONY: re clean fclean test time
