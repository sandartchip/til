

# Detectron2

- Facebook AI Research에서 개발한 Pytorch 기반의 Object Detection, Segmentation 라이브러리


### Run a pre-trained detectron2 model

- **COCO 형식 이미지 준비**
- Config와 DefaultPredictor 생성, Inference 하기
- 결과 시각화




### Standard Dataset Dicts
- Dict는 한 이미지에 대한 정보를 담고 있음
- Object Detection의 다음 필드를 필요로 한다.

```
file_name / height / width / image_id / annotations

```

- annotation은 다음과 같은 key를 갖는다.

|제목|내용|설명|
|-------|---|---|
|bbox|list[float], required|bounding box 좌표값 4개(숫자)|
|bbox_mode|int, required|bbox 포맷|
|category_id|int, required|[0, num_categories-1] 사이의 숫자|
|segmentation|list[list[float]] or dict| list[list[float]] - 폴리곤을, dict-RLE 포맷|
|keypoints|list[float]|[x1, y1, v1, ...xn, yn, vn] 이 때 v은 키포인트가 보이는지 여부 정보를 담는다|


### Metadata for Datasets
- 각각의 데이터셋은 MetadataCatalog.get
  


https://comlini8-8.tistory.com/87
