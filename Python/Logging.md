
```python
import logging
import sys

logger = logging.getLogger()
fileHandler = logging.FileHandler("logfile.log")  # 파일 핸들러를 생성하고 여기에 파일명을 할당.
streamHandler = logging.StreamHandler(sys.stdout) # 로그 메세지를 콘솔 창에 인쇄할 수 있는 스트림 핸들러 생성 
formatter = logging.Formatter('%(asctime)s - %(name)s - %(levelname)s - %(message)s')
streamHandler.setFormatter(formatter)    
fileHandler.setFormatter(formatter)
logger.addHandler(streamHandler)
logger.addHandler(fileHandler)
logger.error("This is the first error")

```

