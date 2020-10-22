---
title: readOrCreateJSON
tags: node,beginner,files,json
---

Read JSON file or create it with user content.

- Function take 2 arguments: file path and file content that's applied if file doesn't exists
- Use fs.existsSync() to check if file exists
- If file exists, write its to variable jsonObj
- Else use fs.writeFileSync() to create file with default content
- Return file data

```js
const fs = require('fs');

const readOrCreateJSON = (filePath, defaultFileContent = {}) =>
  {
    let jsonObj = defaultFileContent;
    
    if (fs.existsSync(filePath)) {
      jsonObj = JSON.parse(fs.readFileSync(filePath).toString());
    } else {
      fs.writeFileSync(filePath, JSON.stringify(jsonObj, null, 2));
    }

    return jsonObj;
  }
```

```js
const data = readOrCreateJSON('test.json');
```
