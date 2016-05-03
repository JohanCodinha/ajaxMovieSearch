##Single page movie search engine using OMDb.com Api.

#app.js
```javascript
$('#search > .button').on('click', function() {
    console.log('click');
    var succes = function(response){
        
        //let's delete any result curently on the page
        $('ul#resultUl > li').remove();

        //iterate through all results
        response.Search.forEach(function(movie){

            //console log for the 💛
            console.log(movie.Title);

            var $p = $('<p>').text(movie.Title);
            var $li = $('<li>').append($p);
            $('ul').append($li);
        });
    }

    search = $('div#search > input').val();

    var settings = {
        url: 'http://www.omdbapi.com/?s='+search,
        method: 'get'
    }
    $.ajax(settings).done(succes);
});
```