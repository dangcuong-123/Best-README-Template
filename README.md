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
    <li><a href="#usage">Usage</a>
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

![pionero_okg drawio](https://user-images.githubusercontent.com/48614539/179895654-2ec69dd8-0059-43ff-9baf-b72401dce033.png)


<p align="right">(<a href="#top">back to top</a>)</p>


<!-- USAGE EXAMPLES -->
## Usage
### Tab 検索
The word target (検索語) must be in sequence (用例)

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

