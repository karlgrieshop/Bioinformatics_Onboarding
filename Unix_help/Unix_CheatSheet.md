# Unix Cheat Sheet

A compact reference of common Unix commands and useful one-liners for bioinformatics work. 

---

## Basic file & directory commands

Change directory:
```bash
cd DIRECTORY_NAME
```

List files:
```bash
ls
```

List files including hidden and details:
```bash
ls -al
```

View a file one page at a time (press `G` to jump to end):
```bash
less -S FILE.txt
```

Delete file or directory (use with caution):
```bash
rm -rf FILE.txt
```

Find the path to a file (useful from home directory):
```bash
locate FILE.txt
```

Show disk usage for working directory:
```bash
du -sh
```

Show processes:
```bash
top
```

Kill a process (get PID from `top`):
```bash
kill PROCESS_ID
```

---

## Text processing: grep / awk / sed / perl

Print lines matching a pattern:
```bash
grep "pattern" FILE.txt
```

Print nth column (replace `n` with the column number):
```bash
awk '{print $n}' FILE.txt
```

Print nth column and unique elements:
```bash
awk '{print $n}' FILE.txt | uniq > NEWFILE.txt
```

Remove first character from every line:
```bash
sed 's/^.//' file
```

Remove lines containing a given pattern:
```bash
sed '/pattern to match/d' file.tsv
```

Remove last character from every line:
```bash
sed 's/.$//' file > file.nolast
```

Filter rows by numeric condition (column 4 > 30):
```bash
awk '($4  > 30)' file.tsv
```

Keep characters after a string:
```bash
grep -o 'string.*$' list.txt 
```

Retain lines whose first column is common with another file:
```bash
awk 'FNR==NR{a[$1];next}($1 in a){print $0}' file.txt file.tsv > output.tsv
```

Delete lines with first column common to another file:
```bash
awk 'FNR==NR{a[$1];next} !($1 in a){print $0}' file.txt file.tsv > output.tsv
```

Remove every occurrence of a character (example removes `"`):
```bash
sed 's/"//g' file
```

Find common lines between four files:
```bash
cat a b c d | sort | uniq -c | sed -n -e 's/^ *4 \(.*\)/\1/p'
```

Alternative method for common lines between two files:
```bash
comm -12 <(sort a) <(sort b)
```

Remove string between two characters (example `>` and `,`):
```bash
sed -E 's/>[^,]+,//g' DGRP177.fa 
```

Remove string after a character (example `:`):
```bash
sed 's/\:.*//' file
```

Remove first 5 lines:
```bash
sed '1,5d' file
# or
tail -n +6 file
```

Remove last 5 lines:
```bash
head -n -5 file
```

Replace whitespace with tab:
```bash
perl -p -e 's/ /\t/g' file
```

Print only rows where a column equals a string (example column 1):
```bash
awk '{if ($1 == "string") print $0;}' file
```

Print awk output with tab as output field separator:
```bash
awk -v OFS='\t' '{print $1, $2}' file.txt
```

Remove n-1 characters from 5th column (example using `substr`):
```bash
awk -v OFS='\t' '{$5 = substr($5, n); print}' file.txt
```

---

## Shell programming snippets

For loop example:
```bash
for i in x y z
do
    echo $i
done
```

If/else example:
```bash
if [[ var -eq 10 ]]; then
    echo "Variable equals 10"
else 
    echo "Variable is not 10"
fi
```

If / elif / else example:
```bash
if [[ var -eq 10 ]]; then
    echo "Variable equals 10"
elif [[ var -eq 15 ]]; then
    echo "Variable equals 15"
else 
    echo "Variable is neither 10 nor 15"
fi
```

---

## Sequence & bioinformatics helpers

Index fasta and fetch region:
```bash
samtools faidx genome.fa chr1:base_position
```

Check SnpEff database:
```bash
java -Xmx8g -jar ~/Apps/snpEff/snpEff.jar databases
```

Download genome from SnpEff:
```bash
java -Xmx8g -jar ~/Apps/snpEff/snpEff.jar download -v dmel_r6.31 &
```

Run SnpEff on VCF:
```bash
java -Xmx8g -jar ~/Apps/snpEff/snpEff.jar dmel_r6.31 DGRP177_sp159n_snps_filtered.vcf.gz > test.vcf.gz &
```

---

## Miscellaneous useful one-liners

Print column count and exit if more/less than required:
```bash
awk -F'\t' 'NF > 12{print; exit}' file
```

Grep for multiple strings:
```bash
fgrep -e "bla" -e "sla"
```

Add header to a file:
```bash
echo -e "geneID\tA1\tA2" | cat - file1 > file2
```

Remove string between two markers example (again):
```bash
sed -E 's/>[^,]+,//g' DGRP177.fa 
```

---

## Notes

- Some `awk`/`sed` examples use placeholders (`n`, `$n`, `<filename>`) — replace them with appropriate values.
- Use caution with destructive commands like `rm -rf`.

---

End of cheat sheet.
