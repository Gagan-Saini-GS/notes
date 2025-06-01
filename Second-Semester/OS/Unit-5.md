# Unit-5

## 🖋️ **Introduction to vi and Emacs Editors**

### **1. vi Editor (Visual Editor)**

- Lightweight, always available on UNIX/Linux.
- Two modes:

  - **Command mode** (default) – for navigation, deletion, etc.
  - **Insert mode** – for typing/editing text

- **Basic Commands**:

  | Action              | Command            |
  | ------------------- | ------------------ |
  | Enter insert mode   | `i`                |
  | Save and exit       | `:wq` or `ZZ`      |
  | Exit without saving | `:q!`              |
  | Delete a line       | `dd`               |
  | Move cursor         | `h`, `j`, `k`, `l` |

### **2. Emacs Editor**

- Feature-rich and extensible (keyboard-focused).
- Ideal for coding, scripting, and advanced editing.
- **Basic Commands**:

  | Action         | Command                     |
  | -------------- | --------------------------- |
  | Open file      | `Ctrl+x Ctrl+f`             |
  | Save file      | `Ctrl+x Ctrl+s`             |
  | Exit           | `Ctrl+x Ctrl+c`             |
  | Cut/Copy/Paste | `Ctrl+k`, `Alt+w`, `Ctrl+y` |

---

## 💻 **Basics of Shell Programming**

Shell scripting is writing sequences of shell commands in a file to automate tasks.

- Common shell: **Bash (Bourne Again Shell)**
- Shell scripts are saved with `.sh` extension and executed with `bash script.sh` or `./script.sh` (after making executable with `chmod +x`).

### 🧪 Example Script:

```bash
#!/bin/bash
echo "Welcome to Shell Programming"
```

### 🔣 **Shell Metacharacters**

Metacharacters have special meanings in the shell. Examples include:

| Metacharacter         | Meaning                          | Example                        |      |             |
| --------------------- | -------------------------------- | ------------------------------ | ---- | ----------- |
| `*`                   | Matches any number of characters | `ls *.txt`                     |      |             |
| `?`                   | Matches a single character       | `ls file?.txt`                 |      |             |
| `>`                   | Redirects output to a file       | `echo hi > file.txt`           |      |             |
| `>>`                  | Appends output to a file         | `echo bye >> file.txt`         |      |             |
| `<`                   | Takes input from a file          | `sort < file.txt`              |      |             |
| \`                    | \`                               | Pipe output to another command | \`ls | grep .txt\` |
| `;`                   | Separates multiple commands      | `echo A; echo B`               |      |             |
| `&`                   | Runs command in background       | `./script.sh &`                |      |             |
| `` ` ` `` or `$(...)` | Command substitution             | `date=$(date)`                 |      |             |

---

## 📦 **Shell Variables**

### 🔹 **Types of Variables:**

1. **Predefined (Environment) Variables**:

   - Provided by the system
   - Examples:

     | Variable | Purpose                       |
     | -------- | ----------------------------- |
     | `$HOME`  | Current user's home directory |
     | `$USER`  | Username                      |
     | `$PATH`  | Search path for executables   |
     | `$PWD`   | Current directory             |
     | `$SHELL` | Current shell                 |

2. **User-Defined Variables**:

   - Created by the user
   - Syntax:

     ```bash
     name="Alice"
     echo $name
     ```

### 🧠 **Key Concepts:**

| Task                 | Syntax Example         |
| -------------------- | ---------------------- |
| Assign a value       | `var="Hello"`          |
| Access value         | `echo $var`            |
| Unset variable       | `unset var`            |
| Store filename       | `file="report.txt"`    |
| Store file content   | `data=$(cat file.txt)` |
| Store command output | `today=$(date)`        |

---

## 📁 **Practical Example:**

```bash
#!/bin/bash

name="John"
greeting="Hello, $name"
file="example.txt"

echo $greeting > $file
echo "Current date: $(date)" >> $file
```

This script:

- Defines variables
- Writes to a file using redirection
- Uses command substitution

---

## ✅ Summary

| Concept            | Summary                                                   |                                           |
| ------------------ | --------------------------------------------------------- | ----------------------------------------- |
| **Editors**        | `vi` for minimal needs, `emacs` for advanced editing      |                                           |
| **Shell Basics**   | Use `#!/bin/bash`, script files, and `echo`, `read`, etc. |                                           |
| **Metacharacters** | Special characters like `*`, \`                           | `, `>\`, used to control command behavior |
| **Variables**      | `name="value"`, use `$name`, unset with `unset name`      |                                           |

---

## 🧾 **Input Handling in Shell Scripts**

### 📌 1. **Reading Word by Word**

Use `read` in a loop to process input one word at a time:

```bash
echo "Enter some words:"
read line
for word in $line
do
  echo "Word: $word"
done
```

Or from a file:

```bash
while read -r word
do
  echo "Word: $word"
done < <(cat file.txt | tr -s ' ' '\n')  # One word per line
```

### 📌 2. **Reading Line by Line**

```bash
while IFS= read -r line
do
  echo "Line: $line"
done < file.txt
```

- `IFS=` prevents trimming whitespace
- `-r` avoids backslash escape interpretation

### 📌 3. **Reading from a File**

```bash
filename="data.txt"
while read -r line
do
  echo "Read: $line"
done < "$filename"
```

Or, reading the entire content into a variable:

```bash
content=$(<file.txt)
echo "$content"
```

---

## 🔢 **Expressions in Shell**

### Arithmetic Expressions:

Use `$((...))` for basic arithmetic:

```bash
a=10
b=20
sum=$((a + b))
echo "Sum: $sum"
```

---

## 🔀 **Decisions (Conditional Statements)**

### if...else Statement:

```bash
num=5
if [ $num -gt 0 ]; then
  echo "Positive"
else
  echo "Non-positive"
fi
```

### if...elif...else:

```bash
if [ "$1" -gt 0 ]; then
  echo "Positive"
elif [ "$1" -lt 0 ]; then
  echo "Negative"
else
  echo "Zero"
fi
```

---

## 🔁 **Repetition (Loops)**

### for Loop:

```bash
for i in 1 2 3 4
do
  echo "Value: $i"
done
```

### while Loop:

```bash
count=1
while [ $count -le 5 ]
do
  echo "Count: $count"
  count=$((count + 1))
done
```

### until Loop:

```bash
count=1
until [ $count -gt 5 ]
do
  echo "Count: $count"
  count=$((count + 1))
done
```

---

## 💡 **Special Parameters and Variables**

| Symbol   | Meaning                            | Example               |
| -------- | ---------------------------------- | --------------------- |
| `$0`     | Script name                        | `echo $0`             |
| `$1..$9` | Arguments 1 to 9                   | `echo $1`, `echo $2`  |
| `$#`     | Number of arguments                | `echo $#`             |
| `$*`     | All arguments as a single word     | `echo $*`             |
| `$@`     | All arguments as separate words    | `for arg in "$@"; do` |
| `$$`     | PID of the current shell           | `echo $$`             |
| `$!`     | PID of the last background command | `sleep 10 & echo $!`  |
| `$?`     | Exit status of the last command    | `echo $?`             |

---

### 📌 Example Script Using Many of These:

```bash
#!/bin/bash

echo "Script name: $0"
echo "First argument: $1"
echo "Total arguments: $#"

echo "Reading from file line by line:"
while read -r line; do
  echo ">> $line"
done < "$1"
```

### ✅ Summary

| Topic              | Key Concepts                                                |
| ------------------ | ----------------------------------------------------------- |
| **Reading Input**  | `read`, `while read`, from file, word-by-word, line-by-line |
| **Expressions**    | Arithmetic: `$((...))`, logical: `if`, `elif`, `else`       |
| **Loops**          | `for`, `while`, `until`                                     |
| **Special Params** | `$0`, `$1`, `$@`, `$#`, `$?`, `$$`, `$!`                    |

---

## 🐚 **Shell Programming in Bash**

### 📥 1. **`read` Command**

Used to **take input from the user**.

```bash
read name
echo "Hello, $name"
```

Prompting inline:

```bash
read -p "Enter your name: " name
echo "Hi, $name"
```

Reading multiple variables:

```bash
read fname lname
echo "First: $fname, Last: $lname"
```

### 🔀 2. **Conditional Statements**

#### ➤ `if`, `if-else`, `elif`

```bash
num=5
if [ $num -gt 0 ]; then
  echo "Positive"
elif [ $num -lt 0 ]; then
  echo "Negative"
else
  echo "Zero"
fi
```

🔸 Use `[` or `[[` for conditions.
🔸 Use `-eq`, `-gt`, `-lt`, etc., for numbers.

#### ➤ String comparisons:

```bash
if [ "$str1" == "$str2" ]; then
  echo "Strings match"
fi
```

### 🔁 3. **Looping Statements**

#### ➤ `for` loop:

```bash
for i in 1 2 3 4 5
do
  echo "Number: $i"
done
```

#### ➤ `while` loop:

```bash
count=1
while [ $count -le 3 ]
do
  echo "Count: $count"
  ((count++))
done
```

#### ➤ `until` loop:

```bash
x=1
until [ $x -gt 5 ]
do
  echo "x: $x"
  x=$((x + 1))
done
```

### 🧩 4. **Case Statements**

Cleaner alternative to `if-elif`.

```bash
read -p "Enter a letter: " letter

case $letter in
  [a-z])
    echo "Lowercase letter";;
  [A-Z])
    echo "Uppercase letter";;
  [0-9])
    echo "Digit";;
  *)
    echo "Other character";;
esac
```

### 🔄 5. **Changing Positional Parameters**

Normally, `$1`, `$2`, etc. represent script arguments. You can **manipulate them** using `set`.

```bash
set apple banana cherry
echo $1  # apple
echo $2  # banana
```

Reset with:

```bash
set --
```

### 🛡️ 6. **Argument Validation**

Ensure script is run with required arguments:

```bash
if [ $# -lt 2 ]; then
  echo "Usage: $0 arg1 arg2"
  exit 1
fi
```

Explanation:

- `$#` → number of arguments
- `$0` → script name
- `$1`, `$2`, etc. → argument values

### 🔤 7. **String Manipulation in Bash**

#### ➤ String length:

```bash
str="hello"
echo ${#str}  # Output: 5
```

#### ➤ Substring extraction:

```bash
echo ${str:1:3}  # Output: ell
```

#### ➤ Replace part of string:

```bash
str="apple pie"
echo ${str/pie/cake}  # Output: apple cake
```

#### ➤ Concatenation:

```bash
str1="Good"
str2="Morning"
str3="$str1 $str2"
echo $str3  # Output: Good Morning
```

### ✅ Summary Table

| Feature           | Command/Keyword                                 |
| ----------------- | ----------------------------------------------- |
| User input        | `read`, `read -p`                               |
| Conditionals      | `if`, `elif`, `else`, `test`, `[ ]`             |
| Loops             | `for`, `while`, `until`                         |
| Pattern matching  | `case ... esac`                                 |
| Argument handling | `$#`, `$@`, `$1`, `set`, `shift`                |
| String operations | `${#}`, `${var:start:length}`, `${var/old/new}` |

---

## 🧹 **Simple Filter Commands**

Filter commands process text from **standard input** (stdin) and send results to **standard output** (stdout).

### 📄 1. `pr` – Paginate File for Printing

Formats a file for printing (adds headers, pages, etc.)

```bash
pr filename.txt           # Add headers and breaks
pr -n filename.txt        # Line numbers
pr -l 20 filename.txt     # Set page length to 20 lines
```

### 🧢 2. `head` – Display First Few Lines

Shows the first **10 lines** by default.

```bash
head filename.txt         # First 10 lines
head -n 5 filename.txt    # First 5 lines
```

### 👞 3. `tail` – Display Last Few Lines

Shows the last **10 lines** by default.

```bash
tail filename.txt         # Last 10 lines
tail -n 5 filename.txt    # Last 5 lines
```

### ✂️ 4. `cut` – Extract Columns

Extracts selected fields or characters from each line.

```bash
cut -d "," -f1 data.csv   # Get 1st field, comma delimiter
cut -c1-5 filename.txt    # Get characters 1 to 5
```

### 🪢 5. `paste` – Merge Lines

Joins lines from multiple files **side by side**.

```bash
paste file1.txt file2.txt
```

### 🪜 6. `sort` – Sort Lines

Sorts lines alphabetically or numerically.

```bash
sort names.txt                # Sort alphabetically
sort -n numbers.txt           # Sort numerically
sort -r names.txt             # Reverse order
```

### 🔂 7. `uniq` – Remove Duplicates

Removes adjacent duplicate lines.

```bash
sort data.txt | uniq              # Remove duplicates
uniq -c data.txt                  # Count duplicates
```

> ✅ Note: Use `sort` before `uniq` to group duplicates together.

### 🔄 8. `tr` – Translate or Delete Characters

```bash
echo "hello" | tr 'a-z' 'A-Z'     # Convert to uppercase
tr -d '0-9' < file.txt            # Delete all digits
```

### 🔍 **Regular Expressions and `grep`**

#### 📌 **Atoms and Operators (Basic Regex)**

##### Atoms:

- `.` – Matches **any single character**
- `^` – Start of line
- `$` – End of line
- `[...]` – Matches any character in set

##### Operators:

- `*` – Zero or more occurrences
- `\{n,m\}` – Between _n_ and _m_ times
- `\+` – One or more (extended regex)
- `\?` – Zero or one (extended regex)

#### 📘 **Examples with `grep`**

```bash
grep "word" file.txt              # Search for exact word
grep "^start" file.txt            # Lines starting with 'start'
grep "end$" file.txt              # Lines ending with 'end'
grep "[0-9]" file.txt             # Lines with any digit
grep -i "hello" file.txt          # Case-insensitive match
grep -v "skip" file.txt           # Exclude lines containing 'skip'
grep -n "error" file.txt          # Show line numbers
```

> 🔹 Use `egrep` or `grep -E` for extended regex (`+`, `?`, `{}`).

### ✅ Summary Table

| Command        | Use                              |
| -------------- | -------------------------------- |
| `pr`           | Print formatting (paginate text) |
| `head`, `tail` | View top/bottom lines            |
| `cut`, `paste` | Extract/join columns             |
| `sort`, `uniq` | Sort and remove duplicates       |
| `tr`           | Character translation            |
| `grep`         | Pattern search with regex        |

---

## **`Gagan Saini`**
