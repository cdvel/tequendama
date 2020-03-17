![CI](https://github.com/cdvel/tequendama/workflows/CI/badge.svg)

# Tequendama theme for Ghost

Ghost theme for personal blog

## Recompile theme

```
 sass -t compressed assets/css/styles.scss assets/css/styles.css
```


## Run process with forever

```

/opt/ghost$ sudo NODE_ENV=production forever start index.js

```



#Migration links

manual installation

https://nehalist.io/installing-ghost-1-0-without-ghost-cli/


How to migrate

https://docs.ghost.org/docs/migrating-to-ghost-1-0-0#section-4-copy-your-images


Updating your theme

https://gscan.ghost.org/





## How to update Ghost to latest version:

At `~/` follow these comands:

```
curl -LOk https://ghost.org/zip/ghost-latest.zip
unzip ghost-latest.zip -d ghost-temp
sudo rm -rf /opt/ghost/core
sudo rm  /opt/ghost/index.js 
sudo rm  /opt/ghost/*.json
sudo rm  /opt/ghost/*.md


sudo cp -R  ~/ghost-temp/core /opt/ghost/
sudo cp -R  ~/ghost-temp/index.js /opt/ghost/
sudo cp -R  ~/ghost-temp/package.json /opt/ghost/
sudo cp -R  ~/ghost-temp/npm-shrinkwrap.json /opt/ghost/
sudo cp -R  ~/ghost-temp/*.md /opt/ghost/
sudo chown -R ghost:ghost /opt/ghost

sudo npm install --production
sudo chown -R ghost:ghost /opt/ghost
```

Then restart service

```
sudo su
forever restartall
service nginx restart
exit


### troubleshoot


If `npm install` fails, try upgrading:

```
sudo npm install -g npm
```
