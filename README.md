## Introduction
We will continue from hw1, the previous website. The main goal of this task is to write a backend server instead of the JSON server in hw1.

1. We will use a Mongo database service from Atlas.
2. The database will hold the notes data.
3. We will use Express to implement the backend, which will support fetching, adding, deleting, and removing messages.
4. implement a logger middleware.
5. Most of the material can be found in [Full Stack Open- part 3](https://fullstackopen.com/en/part3).
6. In hw1, I accidentally used 'note' and 'post'. As a result, many people use '/posts.json' instead of '/notes.json' as a JSON server input, so we changed the tests to fit both. From HW2 on, we'll align on 'note.' Please change the HTML names of the buttons and in other places from 'post' to 'note'. 

## Submission
1. Submission is in pairs, but starting alone is better for practice.
2. Coding: 70%, Questions: 30%.
3. Your submitted git repo should be *private*, please make barashd@post.bgu.ac.il and nitzanlevy (github username) collaborators.
4. Do not use external libraries that provide the pagination component. If in doubt, contact the course staff.
5. Deadline: 30.6.24, end of day.
6. Additionally, solve the [theoretical questions](https://forms.gle/r4gVbb16KKNjmW1e8).
7. Fill in repository details in (Moodle's "הגשה מטלה 2").
8. Use Typescript.
9. The ex2 forum is open for questions in Moodle.
10. Git repository content:
    1. Aim for a minimal repository size that can be cloned and installed:  most of the files in github should be code and package dependencies (package.json).
    2. Don't submit node_modules dir, .next project dir, JSON creation script, .env file, or JSON files.
11. If a specific use case is not described here, you can code it as you see fit.

## AI
Recommendation about using an AI assistant: You can ask questions and read the answers but never copy them. Understand the details, but write the code yourself. If two people copy the same AI code, it will be considered plagiarism.

## Plagiarism
1. We use a plagiarism detector.
2. The person who copies and the person who was copied from are both responsible. Set your repository private, and don't share your code.


## Code
1. Please put the previous code in a subdirectory called "frontend" and create a new directory called "backend." you can use the same GitHub link.
2. As before, we will run the frontend on port 3000 and the backend on port 3001.

4. The backend will have a middleware logger for the incoming and outgoing messages; the log is a file called "log.txt."
5. .env file will be used to define your environment variables:
    1. Atlas connection string: You'll use your own, and the tests will use a new .env file.

### Github 
As before, Hw2 will be submitted via Github.

## Prerequisites
### Tools
The hw1 tools, plus:
1. Enable requests between the frontend and backend by using cors in the backend: [CORS](https://fullstackopen.com/en/part3/deploying_app_to_internet#same-origin-policy-and-cors)
2. Read local .env file: [dotenv](https://www.npmjs.com/package/dotenv)
3. The backend uses Mongoose to query the database. [mongoose](https://mongoosejs.com/docs/index.html)
4. Use nodemon to rerun the backend automatically when the source file changes. [nodemon](https://www.npmjs.com/package/nodemon)
5. Refresh: Read about [await/async](https://javascript.info/async-await)
6. What is [express](https://expressjs.com)

## Initialize a mongo server
1. We will use the Mongo database to store the notes. It can be local or external to your machine. This task will use the external.
2. We will follow the example from [Saving data to MongoDB- MongoDB](https://fullstackopen.com/en/part3/saving_data_to_mongo_db#mongo-db). 
3. Open a free account and initialize a new database in Atlas.

## Frontend Description:
1. The front end should connect to the backend with Axios HTTP requests.
2. The UI will have buttons (see backend section for routes description):
    1. add an edit button for each note: Replace the content with an editable text initialized with the note's current content.
    2. For each note, add a delete button.
    2. One "add new note" button.
3. Like before, each page has ten notes. The backend is now responsible for fetching only ten at a time.

## Backend Description:
1. The front end should connect to the backend with Axios HTTP requests.
2. The UI will have buttons (see backend section for routes description):
    1. add an edit button for each note: Replace the content with an editable test initialized with the note's current content.
    2. For each note, add a delete button.
    2. One "add new note" button.
3. Like before, each page has ten notes. Please use Mongoose's pagination API.


## middleware Description:
1. The backend should use dotenv to read the ".env" file. It will contain "MONGODB_CONNECTION_URL = '...'", which Mongoose will use.
2. Routes:
    1. Get all notes, HTTP GET request to '/notes.'
    2. Get the i'th note, GET request to '/notes/[i].' (For example, http://localhost:3001/notes/1)
    3. Create a new note POST request to '/notes.'
    4. Update the i'th note, PUT request to 'notes/[i].'
    5. Delete the i'th note, DELETE request to 'notes/[i].'

## Atlas Description:
1. Like before, the destination Mongodb will always contain at least one note.
2. Like in the full-stack course (link above), the collection name is `notes,` and the schema will match the `note structure`:
```
{
 id: number;
 title: string;
 author: {
 name: string;
 email: string;
 } | null;
 content: string;
};
```

3. Read and use the following error codes: [HTTP response status codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)
    1. Unknown route/note number: 404
    2. Generic error response, cannot delete/update note: 500
    4. Missing fields in the request: 400.
    5. Success codes:
        1. Saved note: 201.
        2. Deleted note: 204.
        3. Other: 200.

## Checking the coding task:

## Test requirements- hw1
1. Each note should be of [class name](https://www.w3schools.com/html/html_classes.asp) **"note"**. (And not note)
2. A note must get the unique ID from the database and use it as the [html id attribute](https://www.w3schools.com/html/html_id.asp).
3. Pagination buttons:
    1. Navigation buttons should be with [html name attribute](https://www.w3schools.com/tags/att_name.asp) **"first"**, **"previous"**, **"next"**, **"last"**.
    2. Page buttons should be with the [html name attribute](https://www.w3schools.com/tags/att_name.asp) **"page-<target_page_number>"**

## Test requirements- hw2
1. [html name attributes](https://www.w3schools.com/tags/att_name.asp):
    1. Per note, `Edit`/`Delete` buttons should have **"delete-<note_id>"**, **"edit-<note_id>"**
    2. The `Add new note` button should have **"add-note"**.

### The tester will:
1. `git clone <your_submitted_github_repo>`
2. `npm install` from the `frontend` dir (package.json should exist)
3. `npm run dev` from the `frontend` dir  (configured to default port 3000)
3. Copy a `.env` file into the `backend` dir.
4. `npm install` from the `backend` dir (package.json should exist)
5. `node index.js` from the `backend` dir (configured to default port 3001)
6. Run tests.



## Good luck!

