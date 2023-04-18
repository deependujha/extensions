# Chrome extensions 📱💻

## What are extensions?

Chrome extensions enhance the browsing experience by adding features and functionality to the Chrome browser, providing things like:

- Productivity tools.
- Web page content enrichment.
- Information aggregation.

~> Extensions are written with the same web technologies used to create web applications: (HTML, CSS, JS).

~> **Extensions can use all the JavaScript APIs that the browser provides. What makes extensions more powerful than a web app is their access to Chrome APIs**. The following are just a few examples of what extensions can do:

- `Change the functionality or behavior of a website.`
- `Allow users to collect and organize information across websites.`
- `Add features to Chrome DevTools.`

---

## Extension files 🗃️

### **`The manifest (manifest.json)`**:

- The extension's manifest is the **only required file** that must have a specific file name: manifest.json.

- **It also has to be located in the extension's root directory**.

- `The manifest records important metadata, defines resources, declares permissions, and identifies which files to run in the background and on the page.`

<br/>

### **`The service worker`**:

- The extension service worker **handles and listens for browser events**.

- There are many types of events, ***such as navigating to a new page, removing a bookmark, or closing a tab**.

- **`It can use all the Chrome APIs`**, but it **cannot interact directly with the content of web pages**; that’s the job of content scripts.

<br/>

### **`Content scripts`**:

- Content scripts execute Javascript in the context of a web page.

- They can also **read and modify the DOM of the pages they're injected into**.

- **`Content Scripts can only use a subset of the Chrome APIs but can indirectly access the rest by exchanging messages with the extension service worker`**.

<br/>

### **`The popup and other pages`**:

- An extension can include various HTML files, such as a popup, an options page, and other HTML pages.

- **`All these pages have access to Chrome APIs`**.

<br/>

### ~> 💡 Do all extensions have a popup?

Many extensions use a popup to customize the user experience, however this is **not required**.

---


## Steps to create an extension 📝

### 1. Create a new folder for your extension

### 2. Create a manifest.json file
 

```json
// ~> example of a sample manifest.json file:

{
  "manifest_version": 3,
  "name": "My Extension",
  "version": "1.0",
  "description": "My first extension",

//  the "action" key declares the image Chrome should use as the action's icon,
//  and the HTML page to show in a popup when the action is clicked.

  "browser_action": {
    "default_icon": "icon.png",
    "default_popup": "popup.html"
  }
}
```

### 3. Place the icon.png file in the root folder (or at the path specified in the manifest.json file)

### 4. Create the popup.html file

```html
 <!-- ~> example of a sample popup.html file: -->
<html>
  <body>
    <h1>Hello Extensions</h1>
  </body>
</html>
```

---

## Loading an unpacked extension (testing & debugging) 🐛

To load an unpacked extension in developer mode:

1. Go to the Extensions page by entering `chrome://extensions` in a new tab. (By design chrome:// URLs are not linkable.)

2. Alternatively, **click on the Extensions menu puzzle button and select Manage Extensions at the bottom of the menu**.

3. Enable Developer Mode by clicking the toggle switch next to Developer mode.

4. Click the Load unpacked button and select the extension directory.

![upload unpacked extension](./readme_assets/uploadUnpackedExtension.avif)

---

## Reloading the extension 🔄

- Once you've loaded an unpacked extension, you can make changes to the extension's files and reload the extension to see the changes.

- To reload an extension, Go to the Extensions page and click the refresh icon next to the on/off toggle:

![reload extension](./readme_assets/reloadExtension.avif)

---

## Pinning the extension 📌

- By default, when you load your extension locally, it will appear in the **extensions menu Puzzle**🧩. Pin your extension to the toolbar to quickly access your extension during development.

![pin extension](./readme_assets/pinExtension.avif)

---

## Finding console logs 🤟

During development, you can debug your code by accessing the browser console logs. In this case, we will locate the logs for the popup. Start by adding a script tag to hello.html.

```html
<html>
  <body>
    <h1>Hello Extensions</h1>
    <script src="popup.js"></script>
  </body>
</html>
```

- Create a popup.js file and add the following code:

```js
console.log("This is a popup!")
```

####To see this message logged in the Console:

1. Open the popup.
2. Right-click on the popup.
3. Select Inspect.
![inspect popup](./readme_assets/inspect.avif)
4. In the DevTools, navigate to the Console panel.
![console panel](./readme_assets/console.avif)

---

## Structuring an extension project 👷🏗️

![extension project structure](./readme_assets/structure.avif)

---