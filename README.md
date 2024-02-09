# SkeleWiki

A _dead_ simple tool for creating bare _bones_ multi-page sites in a single HTML file.

SkeleWiki is a super hackable, self-replicating web app that lets you create inter-linking pages formatted with Markdown.
All data created with SkeleWiki is simply stored directly as HTML on the page, and the code within the HTML file is not
minified at all, making it easier to simply crack open in a text editor and modify however you wish!

It's page management with Markdown formatting and a simple search bar all rolled up into a single HTML file that's _less
than 32 kilobytes!_

## How to Use

Just download the HTML file and open it in a browser to get started. It's pretty simple:

- Use the "Settings" button to change the wiki's name, description, and CSS, then push "Save" to make your changes.
- Create a new page by using the "New Page" button. This will create an empty page that you can start editing right away.
    - Set a page title in the "Name" field and write some text for the page with Markdown formatting.
        - In addition to Markdown, you can link between pages using wiki link format by putting the (case insensitive) page name in 2 square braces \[\[like this\]\]! If you want the link to have different text than the page's name, then put the page name first then the text to display after a vertical bar \[\[other page|like this\]\]!
    - If you have multiple pages, you can change the order they display in the navigation by changing the Sort Position.
        - The page in the `0` position will be the "home" page of your SkeleWiki that is displayed when the file loads or when the Wiki Title is clicked.
    - Use "Save" to save the page and view the page.
    - Use "Cancel" to prevent any changes from being saved (results in an empty page if it's newly created).
    - Use "Delete" to remove the page and navigation entry.
- Search for text in your pages using the Search bar. Check the Particularities below for exactly how the results are found & sorted.
- Click the "Edit" button at the bottom of a page to change that page. The date at the bottom of the page will be updated when you save your changes.
- Save your changes to a new HTML file by using the "Save" button (or <kbd>Ctrl</kbd>+<kbd>S</kbd>). The HTML file defaults to a lowercase version of your wiki's name with any non-alphanumeric characters converted to underscores `like_this.html`.

And that's pretty much it!

### Particularities

- New pages are always added to the end of the page order, and thus the end of the nav bar.
- Pages without a name cannot be linked to and display in the navigation as "No content."
- Navigating to a different page while editing will change the page _immediately_ and **discard any unsaved changes** to the page.
- When editing a page, pressing <kbd>Tab</kbd> in the Markdown Content text area (also the Wiki CSS text area in Settings) will type a `Tab` character instead of changing focus to the next form element.
- You _can_ use HTML in the wiki name and description, but should you?
- The Wiki CSS is actually the literal contents of the `<style>` tag in the HTML's head. You can change it however you wish, but it might affect the wiki's page structure if you remove too much stuff.
- Every page exists in the file's HTML, but all pages except for the current one are hidden by default.
- The "Updated" timestamp at the bottom of a page is set to _your_ local date and time.
- Hover over the "Updated" timestamp at the bottom of a page to see the timestamp of when the page was first created, i.e. the moment "New Page" was pressed.
- Search prioritizes exact matches over case-insensitive ones and will display matching pages in order by where the match is found, prioritizing page names over page text, and only the text content of the parsed Markdown is searched when looking for results within the page text.
- Very large amounts of content on a page and very large numbers of pages may affect the performance of your SkeleWiki because it just uses and manipulates the raw DOM.
- Only the Markdown of each page is saved and can be found directly in the HTML file within a `pre` tag in the page's `section` tag. It's parsed into formatted HTML that displays when the page is loaded and the JavaScript runs.
- All pages are on the same level and display in the wiki nav bar.

## Hacking

Since it's literally just an HTML file with all its code visibly formatted in the way the developer writes it, you can just change the content or behavior! All you need is a text editor and a basic understanding of web development (HTML, CSS, and JavaScript).

The only HTML altered by the app is:

- The `<a id="name">` element in the wiki header
- The `<span id="desc">` element in the wiki header
- The CSS within the `<style id="css">` element in the HTML `head`
- The HTML content within the `<main>` element.

Pretty much anywhere else is untouched by the JavaScript and can be modified. If you need to add meta tags to the head or additional code, you can just do that. In addition, all the app functions can be accessed through `window` in JavaScript under the `app` Object. There are also a couple global helper methods in there to keep the code small.

### Ideas

- Don't want your updated time visible on a page? Find the `main>section>footer>time` entry in the Wiki CSS and add `display: none;` to hide it.
    - Don't want it in the HTML at all? Then you'll need to update the code to stop the `<time>` elements from being created and then remove them from your HTML. It's set in the `app.add()` method and modified in the `app.edit()` method.
- Need SkeleWiki in your own language? Just modify the UI text in the HTML file!
- Want to restructure the whole app? You can change the CSS and HTML completely if you need to! Just check the code for any expected structure patterns first so you don't break anything.
- Don't like the Markdown parser? Replace it! As long as whatever parser you use has its parse function set to `window.md()`, SkeleWiki should handle it fine!
