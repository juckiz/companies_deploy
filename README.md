# companies_deploy
Only built public folder and node server with dependencies from companies project
#### Note:
This is a very poor deployment method. Too much is done manually and relative paths don't translate from development. This repository exists to demostrate the app being developed. Compared to development project in this you don't have to install node modules. Starting the server is enough.
## Requirements
Node should be installed
## What is this?
- The idea is that we run ```npm run build``` in [companies](https://github.com/juckiz/companies) client folder
- This produces ```build``` folder which contains all ```companies``` app's HTML, JavaScript, and CSS (static) files
- This project contains
  - ```build``` folder for static files
  - ```node_modules``` folder for Node requirements
  - ```server/api``` folder for api routes 
  - ```server.js``` Node server file

Out Node server has been configured to also serve static files from "build" folder.
```
server.route({
    method: 'GET',
    path: '/{path*}',
    handler: {
        directory: {
          path: Path.join(__dirname, '../../build'),
          listing: false,
          index: true
        }
    }
})
```
## Running
- In the ```companies_deploy``` root start Node server
  - ```node server.js```
    - Should output ```Server running at http://localhost:3001```
- Navigate to ```http://localhost:3001/index.html``` and you should see the app
