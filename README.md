# Heroku buildpack : Gradle
This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpack) for [Gradle](http://www.gradle.org/) apps.  
It has been updated to support latest version of Gradle.

## Usage
Example usage :

    $ ls  
    build.gradle

For a new app :

    $ heroku create --buildpack https://github.com/joow/heroku-buildpack-gradle.git
    
or for an existing app :

    $ heroku config:set BUILDPACK_URL=https://github.com/joow/heroku-buildpack-gradle

    $ git push heroku master
    -----> Fetching custom git buildpack... done
    -----> Gradle app detected
    -----> Building Gradle app...

It is worth mentioning that your gradle build should :

1. Use the [application plugin](http://www.gradle.org/docs/current/userguide/application_plugin.html) :  
`apply plugin: 'application'`

2. Define the main class name and the application name (used by the application plugin to run your app) :  
`mainClassName = 'my.main.class.Name'`  
`applicationName = 'MyApplicationName'`

3. Define a new task called "stage" used by the buildpack to compile your app :  
`task stage(dependsOn: ['clean', 'installApp'])`

## License
See LICENSE file.
