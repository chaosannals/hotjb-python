# hotjb-python

```python
# 使用客户端
from hotjb.client import HotJBClient

async def main(loop):
    client = HotJBClient(host='127.0.0.1', port=30000)
    r = await client.tokenize('中文分词库')
    print(r)

if __name__ == '__main__':
    loop = asyncio.get_event_loop()
    loop.run_until_complete(main(loop))
```

```python
# 使用压力测试
from loguru import logger
from hotjb.pressuror import HotJBPressuror

async def main(loop):
    '''
    '''

    logger.remove()
    logger.add(
        'logs/{time}.log',
        level='INFO',
        rotation='00:00',
        retention='7 days',
    )
    pressuror = HotJBPressuror(logger)
    await pressuror.pressure()

if __name__ == '__main__':
    loop = asyncio.get_event_loop()
    loop.run_until_complete(main(loop))
```
