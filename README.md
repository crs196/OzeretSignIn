# Ozeret Sign In <!-- omit in TOC -->

*written by Cooper Schwartz*

## **Table of Contents** <!-- omit in TOC -->
- [License](#license)
- [Instructions](#instructions)
  - [*Spreadsheet Format*](#spreadsheet-format)
  - [*Application Use*](#application-use)
- [Known Bugs](#known-bugs)
  - [*Blank Staff Member*](#blank-staff-member)

## License

   Copyright 2020 Cooper Schwartz

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.

---

## Instructions

### *Spreadsheet Format*

I have provided a sample spreadsheet as a means to show you a possible way to have your input spreadsheet formatted. You can find it [here](resources/files/Sample_Attendance_File.xlsx). I recommend that you leave my sample as-is and either copy it or make your own for use.  

The way that my sample is formatted is not the only way that the spreadsheet can be formatted, so feel free to set yours up in a way that makes sense to you and follows the rules outlined below.

![screenshot of sample spreadsheet](resources/images/instructions/spreadsheet_format.png)  

The `Bunk` and `Name` columns *must* be present in the spreadsheet; they are in fact the only two required columns.   
The `ID` column holds the ID that staff members sign in with is something other than their name (e.g. a number). If staff members sign in with their name, the `ID` column does not need to exist. 
The `On Time`, `Late`, and `Absent` columns can exist if you want to gather the respective summary statistics about how many times each staff member was on time, late, or absent, respectively. You don't have to have all three if you don't want to—just pick the ones you want.  

These columns can be in whatever order you want them to be, and you can feel free to add empty columns between them to space them out (as the sample does between `ID` and `On Time`).


The second and third rows should not be empty. The program will write the name of the person on Ozeret in the second row and the time of curfew in the third, so it probably makes sense to write something in those rows to say that. The sample has `Ozeret` and `Curfew`, but the exact text doesn't matter. It also doesn't matter whether the cells are merged across the columns (as the sample has it) or not. I did so in the sample because I thought it looked nicer.


Each row represents a staff member. The staff member's name should be in the `Name` column, their bunk in the `Bunk` column, and their ID in the `ID` column (if it exists). The `On Time`, `Late`, and `Absent` columns (if they exist) can either be empty or have a number in them (an empty cell is treated as if it has a 0 in it).  


Once you're satisfied with your spreadsheet's layout, save it (it doesn't matter where, but I recommend saving it in this folder for ease of access) and [start the application](OzeretSignIn.exe).

### *Application Use*

![initial screen of application](resources/images/instructions/start_window.png)

The first screen that shows up on application start-up is relatively self-explanatory. Type in your name and what time curfew is, then select `Choose File` to select the attendance spreadsheet.

![sign in window of application](resources/images/instructions/sign_in_window.png)

This is the main window of the application. In order to sign in a staff member, type/scan/enter their name (or ID, if it exists) into the text field and click the `Sign In` button or press Enter. Confirmation and error messages will be displayed on the area below the text field and the `Sign In` button.  
If you want to write all currently taken data back to the attendance spreadsheet, press the `Save` button, and if you're done signing in, press the `Save and Return to Setup` button to write back to the attendance spreadsheet and return to the previous (setup) screen.  

**VERY IMPORTANT: Make sure you do not have your attendance spreadsheet open while attempting to write to it (`Save` or `Save and Return to Setup`). The write will fail and data may be lost.**

![unacounted-for staff list](resources/images/instructions/unaccounted_staff.png)

Clicking on `View Unaccounted-for Staff Members` will bring up a list of all staff members listed in the attendance file that have not yet signed in in this session, listed by bunk. Clicking on the name of a staff member in this list will bring up additional options for them.

![additional staff sign-in options](resources/images/instructions/manual_sign_in.png)

Clicking on the `Sign In`, `Shmira`, or `Day Off` buttons in this window will sign in the listed staff member either normally, as on shmira, or as on a day off, respectively.

---

## Known Bugs

### *Blank Staff Member*

If the first "staff" row in an input spreadsheet (e.g. row 4 in the sample) is a blank row, sometimes a blank space will appear first when clicking on the `View Unaccounted-for Staff Members` button. This is treated as if the spreadsheet listed a staff member with no name and no bunk, and allows the user to sign this staff member in as normal.  

I have no idea how to reliably reproduce this bug, but I suspect it's due to my misunderstanding of the Apache POI library causing a formatting issue in the Excel spreadsheet. If you can find a way to reliably reproduce this bug, I would love to know how.