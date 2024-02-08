
### Example

![image](https://github.com/sandartchip/TIL/assets/15938354/3a063708-8542-4b3f-8df1-9395805cbd09)

- COCO Dataset의 annotation 파일은 기본 구조에 파일 형식을 더한 형태로 되어 있음. 

- **기본 구조**에 **분야별 형식**을 더한 형태로 구성되어 있음.
- object detection, segmentation, key point detection 등 분야에 따라 정해진 형식을 사용함.

- segmentation의 경우, segmentation 정보와 bbox, category_id, id, bbox, image_id, iscrowd, area가 필요 함.

- segmentation의 경우, 값이 list라면 폴리곤(각 connected component 별로 생성됨)의 list를 의미함.
- segmentation의 각각의 리스트는 단순한 **[x1, y1, ..., cn, yn]** (n>=3)포맷의 폴리곤임.
- x와 y는 픽셀 단위로 표현한 절대 좌표임.
- 값이 dict라면 COCO의 압축 RLE 포맷으로 나타낸 픽셀 별 Segmentation Mask를 나타냄.
- dict에는 "size"와 "counts" 키가 있어야 함. 

- 아래는 분야에 상관없이 항상 가지고 있는 기본 구조임.

### 기본 형식 
```
{
"images" : [image],  (필수)
"annotations" : [annotation], (필수)
"categories": [categories],  (필수) 
"info" : info, (필수X)
"licenses" : [license], (필수X)
}
```

- 전체는 3~5개의 항목을 가진 dictionary임.
- 각각 element 중에 info만 dict고 나머지는 리스트임.
```
info{
"year" : int, 
"version" : str, 
"description" : str, 
"contributor" : str, 
"url" : str, 
"date_created" : datetime,
}
 
image
[{
  "id" : int,  (필수)
  "width" : int, (필수)
  "height" : int,  (필수)
  "file_name" : str, (필수)
  "date_captured": str, (필수)
  "license" : int, 
  "flickr_url" : str, 
},
{
}
]

licenses
[{
  "id" : int, 
  "name" : str, 
  "url" : str,
},
{
```

- object detection 분야라면 기본 구조에 아래의 형식을 추가 함.
```
annotation
[{
  "id" : int,  (필수. 없으면 COCO 변환 시 에러)
  "image_id" : int, (필수)
  "category_id" : int,  (필수) 
  "bbox" : [좌상단 x, 좌상단 y,width,height], (필수) 
  "segmentation" : RLE or [polygon],  
  "area" : float, 
  "iscrowd" : 0 or 1, 
},
{...
}
```
<img src="https://github.com/sandartchip/TIL/assets/15938354/78157e7f-9c12-4682-b28e-a2fd1f06dba8" />

```
categories[{
  "id" : int(필수),
  "name": str(필수),
  "supercategory" : str(필수 X)}
  ,
  {...
  } 
```

- 이미지와 annotation, categories, licenses은 여러개가 올 수 있음
- images (list[dict])
- annotations (list[dict])

### 예시
<img src="https://github.com/sandartchip/TIL/assets/15938354/b707dd59-d97d-4b0f-9c90-ff395b888674" width="500px" /> <br>
<img src="https://github.com/sandartchip/TIL/assets/15938354/d21a9e74-726e-42b2-901e-548693859930" width="300px"/><br>
<img src="https://github.com/sandartchip/TIL/assets/15938354/e583ddf4-95a4-4ddd-aa8f-aab733927b42" width="600px" />





### 참고자료

https://ctkim.tistory.com/entry/coco-data-set-%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C%EC%99%80-%EA%B5%AC%EC%84%B1%EC%9A%94%EC%86%8C-%EB%B0%8F-%EC%8B%9C%EA%B0%81%ED%99%94%EC%BD%94%EB%93%9C#:~:text=COCO%20Data%20Set%EC%9D%80%20%22Common,%EB%8C%80%EA%B7%9C%EB%AA%A8%20%EC%9D%B4%EB%AF%B8%EC%A7%80%20%EB%8D%B0%EC%9D%B4%ED%84%B0%EC%85%8B%EC%9E%85%EB%8B%88%EB%8B%A

https://detectron2-kr.netlify.app/tutorials/datasets.html

- 필수필드 : https://docs.aws.amazon.com/ko_kr/rekognition/latest/customlabels-dg/md-coco-overview.html
