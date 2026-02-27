# FILE
`nano`,`vim`, `cat`, `less`, `tac`, `head`, `tail`, `sed`, `grep`, `xdg-open`, `xdg-mime`

<h6>

| Command    | One-line Explanation                                        |
| ---------- | ----------------------------------------------------------- |
| `nano`     | Terminal দিয়ে সহজে file edit করার text editor  —   `Not an acronym` |
| `cat`      | File দেখানো ও একাধিক file জোড়া লাগানোর কমান্ড    –  `Concatenate`           |
| `less`     | বড় file scroll করে safe ভাবে দেখার viewer   –  `Not an acronym`   |
| `tac`      | File উল্টোভাবে দেখায় (শেষ লাইন আগে)   –  `cat backwards`   |
| `head`     | File-এর শুরুর কয়েকটি লাইন দেখায়                             |
| `tail`     | File-এর শেষ কয়েকটি লাইন দেখায় (live দেখতে `-f`)             |
| `sed`      | File না খুলেই search, replace, delete করার  –  `Stream Editor`|
| `xdg-open` | Linux desktop-এ default application দিয়ে file/link open করে  –  `X Desktop Group open` |
| `xdg-mime` | কোন file কোন application দিয়ে open হবে তা জানে বা সেট করে   –  `X Desktop Group – MIME handler` |
| `grep`     | File বা output থেকে নির্দিষ্ট word/pattern খুঁজে বের করে    |
| `awk`      | Column, condition ও logic দিয়ে advanced text processing করে |
| `cut`      | Delimiter অনুযায়ী file থেকে নির্দিষ্ট column কেটে নেয়       |

</h6>



<br>

### nano / vim  - সহজ terminal text editor (beginner-friendly)

```bash
nano file.txt        # ফাইল খুলে edit করা
nano new.txt         # নতুন ফাইল তৈরি করে edit
```

---

### cat - concatenate (ফাইল দেখা ও জোড়া লাগানোর কমান্ড)
```bash
cat file.txt        # একটি ফাইলের সব কনটেন্ট দেখায়
cat a.txt b.txt     # একাধিক ফাইল একসাথে দেখায়

cat -n a.txt        # সব লাইনের সাথে লাইন নম্বর দেখায়
cat -b a.txt        # শুধু non-empty লাইনে নম্বর দেখায়
cat -A a.txt        # special character দেখায় (^M, $, tab ইত্যাদি)

cat > new.txt       # নতুন ফাইল তৈরি করে (Ctrl + D দিয়ে শেষ)
cat >> new.txt      # existing ফাইলে লেখা যোগ করে (append)

cat a.txt b.txt > c.txt   # a.txt ও b.txt জোড়া দিয়ে c.txt তৈরি

cat a.txt | grep x  # a.txt থেকে যেখানে 'x' আছে সেই লাইন দেখায়
```
```bash
cat /dev/null > a.txt   # ফাইল খালি (empty) করে
tac a.txt               # ফাইল উল্টো করে দেখায় (reverse cat)
```
<br>

> ছোট ফাইল → cat
বড় ফাইল → less
edit → nano / vim

---

### less -  বড় ফাইল scroll করে দেখার জন্য (read-only viewer)
```bash
less file.txt        # ফাইল scroll করে দেখা
less +F file.txt     # live mode (tail -f এর মতো)
```


---


### tac - cat-এর উল্টো (reverse concatenate)

```bash
tac file.txt        # ফাইল নিচ থেকে উপরে (শেষ লাইন আগে) দেখায়
```



---


### head  - ফাইলের শুরুর দিকের লাইন দেখায়

```bash
head file.txt        # ফাইলের প্রথম 10 লাইন দেখায়
head -n 5 file.txt   # ফাইলের প্রথম 5 লাইন দেখায়
head -n 20 file.txt  # ফাইলের প্রথম 20 লাইন দেখায়


tail  # ফাইলের শেষ দিকের লাইন দেখায়

tail file.txt        # ফাইলের শেষ 10 লাইন দেখায়
tail -n 5 file.txt   # ফাইলের শেষ 5 লাইন দেখায়
tail -n 20 file.txt  # ফাইলের শেষ 20 লাইন দেখায়

tail -f file.txt     # ফাইল live monitor করে (নতুন লাইন আসলেই দেখায়)
```

```
head scan.txt            # scan output শুরুটা দ্রুত দেখার জন্য
tail scan.txt            # scan শেষ হয়েছে কিনা বোঝার জন্য
tail -f /var/log/auth.log  # live login attempt মনিটর
```

<br>

> head = মাথা → শুরু
tail = লেজ → শেষ
tail -f = live



---



### sed  - Stream Editor (ফাইল না খুলেই text edit করে)
> sed = editor without opening editor
s = substitute
d = delete
p = print

```bash
sed 's/old/new/' file.txt        # old → new (প্রতি লাইনে প্রথম match)
sed 's/old/new/g' file.txt       # old → new (সব match)

sed -i 's/old/new/g' file.txt    # ফাইলের ভেতর permanent change (⚠️ undo নেই)

sed '2d' file.txt                # ২ নম্বর লাইন delete
sed '1,3d' file.txt              # ১–৩ নম্বর লাইন delete
sed '/error/d' file.txt          # যেখানে 'error' আছে সেই লাইন delete

sed -n '5p' file.txt             # শুধু ৫ নম্বর লাইন দেখায়
sed -n '1,5p' file.txt           # ১–৫ নম্বর লাইন দেখায়

sed 's/^/>> /' file.txt          # প্রতিটি লাইনের শুরুতে >> যোগ
sed 's/$/ END/' file.txt         # প্রতিটি লাইনের শেষে END যোগ
```

```bash
sed '/Failed password/d' auth.log     # failed login লাইন বাদ
sed 's/[0-9]\+/X/g' data.txt          # সংখ্যা mask করা
sed 's/[0-9]\+\.[0-9]\+\.[0-9]\+\.[0-9]\+/[IP]/g' log.txt
sed -i 's/http/https/g' config.txt    # config update
```



---



## xdg-open -  X Desktop Group → default application দিয়ে open করে

```bash
xdg-open file.txt        # system default text editor দিয়ে ফাইল খুলে
xdg-open image.jpg       # default image viewer দিয়ে খুলে
xdg-open file.pdf        # default PDF reader দিয়ে খুলে
xdg-open .               # current folder file manager-এ খুলে
xdg-open https://google.com   # default web browser-এ খুলে
```

` MIME / default app check (useful)`

```bash
xdg-mime query filetype file.txt        # ফাইলের MIME type দেখায়
xdg-mime query default text/plain       # কোন app দিয়ে .txt খুলবে
```

<br>

---

<br>



### grep  - Global Regular Expression Print (খুঁজে বের করে দেখায়)

```bash
grep word file.txt          # file.txt থেকে 'word' থাকা লাইন দেখায়
grep -i word file.txt       # case-insensitive (Word / WORD / word)
grep -v word file.txt       # 'word' ছাড়া বাকি সব লাইন দেখায় (Invert match )

grep -n word file.txt       # line number সহ দেখায়
grep -c word file.txt       # কতবার match হয়েছে সংখ্যা দেখায়

grep -w word file.txt       # শুধু সম্পূর্ণ word match করে
grep -x "exact line" file.txt         # Match exact line
grep "open" scan.txt        # scan.txt থেকে 'open' থাকা লাইন

grep -r "text" /path                  # Recursive search in directory
grep -R "text" /path                  # Follow symbolic links too

grep -l "text" *.txt                  # List files with matches
grep -L "text" *.txt                  # List files WITHOUT matches

grep -A 3 "text" file.txt             # Show 3 lines After match
grep -B 3 "text" file.txt             # Show 3 lines Before match
grep -C 3 "text" file.txt             # Show 3 lines Context (before+after)
```
 

#### Advanced grep
```bash
grep -E "pattern1|pattern2" file.txt  # Extended regex (OR)
grep -e "pat1" -e "pat2" file.txt     # Multiple patterns
grep -f patterns.txt file.txt         # Patterns from file
grep -o "text" file.txt               # Show only matching part
grep -q "text" file.txt               # Quiet mode (no output, exit code only)
grep -m 5 "text" file.txt             # Stop after 5 matches
grep -h "text" *.txt                  # No filename prefix
grep -H "text" file.txt               # Always show filename
grep --color=auto "text" file.txt     # Colorize matches
```

#### Regular Expressions with grep
```bash
grep "^start" file.txt                # Lines starting with "start"
grep "end$" file.txt                  # Lines ending with "end"
grep "^$" file.txt                    # Empty lines
grep "[0-9]" file.txt                 # Lines with numbers
grep "[a-zA-Z]" file.txt              # Lines with letters
grep "a.c" file.txt                   # a + any char + c (abc, adc, a1c)
grep "a*" file.txt                    # Zero or more 'a'
grep "a\+" file.txt                   # One or more 'a'
grep "a\{3\}" file.txt                # Exactly 3 'a's (aaa)
grep "a\{2,4\}" file.txt              # 2 to 4 'a's
grep "\<word\>" file.txt              # Whole word boundary
```

### Practical grep Examples
```bash
# Find IP addresses
grep -E '\b([0-9]{1,3}\.){3}[0-9]{1,3}\b' file.txt

# Find email addresses
grep -E '\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b' file.txt

# Find lines with phone numbers
grep -E '\b[0-9]{3}[-.]?[0-9]{3}[-.]?[0-9]{4}\b' file.txt

# Find TODO comments in code
grep -rn "TODO:" /path/to/code

# Find files modified today
find . -type f -mtime 0 -exec grep -l "text" {} \;

# Case insensitive search in logs
grep -i "error" /var/log/syslog
```









Pipe দিয়ে ব্যবহার (সবচেয়ে common)
```bash
cat file.txt | grep error
nmap target.com | grep open
ps aux | grep apache
```

Multiple file / recursive search
```bash
grep word a.txt b.txt           # একাধিক ফাইলে খোঁজা
grep -r "password" /etc/       # folder এর ভিতরে recursive search

/etc/ ফোল্ডারের ভেতরে থাকা সব ফাইলের মধ্যে, যেখানে যেখানে 
password লেখা আছে, সেই লাইনগুলো খুঁজে দেখাও।
```
 

Real / Cyber security use
```bash
grep "Failed password" /var/log/auth.log
grep "200 OK" access.log
grep -r "admin" .
```


> Quick memory trick
grep = search
-i = ignore case
-v = invert (বাদ দিয়ে দেখাও)
-r = recursive

<br>

---

*Written by*
[*anmamuncoder*](https://anmamuncoder.vercel.app/) — thanks for reading, hope this post added a little value or clarity.