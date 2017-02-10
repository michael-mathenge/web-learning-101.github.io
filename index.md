# Getting started with Grunt #

1. Install *NodeJS* then run command `npm install -g grunt-cli`.
2. Install *grunt* locally on your project in this case we'll use project1 i.e. `location/to/project1>npm install grunt --save-dev`. This will create a folder called `node_modules`
3. Create *Package.json* by running command `npm init` and follow the on-screen prompts. his will generate for you a file called `package.json`. Open this file.
4. Go to http://gruntjs.com/plugins and get the plugin you want, for this example, we want to "watch" a javascript file called `bootstrap.js`, so in the page look for watch plugin https://www.npmjs.com/package/grunt-contrib-watch.
5. Run `npm install grunt-contrib-watch --save-dev` in the root of the project, this will add the dependency in package.json like 

``` "devDependencies": {
    "grunt-contrib-watch": "^1.0.0"
  } ```
  
  we'll get to that later.
  
6. Inside package.json set up a "wrapper" function 

``` module.exports = function(grunt) {
  // Add configuration, tasks and plugins here
}; ```

7. Set up the configuration like 

```grunt.initConfig({

    // imports the config data from the package.json
    pkg: grunt.file.readJSON('package.json'),


}); ```

your entire file should look like 

``` "use strict";
module.exports = function(grunt){

grunt.initConfig({
	//imports the config data from the package.json
	pkg: grunt.file.readJSON('package.json'),

uglify: {
		my_target: {
			files: {
				'js/output.min.js': ['mathenge.js']
		}
	}
},
	watch: {
		scripts: {
			files: ['mathenge.js'],
			tasks: ['jshint'],
			options: {
				spawn: false
			},
		},
	}
});

grunt.loadNpmTasks('grunt-contrib-uglify');
    grunt.loadNpmTasks('grunt-contrib-watch');

      grunt.registerTask('default', ['uglify','watch']);

}; ```



