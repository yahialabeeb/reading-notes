# Web Scraping
* **Web scraping is a technique to automatically access and extract large amounts of information from a website, which can save a huge amount of time and effort.**
* **Web scraping is a task that has to be performed responsibly so that it does not have a detrimental effect on the sites being scraped.**
## Important notes about web scraping:
1. **Read through the website’s Terms and Conditions to understand how you can legally use the data**
2. **Make sure you are not downloading data at too rapid a rate because this may break the website.**

## Inspecting the Website
* finding the relevant pieces of code that contains our data.
  * “Inspect” allows you to see the raw code behind the site.
  * arrow makes the code for that particular item will be highlighted in the console.
  * .txt files are inside the <a> tag

## Python Code
### importing the following libraries.
```python 

import requests
import urllib.request
import time
from bs4 import BeautifulSoup
```
### set the url to the website and access the site.
```python
url = 'http://web.mta.info/developers/turnstile.html'
response = requests.get(url)
```

### parse the html with BeautifulSoup 
```python 
soup = BeautifulSoup(response.text, “html.parser”)
```
## findAll to locate all of our <a> tags.
```
soup.findAll('a')
```

extract the actual link that we want.
```pyhton 
one_a_tag = soup.findAll(‘a’)[38]
link = one_a_tag[‘href’]
```
### The full url to download the data is actually:
```python
download_url = 'http://web.mta.info/developers/'+ link
urllib.request.urlretrieve(download_url,'./'+link[link.find('/turnstile_')+1:])
```

putting thimer helps us avoid getting flagged as a spammer.
```
time.sleep(1)
``` 