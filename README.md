# PHP Web Server Application

The disadvantage of a PHP script is that a lot of the same initialization has to be done before a request can be serviced.
A interface to integrate a PHP application with the webserver could offer a serious positive impact on performance.
Offcourse, this creates a need for a module for the server software to implement it.

The interface could look like the following:

    <?php
    
    interface WebServerApplication {
    
        /**
         * Initializes the web application, is invoked when the web server starts or reloads
         * @return null
         */
        public function boot();
        
        /**
         * Services an incoming request like any normal PHP request
         * @return null
         */
        public function service();
    
    }
    
When a fatal error occurs on the PHP side of the application, the server module should log the error and boot the application again.
If the boot process of the application crashes, the web server should disable the application until restarted or reloaded.