# bithumb-api
Python Wrapper for Bithumb API

## Installation
```sh
pip3 install pybithumb
```
### 로컬에 설치하기
로컬에 설치하기 위해 요구되는 모듈 의존성은 다음과 같다. (설치 시, ModuleNotFoundError를 발생하는 모듈들 목록임)

```sh
sudo apt install python3-pip
pip3 install setuptools
python3 setup.py build
sudo python3 setup.py install
```


## Import
```python
from pybithumb import Bithumb
```

## Public API
####  암호화폐 목록
빗썸이 지원하는 암호화폐 목록을 얻어온다.
```python
print(Bithumb.get_tickers())
```

#### 최근 체결가격
```python
for coin in Bithumb.get_tickers():
    print(coin, Bithumb.get_current_price(coin))
```

#### 시장 현황 상세정보
```python
for coin in  Bithumb.get_tickers():
    print(coin, Bithumb.get_market_detail(coin))
```

#### 매수/매도 호가
```python
for coin in  Bithumb.get_tickers():
    print(coin, Bithumb.get_orderbook(coin))
```  


## Private API
#### 로그인
connectkey와 secretkey를 사용해서 로그인한다. 
두 key를 생성하는 방법은 [링크](http://sharebook.kr/x/ZQov)를 참조한다. 
```python
bithumb = Bithumb("conkey", "seckey")
```

#### 수수료 조회
```python
print(bithumb.get_trading_fee())
```

#### 잔고 조회
```python
for coin in Bithumb.get_tickers():
    print(coin, bithumb.get_balance(coin))
```

#### 매수/매도 주문
비트코인을 1100만원에 1개 매수/매도한다. 
```python
desc = bithumb.buy_limit_order("BTC", 11000000, 1)
desc = bithumb.sell_limit_order("BTC", 11000000, 1)
```

#### 매수/매도 잔량 확인
```python
quanity = bithumb.get_outstanding_order(desc)
```

#### 매수/매도 주문 취소
```python
status = bithumb.cancel_order(desc)
```

