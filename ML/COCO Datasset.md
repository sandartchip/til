
### Example

![image](https://github.com/sandartchip/TIL/assets/15938354/3a063708-8542-4b3f-8df1-9395805cbd09)

- COCO Dataset의 annotation 파일은 기본 구조에 파일 형식을 더한 형태로 되어 있음. 

- **기본 구조**에 **분야별 형식**을 더한 형태로 구성되어 있음.
- object detection, segmentation, key point detection 등 분야에 따라 정해진 형식을 사용함.

- segmentation의 경우, segmentation 정보와 bbox, category_id, id, bbox, image_id, iscrowd, area가 필요 함.

- 아래는 분야에 상관없이 항상 가지고 있는 기본 구조임.

### 기본 형식 
```
{
"info" : info, 
"images" : [image], 
"annotations" : [annotation], 
"licenses" : [license],
}

info{
"year" : int, 
"version" : str, 
"description" : str, 
"contributor" : str, 
"url" : str, 
"date_created" : datetime,
}

image{
"id" : int, 
"width" : int, 
"height" : int, 
"file_name" : str, 
"license" : int, 
"flickr_url" : str, 
"coco_url" : str, 
"date_captured" : datetime,
}

license{
"id" : int, 
"name" : str, 
"url" : str,
}
```

- object detection 분야라면 기본 구조에 아래의 형식을 추가 함.
```
annotation{
"id" : int, 
"image_id" : int, 
"category_id" : int, 
"segmentation" : RLE or [polygon], 
"area" : float, 
"bbox" : [x,y,width,height], 
"iscrowd" : 0 or 1,
}

categories[{
"id" : int, 
"name" : str, 
"supercategory" : str,
}]
```


https://ctkim.tistory.com/entry/coco-data-set-%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C%EC%99%80-%EA%B5%AC%EC%84%B1%EC%9A%94%EC%86%8C-%EB%B0%8F-%EC%8B%9C%EA%B0%81%ED%99%94%EC%BD%94%EB%93%9C#:~:text=COCO%20Data%20Set%EC%9D%80%20%22Common,%EB%8C%80%EA%B7%9C%EB%AA%A8%20%EC%9D%B4%EB%AF%B8%EC%A7%80%20%EB%8D%B0%EC%9D%B4%ED%84%B0%EC%85%8B%EC%9E%85%EB%8B%88%EB%8B%A4.
