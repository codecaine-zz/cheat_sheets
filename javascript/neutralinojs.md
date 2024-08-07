### Application

**Neutralino.app.exit**

```javascript
Neutralino.app.exit();
```

**Neutralino.app.getConfig**

```javascript
Neutralino.app.getConfig().then((config) => {
    console.log(config);
});
```

**Neutralino.app.broadcast**

```javascript
Neutralino.app.broadcast('myEvent', { message: 'Hello, world!' });
```

### Events

**Neutralino.events.on**

```javascript
Neutralino.events.on('myEvent', (event) => {
    console.log(event);
});
```

### File System

**Neutralino.filesystem.readFile**

```javascript
Neutralino.filesystem.readFile('path/to/file.txt').then((content) => {
    console.log(content);
});
```

**Neutralino.filesystem.writeFile**

```javascript
Neutralino.filesystem.writeFile('path/to/file.txt', 'Hello, world!').then(() => {
    console.log('File written successfully');
});
```

**Neutralino.filesystem.removeFile**

```javascript
Neutralino.filesystem.removeFile('path/to/file.txt').then(() => {
    console.log('File removed successfully');
});
```

**Neutralino.filesystem.readDirectory**

```javascript
Neutralino.filesystem.readDirectory('path/to/directory').then((files) => {
    console.log(files);
});
```

**Neutralino.filesystem.createDirectory**

```javascript
Neutralino.filesystem.createDirectory('path/to/new/directory').then(() => {
    console.log('Directory created successfully');
});
```

**Neutralino.filesystem.removeDirectory**

```javascript
Neutralino.filesystem.removeDirectory('path/to/directory').then(() => {
    console.log('Directory removed successfully');
});
```

### Computer

**Neutralino.computer.getMemoryInfo**

```javascript
Neutralino.computer.getMemoryInfo().then((memoryInfo) => {
    console.log(memoryInfo);
});
```

**Neutralino.computer.getOSInfo**

```javascript
Neutralino.computer.getOSInfo().then((osInfo) => {
    console.log(osInfo);
});
```

### Debug

**Neutralino.debug.log**

```javascript
Neutralino.debug.log('INFO', 'This is an info message');
```

### Window

**Neutralino.window.setTitle**

```javascript
Neutralino.window.setTitle('New Title');
```

**Neutralino.window.maximize**

```javascript
Neutralino.window.maximize();
```

**Neutralino.window.minimize**

```javascript
Neutralino.window.minimize();
```

**Neutralino.window.fullscreen**

```javascript
Neutralino.window.fullscreen();
```

**Neutralino.window.isFullscreen**

```javascript
Neutralino.window.isFullscreen().then((isFullscreen) => {
    console.log(isFullscreen);
});
```

**Neutralino.window.show**

```javascript
Neutralino.window.show();
```

**Neutralino.window.hide**

```javascript
Neutralino.window.hide();
```

**Neutralino.window.focus**

```javascript
Neutralino.window.focus();
```

**Neutralino.window.setIcon**

```javascript
Neutralino.window.setIcon('path/to/icon.png');
```

**Neutralino.window.create**

```javascript
Neutralino.window.create('https://neutralino.js.org', {
    width: 800,
    height: 600,
    title: 'Neutralino.js Window',
    icon: 'path/to/icon.png'
});
```

### Storage

**Neutralino.storage.putData**

```javascript
Neutralino.storage.putData('key', 'value').then(() => {
    console.log('Data stored successfully');
});
```

**Neutralino.storage.getData**

```javascript
Neutralino.storage.getData('key').then((data) => {
    console.log(data);
});
```

**Neutralino.storage.clearData**

```javascript
Neutralino.storage.clearData().then(() => {
    console.log('All data cleared');
});
```

### Updates

**Neutralino.updates.checkForUpdates**

```javascript
Neutralino.updates.checkForUpdates().then((updateInfo) => {
    console.log(updateInfo);
});
```

### OS

**Neutralino.os.execCommand**

```javascript
Neutralino.os.execCommand('echo Hello, world!').then((output) => {
    console.log(output);
});
```

**Neutralino.os.open**

```javascript
Neutralino.os.open('https://neutralino.js.org');
```

### Settings

**Neutralino.settings.getSettings**

```javascript
Neutralino.settings.getSettings().then((settings) => {
    console.log(settings);
});
```

### Notification

**Neutralino.notification.show**

```javascript
Neutralino.notification.show('Notification Title', 'This is a notification message.');
```

### Clipboard

**Neutralino.clipboard.writeText**

```javascript
Neutralino.clipboard.writeText('Hello, world!').then(() => {
    console.log('Text copied to clipboard');
});
```

**Neutralino.clipboard.readText**

```javascript
Neutralino.clipboard.readText().then((text) => {
    console.log(text);
});
```
