# 類似語検索システム
<div id="top"></div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#environment">Environment</a></li>
        <li><a href="#installation">Installation</a></li>
        <li><a href="#install-with-docker-option">Install with docker [Option] </a></li>
      </ul>
    </li>
    <li><a href="#pipeline-modeling">Pipeline modeling</a></li>
    <li>
      <a href="#usage">Usage</a>
        <ul>
          <li><a href="#tab-検索">Tab 検索</a></li>
          <li><a href="#tab-まとめて検索">Tab まとめて検索</a></li>
        </ul>
    </li>
    <li><a href="#references">References</a></li>
  </ol>
</details>


<!-- GETTING STARTED -->
## Getting Started

### Environment

`python 3.9`

`docker` [Option]

### Installation

1. Clone the this repo
2. Install packages
```sh
pip install -r requirements.txt
   ```
3. Run app 
```sh
python3 app.py
   ```

### Install with docker [Option] 

1. Clone the this repo
2. Build docker 
```sh
sudo docker image build -t app .
   ```
3. Run docker 
```sh
sudo docker run -p 5000:5000 -d app
   ```


<p align="right">(<a href="#top">back to top</a>)</p>


## Pipeline modeling 

![pionero_okg drawio (1)](https://user-images.githubusercontent.com/48614539/179896314-d48005ce-c23a-44eb-965e-66af3b6c4e8b.png)


Model datamuse api may stop serving in the future or if the number of requests is more than 100000 requests/1 day, then fasttext can be used.

<p align="right">(<a href="#top">back to top</a>)</p>

## Deloy server 
Step 1 - Setup server and download necessary libraries
- Setting server
```ubuntu 20.04```
```python 3.8```
- Open port 80 in server
- Ssh to server 
- ```sudo apt install git```
- git clone this repo
- ```sudo apt install python3-pip python3-dev build-essential libssl-dev libffi-dev python3-setuptools```

Step 2 - Creating a Python Virtual Environment
- ```cd ~/web/```
- ```sudo apt install python3-venv```
-```python3.8 -m venv myprojectenv```
- ```source myprojectenv/bin/activate```
- ```pip install -r requirements.txt```
- ```pip install wheel```
- ```pip install gunicorn```
- ```deactivate```

Step 3 — Configuring Gunicorn
- ```cd ~/```
- ```sudo nano /etc/systemd/system/myproject.service```

copy below code and save to file 

```
[Unit]
Description=Gunicorn instance to serve myproject
After=network.target

[Service]
User=ubuntu
Group=www-data
WorkingDirectory=/home/ubuntu/web
Environment="PATH=/home/ubuntu/web/myprojectenv/bin"
ExecStart=/home/ubuntu/web/myprojectenv/bin/gunicorn --workers 3 --bind unix:myproject.sock -m 007 --timeout 600 wsgi:app

[Install]
WantedBy=multi-user.target
```
- ```sudo systemctl start myproject```
- ```sudo systemctl enable myproject```
- Check the status: 
```sudo systemctl status myproject```

Step 4 — Configuring Nginx to Proxy Requests
- ```sudo nano /etc/nginx/sites-available/myproject```
- copy below code and save to file

```
server {
    listen 80;
    server_name 219.94.240.172 www.219.94.240.172;

    location / {
        include proxy_params;
        proxy_pass http://unix:/home/ubuntu/web/myproject.sock;
    }
}
```

- ```sudo ln -s /etc/nginx/sites-available/myproject /etc/nginx/sites-enabled```
- ```sudo nginx -t```
- ```sudo systemctl restart nginx```
- ```sudo ufw allow 'Nginx Full'```

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- USAGE EXAMPLES -->
## Usage
### Tab 検索
Enter one word in the sentence

### Tab まとめて検索

Input example

1. example.csv
```
context,word
The teacher gave some suggestions on what could come out for the examination,suggestions
I love you, love
```

2. example.json
```
{
    "context":{
        "0":"The teacher gave some suggestions on what could come out for the examination",
        "1":"I love you"
    },
    "word":{
        "0":"suggestions",
        "1":"love"
    }
}
```

3. example.xlsx
![image](https://user-images.githubusercontent.com/48614539/179150089-9e3d8599-3285-4972-85e9-1b4a5b1e706d.png)

<p align="right">(<a href="#top">back to top</a>)</p>

## References

* [Gensim](https://radimrehurek.com/gensim/)
* [Datamuse api](https://www.datamuse.com/api/)
* [Fitbert](https://github.com/writerai/fitbert)
* [Details on how to deploy](https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-gunicorn-and-nginx-on-ubuntu-18-04#step-2-creating-a-python-virtual-environment)
