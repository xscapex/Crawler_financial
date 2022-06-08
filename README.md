# Crawler_financial
===

![image](https://github.com/xscapex/Crawler_financial/blob/main/flow.PNG)

Mysql Docker
---

docker volume create mysql

docker-compose -f mysql.yml up

Crawler
---
python twse_crawler.py 2022-06-05 2022-06-06

Create API
---
python -m uvicorn main:app --reload --port 8888


User
---

import requests
import pandas as pd

payload = dict(
    stock_id="2330",
    start_date="2022-06-05",
    end_date="2022-06-05",
)

res = requests.get("http://127.0.0.1:8888/taiwan_stock_price", params=payload)

df = pd.DataFrame(res.json()["data"])

df
