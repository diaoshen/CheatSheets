# Version 1

## Todos

```
    1. Basic CMD stuff
```

#### Symbols

```
    Rem <contents>  - Comments
    &       separates commands on a line
    &&      executes if previous command errorlevel is 0 meaning successful
    ||      executes if previous command errorlevel is not 0
    >       output to a file
    >&      redirects output to another file descriptor ex.  >&1 , >&2
    >>      append output to a file
    <       input from a file
    |       output of one command into input of another command
    %<number> (%1) the nth command line parameter passed to a batch file. %0 is the batchfile's name.
    %variablename% a inbuilt or user set environmental variable like %cd%
```

#### Redirection

```
Numeric handles:

STDIN  = 0  Keyboard input
STDOUT = 1  Text output
STDERR = 2  Error text output
UNDEFINED = 3-9

   command 2> filename       Redirect any error message into a file
   command 2>> filename      Append any error message into a file
  (command)2> filename       Redirect any CMD.exe error into a file
   command > file 2>&1       Redirect errors and output to one file
   command > fileA 2> fileB  Redirect output and errors to separate files

   command 2>&1 >filename    This will fail!

Redirect to NUL (hide errors)

   command 2> nul            Redirect error messages to NUL
   command >nul 2>&1         Redirect error and output to NUL
   command >filename 2> nul  Redirect output to file but suppress error
  (command)>filename 2> nul  Redirect output to file but suppress CMD.exe errors
```

## Folders

#### Current Directory

```
    %cd%
```

#### dir

```
dir /b /a-d will give you files without directories. Note there is no space between /a-d. The '-' says "NOT" directories.

From the dir /? help information:

  /A          Displays files with specified attributes.
  attributes   D  Directories                R  Read-only files
               H  Hidden files               A  Files ready for archiving
               S  System files               -  Prefix meaning not
  /B          Uses bare format (no heading information or summary).
```

#### List Empty Directory

```
cd example
for /d %%i in (*) do @dir /b /s /a-d "%%i">nul 2>&1|| @echo "%%i" has no files
give for an additional /r if you want to check subfolders too.

The trick is to list files only (/a-d) in the folder and all subfolders (/s) and if this fails (||) (because there are no files), do something with this folder (just echo here, but rd /s /q or ren is also possible)
```

#### findstr

```
Search for "granny" OR "Smith" in the files Apples.txt or Pears.txt

FINDSTR "granny Smith" Apples.txt Pears.txt

Join two files, return only the lines that they both have in common:

FINDSTR /g:"file1.txt" "file2.txt"
```

#### Run Batch File

```
    `call : execute batch file in a single thread
    start : execute batch file parallel in a new window
```

#### Prevent Auto Closing console after execution of batch file

```
    pause
    OR
    pause > nul  // to not show messages
    OR
    start batch file with cmd /k  Ex : cmd /k foo.bat
```

#### Force kill task by .exe name

```
    taskkill /f /im Vindictus.exe
```

#### Find and kill process using port xxxx
```
netstat -ano | findstr :<PORT>
taskkill /PID <PID> /F
```

# Examples

```
Rem This Program Sets time in Minutes to terminate Vindictus.exe , must run using administrator
SET /A time=60*62
timeout /t %time% /NOBREAK
taskkill /im Vindictus.exe /f
```



