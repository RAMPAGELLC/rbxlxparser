# rbxlxparser
Rbxlx - A .rbxlx file parser for NodeJS

# Credits
Originally created and opensourced by Jhxan on the Roblox Developer Forum. RAMPAGE Interactive has forked it for GitHub usage and contributions to the code.

Original article: https://devforum.roblox.com/t/rbxlx-a-rbxlx-file-parser-for-nodejs/488977

# NPM Package
[View package](https://www.npmjs.com/package/rbxlx-parser)

# Usage
```js
const rbxlx = require("rbxlx-parser");
const util = require("util");
const path = require("path");
const fs = require("fs");

rbxlx.parse(fs.readFileSync(path.join(__dirname, "test.rbxlx")))
.then(tree => {
    console.log("Parsed file!");

    var descendants = tree.getDescendants();
    for (var object of descendants) {
        if (object.class == "Part") {
            console.log("We found a Part named", object.getProperty("Name"));
        }
    }

    // You can also output the entire tree structure
    //console.log(util.inspect(tree, {depth: Infinity, colors: true}));
})
.catch(err => {
    console.log(`Could not parse file because: ${err.message}`);
})
```