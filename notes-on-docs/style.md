#Notes on React Native docs

##Style

React Native doesn't implement CSS but instead relies on JavaScript to let you style your application.

###Problems with CSS at scale

*Global namespace - CSS throw loads of stuff into the global namespace. Bad idea
*Dependencies - ?
*Dead Code Elimination
*Minification
*Sharing Constants - sharing constants between css and js is a bad idea but sometimes nessisary i.e. if you change a *stype property with JS.
*Non-deterministic Resolution - if you load in files asynchronoursly, you have no control over the order of you styles *and cannot be sure of presendence. 
*Isolation - If we are modifying the styles from a base and that changes, our component style may break in the future.

###React Solution
*Global namespace -  All styles ar local JS variables and can be exported when needed
*Dependencies -  You can use a module system
*Dead Code Elimination -  Inline style
*Minification - Inline style
*Sharing Constants - React uses a CSSVar function to solve this aka inline style
*Non-deterministic Resolution - 
*Isolation - 


