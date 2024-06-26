# Developer tools

## Arguments 
The program arguments of the chrome-process are listed in the following cheatsheet: [List of Chromium Command Line Switches](https://peter.sh/experiments/chromium-command-line-switches/#condition-1)

The arguments can be added as a part of a shortcut target on Windows. 
> "C:\Program Files\Google\Chrome\Application\chrome.exe" --remote-debugging-port=9222`
## HSTS - Fix localhost HTTP -> HTTPS redirection 
The problem is related to [[HSTS]] and instructs the client automatically switch non-secure `http://` requests to `https://`

Navigate to `chrome://net-internals/#hsts` using a chromium based browser, and use the page to:
- Delete domain security policies
- Put in `localhost` (or whatever domain)
- Press the **Delete** button 

https://weblog.west-wind.com/posts/2022/Oct/24/Fix-automatic-rerouting-of-http-to-https-on-localhost-in-Web-Browsers