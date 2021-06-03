# CIT281 Lab-6 
Purpose of this lab:
- To gain experience using GitHub by working through "Introduction to GitHub Course". 
- To gain experience creating and testing "Classes" 

### Lab Code:
```
class Book {
  constructor(title, author, pubDate, isbn) {
    this.title = title;
    this.author = author;
    this.pubDate = pubDate;
    this.isbn = isbn;
  }
}

// Create a book
const atomicHabits = new Book("Atomic Habits", "James Clear", "10/16/2018");
console.log(atomicHabits);

class Library {
  constructor(name) {
    this._name = name;
    this._books = [];
  }
  get books() {
    // Return copy of books
    return JSON.parse(JSON.stringify(this._books));
  }
  get count() {
    return this._books.length;
  }
  addBook(book = {}) {
    const { title = "", author = "", pubDate = "", isbn = "" } = book;
    if (title.length > 0 && author.length > 0) {
      const newBook = { title, author, pubDate, isbn };
      this._books.push(newBook);
    }
  }
  deleteBook(isbn) {
    let indexOfBooksToRemove = null;
    for (let index = 0; index < this._books.length; index++) {
      const book = this._books[index];
      if (book.isbn == isbn) {
        indexOfBooksToRemove = index;
        break;
      }
    }
    this._books.splice(indexOfBooksToRemove, 1);
  }
  listBooks() {
    for (const book of this._books) {
      const { title, author, pubDate, isbn } = book;
      console.log(
        `Title: ${title}, Author: ${author}, PubDate: ${pubDate}, ISBN: ${isbn}`
      );
    }
  }
}

// Create library object
const library = new Library("New York Times Best Seller List");

// Create a book
const atomicHabits = new Book(
  "Atomic Habits",
  "James Clear",
  "10/16/2018",
  "123456789"
);
const MyBook = new Book(
  "AP Calc Crash Course",
  "Banu et al.",
  "01/01/2013",
  "987654321"
);
const UO = new Book("UO SUCCESS", "CIT383.", "07/02/2015", "567891234");
// Add book to library and output library count and books
let uoLibary = new Library("Knight Library");
library.addBook(atomicHabits);
library.addBook(MyBook);
library.addBook(UO);
console.log(`Book count: ${library.count}`);
library.listBooks();

// Delete a book and output library books
console.log("* Library after delete *");
library.deleteBook("123456789");
library.listBooks();
```
### What I learned: 
- Learned how to effectively create a class and search for the requested data. 
