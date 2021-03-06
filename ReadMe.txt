Created by Codrops
License: http://tympanus.net/codrops/licensing/

Background Pattern(s) from http://subtlepatterns.com/
http://creativecommons.org/licenses/by-sa/3.0/deed.en_US

normalize.css by Nicolas Gallagher: http://github.com/necolas/normalize.css

To use the windy js plugin you must first include the latest vesrion of jQuery, you can do that by adding the following line into the head section of your HTML
    <script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.8.2/jquery.min.js"></script>

The other two JS files needed are of course the Windy.js and modernizer, which should be stored locally on your machine.
    <script type="text/javascript" src="js/modernizr.custom.79639.js"></script>
    <script type="text/javascript" src="js/jquery.windy.js"></script>

Next you will need some style sheets, there are 2 which are used on every demo, which can be copied from here:
    <link rel="stylesheet" type="text/css" href="css/windy.css" />
    <link rel="stylesheet" type="text/css" href="css/demo.css" />

And the no-js css:
    <noscript><link rel="stylesheet" type="text/css" href="css/noJS.css" /></noscript>

Also each demo has its own styles sheet, numbered like the demos ie:
<link rel="stylesheet" type="text/css" href="css/style1.css" />
<link rel="stylesheet" type="text/css" href="css/style2.css" />

Or if you want to style the code yourself, you don't need to include any of those style sheets, just these lines of CSS, which give the plugin its windy effect

    ul.wi-container li.wi-move {
        pointer-events: none;
        -webkit-transition: -webkit-transform 600ms ease, opacity 600ms ease, left 600ms ease, top 600ms ease;
        -moz-transition: -moz-transform 600ms ease, opacity 600ms ease, left 600ms ease, top 600ms ease;
        -o-transition: -o-transform 600ms ease, opacity 600ms ease, left 600ms ease, top 600ms ease;
        -ms-transition: -ms-transform 600ms ease, opacity 600ms ease, left 600ms ease, top 600ms ease;
        transition: transform 600ms ease, opacity 600ms ease, left 600ms ease, top 600ms ease;
    }

after you have added the JS and CSS, you need to add the call to the plugin into the head, please do this after you call jQuery and windy.js, if you want to just do demo one or two, you can use the following code:
    <script type="text/javascript"> 
        $(function() {

            var $el = $( '#wi-el' ),
                windy = $el.windy( {
                    // rotation and translation boundaries for the items transitions
                    boundaries : {
                        rotateX : { min : 40 , max : 90 },
                        rotateY : { min : -15 , max : 45 },
                        rotateZ : { min : -10 , max : 10 },
                        translateX : { min : -400 , max : 400 },
                        translateY : { min : -400 , max : 400 },
                        translateZ : { min : 350 , max : 550 }
                    }
                } ),
                allownavnext = false,
                allownavprev = false;

            $( '#nav-prev' ).on( 'mousedown', function( event ) {

                allownavprev = true;
                navprev();
            
            } ).on( 'mouseup mouseleave', function( event ) {

                allownavprev = false;
            
            } );

            $( '#nav-next' ).on( 'mousedown', function( event ) {

                allownavnext = true;
                navnext();
            
            } ).on( 'mouseup mouseleave', function( event ) {

                allownavnext = false;
            
            } );

            function navnext() {
                if( allownavnext ) {
                    windy.next();
                    setTimeout( function() {    
                        navnext();
                    }, 150 );
                }
            }

            function navprev() {
                if( allownavprev ) {
                    windy.prev();
                    setTimeout( function() {    
                        navprev();
                    }, 150 );
                }
            }

        });
    </script>

If you would like to add the thumbnail function as in demo 4, you need to add a click function to the above code while looks like this:
    $("ul.bio_thumbnails li").click(function() {
        $("ul#wi-el li").removeClass('active');
        var clicked_thumb = $("ul.bio_thumbnails li").index(this);
        windy.navigate( clicked_thumb );
    });

Finally, you need to add the HTML to your html document, for the first few demos you can use this code:
    <div class="windy-demo">
        <ul id="wi-el" class="wi-container">
            <li>
                <img src="images/demo1/1.jpg" alt="image1"/>
                <h4>Coco Loko</h4>
                <p>Total bicycle rights in blog four loko raw denim ex, helvetica sapiente odio placeat.</p>
            </li>
        </ul>
    </div>

Then each of your slides will be another li, which can just have image and text in it if you prefer, if you would like to use the thumbnails, you need to add this <ul> to where ever you would like your thumbnails to appear:
    <ul class="bio_thumbnails">
        <li>
            <img src="images/demo2/1.jpg" alt="image1"/>
        </li>
    </ul>

Then your code should be ready to go







