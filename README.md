# CRUD For Human Resources using .Net and React.js


# Development History:

## 1) For the DB:

- Created MongoDB database using AWS server;
- Created Collection for the department with the keys: DepartmentId and DepartmentName;
- Created Collection for the employees with the keys: EmplyeeId, EmployeeName, Department, DateOfJoining and PhotoFileName;

## 2) For the Web API:

- Created hr-management project using web API model in Visual Studio
- Enabled CORS policy for allowing requests from different domais using `services.addCorsPolicy` and `app.useCors` . Added json serializer just to keep it as default through nuGet package mvc.NewtonsoftJson (Commit01);
- Added ConnectionStrings to json and through mongoDB “Add your application” option and models for the Department.cs and Employee.cs for `get` and `set` from database itens (Commit02);
- Created the API controllers for the MongoDB’s Department’s collections using the methods `[Http Get/Post/Put/Delete]` . Since MongoDB is the Database, MongoClient was used along with `getDatabase` and `getCollection` to finally apply `Asqueryable`/`InsertOne`/`UpdateOne`/`DeleteOne` methods(Commit03). The 4 implementations were tested OK using Postman;
- Added EmployeeController.cs with the same methods as DepartmentController.cs . Also corrected a typo in database collection Employee which was written “EmplyeeId” instead of “EmployeeId”. Fixed broken EmployeeController.cs Tested everything in Postman before committing. Tried to “add photo” API but erased it to come back at it later when the upload file API has it’s components in startup.cs (Commit04);
- Added File Upload API and a default anonymous profile picture  (Commit05) Since the profile photo is theoretically an statical item, we could use `app.UseStaticFiles` and store it in a folder. For this method, we will use a custom route, described in the EmployeeController.cs because the file paths were stored inside the  Employee collection; Testing using Postman PASSED;
- From this point, the API backbone is ready to use. Now I will build an UI for the front end and if there are any errors found later;

## 3) For the UI:

- Created the React project inside the “front” folder separated from the API folder for better organization. For easier styling, Bootstrap will be used (Commit06);
- React-router-dom installed for the routing through different URL. 3 pages added: Home.js , Department.js , Employee.js . Imported BrowserRouter, Route, Switch Navlink for routing navigation. Finally, routing through navbar. After testing, routing was broken. Fixed changing Switch to Routes and ‘components’ to ‘elements’ so that the routes could be linked correctly to the corresponding imported .js files(Commit07);
- Created bootstrap table for the Department page. Also, created the variables.js file as an auxiliar file to find the photos. Bootstrap icons added for edit and delete functions. Added method for refreshing the data from Department API and use the API. Added sorting and filtering (from stackOverflow) for better functionality. Added popup for creating new department (Commit08);
- Created the Employee page (basically a copy from the Department using the `.map` method to iterate plus the correct keys for the DB) One big difference is the employee’s details screen, because it has 4 editable attributes in the database and the upload button function was implemented using Hooks and append to target file. The icons and structure, otherwise, are the same as the Department page. Had to correct the divisions on VS code many times and the broken photo linkage (known issue: the photo is not resizing according to the screen size) (Commit09);
- Corrected: not used imports, wrong names and minor typos in the interface just to polish the interface a little further and make everything more concise -I wrote many stuff in UI initially using English instead of pt, so this commit just makes everything pt-BR) (Commit10);
