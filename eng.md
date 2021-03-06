# Angry Birds of JavaScript- White Bird: Linting


## Introduction

![][1] 

A diabolical herd of pigs stole all of the front-end architecture from an
innocent flock of birds and now they want it back!

A team of special agent hero birds will attack those despicable pigs until they
recover what is rightfully theirs, front-end JavaScript architecture!

Will the birds be successful in the end? Will they defeat their bacon flavored
foe? Let's find out together in another nail biting episode of Angry Birds of 
JavaScript!

> Check out the **[series introduction post][2]** for a list of all the birds
> and their attack powers.
>![][3] 


### Previous Attacks

* [Red Bird - IIFE][20]
* [Blue Bird - Events][21]
* [Yellow Bird - RequireJS][22]
* [Black Bird - Backbone][23]

### White Bird Attacks

In this post we will take a look at the White Bird who appears to be seemingly
harmless, but when it pulls out it's strict coding style and bursts of quality 
checks the hogs are sure to squeal. Slowly, one by one, the birds will take back
what it theirs to keep!


## What Was Stolen by the Pigs?

The birds all learned how to program in a slightly different way. Some birds
were self-taught and some birds went to college for computer science. Even among
those groups there were a wide range of experiences and talent. When the birds 
got together to build their first large application it was a huge disaster. Each
bird thought their coding standard was the "right way" and it started to become 
an issue. One day a wise White Bird came along and suggested that they come up 
with a common set of coding practices to follow. In addition, the White Bird 
introduced a few tools to help them conform to a standard and to help find 
issues and concerns early before they became a huge issue later.

However, during a recent invasion the pigs stole the birds' coding standards
document and their code quality tools! As a result, one of the White Birds has 
been tasked to reclaim what has been stolen. He will use his overwhelming power 
of quality to help destroy the pigs in order to take back what is theirs.


## JavaScript Coding Standards

There are many coding standards out there to choose from. The most important
thing is that you pick one and stick to it. If you are working with a team, they
should also agree on some standard. If you can't find a standard you exactly 
agree on, then find one that is close and make some exceptions.

By doing so you'll find that…

*   A developer will be able to make sense of other code more quickly
*   Merges in your code repository won't be as awful
*   Having a standard will actually reduce defects
*   The codebase will feel more unified
*   Disagreements about who is "right" will lessen
*   … insert your benefit here …

Here are some of the coding standards that I am aware of…


*   Douglas Crockford's [Code Conventions for the JavaScript Programming Language][29]
*   Rich Waldron's ([@rwaldron][30]) [Idiomatic.js - Principles of Writing Consistent, Idiomatic JavaScript][31] ← Recommended
*   jQuery's [JavaScript Style Guide][32] ← Recommended
*   Google's [JavaScript Style Guide][33]



Addy Osmani ([@addyosmani][4]) has a nice post entitled 
[JavaScript Style Guides And Beautifiers][5] that covers some of these styles
in depth with examples showing how to abide by the standards recommended.


## JavaScript Linting

A linter is a tool that helps find errors and possible issues with your code.
In many cases it can help enforce whatever coding standard you chose from the 
above list.

There are actually several JavaScript linters out there, but the one I like the
best is[JSHint][6] created by Anton Kovalyov ([@valueof][7]). It grew out of a
community effort to fork the popular JSLint library written by Douglas Crockford.
I've enjoyed watching the project grow and see bugs and new features being added.
JSHint has a lot of options that you can choose to opt-in or opt-out of which 
enables a team to figure out what works best for them.

Some of the standard checks that JSHint can verify include…

*   The use of `===` instead of `==` 
*   Using variables that aren't defined
*   Declaring variables that are never used
*   Declaring functions inside of loops
*   And lots more…

For a full list of options see the [JSHint Docs][8].

Some of the more recent additions that I've really enjoyed include:

*   `maxcomplexity` - Maximum cyclomatic complexity (see following Wikipedia
    quote
    )
*   `maxstatements` - Maximum number of statements allowed in a function
*   `maxparams` - Maximum number of parameter allowed in a function
*   `maxdepth` - Maximum depth allowed in a function
*   `maxlen` - Maximum length of line in code

> "The cyclomatic complexity of a section of source code is the count of the
> number of linearly independent paths through the source code.
> " --<http://en.wikipedia.org/wiki/Cyclomatic_complexity> 

    /*jshint maxparams:3, maxdepth:2, maxstatements:5, maxcomplexity:3, maxlen:80 */
    /*global console:false */
     
    (function( undefined ) {
        "use strict";
     
        function test1( arg1, arg2, arg3, arg4 ) {
            console.log( "too many parameters!" );
            if ( arg1 === 1 ) {
                console.log( arg1 );
                if ( arg2 === 2 ) {
                    console.log( arg2 );
                    if( arg3 === 3 ) {
                        console.log( "too much nesting!" ); console.log( arg3 ); console.log( arg4 );
                    }
                }
            }
            console.log( "too many statements!" );
        }
     
        test1( 1, 2, 3, 4 );
    }());

The following errors are generated by JSHint after running it against the above
code snippet.

![][9] 

Thankfully you don't have to run JSHint from the website every time to check
your code. There are several ways to integrate it into your code editor of 
choice:

* VIM Plugin ([jshint.vim][24])
* Sublime Text 2 Extension ([Sublime Linter][25])
* TextMate Bundle ([JSHint TextMate Bundle][26])
* Visual Studio [Web Essentials][27]
* Eclipse IDE ([JSHint Integration][28])

> In the Mighty Eagle post we'll talk about another way to use the JSHint from
> the command line and automatically.
>


## JavaScript Analysis

Code linting is great, but sometimes it is nice to get a high level overview of
your codebase and then be able to drill down and analyze small portions of your 
application.

Thankfully there is a tool called [Plato][10] that will analyse your code and
provide a visual report where you can view the complexity of your application. 
The tool runs in Node and you can install it using`npm install plato -g`. 

Once installed you can run the tool on the command line by 
`plato -r -d report myDirectory`, which will recursively analyse the code in
the`myDirectory` folder and export the results to the `report` folder.

If you were to run the report on the jQuery source code it would look much like
the following report. As you can see, the average number of lines is decreasing 
over time, which is good. The maintainability is decent and then a breakdown of 
the maintainability of each JavaScript file is listed in a bar chart. Further 
down in the report there are a bar charts for Lines of code broken per file, 
Estimated errors per file, and also JSLint errors per file.

![][11] 

If you drill into one of the particular files from above you'll see a view that
looks like the following. The nice part about this report is that it breaks down
each function into complexity and lines of code in a way that is easy to grasp. 
You can quickly jump to various parts of the file to review the concerns the 
tool is identifying.

![][12] 

You can view the above [jQuery Report][13] from Plato's GitHub repository.


## Attack!

The following is a simple Angry Birds clone using [boxbox][14], a framework for
the[box2dweb][15] JavaScript physics library, written by [Bocoup][16]'s 
[Greg Smith][17].

> Press the `space bar` to launch the White Bird and you can also use the arrow
> keys.
>![][18] 

### Conclusion

Front-end web applications can get complicated quickly. If your developers aren
't all on the same page then things can fall apart in a heartbeat, especially on
a large project. Having a unified coding standard and implementing some tools to
help find issues before they become a problem can really help to make your 
project a success.

There are many other front-end architecture techniques that have been stolen by
the pigs. Tune in next time as the next Angry Bird takes its revenge! Dun, dun, 
daaaaaaa!


 [1]: img/angry_birds_wall_decal_by_graphicwolf-d4fwzrc.jpg
 [2]: http://www.elijahmanor.com/2013/03/angry-birds-of-javascript-series.html
 [3]: img/white-bird.png
 [4]: http://twitter.com/addyosmani
 [5]: http://addyosmani.com/blog/javascript-style-guides-and-beautifiers/
 [6]: http://jshint.com/
 [7]: http://twitter.com/valueof
 [8]: http://jshint.com/docs/
 [9]: img/4-3-2013+10-33-12+PM.png
 [10]: https://github.com/jsoverson/plato
 [11]: img/jquery-top-level.png
 [12]: img/jquery-drill-complexity.png
 [13]: http://jsoverson.github.com/plato/examples/jquery/
 [14]: http://incompl.github.com/boxbox/
 [15]: https://code.google.com/p/box2dweb/
 [16]: http://bocoup.com/
 [17]: http://twitter.com/_gsmith
 [18]: img/Screenshot+on+4.4.2013+at+12.14.59+AM.png
 [20]: http://www.elijahmanor.com/angry-birds-of-javascript-red-bird-iife/
 [21]: http://www.elijahmanor.com/angry-birds-of-javascript-blue-bird-events/
 [22]: http://www.elijahmanor.com/angry-birds-of-javascript-yellow-bird-requirejs/
 [23]: http://www.elijahmanor.com/angry-birds-of-javascript-black-bird-backbone/
 [24]: https://github.com/walm/jshint.vim
 [25]: https://github.com/Kronuz/SublimeLinter
 [26]: http://fgnass.posterous.com/jslint-in-textmate
 [27]: http://vswebessentials.com
 [28]: http://github.eclipsesource.com/jshint-eclipse/
 [29]: http://javascript.crockford.com/code.html
 [30]: https://twitter.com/rwaldron
 [31]: https://github.com/rwaldron/idiomatic.js
 [32]: http://contribute.jquery.org/style-guide/js/
 [33]: http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml
