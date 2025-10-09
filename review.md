Peer review from Aruzhan Tursynkhanova

### **Reproducibility Report:**

Steps that I followed to run the code:
1) Cloned the folder in GitBash on my computer.
2) Tried to open the code from GitBash - it turned out to be an .R file, so I downloaded the suggested extension to my VSCode because it is the default code editor for my PC.
3) I changed the directory to path in my PC in the **line 6**. Saved the file and returned to GitBash.
4) I run the line source("Code/Party\_Vote.R"). It froze for 7 minutes and then gave an error about environment.
5) I closed the GitBash and opened Rstudio.
6) I tried to run the code as usual, then it gave me an error because the slashes in my path were like this \\, so I manually set them to /.
7) Then I re-run the code and all missing packages and dependencies were installed. It again gave me an error:" 'eu\_ned\_ep.csv' does not exist in current working directory". There was no instruction in the README file to change directories anywhere else except for line 6.
8) I changed the line 26 to: votes <- read\_csv("Data/eu\_ned\_ep.csv").
9) Re-run the code and it run smoothly. Gave me some graphs. 
10) After I checked the folder, three .png graphs were saved in the main folder Ibnat\_miniproject, not the /Output/.

**To conclude,** I had several errors and changed three lines of code to be able to run the analysis.

### **Overall opinion:**

The idea with colored maps is interesting. The analysis itself is complex and lacks explanatory comments but the code is clean. Use of git is good but there is room for improvement.



### **Suggested improvement:**

* In the analysis .R file, modify the lines of code where relative path is required (That is, line 26 + an output generation into a separate Output/ folder since it says so in the README.md).
* README file seems to have too much information. For example, "Key Insights" and "Future work" are not necessary, and all the Analysis Workflow could be placed into a separate file. 
* Add more comments into the code! To people not familiar with geospatial analysis, it looks unclear.
* Write more meaningful commit messages. It is only written "Update ..." but it is already clear from the commit itself. 

