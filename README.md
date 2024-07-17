# BertForSequenceClassfication 모델 훈련을 위한 데이터 크롤링 모듈

- Category.ipynb - 네이버 쇼핑에 등록되어 있는 상품 카테고리를 기반으로 데이터 수집
- Query.ipynb - 검색하고 싶은 상품의 이름, 카테고리 등을 기반으로 데이터 수집

**requests 라이브러리를 통한 HTML 로드 방법**

1. 네이버 쇼핑 (웹사이트) 에서 요소를 클릭하거나 검색. (예시에서는 한 페이지 당 80개씩 상품을 노출시키는 버튼을 클릭)
2. 개발자 도구 상에 네트워크 (Fetch/XHR) 에 URL 요청이 생성되는 것을 확인할 수 있음.
3. 오른쪽 클릭 후 cURL 복사.

<img width="1468" alt="스크린샷 2024-07-17 오후 1 04 47" src="https://github.com/user-attachments/assets/93b549cb-80f2-419a-ace8-2593dc6051a0">
<br/>

<br/>

4. cURL to Python 을 지원하는 사이트가 존재함. (https://curlconverter.com/)
5. 파이썬 코드가 생성되고 이를 잘 가공. (쿠키의 유효기간이 있을 수 있기 때문에 쿠키 부분을 주기적으로 변경할 필요가 있음.)

<img width="1383" alt="스크린샷 2024-07-17 오후 1 08 42" src="https://github.com/user-attachments/assets/e3665053-4bd8-45be-92dc-6a5e5d535a0c">
<br/>

<br/>

- 생성된 코드 예시

```python
import requests

cookies = {
    '쿠키'
}

headers = {
    '헤더'
}

params = {
    'adQuery': '돼지고기',
    'eq': '',
    'iq': '',
    'origQuery': '돼지고기',
    'pagingIndex': '1',
    'pagingSize': '80',
    'productSet': 'total',
    'query': '돼지고기',
    'sort': 'rel',
    'viewType': 'list',
    'xq': '',
}

response = requests.get('https://search.shopping.naver.com/api/search/all', params=params, cookies=cookies, headers=headers)
```
