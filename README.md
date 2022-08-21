# generate-barcode

generate-barcode is NodeJS for creating a barcode.

## Version of npm and NodeJS
```bash
 NodeJS v14.19.1
 npm 6.14.16
```

## Checking your version of npm and Node.js
```bash
 node -v
 npm -v
```

## Packages
```bash
 fs
 readline
 jsbarcode
 canvas
```

## Installation
```bash
 npm i jsbarcode
 npm i canvas
```

## Usage
```bash
 node index.js
```

## Source Code
```javascript
const fs = require("fs");
const readline = require('readline');
const JsBarcode = require("jsbarcode");
const { Canvas } = require("canvas");

//Initialize readline
const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});

//Input Product ID
rl.question('Enter Product ID: ', function (name) {

    const canvas = new Canvas();
    JsBarcode(canvas, name);
    const res = canvas.createPNGStream()

    //Setting the directory and filename
    const path = "./output/barcode.png";
    const fileStream = fs.createWriteStream(path);
    res.pipe(fileStream);

    //Execute and close filestream
    fileStream.on("finish", () => {
        fileStream.close();
        console.log("File written");
    });

    //Close readlinee
    rl.close();
});
```

## Output
This Sameple QR Code is a link to this repository.
![QR-Code](https://user-images.githubusercontent.com/16742524/185793281-cb300ece-9a43-4d0e-8e36-0e6a7bcf8c0a.png)

## License
[MIT](https://choosealicense.com/licenses/mit/)
