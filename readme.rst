---------------
Task to resolve
---------------

For the page  https://www.imdb.com/chart/top?ref_=nv_mv_250_6, please do the following:

#. List all the test cases you consider necessary ordered by priority starting from the must have ones (at least 10)
#. What tests you would add to the compulsory pre-release test suite?
#. Describe test cases #4 and #8 in details taking into consideration that these tests will be performed by junior testers.
#. Cover at least 2 cases (#4, #8, maybe some others) with automated tests. Make sure that instructions provided with your code allow it to be run in Linux environment.

--------
workflow
--------

Let's start by defining the type of testing. For a web-page, it would be suitable to verify its functionality. We can do it with a help of selenium toolkit. Selenium is suited for functional testing, but for other kinds of testing, like load testing or performance testing, another approaches needed. Other testing types can be performed with toolkits:

- For load and performance testing we can use Jmeter <http://jmeter.apache.org/>`_

In the second step will create a test plan according to page functionality and test design patterns. As next, we will separate test cases according to severity: **critical**, **major** and **minor**, but they can be expanded with other **blocker**, **immediate**, etc, according to project rules.
**Test suite preconditions:**

#. User is not authenticated at IMDB site.

**Critical:**

#. Page should looks fine and all active UI elements should be clickable in popular browsers.
#. Clicking to movie title link leads to movie details page.
#. Clicking to movie icon leads to movie details page.
#. Clicking to movie star "your rating" do nothing until logged in.
#. Clicking to movie button "add to watchlist" leads to login page.
#. Share button is clickable.
#. In dropdown menu share in social networks buttons lead to social network pages.

**Major:**

#. Sort type "Ranking" is correct.
#. Sort type "IMDb Rating" is correct.
#. Sort type "Release Date" is correct.
#. Sort type "Number of Ratings" is correct.
#. Sort type "Your Rating" is correct.
#. In dropdown menu email item has correct link.
#. Top list includes exactly 250 items.

**Minor:**

#. Reverse sort order link works correct.
#. Top list numeration has correct order by default.
#. Copy site address to clipboard in dropdown menu has correct link.

----------------------------------------

Talking about cases in a pre-release test suite. Actually, all cases should be executed during acceptance testing. But in case of strict time limitation, minor severity test cases can be postponed, and further test suite restriction depends on release specific.

----------------------------------------

Description of some test cases, as they should be at test-plan management tool.

Scenario: **Clicking to movie title link leads to movie details page**

**Setup:**

#. Page https://www.imdb.com/chart/top?ref_=nv_mv_250_6 is opened in browser.

**Steps:**

#. Click title movie of first item in movies list
    - Page with detailed info about exactly that movie is opened.

----------------------------------------

Scenario: **Share button is clickable**

**Setup:**

#. Page https://www.imdb.com/chart/top?ref_=nv_mv_250_6 is opened in browser.

**Steps:**

#. Click button "Share".
    - Dropdown menu with social networks buttons to share is present.

----------------------------------------

Scenario: **In dropdown menu social buttons lead to social networks pages**

**Setup:**

#. Page https://www.imdb.com/chart/top?ref_=nv_mv_250_6 is opened in browser.

**Steps:**

#. Click on "Share" button.
    - Dropdown menu with social networks buttons to share is present.
#. Click on "Facebook" button.
    - Dropdown menu is closed.
    - Facebook page to share IMDB page is opened in new window.
#. Click on "Share" button.
    - Dropdown menu with social networks buttons to share is present.
#. Click on "Twitter" button.
    - Dropdown menu is closed.
    - Twitter page to tweet IMDB page is opened in new window.

----------------------------------------

Scenario: **Copy site address to clipboard in dropdown menu**

**Setup:**

#. Page https://www.imdb.com/chart/top?ref_=nv_mv_250_6 is opened in browser.

**Steps:**

#. Click button "Share".
    - Dropdown menu with social network buttons to share is present.
#. Click item "Copy"
    - Dropdown menu is closed.
#. Open text editor and paste link by pushing Ctrl+V
    - link "http://www.imdb.com/chart/top" is pasted.
