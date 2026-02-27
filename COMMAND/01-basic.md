`pwd`, `ls`, `wc`, `cd`, `mkdir`, `touch`, `rm`, `cat`, `echo`, `nano`, `man`, `history`, `clear`, `tree`


##  pwd - Print Working Directory

```bash
pwd  # এখন কোন folder-এর ভেতরে আছো সেটা দেখাবে।
```

---

### File Listing Commands (ls)

### Basic Listing
```bash
ls                    # List files and directories
ls -l                 # Long format (detailed view), show [permission, owner, group, size, date, name]
ls -a                 # Show all files (including hidden), যেসব file . দিয়ে শুরু (hidden)
ls -la                # details + hidden = full view
ls -lh                # Human-readable file sizes (KB, MB, GB), 1024 → 1K, 1048576 → 1M
ls -lah               # Long format + hidden + human-readable
ls -1                 # One file per line
ls -d */              # show only directories

ls -A                 # Hidden ছাড়া ., .. বাদ দিয়ে
ls -R                 # Recursive (list subdirectories) ভিতরের সব folder
```

### Advanced Listing
```bash
ls -t                 # Sort by modification time (newest first)
ls -tr                # Sort by time (oldest first)
ls -ltr               # Long format, sorted by time (oldest first)
ls -ltr               # Long format, sorted by time (oldest first)
ls -S                 # Sort by file size (largest first)
ls -Sr                # Sort by size (smallest first) 
ls -lhS               # Long format, human-readable, sorted by size, for বড় file কোনটা?
```

### Filtering & Specific Files
```bash
ls *.txt              # List only .txt files
ls test*              # start with name 
ls -l file.txt        # Details of specific file
ls -ld /path/to/dir   # Details of directory itself (not contents)
ls --color=auto       # Colored output, folder, file, link আলাদা রঙে
ls -F                 # File type indicator
ls -i                 # Show inode numbers, filesystem debugging এ কাজে লাগে
ls -n                 # Show numeric UID and GID
```

File count করা (with pipe)
```bash
ls | wc -l              # কত file আছে
```

### মনে রাখার ট্রিক:

<h6>

Group-1: দেখানোর ধরন (View)

| Option | মনে রাখার শব্দ |
| ------ | -------------- |
| `-l`   | long           |
| `-a`   | all            |
| `-h`   | human          |
| `-1`   | one line       |

Group-2: Sort (order)
| Option | মনে রাখার শব্দ |
| ------ | -------------- |
| `-t`   | time           |
| `-S`   | size           |
| `-r`   | reverse        |

Group-3: Filter / Special
| Option  | কাজ         |
| ------- | ----------- |
| `-d */` | শুধু folder |
| `*.txt` | pattern     |
| `-F`    | type        |
| `-i`    | inode       |

</h6>



wc = Word Count, এটা দিয়ে তুমি line, word, character/byte গোনা যায়।
l w c m → line word char

```bash
wc file.txt         # count line, word, character/byte

wc -l file.txt      # কত line আছে জানতে
wc -w file.txt      # কত word আছে জানতে
wc -c file.txt      # কত character আছে জানতে
wc -m file.txt      # character (UTF-8 safe)
wc *.txt            # Multiple file একসাথে

```
Real-Life Use Cases
```bash
ls | wc -l          # এই folder-এ কয়টা file সংখ্যা গণনা
ls -d */ | wc -l    # Directory সংখ্যা গণনা
ps aux | wc -l      # Running process count
```

---


### cd — folder change করা
```bash
cd ..     # এক ধাপ পিছনে
cd ~      # home directory
cd /      # root
```

---

### mkdir — নতুন folder বানানো
```bash
mkdir test
mkdir -p test/sub1/sub2
```
---

### touch — file বানানো
```bash
touch a.txt
touch b.txt c.txt
```
---

### rm — file delete 
```bash
rm a.txt        # a.txt file delete
rm -i b.txt     # terminal-এ undo নাই, file delete for Safe practice:
rm -r test      # Folder delete, -r = recursive (folder এর ভিতর সব)
rm -ri test     # Folder delete for Save Practive
```

---

### cat — file দেখা

```bash
cat c.txt
```

---

### echo — file এ লেখা

```bash
echo "Hello Linux" > c.txt  # write overwrite
echo "Second line" >> c.txt # write with Append:
cat c.txt
```

---

### nano — text editor (beginner friendly)
```bash
nano notes.txt
```

---

### man — command help

```bash
man ls
man rm
```

---

### history — আগের all command

```bash
history     # view history list
!23         # Run again:
```

---

### for clear recent terminal
```bash
clear
```

---

### tree 
> tree একটা command যা directory structure কে tree আকারে দেখায়।
```bash
sudo apt install tree
tree                    # view files like ls command 
tree -L 2               # Depth limit করে overview।
tree media              # file সত্যিই আছে কিনা check।
tree > structure.txt    # Documentation / Screenshot, Project structure share করা।

tree -d                 # Directory only
tree -h                 # Human readable size
tree -I "__pycache__|.git|node_modules"   # Ignore folder
tree -a                 # Show hidden
```




































