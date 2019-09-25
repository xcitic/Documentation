## Testing using Selenium Webdriver and Codeception 
+ Link for more info: https://codeception.com/docs/modules/WebDriver#Selenium

### Setup for Local System
- Install Java SDK on your testing system.
   + <a href="https://www.java.com/en/">Download and install Java SDK</a>

- Install ChromeDriver
   + <a href="https://sites.google.com/a/chromium.org/chromedriver/downloads">Download and install the version of ChromeDriver that matches your browser version</a>
       + Alternatively install with brew `brew cask install chromedriver`

- Install Selenium Server 
    + <a href="https://docs.seleniumhq.org/download/">Download from and install Selenium Standalone Server </a>


### Prepare and Launch the Services
- Configure the module to use selenium (inside the project folder)

```yaml
    /* acceptance.suite.yml */ 
    modules:
        enabled:
            - WebDriver:
                url: 'http://localhost:8000'
                window_size: false
                port: 9515
                browser: chrome
                capabilities:
                    "goog:chromeOptions":      
```    
- Start the web server for the project `./bin/run server:run` for symfony
- Start the selenium server <br/>
` java -jar selenium-server-standalone-3.xxx.jas `
- Start the Chromedriver 
    + If installed with brew cask `chromedriver --url-based=/wd/hub`
    + if downloaded as binary `./chromedriver --url-based=/wd/hub` 



## Headless Selenium in Docker
+ Selenium server with all its dependencies and browsers inside a single container. By using --net-host flag we allow selenium to access local websites. 
<br/>
` docker run --net=host selenium/standalone-chrome `


### Using BrowserStack 
+ BrowserStack makes it easy to test cloud applications. 
Set it up with the following config: 

```yaml
modules:
    enabled:
        - WebDriver:
            url: 'http://siteurl.com'
            host: '<username>:<access-key>@hub.browserstack.com'
            port: 80
            browser: chrome 
            capabilities:
                os: Windows
                os_version: 10
                browserstack.local: true  #only for local testing 
``` 


