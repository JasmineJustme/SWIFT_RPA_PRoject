# Code in details  

## 一、以爬取公司信息为例
### 1. 进行初始化并打开网址  
```python
# 进行初始化
r.init()
# 打开网址
link_url = r'qcc.com'
r.url(link_url)
```
### 2. 输入目标公司名称并搜索
该操作有两种方式来实现
* 通过单击搜索键进行搜索确认
```python
r.type('#searchKey','深圳前海微众银行股份有限公司')
r.click('body > div > div.app-home > section.nindex-search > div > div > div > div.app-search-input.big.full > div > div > span > button')
```
* 通过按下回车enter进行搜索确认
```python
r.type('#searchKey','深圳前海微众银行股份有限公司[enter]')
```
### 3. 进入公司主页
值得注意的是，搜素结果页并未打开新的标签页。然而在搜索结果页进入目标公司主页时将要打开新的标签页，因此还需要一步额外的操作才能使程序定位到新的目标页。
```python
r.click('body > div > div.app-search.layout-content > div.container.m-t > div.adsearch-list.search-sticky-container > div > div.msearch > div > table > tr:nth-child(1) > td:nth-child(3) > div > span > span.copy-title > a > span')
r.popup(r'https://www.qcc.com/firm/40283ac0a7052f9bc6e9dae9cb0fc9be.html')
```
### 4. 获取股东数量并获取股东信息
找到每个股东信息的共性，例如第一个股东名称的selector为#partner > div > div.app-tree-table > table > tr:nth-child(2) > td.left.first-td.has-son-td > div.td-coy.partner-app-tdcoy > span.cont > span > span > a
第二个的selector是第一个中的tr:nth-child(2)变为tr:nth-child(3)，所以将(数字)部分删掉就是所有股东名字的共性（还需要注意的是1为标签行，循环时应从2开始）
```python
stockholder_num_array = []
stockholder_num = r.count('#partner > div > div.app-tree-table > table > tr:nth-child(2) > td.left.first-td.has-son-td > div.td-coy.partner-app-tdcoy > span.cont > span > span > a') - 1
for i in range(2,stockholder_num + 1):
  stockholder_num_array.append(r.read(f'#partner > div > div.app-tree-table > table > tr:nth-child({i}) > td.left.first-td.has-son-td > div.td-coy.partner-app-tdcoy > span.cont > span > span > a'))
```
### 4. 检测页面是否加载完成
有时重复操作变多了之后会触发反爬机制，此时程序无法按照正常流程进行导致程序的中断，使用以下方式维持程序的稳定
* 使用try except语句，并搜集报错信息，方便后续在对该信息进行排错以及搜集
* 可能出现验证或其他的操作后使用等待
```python
def wait_till_done(url='', selector=''):
  state = r.dom('''return document.readyState=="complete"''')
  if state == "true":
    return True
  else:
    return False
```
