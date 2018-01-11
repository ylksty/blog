## root/javascript/[other](../README.md)/npm
### npm config get
### nrm
~~~
npm install -g nrm
nrm use
~~~

### npm i 错误
* ChromeDriver installation failed Error with http(s) request: Error: read ETIMEDOUT
~~~
npm install chromedriver --chromedriver_cdnurl=http://cdn.npm.taobao.org/dist/chromedriver
~~~

### npm install --no-optional

### phantomjs
~~~
PHANTOMJS_CDNURL=https://npm.taobao.org/dist/phantomjs npm install phantomjs --registry=https://registry.npm.taobao.org --no-proxy
~~~