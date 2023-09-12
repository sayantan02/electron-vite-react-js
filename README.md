# electron-vite-react-js

![GitHub stars](https://img.shields.io/github/stars/sayantan02/electron-vite-react-js?color=fa6470)
![GitHub issues](https://img.shields.io/github/issues/sayantan02/electron-vite-react-js?color=d8b22d)
![GitHub license](https://img.shields.io/github/license/sayantan02/electron-vite-react-js)
[![Required Node.JS ^20.6.0 || >20.6.0](https://img.shields.io/static/v1?label=node&message=20.6.0%20||%20%3E20.6.0&logo=node.js&color=3f893e)](https://nodejs.org/about/releases)

## 💳 Credit [electron-vite-react](https://github.com/electron-vite/electron-vite-react)

## 👀 Overview

📦 Ready out of the box  
🌱 Easily extendable and customizable  
💪 Supports Node.js API in the renderer process  
🔩 Supports C/C++ native addons  
🐞 Debugger configuration included  
🖥 Easy to implement multiple windows  
🧊 Migrated for Javascript

## 🛫 Quick Setup

```sh
# clone the project
git clone https://github.com/sayantan02/electron-vite-react-js.git

# enter the project directory
cd electron-vite-react-js

# install dependency
npm install

# develop
npm run dev

#Build for Production
npm run build
```

## 📂 Directory structure

Familiar React application structure, just with `electron` folder on the top :wink:  
*Files in this folder will be separated from your React application and built into `dist-electron`*  

```tree
├── electron                                 Electron-related code
│   ├── main                                 Main-process source code
│   └── preload                              Preload-scripts source code
│
├── release                                  Generated after production build, contains executables
│   └── {version}
│       ├── {os}-{os_arch}                   Contains unpacked application executable
│       └── {app_name}_{version}.{ext}       Installer for the application
│
├── public                                   Static assets
└── src                                      Renderer source code, your React application
```


## ⚠️ Some Precautions

This template is containg a file for integrating Node.js API to the renderer process which is turned off by default. If you want to work with the renderer processes use the **Context Bridge** feature for enabling specific features to be open for the main world.

If you don't want to use the Context Bridge feature and expose the whole Node.js API to the renderer process just do the below work. **TIP: 🚨 Don't use ContextIsolation: false in a production Environment**
```js
// electron/main/index.js

ipcMain.handle('open-win', (_, arg) => {
  const childWindow = new BrowserWindow({
    webPreferences: {
      preload,
      nodeIntegration: true,
      contextIsolation: false,
    },
  })
```

## ❔ FAQ

- [C/C++ addons, Node.js modules - Pre-Bundling](https://github.com/electron-vite/vite-plugin-electron-renderer#dependency-pre-bundling)
- [dependencies vs devDependencies](https://github.com/electron-vite/vite-plugin-electron-renderer#dependencies-vs-devdependencies)
