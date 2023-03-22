# Makefile for crafting-interpreters C implementation

EXECUTABLE_NAME=clox

SOURCE_FOLDER=src
OUTPUT_FOLDER=target
OBJECTS_FOLDER=$(OUTPUT_FOLDER)/objs
EXECUTABLE_PATH=$(OUTPUT_FOLDER)/$(EXECUTABLE_NAME)

vpath %.c $(SOURCE_FOLDER)

OBJECTS=$(patsubst %.c,%.o,$(wildcard $(SOURCE_FOLDER)/*.c))

.PHONY: clean run compile

all: compile	

run: compile	
	./$(EXECUTABLE_PATH)

compile: $(EXECUTABLE_PATH)

$(EXECUTABLE_PATH): $(OBJECTS) | $(OUTPUT_FOLDER) $(OBJECTS_FOLDER)
	gcc -o $@ $^
	$(info Executable created.)

%.o: %.c | $(OBJECTS_FOLDER)
	gcc -o $@ -c $<

$(OBJECTS_FOLDER): | $(OUTPUT_FOLDER)
	mkdir $(OBJECTS_FOLDER)

$(OUTPUT_FOLDER):
	mkdir $(OUTPUT_FOLDER)

clean:
ifneq (,$(wildcard ./$(OUTPUT_FOLDER)))
	rm -r $(OUTPUT_FOLDER)
	$(info Cleaning done.)
endif

