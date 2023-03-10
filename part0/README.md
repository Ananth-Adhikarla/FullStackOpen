 **Full Stack Open 2023 - Part 0**
 
 #### 0.1: HTML
Review the basics of HTML by reading this tutorial from Mozilla:  [HTML tutorial](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics).
_This exercise is not submitted to GitHub, it's enough to just read the tutorial_

#### 0.2: CSS
Review the basics of CSS by reading this tutorial from Mozilla:  [CSS tutorial](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/CSS_basics).
_This exercise is not submitted to GitHub, it's enough to just read the tutorial_

#### 0.3: HTML forms
Learn about the basics of HTML forms by reading Mozilla's tutorial  [Your first form](https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/Your_first_HTML_form).
_This exercise is not submitted to GitHub, it's enough to just read the tutorial_

#### 0.4: New note diagram
In the section  [Loading a page containing JavaScript - review](https://fullstackopen.com/en/part0/fundamentals_of_web_apps#loading-a-page-containing-java-script-review), the chain of events caused by opening the page  [https://studies.cs.helsinki.fi/exampleapp/notes](https://studies.cs.helsinki.fi/exampleapp/notes)  is depicted as a  [sequence diagram](https://www.geeksforgeeks.org/unified-modeling-language-uml-sequence-diagrams/)

My Solution 
```mermaid
sequenceDiagram
participant browser
participant server
browser->>server: HTTP POST https://studies.cs.helsinki.fi/exampleapp/new_note
server->>browser: HTTP STATUS CODE 302
Note right of browser: CONTENT TYPE: application/x-www-form-urlencoded. <br/>PAYLOAD: ananth
Note right of browser: PAYLOAD: ananth
Note right of browser: STATUS CODE 302 is a HTTP GET REQUEST on submit button click
Note right of browser: to the address defined in response headers: /exampleapp/notes
browser->>server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/notes
server->>browser: HTTP STATUS CODE 200 OK - Sends HTML code of page requested
browser->>server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/main.css
server->>browser: HTTP STATUS CODE 200 OK - Sends CSS code of page requested
Note right of browser: In main.js if (this.readyState == 4 && this.status == 200)
Note right of browser: when condition matches it makes a GET request to /exampleapp/data.json
browser->>server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/data.json
server->>browser: HTTP STATUS CODE 200 OK - sends json formatted data {content: "" , date: ""}
Note right of browser: browser executes the event handler
Note right of browser: that renders notes to display
participant browser
participant server
```
#### 0.5: Single page app diagram
Create a diagram depicting the situation where the user goes to the  [single-page app](https://fullstackopen.com/en/part0/fundamentals_of_web_apps#single-page-app)  version of the notes app at  [https://studies.cs.helsinki.fi/exampleapp/spa](https://studies.cs.helsinki.fi/exampleapp/spa).
My Solution 
```mermaid
sequenceDiagram
participant browser
participant server
browser->>server: HTTP GET request  https://studies.cs.helsinki.fi/exampleapp/spa
server-->>browser: HTTP STATUS CODE 200 OK sends HTML file
browser->>server: HTTP GET request  https://studies.cs.helsinki.fi/exampleapp/main.css
server-->>browser: HTTP STATUS CODE 200 OK sends CSS file
browser->>server: HTTP GET request  https://studies.cs.helsinki.fi/exampleapp/spa.js
server-->>browser: HTTP STATUS CODE 200 OK sends JS file
Note right of browser: Browser"GET", "/exampleapp/data.json" from spa.js file
browser->>server: HTTP GET request  https://studies.cs.helsinki.fi/exampleapp/data.json
server-->>browser: HTTP STATUS CODE 200 OK sends back json data
Note right of browser: browser executes the event handler
Note right of browser: that renders notes to display
participant browser
participant server
```
#### 0.6: New note in Single page app diagram
Create a diagram depicting the situation where the user creates a new note using the single-page version of the app.
My Solution 
```mermaid
sequenceDiagram
participant browser
participant server
browser->>server: HTTP POST request  https://studies.cs.helsinki.fi/exampleapp/new_note_spa
server-->>browser: HTTP STATUS CODE 201 OK sends HTML file
Note right of browser: since its SPA application it will not redirect
Note right of browser: it uses ajax to render pages on updates
participant browser
participant server
```