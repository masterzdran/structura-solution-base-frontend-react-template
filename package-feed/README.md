# Package Feed Configuration

This folder contains an `.npmrc` file that configures npm to use both the public npm registry and a private npm registry for scoped packages.

## Usage

- **Public Registry:**  
  All packages are fetched from the default public npm registry:  
  `https://registry.npmjs.org/`

- **Private Registry:**  
  Packages with the scope `@your-scope` are fetched from your private registry:  
  `https://your-private-registry.example.com/`  
  Replace `@your-scope` and the registry URL with your actual scope and private registry address.

- **Authentication (Optional):**  
  If your private registry requires authentication, uncomment and set the following line in `.npmrc` with your auth token:
  ```
  //your-private-registry.example.com/:_authToken=YOUR_AUTH_TOKEN
  ```

## How It Works

- When you run `npm install`, npm will:
  - Download public packages from the public registry.
  - Download packages with the specified scope from your private registry.

## Customization

- Change `@your-scope` to match your organization's npm scope.
- Update the private registry URL as needed.
- Add your authentication token if required.

## Example

To install a package from your private registry:
```
npm install @your-scope/package-name
```

To install a public package:
```
npm