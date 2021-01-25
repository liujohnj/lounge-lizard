# Searching for Slack deprecations

A PowerShell script file was written to search for Slack deprecations in the lounge-lizard repository.  The .ps1 file(s) above themselves contain comments regarding use and other matters.  For the reader's convenience, a portion of these comments is replicated further below.


### Additional Notes

1. Feedback on errors that may have been made are VERY APPRECIATED.  It is very possible (or even probable) that some mistakes were made along the way. 
2. Included above as of 01/25/2021 are two log files, each representing the output generated from the main and fall2020 branches, respectively.  A diff operation was performed between the two files, the command being replicated below, and the files, which are the same size, appear to be identical:

   diff (cat .\deprecated_batch_itemized_fall2020_branch.log) (cat .\deprecated_batch_itemized_main_branch.log)

3. A test file named test_john.txt was included as a "sanity" check for the script, particularly as it relates to the search for the deprecated "token" usage.


### Excerpts of Comments from .ps1 file (as of 01/25/2021)

======================================== Purpose ==============================

The purpose of this Windows PowerShell script is to automate the process for
searcing a local Lounge-Lizard repository for occurrences of each of the
individual methods Slack is deprecating effective February 24, 2021.  These
methods are itemized at:

  https://api.slack.com/changelog/2020-01-deprecating-antecedents-to-the-conversations-api

In addition, the usage of "token" as a query string parameter in Web API
requests also is being deprecated on the same date, this script attempts to
identify any reliances on such token usage. More information on this can be
found at:

  https://api.slack.com/changelog/2020-11-no-more-tokens-in-querystrings-for-newly-created-apps

Finally, two fields from the Events API are being deprecated effective this
same date, and these are reflected in the script below.  Information on
this deprecation can be found at:

  https://api.slack.com/changelog/2020-09-15-events-api-truncate-authed-users

==============================Instructions====================================

To use this .ps1 script file:

1. Run PowerShell as Administrator.
2. Navigate to your local Lounge-Lizard repository and switch to the desired
   existing git branch, e.g.,:

     PS C:\Users\john\lounge-lizard\lounge-lizard> git checkout fall2020

3. To verify you are in the correct branch, use the "git branch" command.
4. Copy this .ps1 file to the root directory of your local Lounge-Lizard
   repository (or in a directory above the root directory, although this may
   yield results outside the actual repository, e.g., previously
   generated .log files).
5. The Script outputs the results to a .log (text) file.  Modify the final
   line of the script to reflect where you would like the .log file to be
   be written and, if desired, what name to give the file.
6. Set the PowerShell execution policy to run .ps1 scripts, as follows:

     PS C:\Users\john\lounge-lizard\lounge-lizard> Set-ExecutionPolicy RemoteSigned

7. At the resulting prompt, enter "Y".
8. From the directory where the script file is located, run the script using a
   a dot (.) notation, e.g.:

     PS C:\Users\john\lounge-lizard\lounge-lizard> .\search_slack_deprecations.ps1

9. Open the resulting .log file using the text editor of your choice to
   review the results.

10. COMMENTS:
    (A) Please note that the first line in the script below may exclude
    certain files from the search, e.g., *.exe, *.min, *.min.js, *.map, *.md,
    and *.ps1.
    (B) The script below likely will generate false positives.
    (C) Only one usage for token deprecation was used as a search term, and
    others should be considered.
