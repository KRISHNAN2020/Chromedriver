
package org.example;

import org.junit.platform.suite.api.ConfigurationParameter;
import org.junit.platform.suite.api.IncludeEngines;
import org.junit.platform.suite.api.SelectPackages;
import org.junit.platform.suite.api.Suite;

import static io.cucumber.junit.platform.engine.Constants.PLUGIN_PROPERTY_NAME;

@Suite
@IncludeEngines("cucumber")
@SelectPackages("org.example")
@ConfigurationParameter(key = PLUGIN_PROPERTY_NAME, value = "pretty")
public class RunCucumberTest {
}





Feature: An example

  Scenario: The example
    Given an example scenario
    When all step definitions are implemented
    Then the scenario passes


  Scenario: Launch a webpage and verify its title
    Given I launch the Chrome browser
    When I navigate to "https://www.flipkart.com/"
    Then the page title should be "Online Shopping Site for Mobiles, Electronics, Furniture, Grocery, Lifestyle, Books & More. Best Offers!"



package org.example;

import io.cucumber.java.en.*;
import io.github.bonigarcia.wdm.WebDriverManager;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

import static org.junit.jupiter.api.Assertions.*;

public class StepDefinitions {
    private WebDriver driver;
    @Given("an example scenario")
    public void anExampleScenario() {
    }

    @When("all step definitions are implemented")
    public void allStepDefinitionsAreImplemented() {
    }

    @Then("the scenario passes")
    public void theScenarioPasses() {
    }


    @Given("I launch the Chrome browser")
    public void i_launch_the_chrome_browser() {
        // Set up ChromeDriver using WebDriverManager
        WebDriverManager.chromedriver().setup();
        driver = new ChromeDriver();
        driver.manage().window().maximize(); // Optional: Maximize the browser window
    }

    @When("I navigate to {string}")
    public void i_navigate_to(String url) {
        driver.get(url);

    }

    @Then("the page title should be {string}")
    public void the_page_title_should_be(String expectedTitle) {
        String actualTitle = driver.getTitle();
        assertEquals(expectedTitle, actualTitle, "Page title does not match!");
        driver.quit(); // Close the browser after the test
    }

}
