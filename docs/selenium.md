# Selenium
De-facto browser based test automation tool, mainly used for functional testing
[https://www.seleniumhq.org/](https://www.seleniumhq.org/)

## Selenium with python
- Documentation
[https://selenium-python.readthedocs.io/](https://selenium-python.readthedocs.io/)
- Install
```
pip install selenium
```
- Driver
From the documentation [https://selenium-python.readthedocs.io/installation.html#drivers](https://selenium-python.readthedocs.io/installation.html#drivers)
[http://chromedriver.chromium.org/getting-started](http://chromedriver.chromium.org/getting-started)
```
Selenium requires a driver to interface with the chosen browser. Firefox, for example, requires geckodriver, which needs to be installed before the below examples can be run. Make sure it’s in your PATH, e. g., place it in /usr/bin or /usr/local/bin.
```
- Get appropriate version of chrome driver matching with chrome version from [http://chromedriver.storage.googleapis.com/index.html](http://chromedriver.storage.googleapis.com/index.html)
- Unzip the chromedriver.zip
- Move the file to /usr/bin directory sudo mv chromedriver /usr/bin
- Goto /usr/bin directory cd /usr/bin
-  To mark it executable
```
sudo chmod a+x chromedriver
```


- A sample script to extract latest news on India in Google Search
```
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
import json

driver = webdriver.Chrome()


item_list_url = "https://www.google.com"
driver.get(item_list_url)
searchbox = driver.find_element_by_name('q')
search_str = 'india + news'
searchbox.send_keys(search_str)
searchbox.send_keys(u'\ue007')

news_tab = driver.find_element_by_link_text('News').click()
res_list = driver.find_elements_by_class_name('lLrAF')
for res in res_list:
    
    single_res = {}
    single_res['link'] = res.get_attribute('href')
    single_res['text'] = res.text
    print(single_res)

```

- Run selenium as headless mode, useful to run in server setup, where browser interface not present
```
from selenium.webdriver import Firefox
from selenium.webdriver.firefox.options import Options
opts = Options()
opts.set_headless()
assert opts.headless  # Operating in headless mode
browser = Firefox(options=opts)
browser.get('http://yule.sohu.com/')
results= browser.find_element_by_class_name('news-2')
print_results=results.get_attribute("innerHTML")
print(print_results)
browser.quit()
```

## Common features
- Timeout
driver.set_page_load_timeout() - Sets the amount of time to wait for a page load to complete before throwing an error. If the timeout is negative, page loads can be indefinite.

driver.implicitly_wait() - Specifies the amount of time the driver should wait when searching for an element if it is not immediately present.

driver.set_script_timeout() - Sets the amount of time to wait for an asynchronous script to finish execution before throwing an error. If the timeout is negative, then the script will be allowed to run indefinitely.

In python, you can use ``` sleep() `` to set wait time.
- Maximize window
```
driver.maximize_window()
```
- Run custom js code
Example code to scroll down to bottom of page
```
webdriver.execute_script("window.scrollTo(0,document.body.scrollHeight);")
```
