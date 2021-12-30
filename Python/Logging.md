
```python
import logging
import sys

logger = logging.getLogger()
fileHandler = logging.FileHandler("logfile.log")  # 파일 핸들러를 생성하고 여기에 파일명을 할당.

formatter = logging.Formatter('%(asctime)s - %(name)s - %(levelname)s - %(message)s')


fileHandler.setFormatter(formatter)
logger.addHandler(streamHandler)
logger.addHandler(fileHandler)
logger.error("This is the first error")

```

