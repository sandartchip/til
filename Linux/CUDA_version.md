
- Cuda Version에는 2가지가 있음.

### runtime api 
nvcc --version -> runtime api

-주의사항 : nvcc version은 conda 환경을 활성화하면 conda 안에 다른 Cuda version이 잡힐 수 있음. 충격적이긴 함.....
-conda 끄기 / 안 끄기 상태에 따라서 nvcc version, 즉 runtime api version이 달라짐

### Driver API 
nvidia-smi : Driver API 
