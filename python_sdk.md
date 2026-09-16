# 🐍 Python Master SDK

> Reusable Python reference for development, backend, data science, AI/ML, automation, APIs, databases, testing and deployment.

---

# 1. Python Installation

Check version:

```bash
python --version
```

or:

```bash
python3 --version
```

Create virtual environment:

```bash
python -m venv venv
```

Activate on Linux/macOS:

```bash
source venv/bin/activate
```

Windows:

```bash
venv\Scripts\activate
```

Deactivate:

```bash
deactivate
```

---

# 2. pip

Upgrade pip:

```bash
python -m pip install --upgrade pip
```

Install package:

```bash
pip install requests
```

Install specific version:

```bash
pip install requests==2.32.3
```

Upgrade:

```bash
pip install -U requests
```

Uninstall:

```bash
pip uninstall requests
```

List packages:

```bash
pip list
```

Freeze dependencies:

```bash
pip freeze > requirements.txt
```

Install requirements:

```bash
pip install -r requirements.txt
```

---

# 3. Python Basics

## Hello World

```python
print("Hello World")
```

---

# 4. Variables

```python
name = "Adnan"
age = 22
price = 99.5
is_active = True
```

Check type:

```python
type(name)
```

---

# 5. Data Types

```text
str
int
float
bool
list
tuple
set
dict
None
```

Example:

```python
name = "Adnan"
age = 22
price = 99.99
active = True
skills = ["Python", "SQL"]
coordinates = (10, 20)
unique_numbers = {1, 2, 3}
user = {
    "name": "Adnan",
    "age": 22
}

value = None
```

---

# 6. Type Conversion

```python
int("10")
float("10.5")
str(100)
bool(1)
```

Example:

```python
age = int(input("Enter age: "))
```

---

# 7. Input

```python
name = input("Enter your name: ")

print(name)
```

---

# 8. Operators

Arithmetic:

```python
+
-
*
/
//
%
**
```

Example:

```python
a = 10
b = 3

print(a + b)
print(a - b)
print(a * b)
print(a / b)
print(a // b)
print(a % b)
print(a ** b)
```

Comparison:

```python
==
!=
>
<
>=
<=
```

Logical:

```python
and
or
not
```

---

# 9. if / elif / else

```python
age = 22

if age >= 18:
    print("Adult")
elif age >= 13:
    print("Teenager")
else:
    print("Child")
```

---

# 10. Ternary Operator

```python
status = "Adult" if age >= 18 else "Minor"
```

---

# 11. for Loop

```python
for i in range(5):
    print(i)
```

---

# 12. while Loop

```python
i = 0

while i < 5:
    print(i)
    i += 1
```

---

# 13. break

```python
for i in range(10):

    if i == 5:
        break

    print(i)
```

---

# 14. continue

```python
for i in range(10):

    if i % 2 == 0:
        continue

    print(i)
```

---

# 15. pass

```python
def future_function():
    pass
```

---

# 16. Strings

```python
name = "Adnan"
```

Length:

```python
len(name)
```

Uppercase:

```python
name.upper()
```

Lowercase:

```python
name.lower()
```

Capitalize:

```python
name.capitalize()
```

Strip:

```python
name.strip()
```

Replace:

```python
name.replace("A", "M")
```

Split:

```python
text = "Python,Java,Go"

languages = text.split(",")
```

Join:

```python
" - ".join(languages)
```

---

# 17. f-string

```python
name = "Adnan"
age = 22

print(f"My name is {name} and I am {age} years old.")
```

---

# 18. List

Create:

```python
skills = [
    "Python",
    "SQL",
    "Flask"
]
```

Access:

```python
skills[0]
```

Last:

```python
skills[-1]
```

Add:

```python
skills.append("React")
```

Insert:

```python
skills.insert(1, "JavaScript")
```

Remove:

```python
skills.remove("SQL")
```

Pop:

```python
skills.pop()
```

Sort:

```python
skills.sort()
```

Reverse:

```python
skills.reverse()
```

---

# 19. List Slicing

```python
numbers = [1, 2, 3, 4, 5]

numbers[1:4]
```

Output:

```text
[2, 3, 4]
```

---

# 20. List Comprehension

Normal:

```python
squares = []

for i in range(10):
    squares.append(i * i)
```

Comprehension:

```python
squares = [
    i * i
    for i in range(10)
]
```

With condition:

```python
even = [
    i
    for i in range(10)
    if i % 2 == 0
]
```

---

# 21. Tuple

```python
point = (10, 20)
```

Access:

```python
point[0]
```

Tuple unpacking:

```python
x, y = point
```

---

# 22. Set

```python
numbers = {1, 2, 3, 3}
```

Output:

```text
{1, 2, 3}
```

Add:

```python
numbers.add(4)
```

Remove:

```python
numbers.remove(2)
```

---

# 23. Set Operations

Union:

```python
a | b
```

Intersection:

```python
a & b
```

Difference:

```python
a - b
```

Symmetric difference:

```python
a ^ b
```

---

# 24. Dictionary

```python
user = {
    "name": "Adnan",
    "age": 22,
    "city": "Bihar"
}
```

Access:

```python
user["name"]
```

Safe access:

```python
user.get("name")
```

Add:

```python
user["email"] = "adnan@example.com"
```

Update:

```python
user["age"] = 23
```

Delete:

```python
del user["city"]
```

---

# 25. Dictionary Methods

```python
user.keys()
user.values()
user.items()
```

Loop:

```python
for key, value in user.items():
    print(key, value)
```

---

# 26. Dictionary Comprehension

```python
squares = {
    i: i * i
    for i in range(5)
}
```

---

# 27. Functions

```python
def add(a, b):
    return a + b
```

Call:

```python
result = add(10, 20)
```

---

# 28. Default Arguments

```python
def greet(name="User"):
    return f"Hello {name}"
```

---

# 29. *args

```python
def add(*numbers):
    return sum(numbers)
```

Usage:

```python
add(1, 2, 3, 4)
```

---

# 30. **kwargs

```python
def create_user(**data):
    print(data)
```

Usage:

```python
create_user(
    name="Adnan",
    age=22
)
```

---

# 31. Lambda

```python
square = lambda x: x * x
```

---

# 32. map()

```python
numbers = [1, 2, 3, 4]

squares = list(
    map(lambda x: x * x, numbers)
)
```

---

# 33. filter()

```python
numbers = [1, 2, 3, 4, 5]

even = list(
    filter(lambda x: x % 2 == 0, numbers)
)
```

---

# 34. zip()

```python
names = ["A", "B", "C"]
ages = [20, 21, 22]

data = list(zip(names, ages))
```

---

# 35. enumerate()

```python
skills = ["Python", "SQL", "Flask"]

for index, skill in enumerate(skills):
    print(index, skill)
```

---

# 36. Exception Handling

```python
try:
    x = 10 / 0

except ZeroDivisionError:
    print("Cannot divide by zero")

finally:
    print("Done")
```

---

# 37. Multiple Exceptions

```python
try:
    number = int(input())

except ValueError:
    print("Invalid number")

except Exception as e:
    print(e)
```

---

# 38. Raise

```python
age = 15

if age < 18:
    raise ValueError("Age must be 18+")
```

---

# 39. Custom Exception

```python
class UserNotFoundError(Exception):
    pass
```

---

# 40. File Handling

Read:

```python
with open("data.txt", "r") as file:
    content = file.read()
```

Write:

```python
with open("data.txt", "w") as file:
    file.write("Hello")
```

Append:

```python
with open("data.txt", "a") as file:
    file.write("\nNew line")
```

---

# 41. pathlib

```python
from pathlib import Path

path = Path("data.txt")

print(path.exists())
print(path.name)
print(path.suffix)
```

Create directory:

```python
Path("data").mkdir(
    exist_ok=True
)
```

---

# 42. JSON

```python
import json
```

Python → JSON:

```python
data = {
    "name": "Adnan",
    "age": 22
}

json_string = json.dumps(data)
```

JSON → Python:

```python
data = json.loads(json_string)
```

File:

```python
with open("data.json", "w") as file:
    json.dump(data, file, indent=4)
```

---

# 43. CSV

```python
import csv
```

Read:

```python
with open("users.csv") as file:

    reader = csv.DictReader(file)

    for row in reader:
        print(row)
```

Write:

```python
with open(
    "users.csv",
    "w",
    newline=""
) as file:

    writer = csv.DictWriter(
        file,
        fieldnames=["name", "email"]
    )

    writer.writeheader()

    writer.writerow({
        "name": "Adnan",
        "email": "adnan@example.com"
    })
```

---

# 44. Modules

Create:

```text
math_utils.py
```

```python
def add(a, b):
    return a + b
```

Import:

```python
from math_utils import add
```

---

# 45. Packages

```text
project/
│
├── app.py
│
└── utils/
    ├── __init__.py
    └── math.py
```

Import:

```python
from utils.math import add
```

---

# 46. __name__

```python
if __name__ == "__main__":
    print("Running directly")
```

---

# 47. Classes

```python
class User:

    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        return f"Hello {self.name}"
```

Create object:

```python
user = User("Adnan", 22)

print(user.greet())
```

---

# 48. Inheritance

```python
class Animal:

    def speak(self):
        print("Animal sound")


class Dog(Animal):

    def speak(self):
        print("Bark")
```

---

# 49. Dataclass

```python
from dataclasses import dataclass


@dataclass
class User:

    name: str
    age: int
```

Usage:

```python
user = User(
    name="Adnan",
    age=22
)
```

---

# 50. Type Hints

```python
def add(
    a: int,
    b: int
) -> int:

    return a + b
```

List:

```python
def get_names() -> list[str]:
    return ["A", "B"]
```

Optional:

```python
def get_user(
    id: int
) -> str | None:

    return None
```

---

# 51. Generators

```python
def numbers():

    for i in range(5):
        yield i
```

Usage:

```python
for number in numbers():
    print(number)
```

---

# 52. Decorators

```python
def logger(func):

    def wrapper(*args, **kwargs):

        print("Calling function")

        result = func(*args, **kwargs)

        print("Finished")

        return result

    return wrapper
```

Use:

```python
@logger
def hello():
    print("Hello")
```

---

# 53. Context Manager

```python
with open("file.txt") as file:
    data = file.read()
```

Custom context managers can be created using:

```python
from contextlib import contextmanager
```

---

# 54. Iterators

```python
numbers = iter([1, 2, 3])

print(next(numbers))
print(next(numbers))
print(next(numbers))
```

---

# 55. Regular Expressions

```python
import re
```

Search:

```python
text = "My phone is 9876543210"

match = re.search(
    r"\d{10}",
    text
)

print(match.group())
```

Email pattern:

```python
pattern = r"^[\w.-]+@[\w.-]+\.\w+$"
```

---

# 56. datetime

```python
from datetime import datetime

now = datetime.now()

print(now)
```

Format:

```python
now.strftime("%d/%b/%Y")
```

Example:

```text
12/Apr/2023
```

Only year:

```python
now.strftime("%Y")
```

---

# 57. time

```python
import time

time.sleep(2)
```

---

# 58. random

```python
import random

random.randint(1, 100)
```

Random choice:

```python
random.choice(
    ["Python", "Java", "Go"]
)
```

---

# 59. math

```python
import math

math.sqrt(25)
math.ceil(4.2)
math.floor(4.8)
math.pi
```

---

# 60. statistics

```python
import statistics

numbers = [10, 20, 30, 40]

statistics.mean(numbers)
statistics.median(numbers)
statistics.stdev(numbers)
```

---

# 61. collections

```python
from collections import Counter
```

```python
Counter(
    ["Python", "Python", "SQL"]
)
```

---

# 62. defaultdict

```python
from collections import defaultdict

data = defaultdict(list)

data["python"].append("Flask")
```

---

# 63. deque

```python
from collections import deque

queue = deque()

queue.append("A")
queue.append("B")

queue.popleft()
```

---

# 64. itertools

```python
import itertools
```

Useful functions:

```text
product
permutations
combinations
chain
groupby
```

Example:

```python
list(
    itertools.combinations(
        [1, 2, 3],
        2
    )
)
```

---

# 65. functools

```python
from functools import lru_cache
```

```python
@lru_cache
def fibonacci(n):

    if n < 2:
        return n

    return (
        fibonacci(n - 1)
        + fibonacci(n - 2)
    )
```

---

# 66. os

```python
import os

os.getcwd()
os.listdir()
os.getenv("DATABASE_URL")
```

---

# 67. sys

```python
import sys

print(sys.argv)
```

Example:

```bash
python app.py input.txt
```

Then:

```python
sys.argv[1]
```

---

# 68. subprocess

```python
import subprocess

result = subprocess.run(
    ["python", "--version"],
    capture_output=True,
    text=True
)

print(result.stdout)
```

---

# 69. logging

```python
import logging

logging.basicConfig(
    level=logging.INFO
)

logging.info("Server started")
logging.warning("Warning")
logging.error("Something went wrong")
```

---

# 70. NumPy

Install:

```bash
pip install numpy
```

Import:

```python
import numpy as np
```

---

# 71. NumPy Array

```python
arr = np.array(
    [1, 2, 3, 4]
)
```

2D:

```python
matrix = np.array([
    [1, 2],
    [3, 4]
])
```

---

# 72. NumPy Properties

```python
arr.shape
arr.ndim
arr.size
arr.dtype
```

---

# 73. NumPy Creation

Zeros:

```python
np.zeros(5)
```

Ones:

```python
np.ones(5)
```

Range:

```python
np.arange(0, 10, 2)
```

Evenly spaced:

```python
np.linspace(0, 1, 5)
```

Identity matrix:

```python
np.eye(3)
```

---

# 74. NumPy Operations

```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

a + b
a - b
a * b
a / b
```

---

# 75. NumPy Statistics

```python
np.mean(arr)
np.median(arr)
np.std(arr)
np.var(arr)
np.min(arr)
np.max(arr)
np.sum(arr)
```

---

# 76. NumPy Reshape

```python
arr = np.arange(12)

matrix = arr.reshape(3, 4)
```

Flatten:

```python
matrix.flatten()
```

---

# 77. NumPy Indexing

```python
arr[0]
arr[-1]
arr[1:4]
```

2D:

```python
matrix[0, 1]
```

---

# 78. NumPy Boolean Filtering

```python
arr[arr > 5]
```

---

# 79. NumPy Random

```python
np.random.rand(3)
```

Random integers:

```python
np.random.randint(
    1,
    100,
    size=10
)
```

---

# 80. Pandas

Install:

```bash
pip install pandas
```

Import:

```python
import pandas as pd
```

---

# 81. Series

```python
s = pd.Series(
    [10, 20, 30]
)
```

---

# 82. DataFrame

```python
df = pd.DataFrame({
    "name": ["A", "B", "C"],
    "age": [20, 21, 22]
})
```

---

# 83. Read CSV

```python
df = pd.read_csv("users.csv")
```

---

# 84. Read Excel

```python
df = pd.read_excel("users.xlsx")
```

---

# 85. Write CSV

```python
df.to_csv(
    "output.csv",
    index=False
)
```

---

# 86. DataFrame Inspection

```python
df.head()
df.tail()
df.info()
df.describe()
df.shape
df.columns
df.dtypes
```

---

# 87. Select Column

```python
df["name"]
```

Multiple:

```python
df[
    ["name", "age"]
]
```

---

# 88. Filtering

```python
df[
    df["age"] > 20
]
```

Multiple:

```python
df[
    (df["age"] > 20)
    &
    (df["city"] == "Patna")
]
```

---

# 89. loc

```python
df.loc[
    df["age"] > 20,
    ["name", "age"]
]
```

---

# 90. iloc

```python
df.iloc[0]
```

```python
df.iloc[0:5, 0:2]
```

---

# 91. Missing Values

Check:

```python
df.isna()
```

Count:

```python
df.isna().sum()
```

Drop:

```python
df.dropna()
```

Fill:

```python
df.fillna(0)
```

---

# 92. Duplicate Rows

```python
df.duplicated()
```

Remove:

```python
df.drop_duplicates()
```

---

# 93. Sorting

```python
df.sort_values(
    "age"
)
```

Descending:

```python
df.sort_values(
    "age",
    ascending=False
)
```

---

# 94. GroupBy

```python
df.groupby(
    "city"
)["salary"]
.mean()
```

Multiple aggregations:

```python
df.groupby("city")["salary"].agg([
    "mean",
    "min",
    "max"
])
```

---

# 95. Merge

```python
result = pd.merge(
    users,
    orders,
    on="user_id",
    how="inner"
)
```

Types:

```text
inner
left
right
outer
```

---

# 96. concat

```python
result = pd.concat(
    [df1, df2]
)
```

---

# 97. Apply

```python
df["age2"] = df["age"].apply(
    lambda x: x + 1
)
```

---

# 98. Pandas Datetime

```python
df["created_at"] = pd.to_datetime(
    df["created_at"]
)
```

Extract year:

```python
df["year"] = (
    df["created_at"].dt.year
)
```

Month:

```python
df["month"] = (
    df["created_at"].dt.month
)
```

---

# 99. Matplotlib

Install:

```bash
pip install matplotlib
```

Import:

```python
import matplotlib.pyplot as plt
```

---

# 100. Line Plot

```python
plt.plot(
    [1, 2, 3, 4],
    [10, 20, 15, 30]
)

plt.xlabel("X")
plt.ylabel("Y")
plt.title("Line Chart")

plt.show()
```

---

# 101. Bar Chart

```python
plt.bar(
    ["A", "B", "C"],
    [10, 20, 15]
)

plt.show()
```

---

# 102. Scatter Plot

```python
plt.scatter(
    [1, 2, 3],
    [10, 20, 15]
)

plt.show()
```

---

# 103. Histogram

```python
plt.hist(
    [10, 12, 15, 15, 20, 22]
)

plt.show()
```

---

# 104. Save Plot

```python
plt.savefig(
    "chart.png",
    dpi=300,
    bbox_inches="tight"
)
```

---

# 105. Seaborn

Install:

```bash
pip install seaborn
```

Import:

```python
import seaborn as sns
```

Example:

```python
sns.scatterplot(
    data=df,
    x="age",
    y="salary"
)

plt.show()
```

---

# 106. Heatmap

```python
sns.heatmap(
    df.corr(numeric_only=True),
    annot=True
)

plt.show()
```

---

# 107. SciPy

Install:

```bash
pip install scipy
```

Import:

```python
from scipy import stats
```

Example:

```python
stats.mean([1, 2, 3])
```

Common modules:

```text
scipy.stats
scipy.optimize
scipy.integrate
scipy.linalg
scipy.signal
scipy.spatial
```

---

# 108. Scikit-learn

Install:

```bash
pip install scikit-learn
```

Import:

```python
import sklearn
```

---

# 109. Train/Test Split

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = (
    train_test_split(
        X,
        y,
        test_size=0.2,
        random_state=42
    )
)
```

---

# 110. Linear Regression

```python
from sklearn.linear_model import LinearRegression

model = LinearRegression()

model.fit(
    X_train,
    y_train
)

predictions = model.predict(
    X_test
)
```

---

# 111. Logistic Regression

```python
from sklearn.linear_model import LogisticRegression

model = LogisticRegression()

model.fit(
    X_train,
    y_train
)
```

---

# 112. Decision Tree

```python
from sklearn.tree import DecisionTreeClassifier

model = DecisionTreeClassifier()

model.fit(
    X_train,
    y_train
)
```

---

# 113. Random Forest

```python
from sklearn.ensemble import RandomForestClassifier

model = RandomForestClassifier(
    n_estimators=100,
    random_state=42
)

model.fit(
    X_train,
    y_train
)
```

---

# 114. KNN

```python
from sklearn.neighbors import KNeighborsClassifier

model = KNeighborsClassifier(
    n_neighbors=5
)

model.fit(
    X_train,
    y_train
)
```

---

# 115. SVM

```python
from sklearn.svm import SVC

model = SVC()

model.fit(
    X_train,
    y_train
)
```

---

# 116. K-Means

```python
from sklearn.cluster import KMeans

model = KMeans(
    n_clusters=3,
    random_state=42
)

model.fit(X)
```

---

# 117. StandardScaler

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()

X_train_scaled = scaler.fit_transform(
    X_train
)

X_test_scaled = scaler.transform(
    X_test
)
```

Important:

```text
fit_transform → training data
transform     → test/new data
```

---

# 118. OneHotEncoder

```python
from sklearn.preprocessing import OneHotEncoder

encoder = OneHotEncoder(
    handle_unknown="ignore"
)

X_encoded = encoder.fit_transform(
    X
)
```

---

# 119. Metrics

Accuracy:

```python
from sklearn.metrics import accuracy_score

accuracy_score(
    y_test,
    predictions
)
```

Precision:

```python
from sklearn.metrics import precision_score
```

Recall:

```python
from sklearn.metrics import recall_score
```

F1:

```python
from sklearn.metrics import f1_score
```

Confusion matrix:

```python
from sklearn.metrics import confusion_matrix
```

---

# 120. Regression Metrics

```python
from sklearn.metrics import (
    mean_absolute_error,
    mean_squared_error,
    r2_score
)
```

---

# 121. Pipeline

```python
from sklearn.pipeline import Pipeline

pipeline = Pipeline([
    ("scaler", StandardScaler()),
    ("model", LogisticRegression())
])

pipeline.fit(
    X_train,
    y_train
)
```

---

# 122. Cross Validation

```python
from sklearn.model_selection import cross_val_score

scores = cross_val_score(
    model,
    X,
    y,
    cv=5
)
```

---

# 123. Grid Search

```python
from sklearn.model_selection import GridSearchCV

grid = GridSearchCV(
    model,
    param_grid,
    cv=5
)

grid.fit(X_train, y_train)
```

---

# 124. Joblib

Save ML model:

```python
import joblib

joblib.dump(
    model,
    "model.pkl"
)
```

Load:

```python
model = joblib.load(
    "model.pkl"
)
```

> Only load trusted model files.

---

# 125. Requests

Install:

```bash
pip install requests
```

GET:

```python
import requests

response = requests.get(
    "https://api.example.com/users"
)

data = response.json()
```

POST:

```python
response = requests.post(
    "https://api.example.com/users",
    json={
        "name": "Adnan"
    }
)
```

---

# 126. Requests Headers

```python
headers = {
    "Authorization": "Bearer TOKEN",
    "Content-Type": "application/json"
}

response = requests.get(
    url,
    headers=headers
)
```

---

# 127. Requests Timeout

```python
response = requests.get(
    url,
    timeout=10
)
```

Always set a reasonable timeout for production network calls.

---

# 128. BeautifulSoup

Install:

```bash
pip install beautifulsoup4 requests
```

```python
import requests
from bs4 import BeautifulSoup

response = requests.get(url)

soup = BeautifulSoup(
    response.text,
    "html.parser"
)

title = soup.title.text
```

---

# 129. HTML Elements

```python
soup.find("h1")
```

All:

```python
soup.find_all("a")
```

CSS selector:

```python
soup.select(".card")
```

---

# 130. Flask

Install:

```bash
pip install flask
```

Basic:

```python
from flask import Flask

app = Flask(__name__)


@app.get("/")
def home():
    return {
        "message": "Hello"
    }


if __name__ == "__main__":
    app.run(debug=True)
```

---

# 131. Flask POST

```python
from flask import request


@app.post("/users")
def create_user():

    data = request.get_json()

    return {
        "name": data["name"]
    }
```

---

# 132. Flask Route Parameter

```python
@app.get("/users/<int:user_id>")
def get_user(user_id):

    return {
        "id": user_id
    }
```

---

# 133. FastAPI

Install:

```bash
pip install fastapi uvicorn
```

Basic:

```python
from fastapi import FastAPI

app = FastAPI()


@app.get("/")
def home():

    return {
        "message": "Hello"
    }
```

Run:

```bash
uvicorn main:app --reload
```

---

# 134. Pydantic

Install:

```bash
pip install pydantic
```

```python
from pydantic import BaseModel


class User(BaseModel):

    name: str
    age: int
```

---

# 135. SQLAlchemy

Install:

```bash
pip install sqlalchemy psycopg
```

Connection:

```python
from sqlalchemy import create_engine

engine = create_engine(
    "postgresql+psycopg://"
    "postgres:password@localhost:5432/mydb"
)
```

---

# 136. PostgreSQL with Psycopg

```bash
pip install psycopg
```

```python
import psycopg

conn = psycopg.connect(
    "dbname=mydb "
    "user=postgres "
    "password=password "
    "host=localhost"
)

cur = conn.cursor()

cur.execute(
    "SELECT * FROM users"
)

rows = cur.fetchall()

conn.close()
```

---

# 137. SQLite

Built into Python:

```python
import sqlite3

conn = sqlite3.connect(
    "database.db"
)

cursor = conn.cursor()

cursor.execute("""
CREATE TABLE IF NOT EXISTS users (
    id INTEGER PRIMARY KEY,
    name TEXT
)
""")

conn.commit()
```

---

# 138. Asyncio

```python
import asyncio


async def hello():

    print("Hello")
    await asyncio.sleep(1)
    print("Done")


asyncio.run(hello())
```

---

# 139. Async Function

```python
async def fetch_data():
    ...
```

Call:

```python
await fetch_data()
```

---

# 140. aiohttp

Install:

```bash
pip install aiohttp
```

```python
import aiohttp
import asyncio


async def main():

    async with aiohttp.ClientSession() as session:

        async with session.get(url) as response:

            data = await response.json()

            print(data)


asyncio.run(main())
```

---

# 141. Threading

```python
import threading


def task():
    print("Running")


thread = threading.Thread(
    target=task
)

thread.start()
thread.join()
```

---

# 142. Multiprocessing

```python
from multiprocessing import Process


def task():
    print("Running")


process = Process(
    target=task
)

process.start()
process.join()
```

---

# 143. Concurrent Futures

```python
from concurrent.futures import ThreadPoolExecutor

with ThreadPoolExecutor(
    max_workers=5
) as executor:

    results = executor.map(
        task,
        items
    )
```

---

# 144. Pytest

Install:

```bash
pip install pytest
```

Test:

```python
def add(a, b):
    return a + b
```

```python
def test_add():

    assert add(2, 3) == 5
```

Run:

```bash
pytest
```

---

# 145. unittest

```python
import unittest


class TestMath(unittest.TestCase):

    def test_add(self):

        self.assertEqual(
            2 + 3,
            5
        )


if __name__ == "__main__":
    unittest.main()
```

---

# 146. Mock

```python
from unittest.mock import Mock

api = Mock()

api.get_user.return_value = {
    "id": 1
}
```

---

# 147. Environment Variables

Install:

```bash
pip install python-dotenv
```

`.env`

```env
DATABASE_URL=postgresql://...
SECRET_KEY=secret
API_KEY=abc123
```

Python:

```python
from dotenv import load_dotenv
import os

load_dotenv()

database_url = os.getenv(
    "DATABASE_URL"
)
```

---

# 148. Pydantic Settings

Install:

```bash
pip install pydantic-settings
```

```python
from pydantic_settings import BaseSettings


class Settings(BaseSettings):

    database_url: str
    secret_key: str

    class Config:
        env_file = ".env"
```

---

# 149. Password Hashing

Install:

```bash
pip install pwdlib[argon2]
```

```python
from pwdlib import PasswordHash

password_hash = PasswordHash.recommended()

hashed = password_hash.hash(
    "mypassword"
)

password_hash.verify(
    "mypassword",
    hashed
)
```

---

# 150. JWT

Install:

```bash
pip install PyJWT
```

Create token:

```python
import jwt

token = jwt.encode(
    {
        "user_id": 1
    },
    "secret-key",
    algorithm="HS256"
)
```

Decode:

```python
payload = jwt.decode(
    token,
    "secret-key",
    algorithms=["HS256"]
)
```

Use strong secrets and appropriate token expiry in real applications.

---

# 151. OpenCV

Install:

```bash
pip install opencv-python
```

Import:

```python
import cv2
```

Read image:

```python
image = cv2.imread(
    "image.jpg"
)
```

Display:

```python
cv2.imshow(
    "Image",
    image
)

cv2.waitKey(0)
cv2.destroyAllWindows()
```

---

# 152. OpenCV Resize

```python
resized = cv2.resize(
    image,
    (800, 600)
)
```

---

# 153. OpenCV Grayscale

```python
gray = cv2.cvtColor(
    image,
    cv2.COLOR_BGR2GRAY
)
```

---

# 154. Pillow

Install:

```bash
pip install pillow
```

```python
from PIL import Image

image = Image.open(
    "image.jpg"
)

print(image.size)
```

Resize:

```python
image = image.resize(
    (800, 600)
)
```

Save:

```python
image.save(
    "output.jpg"
)
```

---

# 155. PyTorch

Install according to your system/device requirements.

```bash
pip install torch
```

Import:

```python
import torch
```

Tensor:

```python
x = torch.tensor([
    [1, 2],
    [3, 4]
])
```

---

# 156. PyTorch Tensor Properties

```python
x.shape
x.dtype
x.device
```

---

# 157. PyTorch Neural Network

```python
import torch
import torch.nn as nn


class Model(nn.Module):

    def __init__(self):

        super().__init__()

        self.network = nn.Sequential(
            nn.Linear(10, 32),
            nn.ReLU(),
            nn.Linear(32, 1)
        )

    def forward(self, x):

        return self.network(x)
```

---

# 158. PyTorch Dataset

```python
from torch.utils.data import Dataset


class MyDataset(Dataset):

    def __init__(self, X, y):

        self.X = X
        self.y = y

    def __len__(self):

        return len(self.X)

    def __getitem__(self, index):

        return (
            self.X[index],
            self.y[index]
        )
```

---

# 159. PyTorch DataLoader

```python
from torch.utils.data import DataLoader

loader = DataLoader(
    dataset,
    batch_size=32,
    shuffle=True
)
```

---

# 160. Transformers

Install:

```bash
pip install transformers
```

Import:

```python
from transformers import pipeline
```

Sentiment:

```python
classifier = pipeline(
    "sentiment-analysis"
)

classifier(
    "I love Python"
)
```

---

# 161. Tokenizer

```python
from transformers import AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained(
    "model-name"
)
```

---

# 162. Hugging Face Model

```python
from transformers import AutoModel

model = AutoModel.from_pretrained(
    "model-name"
)
```

---

# 163. LangChain

Install the packages required by the specific integrations you use.

Typical:

```bash
pip install langchain
```

Basic concept:

```text
Document
   ↓
Loader
   ↓
Splitter
   ↓
Embeddings
   ↓
Vector Store
   ↓
Retriever
   ↓
LLM
   ↓
Response
```

---

# 164. RAG

```text
User Question
      ↓
Embedding
      ↓
Vector Search
      ↓
Relevant Documents
      ↓
Prompt
      ↓
LLM
      ↓
Answer
```

Common components:

```text
LangChain
LangGraph
Vector Database
Embeddings
LLM
```

---

# 165. BeautifulSoup vs Requests

```text
Requests
→ downloads HTTP response

BeautifulSoup
→ parses HTML
```

Typical:

```python
response = requests.get(url)

soup = BeautifulSoup(
    response.text,
    "html.parser"
)
```

---

# 166. SQLModel

Install:

```bash
pip install sqlmodel
```

Example:

```python
from sqlmodel import (
    SQLModel,
    Field
)


class User(SQLModel, table=True):

    id: int | None = Field(
        default=None,
        primary_key=True
    )

    name: str
```

---

# 167. Redis

Install Python client:

```bash
pip install redis
```

```python
import redis

client = redis.Redis(
    host="localhost",
    port=6379,
    decode_responses=True
)

client.set(
    "name",
    "Adnan"
)

print(
    client.get("name")
)
```

---

# 168. Celery

Install:

```bash
pip install celery
```

Concept:

```text
API
 ↓
Task Queue
 ↓
Worker
 ↓
Long-running task
```

Useful for:

```text
Email
PDF generation
Image processing
Background jobs
Scheduled jobs
```

---

# 169. APScheduler

Useful for scheduled Python jobs.

Typical use cases:

```text
Daily task
Hourly task
Periodic API call
Scheduled cleanup
```

---

# 170. Typer

CLI applications:

```bash
pip install typer
```

```python
import typer

app = typer.Typer()


@app.command()
def hello(name: str):

    print(f"Hello {name}")


if __name__ == "__main__":
    app()
```

---

# 171. Rich

Install:

```bash
pip install rich
```

```python
from rich import print

print(
    "[bold green]Success[/bold green]"
)
```

Useful for:

```text
CLI
Logging
Tables
Progress bars
Debugging
```

---

# 172. Click

```bash
pip install click
```

```python
import click


@click.command()
@click.option("--name")
def hello(name):

    click.echo(
        f"Hello {name}"
    )
```

---

# 173. HTTPX

Install:

```bash
pip install httpx
```

Sync:

```python
import httpx

response = httpx.get(
    url,
    timeout=10
)
```

Async:

```python
async with httpx.AsyncClient() as client:

    response = await client.get(
        url
    )
```

---

# 174. Pydantic Validation

```python
from pydantic import BaseModel, Field


class User(BaseModel):

    name: str

    age: int = Field(
        ge=18,
        le=100
    )
```

---

# 175. Email Validation

Install:

```bash
pip install pydantic[email]
```

```python
from pydantic import BaseModel
from pydantic import EmailStr


class User(BaseModel):

    email: EmailStr
```

---

# 176. YAML

Install:

```bash
pip install pyyaml
```

```python
import yaml

with open("config.yaml") as file:

    data = yaml.safe_load(file)
```

---

# 177. XML

Built-in:

```python
import xml.etree.ElementTree as ET
```

---

# 178. Hashing

```python
import hashlib

hash_value = hashlib.sha256(
    b"hello"
).hexdigest()
```

---

# 179. Secrets

Use `secrets` for security-sensitive random values:

```python
import secrets

token = secrets.token_urlsafe(32)
```

---

# 180. Base64

```python
import base64

encoded = base64.b64encode(
    b"Hello"
)

decoded = base64.b64decode(
    encoded
)
```

---

# 181. UUID

```python
import uuid

id = uuid.uuid4()

print(id)
```

---

# 182. Hashlib vs Password Hashing

```text
hashlib
→ general hashing

Argon2 / bcrypt
→ password hashing
```

Do not store passwords using plain SHA-256 alone.

---

# 183. Python Project Structure

```text
project/
│
├── app/
│   ├── __init__.py
│   ├── main.py
│   │
│   ├── routes/
│   ├── models/
│   ├── schemas/
│   ├── services/
│   ├── repositories/
│   ├── utils/
│   └── core/
│
├── tests/
│
├── .env
├── .env.example
├── .gitignore
├── requirements.txt
└── README.md
```

---

# 184. Recommended Backend Architecture

```text
Frontend
   ↓
API Route
   ↓
Schema Validation
   ↓
Service Layer
   ↓
Repository / ORM
   ↓
Database
```

Example:

```text
POST /users
      ↓
Router
      ↓
Pydantic Schema
      ↓
User Service
      ↓
SQLAlchemy
      ↓
PostgreSQL
```

---

# 185. Requirements File

Example:

```text
fastapi
uvicorn
sqlalchemy
psycopg
pydantic
pydantic-settings
python-dotenv
```

Generate automatically:

```bash
pip freeze > requirements.txt
```

---

# 186. pyproject.toml

Modern Python projects commonly use:

```toml
[project]
name = "my-project"
version = "0.1.0"
description = "My Python project"
requires-python = ">=3.12"

dependencies = [
    "fastapi",
    "uvicorn",
    "sqlalchemy",
]
```

---

# 187. Ruff

Install:

```bash
pip install ruff
```

Check:

```bash
ruff check .
```

Format:

```bash
ruff format .
```

---

# 188. Black

Install:

```bash
pip install black
```

Format:

```bash
black .
```

---

# 189. mypy

Install:

```bash
pip install mypy
```

Run:

```bash
mypy .
```

Useful for static type checking.

---

# 190. Pre-commit

Install:

```bash
pip install pre-commit
```

Typical use:

```text
Git commit
   ↓
Lint
   ↓
Format
   ↓
Tests
   ↓
Commit
```

---

# 191. Docker + Python

`Dockerfile`

```dockerfile
FROM python:3.12-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir \
    -r requirements.txt

COPY . .

CMD ["python", "main.py"]
```

---

# 192. Docker FastAPI

```dockerfile
FROM python:3.12-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir \
    -r requirements.txt

COPY . .

CMD [
    "uvicorn",
    "app.main:app",
    "--host",
    "0.0.0.0",
    "--port",
    "8000"
]
```

---

# 193. Python Environment Variables

Never:

```python
DATABASE_PASSWORD = "mypassword"
```

Use:

```env
DATABASE_PASSWORD=mypassword
```

Then:

```python
import os

password = os.getenv(
    "DATABASE_PASSWORD"
)
```

---

# 194. Python Security Checklist

```text
✓ Don't hardcode secrets
✓ Use environment variables
✓ Validate input
✓ Parameterize SQL queries
✓ Hash passwords with Argon2/bcrypt
✓ Set HTTP timeouts
✓ Validate uploaded files
✓ Limit upload size
✓ Don't load untrusted pickle files
✓ Keep dependencies updated
✓ Use HTTPS in production
✓ Don't expose debug mode in production
✓ Use least-privilege database credentials
✓ Log security-relevant events carefully
```

---

# 195. Pickle Warning

This is dangerous with untrusted files:

```python
import pickle

pickle.load(file)
```

Never load untrusted pickle data.

---

# 196. Python Performance Basics

Prefer:

```python
sum(numbers)
```

instead of unnecessary manual loops.

Use generators for large streams:

```python
(
    process(x)
    for x in items
)
```

Use:

```text
NumPy
Pandas
vectorization
database queries
caching
async I/O
multiprocessing
```

when appropriate.

---

# 197. When to Use What

```text
Python List
→ normal collection

NumPy
→ numerical arrays / scientific computing

Pandas
→ tabular data / CSV / data analysis

Matplotlib
→ visualization

Seaborn
→ statistical visualization

SciPy
→ scientific algorithms

Scikit-learn
→ traditional ML

PyTorch
→ deep learning

Transformers
→ modern NLP / multimodal models

OpenCV
→ computer vision

Pillow
→ image manipulation

Requests
→ HTTP API calls

HTTPX
→ sync/async HTTP

BeautifulSoup
→ HTML parsing

Flask
→ lightweight web applications

FastAPI
→ modern APIs

Pydantic
→ validation / schemas

SQLAlchemy
→ database ORM / SQL toolkit

Psycopg
→ PostgreSQL driver

Redis
→ caching / queues / fast storage

Celery
→ background task processing

Pytest
→ testing
```

---

# 198. Data Science Stack

```text
Python
   ↓
NumPy
   ↓
Pandas
   ↓
Matplotlib / Seaborn
   ↓
SciPy
   ↓
Scikit-learn
```

---

# 199. AI/ML Stack

```text
Python
   ↓
NumPy / Pandas
   ↓
Scikit-learn
   ↓
PyTorch
   ↓
Transformers
   ↓
LLM / RAG
```

---

# 200. Full-Stack Python Stack

```text
HTML
CSS
JavaScript
     ↓
React
     ↓
FastAPI / Flask
     ↓
Pydantic
     ↓
SQLAlchemy
     ↓
PostgreSQL
     ↓
Redis
     ↓
Celery
```

---

# 201. Typical AI Application

```text
React
  ↓
FastAPI
  ↓
Authentication
  ↓
Service Layer
  ↓
RAG Pipeline
  ↓
Embedding Model
  ↓
Vector Database
  ↓
LLM
  ↓
Response
```

---

# 202. Typical Data Science Project

```text
Raw CSV
   ↓
Pandas
   ↓
Cleaning
   ↓
EDA
   ↓
Matplotlib / Seaborn
   ↓
Feature Engineering
   ↓
Scikit-learn
   ↓
Training
   ↓
Evaluation
   ↓
Model
   ↓
FastAPI
   ↓
Frontend
```

---

# 203. Typical Computer Vision Project

```text
Image
  ↓
OpenCV / Pillow
  ↓
Preprocessing
  ↓
NumPy
  ↓
PyTorch
  ↓
CNN / Vision Model
  ↓
Prediction
  ↓
FastAPI
  ↓
Frontend
```

---

# 204. Library Categories

## Standard Library

```text
os
sys
json
csv
re
math
random
datetime
time
pathlib
logging
sqlite3
subprocess
asyncio
threading
multiprocessing
collections
itertools
functools
statistics
secrets
hashlib
uuid
```

## Data

```text
numpy
pandas
scipy
```

## Visualization

```text
matplotlib
seaborn
plotly
```

## Machine Learning

```text
scikit-learn
xgboost
lightgbm
catboost
```

## Deep Learning

```text
torch
torchvision
torchaudio
tensorflow
keras
```

## NLP / AI

```text
transformers
tokenizers
sentence-transformers
langchain
langgraph
```

## Web

```text
flask
fastapi
django
starlette
```

## HTTP

```text
requests
httpx
aiohttp
```

## Scraping

```text
beautifulsoup4
scrapy
selenium
playwright
```

## Database

```text
sqlalchemy
psycopg
pymysql
pymongo
redis
sqlmodel
```

## Validation

```text
pydantic
pydantic-settings
```

## Testing

```text
pytest
unittest
mock
coverage
```

## Image / Video

```text
opencv-python
pillow
imageio
moviepy
```

## CLI

```text
typer
click
rich
```

---

# 205. Python Developer Learning Roadmap

```text
LEVEL 1 — Python Fundamentals

Variables
Data Types
if/else
Loops
Functions
Lists
Tuples
Sets
Dictionaries
Comprehensions
Exceptions
Files
Modules
OOP


LEVEL 2 — Python Intermediate

Decorators
Generators
Iterators
Context Managers
Type Hints
Dataclasses
Asyncio
Threading
Multiprocessing
Testing
Logging


LEVEL 3 — Data

NumPy
Pandas
Matplotlib
Seaborn
SciPy


LEVEL 4 — Machine Learning

Scikit-learn
Preprocessing
Feature Engineering
Regression
Classification
Clustering
Metrics
Cross Validation
Pipelines


LEVEL 5 — Backend

HTTP
Requests
FastAPI
Flask
Pydantic
SQLAlchemy
PostgreSQL
Redis
Authentication
JWT
Testing


LEVEL 6 — AI

PyTorch
Transformers
Embeddings
Vector Databases
RAG
LangChain
LangGraph
LLM APIs


LEVEL 7 — Production

Docker
CI/CD
Logging
Monitoring
Caching
Queues
Security
Testing
Cloud Deployment
```

---

# 206. Python Project Checklist

```text
[ ] Virtual environment
[ ] pyproject.toml
[ ] requirements / dependencies
[ ] .env
[ ] .env.example
[ ] .gitignore
[ ] README
[ ] Type hints
[ ] Error handling
[ ] Logging
[ ] Tests
[ ] Database migrations
[ ] Authentication
[ ] Input validation
[ ] API documentation
[ ] Docker
[ ] CI/CD
[ ] Production configuration
```

---

# 207. Golden Rules

```text
1. Keep functions small.

2. Use meaningful variable names.

3. Use type hints.

4. Don't repeat code unnecessarily.

5. Handle exceptions intentionally.

6. Don't hardcode secrets.

7. Use virtual environments.

8. Use parameterized SQL.

9. Write tests for important logic.

10. Use logging instead of random print()
    statements in production.

11. Use Pandas for tabular data.

12. Use NumPy for numerical arrays.

13. Use Scikit-learn for traditional ML.

14. Use PyTorch for deep learning.

15. Use FastAPI/Flask for APIs.

16. Use SQLAlchemy for database abstraction
    when it fits the project.

17. Keep business logic outside route handlers.

18. Validate data at application boundaries.

19. Profile before optimizing performance.

20. Keep dependencies updated and audited.
```

---

# 208. Master Python Architecture

```text
                    PYTHON
                       │
        ┌──────────────┼──────────────┐
        │              │              │
     Backend         Data           AI/ML
        │              │              │
   Flask/FastAPI    Pandas         PyTorch
        │           NumPy         Transformers
   SQLAlchemy        SciPy           RAG
        │              │              │
   PostgreSQL      Matplotlib       LLM
        │              │              │
      Redis       Scikit-learn   Vector DB
        │
     Celery
        │
     Docker
```

---

# END — Python Master SDK
