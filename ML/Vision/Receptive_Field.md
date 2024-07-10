### CNN의 Receptive Field

<img src="https://velog.velcdn.com/images/sandartchip/post/36622689-6a4b-4647-bcf2-5c59d0df5006/image.png" width="400px"/>

- 각 필터들이 배출한 하나의 결과값은 하나의 뉴런임.
- Layer2를 보면 초록색 뉴런 1개의 Receptive Field는 원본 이미지의 3x3 부분임. 
- Layer3의 초록색 뉴런 1개의 Receptive Field는 원본 이미지의 5x5 부분임.
- 즉, 층이 깊어질수록 더 넓은 Receptive Field를 가지게 됨.

- Receptive field, 수용 필드 크기는 뉴런이 **출력을 계산할 때 고려할 수 있는 컨텍스트의 양을 결정**하기 때문에 CNN에서 중요한 개념.

- Receptive field가 작은 뉴런은 이미지의 작은 부분만 볼 수 있음. 작고 국소적인 특징에 민감함.
- Receptive field가 큰 뉴런은 이미지의 더 많은 부분을 볼 수 있음. 더 크고 전역적인 특징에 민감함. 

- 뉴런의 수용 필드는 입력 이미지에 적용되는 필터/커널의 크기와 모양에 의해 정의됨.
- 필터 크기가 클 수록 수용 필드가 커지고, 수용 필드는 풀링 및 컨볼루션 작업의 결과로, 네트워크 깊숙히 이동할수록 커짐.
- 수용 필드 크기는 CNN 아키텍처를 설계할 때 고려해야 할 중요한 요소이며, 특히 이미지 분할과 같이 수용필드가 전역 특징을 캡쳐할 수 있을만큼 충분히 커야 하는 작업의 경우 더욱 그러함.
-  수용 필드의 크기와 계산 효율성 사이의 균형의 고려가 필요함. 더 큰 수용필드를 사용하면 성능이 향상될 수는 있지만, 계산 및 메모리 요구사항이 증가함.
- 
#### 참고자료
https://itrepo.tistory.com/32
https://hyunhp.tistory.com/695
