# Fingerprint Recongnizer GUI

A GUI allowing users to upload a fingerprint file and compare the fingerprint with others from the database.

## GUI

### Steps

1. Create a GUI using tkinter

![](/images/study/elec4630-fingerprint/GUI_1.jpg)

2. Allow user to input the file path
  - Show fingerprint image if the file path is correct

![](/images/study/elec4630-fingerprint/GUI_3.jpg)

  - Show error message if the file is not found
  
![](/images/study/elec4630-fingerprint/GUI_2.jpg)

3. Show local structure for input fingerprint when click the button

![](/images/study/elec4630-fingerprint/GUI_10.jpg)

  - Use scale to control the local of local structure

![](/images/study/elec4630-fingerprint/GUI_4.jpg)

4. Create a list of images in SQLite

![](/images/study/elec4630-fingerprint/GUI_5.jpg)

5. Show the comparison image of input fingerprint and selected SQLite fingerprint when click the button
  - Disable widgets from other parts

![](/images/study/elec4630-fingerprint/GUI_6.jpg)

![](/images/study/elec4630-fingerprint/GUI_7.jpg)

  - Use scale to control the local of local structure

![](/images/study/elec4630-fingerprint/GUI_8.jpg)

6. Show the ROC curve and estimated FPR when click the button
  - Disable widgets from other parts

![](/images/study/elec4630-fingerprint/GUI_9.jpg)

7. User can update the file path at anytime

### Feedback

1. Learn how to use tkinter
2. Preferred place more than pack and grid
3. Spent hours to figure out how to update the images using sclaes
4. SQLite is not as hard as imaging
5. Most comparisons have score higher than / around 0.5 (?)
6. Estimated FPR is 0 most of the time (?)
7. ROC curve seems too perfect (?)
