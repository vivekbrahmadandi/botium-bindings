# Botium Bindings Sample: PHP Chatbot

The Chatbot used in this sample project is based on the [Chatbot PHP Boilerplate](https://github.com/christophrumpel/chatbot-php-boilerplate) project.

## Code Changes to the boilerplate code

There are some minor changes in code required:
* Point the file "debug.log" to "/tmp/debug.log", as the current directory usually isn't writeable
* Set some curl options (in src/FacebookSend.php) to allow connection to the TestMyBot Mocker

      curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, FALSE);
      curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, 0);

## The Botium Configuration

The docker image used is "webdevops/php-nginx:7.1", with php and nginx. The command "composer install && supervisord" runs composer to install PHP dependencies and then starts the background processes (supervisord is included with the docker images from webdevops).

The environment variable "WEB_DOCUMENT_ROOT" points to the web server document root.

## Setting up Botium Bindings

Now you can just initialize your project directory with Botium.

    $ npm init
    $ npm install botium-bindings --save-dev
    $ npm install jasmine --save-dev
    $ ./node_modules/.bin/jasmine init
    $ ./node_modules/.bin/botium-bindings init jasmine
    $ ./node_modules/.bin/jasmine
