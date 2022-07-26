make new project directory

npm init -yes
npm i express sass
npm i nodemon --save-dev
npm i govuk-frontend --save

within package.json edit "main" & "scripts" to include
  "main": "index.js" ---> to "src/index.js"
"scripts": {
    "tests: THIS IS ALREADY PRESENT, NO NEED TO ADD THIS LINE
    "start": "node .",
    "dev": "nodemon . & npm run scss",
    "scss": "sass --watch src/scss/main.scss public/styles/main.css"
},

touch .gitignore
add within git ignore.
    node_modules
mkdir public/styles
mkdir src
touch src/index.js
    within src/index.js add:
    ###
        const express = require('express')
        const path = require('path')

        const app = express()
        const PORT = 3000

        app.get('/', (req, res) => {
        res.sendFile(path.join(__dirname, 'pages/index.html'))
        })

        app.use(express.static(path.join(__dirname, '../public')))

        app.listen(PORT, () => {
        console.log(`App running on port ${PORT}`)
        })
    ###
mkdir src/pages
touch src/pages/index.html
    <html lang="en">
    <head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <link rel="stylesheet" type="text/css" href="styles/main.css">

    <title>Document</title>
    </head>
    <body>
    <h1>Color red</h1>
    </body>
    </html>

    within pages directory add gov templates
mkdir src/scss
touch src/scss/main.scss
    within main.scss add
    ###
    @import "../../node_modules/govuk-frontend/govuk/all";
    ###


npm run dev #this runs the server on localhost 3000, this shoudl also populate main.css

