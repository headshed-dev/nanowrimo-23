- {{renderer :wordcount_}}
	- regular expressions are a way to describe patterns in strings and the Perl programming language has many powerful tools for working with them. I could say that this is the one thing I miss no longer writing Perl and that is missing from other languages I use regularly. This is not to say that you can't use regular expressions in other languages, but Perl has a very rich set of tools for working with them.
	  ```perl
	    ($postcode) =
	       ($address =~
	   /(
	       # UK Postcode:
	         [A-Z]{1,2} # Post town
	         \d{1,3}    # Area
	         [ \t]+
	         \d{1,2}    # Region
	         [A-Z][A-Z] # Street part
	       |
	       # US Postcode:
	         [A-Z][A-Z]   # State
	         [\t ]+
	         \d{5}        # ZIP+5
	   )/x);
	  ```
	- this for [example in perl](https://www.perl.com/pub/2003/06/06/regexps.html/) dating back to June 2003 is a good example of how to use regular expressions to extract data from a string. There is nothing old or ferclugetty about this code yet regular expressions are somehting that cause a lot to stare into space and some to black out in panic due to what can be a mind bending syntax.
	- Perl got some things wrong but it also got some things ritght and its ability to use the addition of the `x` modifier to allow for whitespace and comments in the regular expression is one of those things, permtting us to express the regular expression in a way that is easier to read and understand. It even looks a bit like a data structure.
	- So in the then, typical world of work on the internet and with software and data as was frequently used of the time, regular expressions were a very useful as often data would appear to us in regular patterns but not standardised formats. HTML was a form of data formatting that we had to adher to, without which, the internet would not have been possible, as it was used by the browser to render pages. XML ( Extended Markup Language ) was a way to describe data in a way that was not tied to a specific language or platform and had its roots in SGML ( Standard Generalised Markup Language ) which was a way to describe data in a way that was not tied to a specific language or platform. Each of these having the word Markup in their name, as they were a way to mark up data in a way that was not tied to a specific language or platform and similar to the way that HTML was used to mark up data in a way that was not tied to a specific language or platform.
	- XML became the standard for data interchange and was used in many places, including the web and in particular by AJAX ( Asynchronous JavaScript and XML )
	- To parse data in XML and even HTML using regular expressions is possible but not in my view a good idea. It would be something I might have done 'in a push' to get something done but not a solution I would want to return to having slept and fogotten why I did it the day previouse.
	- as time and approaches to encoding data have moved on, so have the tools we use to work with them and even Perl has many modules that can be used to parse XML and HTML and the accpted wisdom was to use these rather than regular expressions for such stucutred data.
	- {{renderer :wordcount_}}
		- here comparing this to json seriaizer in dart and the use of regular expressions to parse json in dart bings things up to date.
		- also, what happened with ajax, that chnged