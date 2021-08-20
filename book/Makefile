OUTPUT_FILES = output/book.pdf

all: $(OUTPUT_FILES)

output/%.pdf: %.md
	filepp $< | pandoc -o $@

clean:
	rm -f output/*

.PHONY: clean