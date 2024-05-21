## Introduction
We will implement a simple front-end app that shows user posts. The app uses json-server, which uses a JSON file as a post database and displays them to the user, split into pages.

1. A JSON server is initialized using a JSON file, which will hold the posts. The JSON file is initially small, but you will replace it with your own, much larger, JSON file.
2. The client sees the posts split into pages: 10 posts at a page. Initially, only the first page is shown to the user.
3. The UI component used is called pagination. 
4. When a specific page loads, only the messages of that page will be sent from the server for obvious efficiency reasons.

## Submission
1. Submission is in pairs, but starting alone is better for practice.
2. Coding: 70%, Questions: 30%.
3. Your submitted git repo should be *private*, please make barashd@post.bgu.ac.il and nitzanlevy (github username) collaborators.
4. Do not use external libraries that provide the pagination component. If in doubt, contact the course staff.
5. Deadline: 11.6.24, end of day.
6. Additionally, solve the [theoretical questions](https://forms.gle/zGDQF3DcPaA6iqCw6).
7. Fill in repository details in (Moodle's "הגשה מטלה 1").
8. The code will be written in typescript.

## AI
Recommendation about using an AI assistant: Think about it as your friend for class: You can ask questions and read the answers, but never copy them. Understand the details but write the code from memory: copying will be considered plagiarism, if two people copied the same AI code.

## Plagiarism
1. We use a plagiarism detector.
2. The person who copies and the person who was copied from are both responsible. Set your repository private, and don't share your code.


### Github 
Hw1 will be submitted via Github. Please open a user with your email address.
To securely update files from your machine by ssh authentication:
https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys 

or using OAuth:
https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token


## Prerequisites
### Tools
1. Chrome browser (comes with DevTools built in).
2. Visual Studio Code
3. Optional: Visual Studio Code [debugger](https://code.visualstudio.com/docs/)
3. [Next.js](https://nextjs.org/docs/getting-started/installation)
4. Git (Start here: [Atlassian](https://www.atlassian.com/git/tutorials/))

### Git
1. clone
2. add
3. commit
4. push

HW1 will be submitted via Github.
To securely update files from your machine by ssh authentication:
https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys 

### Json server
Read how to take some/all messages from the server.
https://www.npmjs.com/package/json-server
For pagination, you'll need request:
```
_page
_per_page
_limit
```
query parameters, please read the relevant docs.

### Github 
Hw1 will be submitted via Github. If you don't have a user, please create one with your BGU email address.

### Clone the project
```bash
git clone git@github.com:bgu-frontend/hw1-posts.git
```
### Install the server locally
```bash
npm install json-server
```

### Run the server with an input JSON file:

```bash
npx json-server --port 3001 --watch ./data/notes.json
```
### Create and seed the database
Create a script (not going to be tested) that creates a JSON file with a number of posts given by an input N. Use it to initialize a JSON file called "./data/notes.json."


## The task
1. Connect to the server: get posts (just) for the current page. Show 10 posts on each page.
2. add [pagination](https://www.w3schools.com/css/css3_pagination.asp) to the website. 

### Implementation
1. Show a list of posts (tip: start from a local variable holding the post list.)
2. Connect to the server: (tip: start by getting all posts.)
3. Add pagination in the UI.
4. Optimize: when rendering a page, send only the data needed now. (tip: use [_page]() route in json_server API)

## Pagination
1. The minimum number of page buttons is 1.
2. The maximum number of page buttons is 5.
3. The first page is 1.
4. The Active page button is shown in bold.
5. Which page numbers to show on the buttons? Let `a` be the current page. 
    1. If there are <=5 total pages, show all.
    2. If there are >=6 total pages: assume there are 10 ( but implement for any number of pages):
        1. if `a <3` : show buttons `[1,2,3,4,5]`
        2. if `3 <= a <= 8` : show buttons `[a-2,a-1,a,a+1,a+2]`
        3. if `a > 8`: show buttons `[6,7,8,9,10]`


## Checking the coding task:

## Test requirements
1. Each post should be of [class name](https://www.w3schools.com/html/html_classes.asp) **"post"**.
2. A post must get the unique ID from the database and use it as the [html id attribute](https://www.w3schools.com/html/html_id.asp).
3. Pagination buttons:
    1. Navigation buttons should be with [html name attribute](https://www.w3schools.com/tags/att_name.asp) **"first"**, **"previous"**, **"next"**, **"last"**.
    2. Page buttons should be with the [html name attribute](https://www.w3schools.com/tags/att_name.asp) **"page-<target_page_number>"**

### The tester will:
1. Clone and install your submitted GitHub repository.
    1. `git clone <your_submitted_github_repo>`
    2. `npm install` (package.json should exist)
    3. `npm run dev` (configured to default port 3000)
3. Start the server with a JSON file. It will always contain at least one post.
    1. `npx json-server --port 3001 ./data/notes.json`
4. Run tests.
5. Check code.


### Example HTML
```
<div class="post" id="1">
    <h2>Note 1</h2>
    <small>By Author 1</small>
    <br>
    Content for note 1
</div>
```

```
<div>
    <button name="first">First</button>
    <button name="previous">Previous</button>
    <button name="page-1">1</button>
    <button name="page-2">2</button>
    <button name="page-3">3</button>
    <button name="page-4">4</button>
    <button name="page-5">5</button>
    <button name="next">Next</button>
    <button name="last">Last</button>
</div>
```



## Good luck!

