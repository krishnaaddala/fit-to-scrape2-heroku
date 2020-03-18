# Fit-To-Scrape

A web scraper app that lets users view and leave comments on the latest quotes that are scrapped form Quotes website.

## Table of contents
Technologies Used
Applications Used
Screenshots of homework progress
Code Snippets

## Technologies Used
Javascript
node.js
Handlebars
Mongo
Express
Heroku
APIs
HTML
Markdown

## Applications Used
GitHub
ChromeDev tools
Visual Studio Code
Chrome browser

## Screenshots of homework progress

![Code progression Final](https://github.com/krishnaaddala/fit-to-scrape2-heroku/blob/master/public/assets/Images/Final-Image-1.png "Final code1")

![Code progression Final](https://github.com/krishnaaddala/fit-to-scrape2-heroku/blob/master/public/assets/Images/Final-Image-2.png "Final Code2")


## Gif walkthrough

![Giphy](https://github.com/krishnaaddala/fit-to-scrape2-heroku/blob/master/public/assets/Images/final-demo.gif)


## Code Snippets
##### Example of HTML routes:
```//html routes
app.get("/", (req, res) => {
    console.log("in the / route");
    db.Quote.find()
        .populate("quotes")
        .lean()
        .then(function (dbQuotes) {
            console.log("***********************")
            console.log(dbQuotes)
            res.render("home",
                {
                    quotes: dbQuotes
                });
        })
});
  ```

  ```//API Routes

app.get("/scrape", function (req, res) {
    var query = {}
    db.Quote.deleteMany(query, function (err, obj) {
        if (err) throw err;
    });
    axios.get("http://quotes.toscrape.com/").then(function (response) {
        var $ = cheerio.load(response.data);
        $("div.quote").each(function (i, element) {
            var result = {};
            result.quote = $(this)
                .children("span.text")
                .text();
            result.author = $(this)
                .children("span")
                .children("small.author")
                .text();
            db.Quote.create(result)
                .then(function (dbQuote) {
                })
                .catch(function (err) {
                    console.log(err)
                });
        });
        res.redirect("/");
    });
});
  ```

  ``` $.ajax({
      method: "GET",
      url: "/quotes/" + thisId
    })
      // With that done, add the note information to the page
      .then(function(data) {
        console.log(data);
        // The title of the article
        $("#notes").append("<h2>" + data.title + "</h2>");
        // An input to enter a new title
        $("#notes").append("<input id='titleinput' name='title' >");
        // A textarea to add a new note body
        $("#notes").append("<textarea id='bodyinput' name='body'></textarea>");
        // A button to submit a new note, with the id of the article saved to it
        $("#notes").append("<button data-id='" + data._id + "' id='savenote'>Save Note</button>");
  
        // If there's a note in the article
        if (data.note) {
          // Place the title of the note in the title input
          $("#titleinput").val(data.note.title);
          // Place the body of the note in the body textarea
          $("#bodyinput").val(data.note.body);
        }
      });
  });
  ```
  ``` {{#unless quotes}}
    <div id='onload-msg'>
      <h2>Uh-Oh Looks like we don't have any new quotes.</h2>
    </div>
    {{/unless}}
    <!-- Pass in data from server.js -->
    <ul class="list">
      {{#each quotes}}
      <li class="quotesList">
        <p><span class="label">Quote:</span> {{quote}}</p>
        <p><span class="label">Author:</span> {{author}}</p>
        <button data-id="{{quote}}" class="saveQuote" id="saveMyQuote">Save Article</button>
  ```
  ```    {{#unless quotes}}
<div id='onload-msg'>
    <h2>No Saved Quotes!!!</h2>
</div>
{{/unless}}
  ```
  ``` {{#each quotes}}
    <li class="quotesList">
        <p><span class="label">Quote:</span> {{quote}}</p>
        <p><span class="label">Author:</span> {{author}}</p>
        <button class="btn btn-primary createNote" id="createMyNote">Quote Notes</button>
  ```
Git commands:

```git status
    git add .
    git commit -m "message"
    git push origin master
    ```