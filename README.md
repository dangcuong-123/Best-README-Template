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
    <li><a href="#usage">Usage</a></li>
     <ul>
        <li><a href="#tag-検索">Tag 検索</a></li>
        <li><a href="#tag-まとめて検索">Tag まとめて検索</a></li>
      </ul>
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

![pionero_okg drawio](https://user-images.githubusercontent.com/48614539/179146005-fee65eb8-24e6-4fed-8ca9-9e0516a9c199.png)

<p align="right">(<a href="#top">back to top</a>)</p>


<!-- USAGE EXAMPLES -->
## Usage
### Tag 検索
The word target (検索語) must be in sequence (用例)

### Tag まとめて検索

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
