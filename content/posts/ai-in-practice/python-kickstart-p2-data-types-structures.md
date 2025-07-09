Title: Python Kickstart (part 2): Data Types and Data Structures
Date: 2025-07-09 09:58
Category: AI in Practice
Tags: python, python kickstart, best practices, open-source
Slug: python-kickstart-p2-data-types-structures
Description: Learn how and when to use Python's fundamental building blocks: data types and data structures, which are crucial for writing effective Python programs.
Summary: Let's dive deeper into Python's fundamental building blocks: data types and data structures. Understanding these concepts is crucial for writing effective Python programs. Think of data types as the different kinds of information your program can work with, while data structures are the containers that organize and store that information. Let's get started!

Welcome back to our Python Kickstart series! In part 1, we covered the basics of Python installation, variables, the `print()` function, and got our feet wet with running Python code. Now it's time to dive deeper into Python's fundamental building blocks: data types and data structures.

Understanding these concepts is crucial for writing effective Python programs. Think of data types as the different kinds of information your program can work with, while data structures are the containers that organize and store that information. Just like a film director needs to understand different shot types and how to arrange them into scenes, a Python programmer needs to master these foundational elements.

## Three Basic Data Types

Python has three basic data types that you'll use constantly: strings, numbers, and booleans. Let's explore each one with fun examples from movies!

### Strings

Strings are sequences of characters enclosed in quotes. They're perfect for storing text data like movie titles, actor names, or dialogue. You can use either single quotes (`'`) or double quotes (`"`), but be consistent within your project.

```python
# Movie titles and names
movie_title = "The Shawshank Redemption"
director = "Frank Darabont"
lead_actor = 'Tim Robbins'

print(movie_title)
print(f"Directed by: {director}")
print(f"Starring: {lead_actor}")
```

Notice the `f` before the string in the last two print statements? This creates an **f-string** (formatted string literal), which lets you embed variables directly inside strings using curly braces `{}`. This is much cleaner than concatenating strings with `+`.

You can also create multi-line strings using triple quotes:

```python
movie_review = """
The Godfather is a masterpiece of American cinema.
Francis Ford Coppola's direction combined with 
Marlon Brando's iconic performance creates 
an unforgettable experience.
"""

print(movie_review)
```

### Numbers

Python handles two main types of numbers: integers (whole numbers) and floats (decimal numbers). Both are incredibly useful for storing numerical data.

```python
# Integers
release_year = 1972
runtime_minutes = 175
box_office_millions = 286

# Floats
imdb_rating = 9.2
rotten_tomatoes_score = 97.5

print(f"The Godfather ({release_year})")
print(f"Runtime: {runtime_minutes} minutes")
print(f"Box office: ${box_office_millions} million")
print(f"IMDB Rating: {imdb_rating}/10")
print(f"Rotten Tomatoes: {rotten_tomatoes_score}%")
```

You can perform mathematical operations on numbers:

```python
# Calculate decades since release
current_year = 2025
decades_since_release = (current_year - release_year) / 10

print(f"The Godfather was released {decades_since_release} decades ago")
```

### Booleans

Booleans represent truth values: either `True` or `False`. They're essential for decision-making in your programs and are often the result of comparisons.

```python
# Boolean values
is_classic = True
won_oscar = True
is_sequel = False

# Comparison operations that return booleans
is_highly_rated = imdb_rating > 9.0
is_long_movie = runtime_minutes > 180
is_recent = release_year > 2000

print(f"Is it a classic? {is_classic}")
print(f"Highly rated? {is_highly_rated}")
print(f"Long movie? {is_long_movie}")
print(f"Recent film? {is_recent}")
```

## Common Data Type Mistakes

Let's look at some errors beginners often encounter with data types:

```python
# Mixing strings and numbers without conversion
year = "1968"
current_year = 2025

# This will cause a TypeError
# age_of_movie = current_year - year  # Error!

# Instead, convert the string to an integer
age_of_movie = current_year - int(year)
print(f"2001: A Space Odyssey is {age_of_movie} years old")
```

Another common mistake is forgetting quotes around strings:

```python
# This will cause a NameError
# director = Stanley Kubrick  # Error!

# Correct way:
director = "Stanley Kubrick"
print(director)
```

## Python Data Structures

Now that we understand basic data types, let's explore Python's built-in data structures. These are containers that hold multiple pieces of data and are incredibly powerful for organizing information.

### Lists

Lists are ordered collections of items that can be changed (mutable). They're perfect for storing sequences of related data like movie collections or cast members.

```python
# Creating lists
kubrick_films = ["2001: A Space Odyssey", "The Shining", "A Clockwork Orange", "Dr. Strangelove"]
box_office_numbers = [190.7, 47.0, 26.6, 9.5]
directors = ["Stanley Kubrick", "Orson Welles", "Christopher Nolan", "Greta Gerwig"]

# Accessing list items (indexing starts at 0)
print(f"First Kubrick film in our list: {kubrick_films[0]}")
print(f"Last director: {directors[-1]}")  # Negative indexing starts from the end

# Adding items to lists
kubrick_films.append("Full Metal Jacket")
directors.insert(0, "Martin Scorsese")  # Insert at specific position

print(f"Updated Kubrick films: {kubrick_films}")
print(f"Updated directors: {directors}")
```

Lists support many useful methods:

```python
# More list operations
nolan_films = ["Inception", "Interstellar", "The Dark Knight", "Dunkirk"]

print(f"Number of films: {len(nolan_films)}")
print(f"Is 'Inception' in the list? {'Inception' in nolan_films}")

# Sorting
nolan_films.sort()
print(f"Alphabetically sorted: {nolan_films}")
```

### Tuples

Tuples are like lists, but they're immutable (cannot be changed after creation). They're perfect for storing related data that should stay together, like movie information.

```python
# Creating tuples
citizen_kane = ("Citizen Kane", 1941, "Orson Welles", 119)
casablanca = ("Casablanca", 1942, "Michael Curtiz", 102)

# Unpacking tuples
title, year, director, runtime = citizen_kane
print(f"{title} ({year}) directed by {director}, runtime: {runtime} minutes")

# Tuples are immutable - this would cause an error:
# citizen_kane[0] = "Kane"  # Error!
```

Tuples are often used for coordinates, database records, or any grouped data that shouldn't change:

```python
# Movie ratings (title, imdb_rating, rotten_tomatoes)
movie_ratings = [
    ("The Godfather", 9.2, 97),
    ("Schindler's List", 9.0, 98),
    ("Pulp Fiction", 8.9, 92)
]

for title, imdb, rt in movie_ratings:
    print(f"{title}: IMDB {imdb}, RT {rt}%")
```

### Sets

Sets are unordered collections of unique items. They're excellent for removing duplicates and performing set operations like finding common elements.

```python
# Creating sets
scorsese_actors = {"Robert De Niro", "Leonardo DiCaprio", "Joe Pesci", "Robert De Niro"}
tarantino_actors = {"Samuel L. Jackson", "Uma Thurman", "Leonardo DiCaprio", "John Travolta"}

print(f"Scorsese actors: {scorsese_actors}")  # Notice duplicate removed
print(f"Tarantino actors: {tarantino_actors}")

# Set operations
common_actors = scorsese_actors & tarantino_actors  # Intersection
all_actors = scorsese_actors | tarantino_actors     # Union
scorsese_only = scorsese_actors - tarantino_actors  # Difference

print(f"Actors who worked with both: {common_actors}")
print(f"All actors: {all_actors}")
print(f"Only in Scorsese films: {scorsese_only}")
```

Sets are also useful for checking membership quickly:

```python
oscar_winners = {"Meryl Streep", "Tom Hanks", "Frances McDormand", "Daniel Day-Lewis"}

actors_to_check = ["Tom Hanks", "Ryan Gosling", "Meryl Streep"]

for actor in actors_to_check:
    if actor in oscar_winners:
        print(f"{actor} is an Oscar winner!")
    else:
        print(f"{actor} hasn't won an Oscar yet.")
```

### Dictionaries

Dictionaries store key-value pairs and are incredibly useful for structured data. Think of them as lookup tables where each key maps to a value.

```python
# Creating dictionaries
the_godfather = {
    "title": "The Godfather",
    "year": 1972,
    "director": "Francis Ford Coppola",
    "runtime": 175,
    "genre": "Crime Drama",
    "imdb_rating": 9.2
}

# Accessing dictionary values
print(f"Movie: {the_godfather['title']}")
print(f"Director: {the_godfather['director']}")
print(f"Year: {the_godfather['year']}")

# Adding new key-value pairs
the_godfather["box_office"] = 286000000
the_godfather["lead_actor"] = "Marlon Brando"

print(f"Box office: ${the_godfather['box_office']:,}")
```

Dictionaries are perfect for more complex data structures:

```python
# Movie database
movie_database = {
    "kubrick": {
        "name": "Stanley Kubrick",
        "notable_films": ["2001: A Space Odyssey", "The Shining", "A Clockwork Orange"],
        "birth_year": 1928,
        "nationality": "American"
    },
    "welles": {
        "name": "Orson Welles", 
        "notable_films": ["Citizen Kane", "The Third Man", "Touch of Evil"],
        "birth_year": 1915,
        "nationality": "American"
    }
}

# Accessing nested data
print(f"Stanley Kubrick's films: {movie_database['kubrick']['notable_films']}")
print(f"Orson Welles was born in {movie_database['welles']['birth_year']}")

# Iterating through dictionaries
for director_key, director_info in movie_database.items():
    print(f"\n{director_info['name']} ({director_info['nationality']})")
    for film in director_info['notable_films']:
        print(f"  - {film}")
```

## Common Data Structure Mistakes

Here are some errors to watch out for:

**List Index Errors:**
```python
actors = ["Tom Hanks", "Meryl Streep", "Robert De Niro"]

# This will cause an IndexError
# print(actors[5])  # Error! List only has 3 items (indices 0, 1, 2)

# Safe way to access:
if len(actors) > 5:
    print(actors[5])
else:
    print("Not enough actors in the list")
```

**Dictionary Key Errors:**
```python
movie = {"title": "Inception", "year": 2010}

# This will cause a KeyError
# print(movie["director"])  # Error! Key doesn't exist

# Safe ways to access:
print(movie.get("director", "Director unknown"))
# or
if "director" in movie:
    print(movie["director"])
```

## When to Use Each Data Structure

Here's a practical guide for choosing the right data structure:

- **Lists**: When you need an ordered, changeable collection (movie watchlist, cast in order of appearance)
- **Tuples**: When you need an ordered, unchangeable collection (movie details, coordinates)
- **Sets**: When you need unique items or set operations (genres, avoiding duplicate actors)
- **Dictionaries**: When you need key-value relationships (movie details, actor information)

## Bringing It All Together

Let's create a practical example that combines multiple data types and structures:

```python
# Movie recommendation system
movie_collection = {
    "drama": [
        {"title": "The Shawshank Redemption", "year": 1994, "rating": 9.3},
        {"title": "Schindler's List", "year": 1993, "rating": 9.0},
        {"title": "12 Angry Men", "year": 1957, "rating": 9.0}
    ],
    "sci_fi": [
        {"title": "2001: A Space Odyssey", "year": 1968, "rating": 8.3},
        {"title": "Blade Runner", "year": 1982, "rating": 8.1},
        {"title": "Interstellar", "year": 2014, "rating": 8.6}
    ]
}

# Function to recommend movies by genre
def recommend_movies(genre, min_rating=8.0):
    if genre not in movie_collection:
        return f"Sorry, no {genre} movies in our collection."
    
    recommendations = []
    for movie in movie_collection[genre]:
        if movie["rating"] >= min_rating:
            recommendations.append(f"{movie['title']} ({movie['year']}) - {movie['rating']}")
    
    return recommendations

# Get recommendations
drama_recs = recommend_movies("drama", 9.0)
sci_fi_recs = recommend_movies("sci_fi", 8.5)

print("Highly-rated Drama recommendations:")
for rec in drama_recs:
    print(f"  - {rec}")

print("\nGreat Sci-Fi recommendations:")
for rec in sci_fi_recs:
    print(f"  - {rec}")
```

## What's Next?

You now have a solid foundation in Python's basic data types and data structures! These are the building blocks you'll use in virtually every Python program you write. Whether you're building a web application, analyzing data, or creating the next great piece of software, these concepts will serve you well.

In the next part of our Python Kickstart series, we'll explore control flow - including conditional statements and loops that will let your programs make decisions and repeat actions. We'll also dive deeper into functions, which will help you organize your code and avoid repetition.

## Practice Improves Your Programming

Remember, the best way to master these concepts is through practice. Try creating your own examples using your favorite movies, TV shows, or books. Build a small program that organizes your media collection, or create a simple movie rating system. The more you experiment with these data types and structures, the more natural they'll become.

Keep coding, keep learning, and remember: understanding these fundamentals will make you a much more effective programmer, whether you're working with an AI assistance or writing code from scratch. As we learned in part 1, vibe coding might be fun, but solid fundamental knowledge is what pays the bills!

Thanks for following along with Python Kickstart part 2. In our next installment, we'll put these data structures to work with control flow and functions. Until then, happy coding!
