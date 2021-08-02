CC=g++
NAME=a.out
FLAGS=-Wall -O2
LIBS=

BUILD_DIR=.build
OBJ_DIR=objs
SRC_DIR=src

# Function wildcard recursive
rwildcard=$(foreach d,$(wildcard $(1:=/*)),$(call rwildcard,$d,$2) $(filter $(subst *,%,$2),$d))
# All objs file to compile
OBJS=$(subst $(SRC_DIR)/,$(BUILD_DIR)/$(OBJ_DIR)/,$(patsubst %.cpp,%.o,$(call rwildcard,$(SRC_DIR),*.cpp)))

install: cdir build

$(BUILD_DIR)/$(OBJ_DIR)/%.o: $(SRC_DIR)/%.cpp
	@mkdir -p $(dir $@)
	$(CC) $(FLAGS) -c $< -o $@

build: $(OBJS)
	$(CC) $(FLAGS) $^ -o $(BUILD_DIR)/$(NAME) $(LIBS)
	@echo compilation is finish

cdir:
	@mkdir -p $(BUILD_DIR)
	
run:
	@./$(BUILD_DIR)/$(NAME)
	
clean:
	@rm -r $(BUILD_DIR)
