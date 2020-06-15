# Note of Blog Build by Hexo 

Content

- Make it work quickly
- Basic Configuration
- Create New Post
- Deploy to server
- Theme
- Make it faster 
- Others
  - Categories

### Main

### Make it work quickly

**Install Requirements**

- Node.js
- Git

Installation in windows. 

download package file.

Installation in Linux. 

Ubuntu, Debian

```
$ sudo apt-get install -y git-core
$ wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.34.0/install.sh | bash
$ nvm install stable
```

Fedora, Red Hat, CentOS

```
$ sudo yum install git-core
```



**Install Hexo**

```shell
$ npm install -g hexo-cli
```

**Init Hexo**

```
$ hexo init [folder]
```

**Run Hexo Server**

```
$ hexo server
```

Starts a local server. By default, this is at `http://localhost:4000/`.



### Basic Configuration

site sertting in /_config.yml

#### Site

| Setting       | Description                     |
| :------------ | :------------------------------ |
| `title`       | The title of your website       |
| `subtitle`    | The subtitle of your website    |
| `description` | The description of your website |
| `author`      | Your name                       |

Other using default settings.



### New, Generate, Publish

```
$ hexo new [layout] <title>
$ hexo generate
//$ hexo publish [layout] <filename>
```



### Deploy to Server

Deployment using Netlify. git push to GitHub, auto deploy on Netlify server.

Set Domain

- redirect to Netlify
- Using NetlifyDNS.

### Theme

**Install**

Execute the following command and modify `theme` in `_config.yml` to `phase`.

```
$ cd themes
$ git clone git://github.com/tommy351/hexo-theme-phase.git phase
```

**Update**

Execute the following command to update Light.

```
cd themes/phase
git pull
```

More themes

- git://github.com/iissnan/hexo-theme-next.git
- git://github.com/tommy351/hexo-theme-phase.git
- git://github.com/litten/hexo-theme-yilia.git
- git://github.com/viosey/hexo-theme-material.git
- git://github.com/tufu9441/maupassant-hexo.git

### Make It Faster



### Others

#### Categories



#### Theme





### References

[hexo docs](https://hexo.io/docs/)