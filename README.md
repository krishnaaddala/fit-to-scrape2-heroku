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

![Code progression Final](https://github.com/krishnaaddala/FriendFinder/blob/master/Images/FinalCode_1.png "Final code1")

![Code progression Final](https://github.com/krishnaaddala/FriendFinder/blob/master/Images/FinalCode2.png "Final Code2")


## Gif walkthrough

![Giphy](https://github.com/krishnaaddala/FriendFinder/blob/master/Images/FinalGiphy.gif)


## Code Snippets
##### Example of friends data used:
```{
        name: "Tom Hardy",
        photo:
          "https://m.media-amazon.com/images/M/MV5BMTQ3ODEyNjA4Nl5BMl5BanBnXkFtZTgwMTE4ODMyMjE@._V1_SY1000_CR0,0,666,1000_AL_.jpg",
        scores: [5, 1, 4, 4, 5, 1, 2, 5, 4, 4]
      },
      {
        name: "Jamie Dornan",
        photo:
          "https://www.usmagazine.com/wp-content/uploads/2018/02/jamie-dornan-nude.jpg",
        scores: [4, 2, 5, 1, 3, 2, 2, 1, 3, 2]
      },
  ```

  ```app.get("/survey", function(req, res) {
    res.sendFile(path.join(__dirname, "../public/survey.html"));
  });

  // If no matching route is found default to home
  app.get("*", function(req, res) {
    res.sendFile(path.join(__dirname, "../public/home.html"));
  });
};
  ```

  ``` var friendsData = require("../data/friends.js");

module.exports = function(app) {

  app.get("/api/friends", function(req, res) {
    res.json(friendsData);
  });
  ```
  ```$("#submit").on("click", function (event) {
                event.preventDefault();

                // Here we grab the form elements
                var userData = {
                    userName: $("#enterName").val().trim(),
                    images: $("#userImage").val().trim(),
                    choices: [
                        $("#q1").val(),
                        $("#q2").val(),
                        $("#q3").val(),
                        $("#q4").val(),
                        $("#q5").val(),
                        $("#q6").val(),
                        $("#q7").val(),
                        $("#q8").val(),
                        $("#q9").val(),
                        $("#q10").val()
                    ]
                };
  ```
  ```    for (f of friendsData) {
        var fScore = 0;
        for(var i = 0; i < 10; i++) {
            var c = 0;
            if(choices[i].length !== 0) {
                c = choices[i];
            }
            absDiff = Math.abs(f.scores[i] - c);
            fScore += absDiff;
        }
        scores.push(fScore);
    }
    var friendIndex = scores.indexOf(Math.min.apply(Math, scores));
    var match = friendsData[friendIndex];
    console.log(friendsData[friendIndex]);
  ```
  ``` $.post("/api/friends", userData, function (data) {
                    console.log(data);
                    $("#modal-text").text(data.name);
                    $("#modal-photo").attr("src", data.photo);
                    $("#modal-photo").width(300);
                    $("#modal-photo").height(250);
                    $("#newModal").modal("show");
                });
  ```
Git commands:

```git status
    git add .
    git commit -m "message"
    git push origin master
    ```