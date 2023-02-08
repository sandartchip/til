
# CAM
- CAM 계산을 위해서 Convolution layer 이후를 Global Average Pooling 레이어로 바꾸어야 함


![image](https://user-images.githubusercontent.com/15938354/217483275-6ff67042-0d12-4207-88ca-2457465049d2.png)



# Grad-CAM
- akc = k번째 feature map Ai,j(k)의 각 원소 i,j가 output class c의 matmul값 Yc에 주는 영향력의 평균
- 이미지에서 특정 클래스에 긍정적인 영향을 미치는 부분에만 관심이 있음
- 

https://velog.io/@mink7878/Grad-CAM-Grad-CAM-Visual-Explanations-from-Deep-Networksvia-Gradient-based-Localization
