      ## You need to using POSTMAN for testing the project
## Models :: ##
## AccessBook.cs
      This file for access book
         this file have : 
        
        // we make list type is static for save data when your add delete update and search in books
        public static List<Book> ListOfbooks = new List<Book>();

        // Get All books
        public List<Book> GetAllBooks()
        
        // add new book
        public bool AddNewBook(Book book)
        
        // Update book
        public bool UpdateBook(Book book)

        // Delete book
        public void (int? id)

        // Search in books by title
        public List<Book> GetBookByTitle(string title)

        // Search in books by description
        public List<Book> GetBookByDesc(string Description)
        
        // Search in books by author
        public List<Book> GetBookByAuthor(string Author)

        // get book by id
        public Book GetBookById(int? id)

        // get total books
        public int GetTotalBooks()

        // get Authors 
        public int GetTotalAuthors()
## Book.cs ##
        public int ID { get; set; }
        
        public string Title { get; set; }
        
        public string Author { get; set; }
        
        public int Year { get; set; }
        
        public string Description { get; set; }
## Json.cs ##
        this function for display json for user
        public static Dictionary<string, object> display(string message, bool status, object data)
        {
            Dictionary<string, object> resultObt = new Dictionary<string, object>();

            resultObt.Add("message", message);
            resultObt.Add("status", status);
            resultObt.Add("data", data);

            return resultObt;
        }
## libDetails.cs ##

        public string TotalBooks { get; set; }
        
        public string TotalAuthors { get; set; }

## the Book Controller having every functions for add delete update and search in books
        // getting the 'AccessBook' model for add edit delete and search
        static AccessBook accessBook = new AccessBook();

        // this function will add 3 books on sstartup application
        [HttpGet]
        public Dictionary<string, object> GetBooks()
        {
            // add some books
            accessBook.AddNewBook(new Book()
            {
                Title = "PHP",
                Author = "Mahmmoud",
                Description = "This book for learn the php language",
                Year = 2015
            });

            accessBook.AddNewBook(new Book()
            {
                Title = "C#",
                Author = "Ahmed",
                Description = "This book for learn the C# language lol",
                Year = 2012
            });

            accessBook.AddNewBook(new Book()
            {
                Title = "Paython",
                Author = "Ahmed",
                Description = "This book for learn the Paython language lol",
                Year = 2012
            });

            // will getting the books
            List<Book> books = accessBook.GetAllBooks();
            // result
            return Json.display("We founded some books", true, books);
        }

        public Dictionary<string, object> GetLibDetails()

        [HttpPost]
        public Dictionary<string, object> AddBook(string Title, string Author, string Description, int Year)

        [HttpPost]
        public Dictionary<string, object> UpdateBook(int? id, string Title, string Author, string Description, int Year)

        [HttpPost]
        public Dictionary<string, object> DeleteBook(int? id)
        
        [HttpPost]
        public Dictionary<string, object> SearchBookByTitle(string sometext)

        [HttpPost]
        public Dictionary<string, object> SearchBookByDesc(string sometext)

        [HttpPost]
        public Dictionary<string, object> SearchBookByAuthor(string sometext)
