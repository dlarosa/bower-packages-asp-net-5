# Bower Packages in ASP.NET 5

[Bower](http://bower.io/) is a Node.js tool to manage front-end dependencies. It's a package manager just like NuGet, but for front-end libraries. With this tool, we can add things like jQuery, Angular or Bootstrap to our project. 

In this demo, I will explain how to use Bower to manage front-end dependencies in our ASP.NET 5 project.

### Installing Node.js

To install Bower, we need to have Node.js installed on our machine. Visual Studio 2015 installs Node.js by default, so you may already probably have it on your computer. If not, you can download and install it from [here](https://nodejs.org/download/). 

To verify that Node.js is installed correctly, open the Command Prompt (or Powershell) and type the following command:

```sh
> Node
```

The output should indicate that we just opened the interactive node.js shell, from which we can start executing JavaScript code directly. 


<p align="center">
  <img width="60%" src="https://raw.githubusercontent.com/dlarosa/bower-packages-asp-net-5/master/images/0.PNG?raw=true" alt=""/>
 </p>

If for any reason, we get a _"node is not recognized as an internal or an external command"_ , make sure Node is added to the Windows PATH environment variable. 

### Installing Bower

Now that Node is installed correctly in our system let’s proceed to install Bower. We are going to do this with the help of [NPM](https://www.npmjs.com/), a package manager for Node. With this tool, we can install things like Gulp, Grunt or in our case, Bower.

To install Bower enter the following command:

```sh
> npm install -g bower
```

The ‘g’ stands for ‘global’, this option installs the package globally so that we can run it from everywhere as a command.


### Managing front-end packages

If everything went correctly, we should now have Bower installed on our machine. It’s time to take advantage of this awesome tool and start adding our favorites front-end libraries to our project. 

There are two main options to manage Bower packages in an ASP.NET 5 project: from the bower.json file or from the Command Prompt.

The bower.json file is the Bower manifest file, from which we can track all the packages that are used by our project. This file is very similar to the project.json file that we use to manage NuGet packages and other dependencies.

We can add a bower.json file to our project very easily from Visual Studio. From the Solution Explorer, right-click on the project -> Add ->  Bower JSON Configuration File

<p align="center">
  <img width="60%" src="https://raw.githubusercontent.com/dlarosa/bower-packages-asp-net-5/master/images/2.PNG?raw=true" alt=""/>
 </p>

Now that the bower.json file is part of our project, let’s add the AngularJs library. To do this, create a new entry under the dependencies section of the bower.json file. This entry will contain the name and the version of the package we want to add.



```js
{
    "name": "BowerApp.Properties",
    "private": true,
    "dependencies": {
        "angular": "1.3.15"
    },
    "exportsOverride": {
    }
}
```


Notice that Visual Studio provides Intellisense to help us to select among all the Bower packages available. By the way, you can find a list of all the Bower packages that are currently available [here](http://bower.io/search/).

We now save the changes, and AngularJs should be added automatically to our project. But before we verify this fact we are going to add another package, however, this time we are going to do it from the Command Prompt.


Let’s add for example [Font Awesome](http://fortawesome.github.io/Font-Awesome/), a font and CSS toolkit for web applications. We can install this package just by entering the following command:

```sh
> bower install font-awesome –save
```

The new package should now be a dependency of our project. If we go back to our bower.json file we can see that a new entry for the Font Awesome package was added.

```js
{
  "name": "BowerApp",
  "private": true,
  "dependencies": {
    "angular": "1.3.15",
    "font-awesome": "~4.3.0"
  },
  "exportsOverride": {}
}
```

What if we want to remove an existing dependency? We again have two options; we can either delete the entry for the package from the bower.json file or use the following command from the Command Prompt:

```sh
> bower uninstall angular
```

If what we want is to update the version of one of our dependencies, update the version number directly in the bower.json file, or from the Command Prompt:

```sh
> bower update angular
```

And this will update the package to the latest version available.

Personally I find editing the bower.json file a much easier approach than from the Command Prompt, but both methods are very simple and easy to use.

### Viewing the list of Bower dependencies

The easiest way to know what dependencies are included in our project is by looking at the bower.json file. Whatever dependencies are included in this file will be the ones included in our project. 

Even if the dependencies are not physically on our machine but are added to this file, they will be downloaded and installed automatically the first time the project is compiled. 

This is a very useful feature because it removes the need of including the dependency files when checking in our code to the source control. We only need to check in the bower.json file that will already the list of project dependencies.

We can also view the Bower dependencies included in our project from the Solution Explorer. They are listed under Dependencies -> Bower

 <p align="center">
  <img  width="30%" src="https://raw.githubusercontent.com/dlarosa/bower-packages-asp-net-5/master/images/7.PNG?raw=true" alt=""/>
 </p>


Or even from the Command Prompt just by typing in the following command:

```sh
> bower list
```

Finally, if what we want is to access the physical files of our Bower packages we should go to the bower-component folder, at the root of our project. This is the place where Bower dependencies are placed by default.

<p align="center">
  <img width="60%" src="https://raw.githubusercontent.com/dlarosa/bower-packages-asp-net-5/master/images/8.PNG?raw=true" alt=""/>
 </p>




