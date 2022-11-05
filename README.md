# About this repository

Graphql with Django

# How to run ?

Install the dependencies:

```
$ pip install -r requirements.txt
```

Run migrates:

```
$ python manage.py migrate
```

Import the data into the database:

```
$ python manage.py loaddata data.json
```

Run the app:

```
$ python manage.py runserver
```

Now visit [GraphIQL interface](http://127.0.0.1:8000/graphql) in your browser.

# Testing the GraphQL API

Requesting all the books from the database:

```
query {
  allBooks {
    id
    title
    author
    yearPublished
    review
  }
}
```

Requests a single book by its id:

```
query {
  book(bookId: 2) {
    id
    title
    author
  }
}
```

Adds a new book to the database:

```
mutation createMutation {
  createBook(bookData: {title: "Things Apart", author: "Chinua Achebe", yearPublished: "1985", review: 3}) {
    book {
      title,
      author,
      yearPublished,
      review
    }
  }
}
```

Updates the book with id=6:

```
mutation updateMutation {
  updateBook(bookData: {id: 6, title: "Things Fall Apart", author: "Chinua Achebe", yearPublished: "1958", review: 5}) {
    book {
      title,
      author,
      yearPublished,
      review
    }
  }
}
```

Deletes the book with id=6 from the database:

```
mutation deleteMutation{
  deleteBook(id: 6) {
    book {
      id
    }
  }
}
```

# Reference(s)

[Building GraphQL APIs in Django with Graphene [pt-br]](https://www.twilio.com/blog/crie-apis-graphql-em-django-com-graphene)

[Building GraphQL APIs in Django with Graphene [en-us]](https://www.twilio.com/blog/graphql-apis-django-graphene)
