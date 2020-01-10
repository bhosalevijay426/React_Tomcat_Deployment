# React_Tomcat_Deployment
Deploy your react application using spring boot and Apache tomcat

Deploy react JS  in tomcat or any servlet container is a challenge and bit tricky. There is an issue in one of my app that I am developing. I have used BrowserRouter in my app.

So the issue is there were no errors as such in the code but nothing is loading.I see a White Screen with no errors. I checked the console and saw its throwing  404 for some of my bundled static resources.

A strange behavior is noticed, if I run the app in web pack dev server same code works fine and routers works fine as well.But same behavior is not observed once I deploy to tomcat.
React router takes the root URL  by default, hence able to serve static resources from tomcat ROOT directory.But Once you deploy the build files to a different path is not able to serve static content.

Tools Used:-
Maven 3.3.9
Npm

 Configure BrowserRouter in our app as follows, provide full path of your context as follows
 
 <BrowserRouter basename={process.env.REACT_APP_ROUTER_BASE||''}>
  
I declared three routes in my sample app, My maven script will replace the basename with actual tomcat url context.process.env.REACT_APP_ROUTER_BASE will be replaced by maven .

Basically, when you type the URL by hand, by default the server will look for a file with that path, stored on its disk — if not found, it will show a 404 error. What we want to do is internally redirect the request for static resources to the index of your application.

Steps : - 
1. Pull or clone project to your local directory
2. Keep pom.xml and web.xml as it is and replace rest of the files with your react application.
3. Change pom.xml as per your needs.
4. Now open command prompt on that directory and run - 
     i. npm install
     ii. mvn clean install
