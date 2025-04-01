# Single-SPA Project Setup

## Root Config

### 1. Upgrade Single-SPA Version
- Change the **Single-SPA** version from `5` to `6.0.1`.

### 2. Add React & React-DOM to EJS File
- Update the **EJS template** to include the latest **React** and **React-DOM**:
  ```json
  "react": "https://cdn.jsdelivr.net/npm/react@19.0.0/+esm",
  "react-dom/client": "https://cdn.jsdelivr.net/npm/react-dom@19.0.0/client/+esm"
  ```

### 3. Add Route to Layout File
- Ensure the **layout file** includes appropriate routes for navigation between microfrontends.

## Applications

### 1. Navigate to Application Directory
- Move to the respective **application directory**:
  ```sh
  cd apps/app-name
  ```

### 2. Install Type Definitions
- Install the latest **React and React-DOM type definitions**:
  ```sh
  npm install @types/react@latest @types/react-dom@latest --save-dev
  ```
- **Important:** Do not use `npm i -f` to resolve dependencies forcefully.

### 3. Install Dependencies
- Run:
  ```sh
  npm install
  ```

### 4. Verify Module Export Functions
- Ensure that `org-appname.js` file **properly loads and exports** the required Single-SPA lifecycle functions:
  ```js
  export const { bootstrap, mount, unmount } = lifecycles;
  ```

### 5. Add Port to Package.json
- Modify `package.json` to specify a port:
  ```json
  "scripts": {
    "start": "webpack serve --port 8081"
  }
  ```

### 6. Modify Webpack Config
#### 6.1 Comment Out `outputSystemJS: true`
- In `webpack.config.js`, **comment out** the following line:
  ```js
  // outputSystemJS: true,
  ```

#### 6.2 Add `externals` for RxJS Support
- Add the following **externals** configuration and merge it:
  ```js
  const externals = [/^rxjs\/?.*$/];
  return merge(defaultConfig, {
    externals,
    // Modify the webpack config however you'd like by adding to this object
  });
  ```

## Summary
- [ ] Upgrade Single-SPA to **v6.0.1**.
- [ ] Add **React & React-DOM** via **CDN in EJS file**.
- [ ] Update **layout file** to include navigation routes.
- [ ] Install latest `@types/react` and `@types/react-dom`.
- [ ] **Verify** correct export of lifecycle methods.
- [ ] Add **port (8081)** in `package.json`.
- [ ] **Modify webpack config** to exclude SystemJS output and support RxJS.

Your Single-SPA microfrontend project is now correctly configured.

