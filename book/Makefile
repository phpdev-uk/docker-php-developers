OUTPUT_FILES = output/book.pdf output/book.html
PANDOC_FLAGS = \
	--table-of-contents \
	--number-sections

all: $(OUTPUT_FILES)

output/%.pdf: %.md chapters/*.md
	filepp $< | pandoc -o $@ $(PANDOC_FLAGS)

output/%.html: %.md chapters/*.md
	filepp $< | pandoc -o $@ $(PANDOC_FLAGS)

clean:
	rm -f output/*

.PHONY: clean