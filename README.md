# My-Vue-App


Created a single page Vue App for a CodeDrills internship assignment. The app contains the following scoreboard UI with options to search, sort, and filter by various categories. I have even added an option to view only those users who have solved select problems. It is also possible to view the submissions by clicking on any of them.

![scoreboard](https://user-images.githubusercontent.com/82885192/169703951-b7ddd0f0-8bd0-4d59-91fc-164c4511e1b0.jpg)

Which takes us to following submissions page in which I have added a CodeMirror component to show the submitted code. There are also options to copy the code and change the theme of the editor.

![image](https://user-images.githubusercontent.com/82885192/169703726-d46b416a-958c-404b-a061-68cc79e4e82b.png)

## Project setup

Clone the repository by downloading the project zip or using the SSH key.
Then use cd into the project folder and then run
```
npm install
```
in the terminal.

### To compile and hot-reload for development
Run
```
npm run serve
```
in the terminal. Then visit
```
http://localhost:8080/scoreboard
http://localhost:8080/submissions/
```
on any browser to access the app.

### To compile for production
```
npm run build
```
