# SkeleWiki

A _dead_ simple tool for creating bare _bones_ multi-page sites in a single HTML file.

SkeleWiki is a super hackable, self-replicating web app that lets you create inter-linking pages formatted with Markdown.
All data created with SkeleWiki is simply stored directly as HTML on the page, and the code within the HTML file is not
minified at all, making it easier to simply crack open in a text editor and modify however you wish!

It's page management with Markdown formatting and a simple search bar all rolled up into a single HTML file that's _less than 20 kilobytes!_

## How to Use

Just download the SkeleWiki HTML file and open it in a browser to get started. It's pretty simple:

- Use the "Settings" button to change the wiki's name, description, and CSS, then push "Save" to make your changes.
- Create a new page by using the "New Page" button. This will create an empty page that you can start editing right away.
    - Set a page title in the "Name" field and write some text for the page with Markdown formatting.
        - In addition to Markdown, you can link between pages using wiki link format by putting the (case insensitive) page name in 2 square braces `[[like this]]`! If you want the link to have different text than the page's name, then put the page name first then the text to display after a vertical bar `[[other page|like this]]`!
    - If you have multiple pages, you can change the order they display in the navigation by changing the Sort Position.
        - The page in the `0` position will be the "home" page of your SkeleWiki that is displayed when the file loads or when the Wiki Title is clicked.
    - Use "Save" to save the page and view the page.
    - Use "Cancel" to prevent any changes from being saved (results in an empty page if it's newly created).
    - Use "Delete" to remove the page and navigation entry.
- Search for text in your pages using the Search bar. Check the Particularities below for exactly how the results are found & sorted.
- Click the "Edit" button at the bottom of a page to change that page. The date at the bottom of the page will be updated when you save your changes.
- Save your changes to a new HTML file by using the "Save" button (or <kbd>Ctrl</kbd>+<kbd>S</kbd>). The HTML file defaults to a lowercase version of your wiki's name with any non-alphanumeric characters converted to underscores `like_this.html`.

And that's pretty much it!

The code in the HTML file is not minified and has some basic comments to help navigate it so you can hack it to your exact needs.

[Visit the site](https://alamantus.codeberg.page/SkeleWiki) to see SkeleWiki in action and for all details and limitations!
