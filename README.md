#Optimus Template
Optimus Template is the native framework for Optimus, designed to help you
to get started with your tests in the swiftest time possible.

####First things first
Before you get your hands on Optimus Template, please make sure your system meets the desired
[prerequisites](Prerequisites.md)

##Features
Now that you have reached till here, we assume that your system is ready to host Optimus successfully. Before we jump straight into writing your first test with Optimus Template, let us understand the prowess of Optimus.
With Optimus, you will be able to write tests capable of running in below modes without ever having to worry about managing servers or device setup.

    * Distributed Mode
    * Parallel Mode

If this might sound obvious like any other framework, with Optimus you will be able to test

    * Single App
    * Inter App
    * Mobile Web

## Test Feed <a id="testFeed"></a>
Optimus is extremely powerful yet fun to work with
once you understand what to feed your tests, for a seamless automation experience.
Test Feed, typically a JSON format, will let you control all your tests from a single source of truth,
giving you complete control of your tests execution. Any Test Feed will contain following sections

    * Common Attributes
    * Appium Server Capabilities
    * Android Only Capabilities
    * Device State

#### Common Attributes
These attributes are set across all tests running on a common test feed.

   <pre>
        <b>Belongs To</b>: Assigns the test to a particular application.
        <b>Runs On</b>: Assigns the test to user specific device. You can choose to run your tests either on device or emulator.
        <b>Application Directory</b>: Specifies the folder name where the application under test is placed.
       </pre>

#####Example

![](docs/CommonAttibutes.png)



#### Appium Server Capabilities 
Optimus by default supports all the capabilities that Appium provides, which you can refer from [here](https://github.com/appium/appium/blob/master/docs/en/writing-running-appium/caps.md).
Since Optimus inherently possesses immense intelligence to handle all capabilities by default without troubling you much,
all it needs are a couple of capabilities.


  <pre>
   <b>App</b>: Name of application to test. Optimus will look for this app under the “appDir” folder specified as part of common attributes.
   <b>Platform Name</b>: Specifies the platform to run the application on.
   </pre>

#####Example 
![](docs/AppiumServerCapabilities.png)

These capabilities will be sufficient enough to run most of the tests if not all.
Under which circumstances you may choose to provide additional
[Appium Server Capabilities](https://github.com/appium/appium/blob/master/docs/en/writing-running-appium/caps.md).

#### Android only Capabilities 
Optimus supports all android related capabilities as specified [here](https://github.com/appium/appium/blob/master/docs/en/writing-running-appium/caps.md).
Optimus does not enforce any of these capabilities to be set for running your tests.
However you are free to provide as many capabilities as you may need.

#### Device State
Optimus while being extremely faithful to Appium in terms of capabilities,
it does provide few handy capabilities out of box which resolves many dire issues of mobile automation.

    * Clear Notification
    * Clear ADB logs
    * Grant All Permissions
    * Capture Video

All these capabilities are boolean flags which by themselves are self-descriptive.

With a fair idea of Optimus, now you are all set for your first test.

##Getting started with Optimus Template
You can either fork Optimus Template repository or download the bundle from [here](//set link here).

If you have forked Optimus Template, you can clone it onto your machine using

```bash
git clone <Enter git clone link here>
```

Use your favourite IDE for building the project, however we love
IntelliJ though.

![](ImportProject.gif)

Optimus Template is inherently a Page Object Model.
If you are new to this design pattern, we strongly recommend you to read about [POM](http://martinfowler.com/bliki/PageObject.html),
before you continue reading further.

#### Template Structure
If your download flavour is of type BDD, you will find that Optimus Template is
structured in the lines of Cucumber with below structure

``` java
optimustemplate/
+-- build.gradle
+-- app //Store Application Under Test for Android or Ios platforms.
    +--AUT.apk
    +--AUT.app
+-- src/test
    +-- java
    ¦   +-- pages 
    ¦        +-- BasePage.java 
    ¦   +-- steps 
    ¦       +-- BaseSteps.java
    ¦       +-- StartingSteps.java
    ¦   +-- utils 
            +-- OptimusImpl.java
    +-- resources
    ¦   +-- features
    ¦   ¦  +-- interApp.feature
    ¦   ¦  +-- singleApp.feature
    +-- interApp.json
    +-- singleApp.json
    +-- tagFile.properties
```

The template comes with few pre-defined classes. You can harness
the power of Optimus through them.

   <pre>
    <b>BasePage.java</b>: Any page you create can extend BasePage to perform most of the
    actions required to test your functionality, without having to reinvent the wheel.
    <b>BaseSteps.java</b>: Any Step definition can extend BaseSteps.
    <b>StartingSteps.java</b>: For Optimus Template use only.
   </pre>

###Your First Test
Writing tests in Optimus is no different than the tests you write everyday,
except that it does most of the heavy lifting, helping you to focus entirely on the test, 
thus the philosophy of Optimus

> Focus On Functionality

#### Building Test Feed
If there is anything at your disposal to tame the mighty Optimus,
then its your [TestFeed](#testFeed). 