## 利用dateime查找当天数据
``````
import datetime
from dateutil import parser

def getTimeDomain( hours = 1):
    nowdate = datetime.datetime.utcnow()
    now_time = nowdate.strftime('%Y-%m-%d')
    tomorrow_time = (nowdate + datetime.timedelta( hours = 24 * hours )).strftime('%Y-%m-%d')
    startStr = now_time + 'T00:00:01Z'
    endStr = tomorrow_time + 'T00:00:01Z'
    starttime = parser.parse(startStr)
    endtime = parser.parse(endStr)
    days = [ starttime, endtime ]
    return days
    
# mongo 查询部分
days = getTimeDomain()
query = {
    "uid" : uid,
    "created_at":{
      "$gte":  days[0],
      "$lt" : days[1],
    }
}
``````

## pymongo 使用db.collection.count() 过慢问题
``````
# Python3.7 安装 pymongo 模块
# 无参数情况下
db_count = cursor.estimated_document_count()
# 有参数情况下
db_count = cursor.count_documents({'status': 0})
``````
### python3 下载并保存 -> requirements.txt
`````
pip install html2text && pip freeze | grep html2text >> requirements.txt
`````

## python3异步函数调用
``````
import asyncio

def _init_():
    print("_init_")
    asyncio.create_task( init())
    
async init():
    print("async init")
    
_init_()
``````
### python3 dict排序
``````
 sort_data = sorted(words_data.items(), key = lambda kv:(kv[1], kv[0]),reverse=True) # 降序
  sort_data = sorted(words_data.items(), key = lambda kv:(kv[1], kv[0])) # 升序
 
``````
### 字符串从后截取
```````
str = '12131312313'
str = str[:-10] # 从后截取10个
```````

### pymongo 查询索引/ 设置索引
```````
// 获取索引
coll_names =  await db_fiction.list_collection_names()
print(coll_names)
for coll_name in coll_names:
    print("~~~~~~~~~~~~~~~")
    # print(coll_name)
    # one = await db_fiction[coll_name].find_one()
    coll = db_fiction[coll_name]
    # print(coll)
    index_infomation = await coll.index_information()
    print(index_infomation)
// 设置索引
await db_fiction.coll_names.create_index([("status", 1),("xid", 1)],unique = False, background = True)
```````

pip install html2text && pip freeze | grep html2text >> requirements.txt索引
pip install html2text && pip freeze | grep html2text >> requirements.txt

## 解决 python3.6 安装python-devel error
``````
yum install python36-devel
``````

## python使用环境变量
```````
# 设置
vi ~/.bash_profile
# 添加
export TEST="test"
# 重启
source ~/.bash_profile

# python 中获取
TEST = os.getenv('TEST')

```````
