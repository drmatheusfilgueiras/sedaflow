{
  "name": "sedaflow",
  "version": "0.1.0",
  "private": true,
  "author": "Dr. Matheus Filgueiras",
  "description": "SedaFlow - prontuário e acompanhamento de pacientes em sedação odontológica.",
  "main": "electron/main.js",
  "scripts": {
    "start": "node server.js",
    "desktop": "electron .",
    "build:desktop": "electron-builder --win nsis",
    "build:desktop-portable": "electron-builder --win portable"
  },
  "dependencies": {
    "nodemailer": "^8.0.6"
  },
  "devDependencies": {
    "electron": "^37.1.0",
    "electron-builder": "^26.0.12",
    "png-to-ico": "^3.0.1"
  },
  "build": {
    "appId": "com.sedaflow.desktop",
    "productName": "SedaFlow",
    "asar": false,
    "directories": {
      "output": "dist-electron",
      "buildResources": "build"
    },
    "files": [
      "build/icon.ico",
      "electron/**/*",
      "public/**/*",
      "scripts/**/*",
      "server.js",
      "package.json",
      "!data{,/**/*}",
      "!desktop{,/**/*}",
      "!dist{,/**/*}",
      "!dist-electron{,/**/*}",
      "!source-docs{,/**/*}",
      "!server*.log"
    ],
    "win": {
      "signAndEditExecutable": false,
      "icon": "build/icon.ico",
      "target": [
        {
          "target": "nsis",
          "arch": [
            "x64"
          ]
        }
      ],
      "artifactName": "SedaFlow-Setup-${version}.exe"
    },
    "nsis": {
      "oneClick": false,
      "allowToChangeInstallationDirectory": true,
      "createDesktopShortcut": true,
      "createStartMenuShortcut": true,
      "shortcutName": "SedaFlow",
      "installerIcon": "build/icon.ico",
      "uninstallerIcon": "build/icon.ico",
      "installerHeaderIcon": "build/icon.ico"
    }
  }
}
