
- Cuda Version에는 2가지가 있음.

### runtime api 
- nvcc : CUDA toolkit과 함께 설치되는 컴파일러.
- 실제 runtime에서 cuda 프로그램을 사용할 때의 cuda 버전. 

```
  nvcc --version -> runtime api
```

* nvcc version은 conda 환경을 활성화하거나 도커 컨테이너 안에 진입하면 conda 안에 다른 Cuda version이 잡힐 수 있음. 신기하긴 함. 
-conda 끄기 / 안 끄기 상태에 따라서 nvcc version, 즉 runtime api version이 달라짐

### Driver API 
- Nvidia의 GPU를 사고 GPU Driver를 Install하게 되는데 이 때 설치된 GPU Driver의 버전.
- nvidia-smi로 나오는 버전 : Driver API 


#### 참고

https://hyoseok-personality.tistory.com/entry/CUDA-%EA%B0%80%EC%83%81%ED%99%98%EA%B2%BD-Complete-CUDA-Installation
