### Installing Dependencies

Developers should have Python3, pip3, node, and npm installed.

### Frontend dependencies

- npm install
- npm start
- Open (opens in a new tab)http://localhost:3000(opens in a new tab) to view it in the browser.

### Backend Dependencies

- virtual environment setup and running, install dependencies by navigating to the `/backend` directory and running:
- pip install -r requirements.txt
- Update DATABASE_URL in .env

## Testing

- python test_flaskr.py
- The backend is hosted at http://localhost:5000/

## API Reference

### Endpoints

#### GET '/categories'

- Fetches a dictionary of all available categories.
- Returns an object with a single key, categories, that contains a object of id: category_string key:value pairs.
- Sample: `curl http://localhost:5000/categories`

```
{
  "categories: {
    '1' : "Science",
    '2' : "Art",
    '3' : "Geography",
    '4' : "History",
    '5' : "Entertainment",
    '6' : "Sports"
    },
  "status": 200
}
```

#### GET '/categories/<int:id>/questions'

- Gets all questions in a specified category by id using url parameters
- Returns a JSON object with paginated questions from a specified category
- Sample: `curl http://localhost:5000/categories/3/questions`

```
{
  "current_category": "Geography",
  "questions": [
    {
      "answer": "Lake Victoria",
      "category": 3,
      "difficulty": 2,
      "id": 13,
      "question": "What is the largest lake in Africa?"
    },
    {
      "answer": "The Palace of Versailles",
      "category": 3,
      "difficulty": 3,
      "id": 14,
      "question": "In which royal palace would you find the Hall of Mirrors?"
    },
    {
      "answer": "Agra",
      "category": 3,
      "difficulty": 2,
      "id": 15,
      "question": "The Taj Mahal is located in which Indian city?"
    }
  ],
  "status": 200,
  "total_questions": 20
}
```

#### GET '/questions'

- Returns a list of questions
  - Includes a list of categories
  - Paginated in groups of 10
  - Includes details of question such as category, difficulty, answer and id
- Sample: `curl http://localhost:5000/questions`

```
{
  "categories": {
    "1": "Science",
    "2": "Art",
    "3": "Geography",
    "4": "History",
    "5": "Entertainment",
    "6": "Sports"
  },
  "questions": [
    {
      "answer": "Maya Angelou",
      "category": 4,
      "difficulty": 2,
      "id": 5,
      "question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
    },
    {
      "answer": "Muhammad Ali",
      "category": 4,
      "difficulty": 1,
      "id": 9,
      "question": "What boxer's original name is Cassius Clay?"
    },
    {
      "answer": "Apollo 13",
      "category": 5,
      "difficulty": 4,
      "id": 2,
      "question": "What movie earned Tom Hanks his third straight Oscar nomination, in 1996?"
    },
    {
      "answer": "Tom Cruise",
      "category": 5,
      "difficulty": 4,
      "id": 4,
      "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
    },
    {
      "answer": "Edward Scissorhands",
      "category": 5,
      "difficulty": 3,
      "id": 6,
      "question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
    },
    {
      "answer": "Brazil",
      "category": 6,
      "difficulty": 3,
      "id": 10,
      "question": "Which is the only team to play in every soccer World Cup tournament?"
    },
    {
      "answer": "Uruguay",
      "category": 6,
      "difficulty": 4,
      "id": 11,
      "question": "Which country won the first ever soccer World Cup in 1930?"
    },
    {
      "answer": "George Washington Carver",
      "category": 4,
      "difficulty": 2,
      "id": 12,
      "question": "Who invented Peanut Butter?"
    },
    {
      "answer": "Lake Victoria",
      "category": 3,
      "difficulty": 2,
      "id": 13,
      "question": "What is the largest lake in Africa?"
    },
    {
      "answer": "The Palace of Versailles",
      "category": 3,
      "difficulty": 3,
      "id": 14,
      "question": "In which royal palace would you find the Hall of Mirrors?"
    }
  ],
  "status": 200,
  "total_questions": 20
}
```

#### POST '/questions'

- Creates a new question using JSON request parameters in the database
- Sample: `curl http://localhost:5000/questions -X POST -H "Content-Type: application/json" -d '{"question": "which is the champion team of the champions 2020?", "answer": "Bayern", "difficulty": 3, "category": "6" }'`
- Created question:

```
{
    "id": 25,
    "question": "which is the champion team of the champions 2020?",
    "answer": "Bayern",
    "difficulty": 3,
    "category": 6
}
```

- JSON response:

```
{
  "created": 25,
  "question_created": "which is the champion team of the champions 2020?",
  "questions": [
    {
      "answer": "Apollo 13",
      "category": 5,
      "difficulty": 4,
      "id": 2,
      "question": "What movie earned Tom Hanks his third straight Oscar nomination, in 1996?"
    },
    {
      "answer": "Tom Cruise",
      "category": 5,
      "difficulty": 4,
      "id": 4,
      "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
    },
    {
      "answer": "Maya Angelou",
      "category": 4,
      "difficulty": 2,
      "id": 5,
      "question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
    },
    {
      "answer": "Edward Scissorhands",
      "category": 5,
      "difficulty": 3,
      "id": 6,
      "question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
    },
    {
      "answer": "Muhammad Ali",
      "category": 4,
      "difficulty": 1,
      "id": 9,
      "question": "What boxer's original name is Cassius Clay?"
    },
    {
      "answer": "Brazil",
      "category": 6,
      "difficulty": 3,
      "id": 10,
      "question": "Which is the only team to play in every soccer World Cup tournament?"
    },
    {
      "answer": "Uruguay",
      "category": 6,
      "difficulty": 4,
      "id": 11,
      "question": "Which country won the first ever soccer World Cup in 1930?"
    },
    {
      "answer": "George Washington Carver",
      "category": 4,
      "difficulty": 2,
      "id": 12,
      "question": "Who invented Peanut Butter?"
    },
    {
      "answer": "Lake Victoria",
      "category": 3,
      "difficulty": 2,
      "id": 13,
      "question": "What is the largest lake in Africa?"
    },
    {
      "answer": "The Palace of Versailles",
      "category": 3,
      "difficulty": 3,
      "id": 14,
      "question": "In which royal palace would you find the Hall of Mirrors?"
    }
  ],
  "status": 200,
  "total_questions": 21
}
```

#### POST '/questions'

- Searches for questions using a search term,
- Returns a JSON object with paginated questions matching the search term
- Sample: `curl http://localhost:5000/questions -X POST -H "Content-Type: application/json" -d '{"searchTerm": "author"}'`

```
{
  "questions": [
    {
      "answer": "Tom Cruise",
      "category": 5,
      "difficulty": 4,
      "id": 4,
      "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
    }
  ],
  "status": 200,
  "total_questions": 1
}
```

#### DELETE '/questions/<int:id>'

- Deletes a question by id using url parameters
- Returns id of deleted questions if successful
- Sample: `curl -X DELETE http://localhost:5000/questions/2`

```
{
  "deleted": 2,
  "status": 200,
  "total_questions": 20
}
```

#### POST '/quizzes'

- Allows user to play the trivia game
- Uses JSON request parameters of a chosen category and previous questions
- Returns JSON object with random available questions which are not among previous used questions
- Sample: `curl http://localhost:5000/quizzes -X POST -H "Content-Type: application/json" -d '{"previous_questions": [10, 11], "quiz_category": {"type": "Sports", "id": "6"}}'`

```
{
  "question": {
    "answer": "Bayern",
    "category": 6,
    "difficulty": 3,
    "id": 25,
    "question": "which is the champion team of the champions 2020?"
  },
  "status": 200
}
```
