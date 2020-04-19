# Full Stack Trivia API Backend

## Getting Started

### Installing Dependencies

#### Python 3.7

Follow instructions to install the latest version of python for your platform in the  [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)

#### [](https://github.com/manishbisht/Udacity/tree/master/Full%20Stack%20Web%20Developer%20Nanodegree%20v2/P2%20-%20Trivia%20API/backend#virtual-enviornment)Virtual Enviornment

We recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organaized. Instructions for setting up a virual enviornment for your platform can be found in the  [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)

#### [](https://github.com/manishbisht/Udacity/tree/master/Full%20Stack%20Web%20Developer%20Nanodegree%20v2/P2%20-%20Trivia%20API/backend#pip-dependencies)PIP Dependencies

Once you have your virtual environment setup and running, install dependencies by naviging to the  `/backend`  directory and running:

pip install -r requirements.txt

This will install all of the required packages we selected within the  `requirements.txt`  file.

##### [](https://github.com/manishbisht/Udacity/tree/master/Full%20Stack%20Web%20Developer%20Nanodegree%20v2/P2%20-%20Trivia%20API/backend#key-dependencies)Key Dependencies

-   [Flask](http://flask.pocoo.org/)  is a backend microservices framework. Flask is required to handle requests and responses.
    
-   [SQLAlchemy](https://www.sqlalchemy.org/)  is the Python SQL toolkit and ORM we'll use handle the database. You'll primarily work in app.py and models.py.
    
-   [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#)  is the extension we'll use to handle cross origin resource sharing requests from our frontend server.
- ## Database Setup

With Postgres running, restore a database using the trivia.psql file provided. From the backend folder in terminal run:

    psql trivia < trivia.psql

## Running the server
From within the  `./src`  directory first ensure you are working using your created virtual environment.

Each time you open a new terminal session, run:

    export FLASK_APP=app.py;
    or
    $env:FLASK_APP="app.py"

To run the server, execute:

    flask run --reload

The  `--reload`  flag restarts the server when will happen a change on the source code.

## API Endpoints
### GET  `/categories`

-   Fetches a dictionary of categories in which the keys are the ids and the value is the corresponding string of the category.
-   Request Arguments: None
-   Returns: List of available categories.

Example Response  `{"categories":[{"id":1,"type":"Science"},{"id":2,"type":"Art"},{"id":3,"type":"Geography"},{"id":4,"type":"History"},{"id":5,"type":"Entertainment"},{"id":6,"type":"Sports"}],"success":true}`

### GET  `/questions?page=<page_number>`

-   Fetches a dictionary of categories in which the keys are the ids and the value is the corresponding string of the category.
-   Fetches a dictionary of questions in which the keys are the answer, category, difficulty, id and question.
-   Request Arguments: Page Number
-   Returns: List of questions, number of total questions, current category and categories.

**Example response:** 
    {"categories":{"1":"Science","2":"Art","3":"Geography","4":"History","5":"Entertainment","6":"Sports"},"questions":[{"answer":"Guru","category":"1","difficulty":5,"id":1,"question":"Who are you?"},{"answer":"Artery","category":"1","difficulty":2,"id":2,"question":"Which of the following is a large blood vessel that carries blood away from the heart?"},{"answer":"Leonardo da Vinci","category":"2","difficulty":2,"id":3,"question":"Who painted the Mona Lisa?"},{"answer":"Seine","category":"3","difficulty":2,"id":4,"question":"Which river flows through Paris?"},{"answer":"Anders Hejlsberg","category":"4","difficulty":3,"id":5,"question":"Who is the creator of the Delphi programming language?"},{"answer":"24th February 2013","category":"5","difficulty":5,"id":6,"question":"When the 85th Academy Awards happened?"},{"answer":"1986","category":"6","difficulty":5,"id":7,"question":"In which year did Maradona score a goal with his hand?"},{"answer":"Yes","category":"3","difficulty":4,"id":8,"question":"Do you Love Delphi?"},{"answer":"Abduraimov","category":"4","difficulty":5,"id":9,"question":"What is the surname of MuminjonGuru?"},{"answer":"2","category":"1","difficulty":1,"id":10,"question":"What is the square root of 4?"}],"success":true,"total_questions":11}

### DELETE  `/questions/<question_id>`

-   Delete question from the questions list.
-   Request Arguments: Question Id
-   Returns: true if successfully deleted.

Example Response  `{"success":true}`

### POST  `/questions`

-   Create a new question
-   Request Body: question, answer, difficulty and category.
-   Returns: true if successfully created.

Example Request Payload  `{"question":"Val__?","answer":"ve","difficulty":"2","category":1}`

Example Response  `{"success":true}`

### POST  `/questions/search`

-   Searches for the questions
-   Request Arguments: Page Number
-   Request Body: search_data
-   Returns: List of questions, number of total questions and current category.

Example Request Payload  `{"searchTerm":"guru"}`

### GET  `/categories/<int:category_id>/questions`

-   To get questions based on category
-   Request Arguments: Category Id and Page Number.
-   Returns: List of questions, number of total questions, current category and categories.

**Example Response:**
{"current_category":1,"questions":[{"answer":"Guru","category":"1","difficulty":5,"id":1,"question":"Who are you?"},{"answer":"Artery","category":"1","difficulty":2,"id":2,"question":"Which of the following is a large blood vessel that carries blood away from the heart?"},{"answer":"2","category":"1","difficulty":1,"id":10,"question":"What is the square root of 4?"}],"success":true,"total_questions":3}

### POST  `/quizzes`

-   To get questions to play the quiz.
-   Request Body: quiz_category and previous_questions.
-   Returns: Random questions within the given category.

Example Request Payload  `{"previous_questions":[],"quiz_category":{"type":"Science","id":1}}`