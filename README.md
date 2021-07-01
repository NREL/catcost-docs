# catcost-docs

## Getting Started

The CatCost User Guide uses [Docsify.js](https://docsify.js.org/). The site is served by GitHub Pages from the main branch at https://catcost-docs.chemcatbio.org: when the user opens the page, the index.html directs their browser to load the Docsify intepreter and render the page.

For local preview, first ensure [Node.js](https://nodejs.org/en/) is installed on your machine. Then install Docsify globally:

`npm i docsify-cli -g`

To preview the site and watch your changes live, run the following from the catcost-docs repository folder:

`docsify serve docs`

## Adding Pages

Docsify automatically finds (and creates routes to) any Markdown pages added to the docs folder. In each folder, the README.md file becomes the homepage for that folder. If you add a visualizations subdirectory to docs and create README.md and Sankey.md files in that directory, those can be accessed at /visualizations/ and /visualizations/Sankey, respectively. See this [Docsify page](https://docsify.js.org/#/more-pages) for more details.
