# DailyMotion
|home|calendar|
|----|----|
|<img src="https://github.com/LIMM036/my_news_webpage/blob/master/images/home.png">|<img src="https://github.com/LIMM036/my_news_webpage/blob/master/images/calendar.png">|
|news|contact|
|<img src="https://github.com/LIMM036/my_news_webpage/blob/master/images/news.png">|<img src="https://github.com/LIMM036/my_news_webpage/blob/master/images/contact.png">|

## 1. DailyMotion 이란?

- Daily + emotion 이라는 의미로 하루하루 경제, 주식 키워드에 관련된 뉴스의 sentiment 분석을 통해 하루하루의 경제의 sentiment를 달력에 뉴스와 함께 보여준다.

## 2. 구성

![](https://github.com/LIMM036/my_news_webpage/blob/master/images/configuration.png)

## 3. 서버
- Naver Cloud Flatform에서 서버를 대여하여 사용 [https://www.ncloud.com/product/compute/server]
- Micro server / ubuntu-18.04 / 2vCPU, 4GB Mem, 50GB Disk
- Mongodb를 사용하여 데이터 관리
- flask를 사용한 웹 서버


## 4. 데이터 수집 / 가공  
 - Naver에서 제공하는 api를 사용하여 데이터를 수집하고 가공한다.  
 - Scrapping하여 데이터를 수집한다.  
 - NaverCloudFunction을 사용하여 서버의 db에 원격 접속하여 수집한 데이터를 저장한다. [https://www.ncloud.com/product/compute/cloudFunctions]


  1. 뉴스 수집  
  - Naver news searching api 사용 [https://developers.naver.com/docs/serviceapi/search/news/news.md]
  - [ title, originallink, link, description, pubDate ] 수집

  2. 뉴스 본문 내용 수집  
  - 수집한 url을 통해 뉴스의 본문을 수집한다.
  - Summary를 하기 위한 본문 수집

  3. Summary  
  - Clova summary api를 사용하여 뉴스 본문을 summary 한다. [https://www.ncloud.com/product/aiService/clovaSummary]
  - sentiment 분석 api의 글자 수 제한이 1000자 이기 때문에 summary가 필요

  4. Sentiment 분석  
  - Clova sentiment api를 사용하여 summary한 내용으로 해당 기사의 sentiment를 분석한다. [https://www.ncloud.com/product/aiService/clovaSentiment]
