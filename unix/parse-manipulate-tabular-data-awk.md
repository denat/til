# Parse and manipulate tabular data with `awk`

`awk` is a Unix command that allows you to parse and view data that is in a structured, tabular format. That's the short description of it. Otherwise, it's actually an entire scripting language!

A simple example. Say we have a file called `grades.txt` containing a list of students and their average grades:

```
01  Julia   3.34
02  Kris    2.65
03  Darika  4.12
04  Rron    3.75
```

Things we can do using `awk`:

```bash
# Print names only
> awk '{ print $2 }' grades.txt
Julia
Kris
Darika
Rron

# Print name and average grade
> awk '{ print $2, $3 }' grades.txt
Julia 3.34
Kris 2.65
Darika 4.12
Rron 3.75

# Print number of lines. 
# END -> special pattern, meaning Awk will execute the following action once after the end of execution
# NR -> number of records
> awk 'END{ print NR }' grades.txt
4

# Print total grade average (sum all third columns, divide by number of records)
> awk '{ SUM += $3 } END { print SUM/NR }' grades.txt
3.465
```

You know what's usually in a structured, tabular format? Logs!

Say we have this sample data in a file called `logs.txt`:

```
2021-08-25 14:23:45.923 +02:00 [INF] Application started. Press Ctrl+C to shut down.
2021-08-25 14:23:45.962 +02:00 [INF] Hosting environment: Development
2021-08-25 14:23:45.964 +02:00 [INF] Content root path: D:\Projects\test-api\
2021-08-25 14:23:48.332 +02:00 [WRN] Test warning
2021-08-25 14:23:48.348 +02:00 [ERR] An unhandled exception has occurred while executing the request.
2021-08-25 14:25:43.964 +02:00 [INF] Completed processing.
2021-08-25 14:27:48.348 +02:00 [ERR] Failed to upload results to S3.
```

Cool stuff we can do:

```bash
# Print only the timestamps of the errors ([ERR] prefix)
> awk '/\[ERR\]/ { print $2 }' logs.txt
14:23:48.348
14:27:48.348

# Print the date and time of a specific log message
> awk '/An unhandled exception/ { print $1, $2 }' logs.txt
2021-08-25 14:23:48.348
```

For more useful info & resources:
* Run `man awk`
* https://arstechnica.com/gadgets/2021/08/linux-bsd-command-line-101-using-awk-sed-and-grep-in-the-terminal/