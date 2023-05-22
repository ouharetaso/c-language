CC			= gcc
CXX			= g++
CFLAGS		= -Wall -std=c99
CXXFLAGS	=
CPPFLAGS	= -lm
LDFLAGS 	= 
LIBS		= 

TARGET		= $(shell basename `pwd`|sed "s/^[0-9]*_//g")
SRCDIR		= src
OBJDIR		= build
INCDIR		= include

SUFFIXES	= .c .cpp .s

SRCS		= $(foreach suffix, $(SUFFIXES), $(wildcard $(SRCDIR)/*$(suffix)))
OBJS		= $(addsuffix .o,$(addprefix $(OBJDIR)/, $(notdir $(basename $(SRCS) ) ) ) )

INCOPT		= $(addprefix -I,$(INCDIR) )

all:$(TARGET)

$(TARGET):$(OBJS)
	$(CC) $(CFLAGS) $(LDFLAGS) $^ -o $@ $(LIBS)


$(OBJDIR)/%.o: $(SRCDIR)/%.c
	@mkdir -p $(OBJDIR)
	$(warning $@)
	$(CC) $(CFLAGS) $(INCOPT) -c $< -o $@

$(OBJDIR)/%.o: $(SRCDIR)/%.cpp
	@mkdir -p $(OBJDIR)
	$(warning $@)
	$(CC) $(INCOPT) $(CFLAGS) -c $< -o $@

$(OBJDIR)/%.o: $(SRCDIR)/%.s
	@mkdir -p $(OBJDIR)
	$(warning $@)
	$(CC) $(INCOPT) $(CFLAGS) -c $< -o $@

clean:
	rm -rf $(OBJDIR) $(TARGET)

.PHONY: all clean