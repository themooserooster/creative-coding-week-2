creative-coding-week-2
======================

Project Repo for Creative Coding Class Week 2

Notes for This week: 

///// Resources - the stuff I didn't give you last week.

Mozilla Developer Network - Documentation and Tutorials
developer.mozilla.org


Web Platform.org - Documentation and Tutorials
www.webplatform.org


Creative JS - Tutorials and Inspiration
www.creativejs.com


Mozilla Demo Studio - Where people go to show off their best stuff.
https://developer.mozilla.org/en-US/demos/


Creative Coding Podcast - Ian Lobb and Seb Lee-Delisle have cheeky, nerdy fun. 
Sporadic episodes, but oh-so-good.
http://creativecodingpodcast.com/


HTML5 Rocks - Google run blog on awesome new open web technologies. Very 
bleeding edge stuff.
www.html5rocks.com


Mozilla Hacks - Mozilla blog for cutting edge web developers. covers new web 
technologies and upcoming Firefox features
hacks.mozilla.org


Acko.net - Super ninja stuff. Just to show you what's possible. If you poop 
yourself, it's not my fault.
www.acko.net

///// Topics for this week:

Basic function syntax:

    function () {
        // code goes here
    }

... thats all you're required to write!!! When you do it like that, the function
is called and ANONYMOUS FUNCTION. Why? Becasue it has no name. You won't be 
writing much of those at first. Well how do we do that? Like this:

    function FUNCTION_NAME_HERE () {
        // code goes here...
    }
    
or this:

    var FUNCTION_NAME_HERE = function () {
        // code goes here...
    };

Those two methods are exactly the same in all respects. Under the hood, the JS
engine treats them no different. I prefer them both in different circumstances,
but its totally a style thing. Every dev does it different. So a function called
"myFunction" (spaces and dashes aren't allowed in functions, so we "camel-case"
them) looks like this:

    function myFunction () {
    
    }
    
OR:

    var myFunction = function () {
    
    }; // REMEMBER THE SEMICOLON IN THIS METHOD!!!!!

Like I said, most functions you write in the beginning will be named ones. This 
is because you can't call (run) a function with out calling it by name. Calling 
a function named "myFunction" just looks like this:

    myFunction();

IMPORTANT: Nothing happens if you just write:

    myFunction;
    
because the bit that makes it run are the "()". Those parens in that 
circumstance are known as the CALL OPERATOR. No call operator, no running 
function.
    
If myFunction takes any input arguments, they go in the call operator when you
call it, separated by commas: 

    myFunction(argument1, argument2);

*Block scoping

So inside functions you can declare variables, perform math operations and even
declare more functions! But there's a catch. If you go

    function someFunction () {
        var bob = 5;
    }

    console.log(bob);
    
Explosions happen. Why? Block scoping, that's why. Chill, its super simple.
Functions are, for the most part, like one-way mirrors. Varibles declared 
outside a function can get in, but ones declared inside can't get out. Like 
this:

    var foo = 100;
    
    function addStuff () {
        var bob = 300;
        
        var addedStuff = bob + foo; // 400; works because foo is outside this function
    }
    
    function addMoreStuff () {
        var otherBob = 1000000;
        
        var moreAddedStuff = bob + otherBob; // This bombs. "bob" was declared in a different scope than the one we're currently in.
        var tryAgain = foo + otherBob; // This guy would work if we hadnt just written a bombing line right above it. The error kills the function.
    }

*Separation of concerns:

JS usually is written entirely in external files that end in the .js extension.
This keeps your JS separate from you HTML and will insulate you from nervous
breakdowns. When you open an empty text file, You CAN just start writing JS 
right away... but long term its a bad idea. Why? Its called polluting the 
Global Namespace. Wha....? If you just start declaring variables willy nilly in 
a script what happens if you give that variable a really common name, like this:

    var counter = 0;
    
Well what if SOME OTHER script running in your page (maybe that you didn't even
write!) also has a variable named counter? Stuff's going to start failing for no
reason. That's because those are GLOBAL variables. That is, every variable that 
isnt enclosed in some sort of function block is global, i.e. a direct child of
the global window object and available (and changeable) anywhere.

Far better is to always wrap your JS in whats called an IIFE (said 'iffy') or 
Immediately Invoked Function Expression. Its exactly what it sounds like. You 
define a function that gets invoked as soon as it gets parsed and compiled. Its
really all way more simple than it sounds. Here's what one looks like:

    (function (){
        // code goes here
    })();

Hey, wait! Thats just a function wrapped in parens with another pair on parens
right after (and the semicolon :P).

This way, if we REALLY want any object to be global and available outside, we 
can just attach it to the global window object:

    (function () {
        window.globallyAvailable = {};
        
        // NOW you can write code willy nilly!
    })();
    
    console.log(globallyAvailable);
    
and the rest of our code is safely firewalled from all other code. The moral of 
the story? The fisrt thing you should always do when you start a new .js file 
is write an IIFE. ALWAYS.

PRO TIP: I always write mine in 3 steps so its easy:

1:
    ()();
    
2:

    (function () {})();
    
3:

    (function () {
        // aaaand go!
    })();

*Writing your own functions to draw custom shapes in canvas






Animations!!!!! with requestAnimationFrame API.
