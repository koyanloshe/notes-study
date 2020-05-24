# Webpack bundle Analyser 

npm install --save-dev webpack-bundle-analyzer

And two lines to package.json

* "stats": "webpack --profile --json --config webpack.client.build.config.js > stats.json"
* "analyze": "webpack-bundle-analyzer stats.json"

npm run stats
npm run analyze

