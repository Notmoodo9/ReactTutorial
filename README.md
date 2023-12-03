Tutorial to make a react application 

# Create a new project
	Create a new Folder
	Run npm init -y in the folder 

# Install React and ReactDOM
	In the directory run 
	npm install react react-dom

# Set up babel (Thing used for building)
	Install all necessary packages run 
 	npm install @babel/core @babel/preset-env @babel/preset-react babel-loader
  
	Create a file called .babelrc in the root of the dir past in 
	{
  	   "presets": ["@babel/preset-env", "@babel/preset-react"]
	}

# Set up webpack
    Install all necessary packages run 
    npm install --save-dev webpack webpack-cli webpack-dev-server style-loader css-loader babel-loader html-webpack-plugin mini-css-extract-plugin
    Create a file called webpack.config.js in the root
    Set the name changing the name const (Good for output makes it better) 

   # Code
    const HtmlWebpackPlugin = require('html-webpack-plugin');
    const MiniCssExtractPlugin = require('mini-css-extract-plugin');
    const path = require("path"); 

    const name = "Project_Name";

    module.exports = {
      output: {
        path: path.resolve(__dirname, 'dist'), 
        filename: `${name}.js`,
      },
      module: {
        rules: [
        {
          test: /\.(js|jsx)$/,
          exclude: /node_modules/,
          use: {
            loader: 'babel-loader'
          }
        },
        {
          test: /\.css$/,
          use: [MiniCssExtractPlugin.loader, 'css-loader']
        }]
      },
      plugins: [
        new HtmlWebpackPlugin({
          template: './src/index.html',
          filename: `${name}.html` // Custom HTML filename
        }),
        new MiniCssExtractPlugin({
          filename: `${name}.css` // Custom CSS filename
        })
      ],
      resolve: {
        extensions: ['.js', '.jsx']
      }
    };

# Add Scripts that give your app functionality 
	Find the package.json file and in the scripts area add
 
	"start": "webpack-dev-server --mode development --open",
  	"build": "webpack --mode production"	

# Set up for actually making things
	Create a new folder called "src"
	create three new files:
	index.html
	index.js
	style.css
	
## In index.js
	import React from 'react';
	import ReactDOM from 'react-dom';

	import "./style.css";

	const App = () => {
  	  return <h1>Hello, React!</h1>;
	};

	// Render the App component into a div with the id of 'root'
	ReactDOM.render(<App />, document.getElementById('root'));
 
	^ This is a simple react project that will render a little html 
 
## In index.html
	<!DOCTYPE html>
	<html lang="en">
	<head>
  	  <meta charset="UTF-8">
  	  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  	  <title>React App</title>
	</head>
	<body>
  	  <div id="root"></div>
	</body>
	</html>
	^ Simple set up more is needed

	Style.css:
	just put the css you want in here
	
# to test 
	to test the code run: 
	npm run start
	It will launch a dev test and if you want to have it update just do ctrl S on the file and it will auto update
	
# to build
	to build the code run: 
	npm run build
	It will output to a a folder called dist 
	With that output you need to set up a node.js server 

