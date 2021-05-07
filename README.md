# Personal site of Jess Budd

[jessbudd.com](https://jessbudd.com)

Based on a skeleton [Eleventy](https://github.com/philhawksworth/eleventyone) site by [Phil Hawksworth](https://twitter.com/philhawksworth). 

Written with markdown and nunjunks, deployed and hosted on [Netlify](https://www.netlify.com/).


### Prerequisites
Node and NPM

Netlify CLI

### Running locally
```
# install the dependencies
npm install

# External data sources can be stashed locally
npm run seed

# It will then be available locally for building with
npm start
```

### Add some Netlify helpers
Netlify Dev adds the ability to use Netlify redirects, proxies, and serverless functions.

```
# install the Netlify CLI in order to get Netlify Dev
npm install -g netlify-cli

# run a local server with some added Netlify sugar in front of Eleventy
netlify dev
```

A serverless functions pipeline is included via Netlify Dev. By running netlify dev you'll be able to execute any of your serverless functions directly like this:

```/.netlify/functions/hello
/.netlify/functions/fetch-joke
```

### Redirects and proxies
Netlify's Redirects API can provide friendlier URLs as proxies to these URLs.

```
/api/hello
/api/fetch-joke
```
