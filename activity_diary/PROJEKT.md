# Project – Activity Diary

**Individual Project Brief – Week 6 · u12**

Start: Monday, 16 November 2026. Show the working program on Monday, 23 November 2026.

## The Idea

You build a diary of your trainings that runs in the terminal. The program shows a short menu, takes your answer, and does one of four things: adds an entry, shows everything you have written, prints a summary, or quits. Every entry goes to `diary.csv`, so the diary survives when the program is closed. At the end, the summary draws the minutes per activity as a PBM picture.

This is your first program that keeps data between runs. Until now every program started from an empty list. Here the list comes back from a file, and the program grows the file one line at a time.

## Why This Project Is Yours

You play basketball and you run, and you said you want to learn Python because a certificate and a CV matter and this may be useful later. A diary is useful immediately: it is the smallest program that does something for you every week. It is also the shape of every bigger program you will meet — a menu, a choice, a loop, and a file that remembers.

## What You Already Have

- Variables, strings, `int()` conversion, `if`/`elif`/`else`, and `while` loops.
- Lists, indexing, `len()` and `for` loops.
- Reading a file line by line with `strip()` and `split(",")`.
- The PBM format from last week: a `P1` header, then a grid of `0` and `1`.

## The New Thing

Three details make the difference between a toy and a program you can actually use. Find out how to:

1. What the mode `"a"` does to a file that already exists, and how it differs from `"w"`.
2. Why a file opened with `"a"` must have a newline at the end of every line you write.
3. How `while True` works with `break`, and where the `break` belongs in a menu.
4. Why the program must read the file again after adding an entry, if the summary is to include it.
5. What happens when the file does not exist yet, and what the program should do on the first run.

**Write it down:** Create `notes.md` with `## The New Thing – appending to a file`. Explain in three sentences what `"a"` does, give one example of a line written twice by mistake, and describe what your program does when `diary.csv` does not exist. Add one sentence about the moment you understood the difference between `"a"` and `"w"`.

## The Plan

### Milestone 1 – A file you can read

Create `diary.csv` by hand.

1. Three columns: `date,activity,minutes`. Dates as `2026-11-04`.
2. Five rows: three `run`, two `basketball`.
3. Write `diary_lab.py`, read the file, and print every entry with its number.
4. Print the number of entries with `len()` and the total minutes with a loop.

At the end of this step the program prints five entries and one total.

### Milestone 2 – A menu

1. Print four options: `add`, `show`, `summary`, `quit`.
2. Read the answer with `input()`, and accept `quit` in any letter case.
3. Use `while True` with `break`, so the menu comes back after every action.
4. Print a short message for an unknown option and show the menu again.

At the end of this step you can choose an option in a loop and leave it with `quit`.

### Milestone 3 – Add an entry

1. Ask for the date, the activity and the minutes.
2. Accept only an activity from a fixed list, and only whole minutes above zero.
3. Write the entry to `diary.csv` with `"a"`, one line, ending with a newline.
4. Print a confirmation that shows what was written.

At the end of this step you add an entry, quit, start the program again, and the entry is still there.

### Milestone 4 – Show everything

1. Read the file and print every entry as an aligned line: number, date, activity, minutes.
2. Print the number of entries at the end.
3. Handle an empty file with a message, not with a crash.
4. Check the entry you added in Milestone 3 is in the list.

### Milestone 5 – The summary

1. Count the entries and the minutes per activity, using two parallel lists.
2. Print one line per activity with the count, the total minutes and the average.
3. Print the grand total and the activity with the most minutes.
4. Write `summary.txt` with the same content, so that it can be read without running the program.

### Milestone 6 – The picture

1. Create `minutes.pbm` with one bar per activity, eight rows tall, the longest bar at most two hundred pixels.
2. Draw each bar in black, with one empty row between bars.
3. Print the same bars to the terminal with `#` and `.`.
4. Compare the bars with the numbers in `summary.txt` and check that the longest bar is the activity with the most minutes.

## Example

```text
Diary - 7 entries

What do you want to do?
  add      - add an entry
  show     - show all entries
  summary  - totals per activity
  quit     - leave the program
> add

Date (YYYY-MM-DD): 2026-11-17
Activity (run, basketball, gym): basketball
Minutes: 90
Saved: 2026-11-17,basketball,90

> summary

run         4 entries   180 minutes   average 45.0
basketball  3 entries   260 minutes   average 86.7
gym         1 entry      55 minutes   average 55.0

Total: 8 entries, 495 minutes
Most minutes: basketball

summary.txt
run         4   180   45.0
basketball  3   260   86.7
gym         1    55   55.0

Saved minutes.pbm (200x26)
```

## Requirements

- One program, `diary.py`, started from the terminal with `python3 diary.py`.
- New entries are appended with `"a"`; the program never rewrites the whole file when adding a line.
- Every line ends with a newline, and every entry has exactly three fields.
- Minutes are validated before conversion, and a rejected value is not written.
- The menu returns after every action and leaves only on `quit`.
- Totals and averages are computed with loops; the average is formatted with `%.1f`.
- `minutes.pbm` has a correct header and one bar per activity in the diary.
- An empty or missing file produces a message, not a traceback.

## Files

```text
activity_diary/
├── diary.csv
├── diary_lab.py
├── diary.py
├── summary.txt
├── minutes.pbm
├── notes.md
└── check.py
```

Commit the whole directory to your repository and push it before the Monday session. A directory that exists only on your laptop cannot be checked.

Run `python3 check.py` in the project directory before you commit. It reads the files your program produced, not your code, and prints one line per requirement.


## How It Will Be Checked

- Adding an entry, quitting and restarting shows the new entry.
- The entry is one line in the file, in the right place, with three fields.
- A letter typed instead of minutes is rejected and nothing is written.
- The summary totals equal the sums of the rows in `diary.csv`.
- The bars in `minutes.pbm` are proportional to the minutes in `summary.txt`.
- You can explain what `"a"` would have done if it were `"w"`, and what you would have lost.

**Hint:** Read the file every time the summary is asked for, instead of keeping the entries in memory. It is slower, but it is always correct — and correctness matters more than speed in a diary.

**Additional challenge:** Add a `week` command that prints only the entries of the last seven days, and a `delete` command that removes the last entry. Removing a line from the middle of a file is not possible with `"a"` — you have to read the file, write a new one and replace the old one. Describe in `notes.md` what you did and why the original file must not be lost if the program stops halfway.

## Suggested Learning Resources

- [Reading and writing files – modes `"r"`, `"w"` and `"a"`](https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files)
- [The `while` statement and `break`](https://docs.python.org/3/tutorial/controlflow.html#break-and-continue-statements-and-else-clauses-on-loops)
- [The `csv` module – reading and writing tabular data](https://docs.python.org/3/library/csv.html)
- [Netpbm – description of the PBM format](https://netpbm.sourceforge.net/doc/pbm.html)

**Final goal:** By the end of this project, you should have a program that keeps a small database in a text file: it adds entries, reads them back, summarizes them and draws them as a PBM picture — using loops, conditions, lists, validation and file handling from the first five weeks.
