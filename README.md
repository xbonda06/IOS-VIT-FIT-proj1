# IOS-VIT-FIT-proj1

## Skript mole (Makes One’s Life Easier)

## NAME

mole - wrapper for efficient use of the text editor with the option of automatic selection of the most frequently or last modified file.

## USAGE

mole -h
mole [-g GROUP] FILE
mole [-m] [FILTERS] [DIRECTORY]
mole list [FILTERS] [DIRECTORY]
mole secret-log [-b DATE] [-a DATE] [DIRECTORY1 [DIRECTORY2 [...]]]

## Description

-h - Prints the script usage help (the secret-log option should not be included in the help; we don't want to alert the mole that we're gathering information).
mole [-g GROUP] FILE - The specified file will be opened.
If the -g switch is provided, the file opening will also be assigned to a group named GROUP. GROUP can be the name of an existing or a new group.
mole [-m] [FILTERS] [DIRECTORY] - If DIRECTORY corresponds to an existing directory, the script will select a file to be opened from this directory.
If no directory is specified, the current directory is assumed.
If more files were edited by the script in the directory, the file that was last opened (edited) with the script will be selected.
If the -m argument was provided, the script will select the file that was opened (edited) most often by the script.
If the -m switch finds more files with the same maximum number of openings, the mole can choose any of them.
File selection can be further influenced by the given FILTERS.
If no file has been opened (edited) in the directory yet, or no file meets the specified filters, this is considered an error.
mole list [FILTERS] [DIRECTORY] - The script will display a list of files that were opened (edited) with the script in the directory.
If no directory is specified, the current directory is assumed.
The list of files can be filtered using FILTERS.
The list of files will be sorted lexicographically and each file will be listed on a separate line.
Each line will be formatted as FILENAME:<INDENT>GROUP_1,GROUP_2,..., where FILENAME is the file name (including any extensions), <INDENT> is the number of spaces needed for alignment, and GROUP_* are the names of the groups where the file is registered.
The list of groups will be sorted lexicographically.
If groups are specified using the -g switch (see FILTERS section), consider only entries belonging to these groups when listing files and groups.
If the file does not belong to any group, only the character - will be printed instead of the list of groups.
The minimum number of spaces used for alignment (INDENT) is one. Each line will be aligned so that the list of groups starts at the same position. For example:
FILE1: grp1,grp2
FILE10: grp1,grp3
FILE: -
mole secret-log [-b DATE] [-a DATE] [DIRECTORY1 [DIRECTORY2 [...]]] - The script, for the purpose of catching the mole, will create a secret compressed log with information about the files opened (edited) through the mole script.
If directories are provided, the secret log will contain records of opened (edited) files only from these directories. Non-existing directories or directories without records will be ignored.
If no directory is provided, the secret log will contain records from all recorded directories.
Opened (edited) files to be recorded in the secret log can be further limited using the -a and -b filters (see below).

## Filters

