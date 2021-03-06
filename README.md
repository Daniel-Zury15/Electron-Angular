# Creating a Project

Install Angular:

```
$ npm install -g @angular/cli
```

```
$ ng new electron-app
$ cd electron-app
$ ng serve
```

Install Electron:

```
$ npm install --save-dev electron@latest
```

Create one `main.js`:

```
const { app, BrowserWindow } = require('electron')
const path = require('path')

process.env['ELECTRON_DISABLE_SECURITY_WARNINGS'] = 'true';

const createWindow = () => {

  const mainWindow = new BrowserWindow({
    width: 800,
    height: 600,
    webPreferences: {
      nodeIntegration: false,
      contextIsolation: true,
      enableRemoteModule: false
    }
  })

  mainWindow.loadFile(path.join(__dirname, `/dist/Electron-Angular/index.html`));

  // mainWindow.webContents.openDevTools()
}

app.whenReady().then(() => {
  createWindow()
  app.on('activate', () => {
    if (BrowserWindow.getAllWindows().length === 0) createWindow()
  })
})

app.on('window-all-closed', () => {
  if (process.platform !== 'darwin') app.quit()
})
```

To edit `package.json`:

```
{
  "name": "electron_angular",
  "version": "0.0.0",
  "main": "main.js",
  "scripts": {
    "ng": "ng",
    "start": "ng build --base-href ./ && electron .",
    "build": "ng build",
    "test": "ng test",
    "lint": "ng lint",
    "e2e": "ng e2e"
  },
// [...]
```

Updating dependencies

```
$ npm install
```

Run the application:

```
$ npm start
```

Finished
