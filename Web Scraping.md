Websites usually reject simple https requests like 
`requests.get("address")` - to avoid bots
We have to access such sites through a browser.
![[Pasted image 20260416145127.png|390]]
![[Pasted image 20260416150312.png|388]]
`soup = BeautifulSoup(webpage,'lxml')
- lxml parser 
`print(soup.prettify())
- formats the html file
