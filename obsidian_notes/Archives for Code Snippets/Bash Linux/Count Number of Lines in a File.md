---
tags:
  - code
  - code_snippet
  - bash/wc
keywords: 
topics: 
language: bash
date of note: 2025-04-02
---

## Code Snippet Summary

>[!important]
>Given a file `filename.csv`, count the number of rows in the file 


## Code

### General Cases

```bash
wc -l filename.csv
```

- Alternatively

```bash
cat filename.csv | wc -l
```

- for `.gz` file

```bash
# For compressed files 
zcat file.gz | wc -l
```


### Other Cases

- To exclude empty lines:

```bash
grep -c "[^[:space:]]" filename.txt
```


- To count lines matching a pattern:

```bash
grep -c "pattern" filename.txt
```


- For multiple files:

```bash
# Count lines in each file 
wc -l file1.txt file2.txt file3.txt  
# Count total lines in all files 
wc -l * | grep total
```


- For large files (more efficient):

```bash
less filename.txt | wc -l
```


- To count lines in all files in a directory:

```bash
# All files 
find . -type f -exec wc -l {} \;  
# Specific extension 
find . -name "*.txt" -exec wc -l {} \;
```

- For specific time period:

```bash
# Files modified in last 24 hours 
find . -mtime -1 -type f -exec wc -l {} \;
```


- With error handling:

```bash
if [ -f filename.txt ]; then     
	wc -l filename.txt 
else     
	echo "File does not exist" 
fi
```


- In a script with variables:

```bash
#!/bin/bash
file="filename.txt"
count=$(wc -l < "$file")
echo "Number of lines in $file: $count"
```


- For specific columns in CSV:

```bash
# Count non-empty values in first column 
awk -F',' '$1!=""' filename.csv | wc -l
```

    


### Examples

Examples with options:

```bash
# Basic count
$ wc -l file.txt
100 file.txt

# Count multiple files
$ wc -l *.txt
  100 file1.txt
  200 file2.txt
  300 file3.txt
  600 total

# Count non-empty lines
$ grep -v "^$" file.txt | wc -l

# Count with pattern
$ grep "ERROR" logfile.txt | wc -l

# Count with header exclusion
$ sed 1d file.csv | wc -l

```

- Another Example

```bash
# Monitor log growth
while true; do
    wc -l logfile.txt
    sleep 60
done

# Check file size before processing
linecount=$(wc -l < bigfile.txt)
if [ $linecount -gt 1000000 ]; then
    echo "File too large"
    exit 1
fi

# Process in chunks
total_lines=$(wc -l < file.txt)
chunk_size=1000
for i in $(seq 1 $chunk_size $total_lines); do
    sed -n "${i},$(($i+$chunk_size-1))p" file.txt > chunk.txt
    # Process chunk.txt
done

```



-----------
##  Recommended Notes


- [[Count Number of Columns in CSV file]]
- [[Count Number of Lines for Each File and Aggregate]]
