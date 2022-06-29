Note: As of AMP 1.8 backup exclusions can be configured via the file manager GUI.

Backup exclusion files allow you to specify files or folders to be excluded from backups. The file is always named `.backupExclude` and needs to be placed in each directory for which you wish exclusions to apply.

If you place such a file in a directory, and that file is completely empty - that entire directory and all its contents will be ignored.

If you want to ignore certain items, you simply list them. You can also use wildcards to exclude extensions or basic patterns.

So for example the following would be an allowable `.backupExclude` file.

    SomeFile.ext
    someDirectory
    level_*.dat
    *.lock
    Screenshot????.jpg

Note that exclusions can't be in subdirectories, so you couldn't have:

    someDirectory/someFile