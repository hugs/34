34.js
=====

Yet another Selenium WebDriver library for Node...

(Warning: This is a design doc... There's no code, yet! But when it lands, it'll most likely be based on [webdriver-http-sync](https://github.com/groupon-testium/webdriver-http-sync).

### Goals:

  - JavaScripty - This should feel like a JavaScript API, not a port from Java
  - For automating web browsers: desktop *and* mobile
  - Synchronous API - Async makes no sense for shell scripts or user interface test automation.
  - Try to reduce locator strategy proliferation. Use CSS selectors as much as possible.
  - Optimize for interactive exploration at the console.
   - Yeah:
      - Pithy property names FTW
      - Easy discovery of properties via tab completion in the console.
      - e.g. thing.fromulated
   - Boo:
      - e.g. driver.window().getFrombulationStatusOfThing(By.whyAmIStillTyping())

### Non-Goals:
  - Automating non-web native apps. (Although I hope this is temporary!)

<hr>

### Install

    npm install 34

### Example Usage

    Driver = require('34').Driver
    se = new Driver()


### API


    // Navigation
    // ----------

    // Open a URL
    se.url = 'http://google.com'
    se.open = function(url) { return this.url = url }
    se.go = se.open

    se.back()
    se.forward()
    se.refresh()

    // Close current window
    se.close()

    // End current session
    se.quit()


    // Frame Navigation

    //   Switch focus to frame
    se("#IdOfSomeFrame").focus()

    //   Switch focus to parent frame
    se.parent()


    // Window Navigation

    //   Switch focus to window
    se.window('nameOfWindow')



    // Interrogation
    // -------------

    // Driver
    se.url
    se.title
    se.source

    // Server status
    se.status

    // Id of current session
    se.session

    // List of all sesions
    se.sessions

    // Handle id of current window
    se.window

    // List of all window handle ids
    se.windows

    // Id of active (focused) element
    se.activeElement

    // Find Element
    e = se("#id")
    // Find All elements
    es = se('*[#id]')

    // By name:
    se('[name="theName"]')

    // By id:
    se('#theId')

    // By tag name:
    // all links
    se('a')

    // Element
    e.attribute('name')
    e.css('propname')
    e.displayed
    e.enabled
    e.location
    e.locationInView
    e.name
    e.selected
    e.size
    e.tag
    e.text

    // Find child element
    e.find('#id')

    // Find all child elements
    e.find('#id')

    // Alerts
    se.alert.text


    // Manipulation
    // ------------

    // Driver

    // Keyboards
    se.keys()
    se.keyDown()
    se.keyUp()

    // Mouse
    se.mouse.click()
    se.mouse.doubleClick()
    se.mouse.down()
    se.mouse.moveTo(0,0
    se.mouse.moveBy(20,100)
    se.mouse.up()

    // Slim Jim (https://www.youtube.com/watch?v=KbneMYYI78Q)
    se.touch.tap()
    se.touch.down()
    se.touch.up()
    se.touch.move()

    // Execute JavaScript
    se.execute()
    se.executeAsync()

    // Take a Screenshot
    se.screenshot()

    // Element
    e.click()
    e.clear()
    e.keys()
    e.submit()

    // Alerts
    se.alert.accept()
    se.alert.dismiss()
    se.alert.focus()
    se.alert.keys()



    // Feng Shui
    // ---------

    // Get size of current window
    se.size

    // Set size of current window
    se.size = [200, 200]

    // Get position of current window
    se.position

    // Get position of current window
    se.position = 200,200

    // Maximize size of current window
    se.maximize()
    
    // (For mobile...)
    se.orientation
    se.orientation = LANDSCAPE
    se.orientation = PORTRAIT
    
    
    
    // Synchronisation
    // ---------------
    se.timeouts.implicitWait = 10000
    se.timeouts.pageLoad = 10000
    se.timeouts.asyncScript = 10000
    

