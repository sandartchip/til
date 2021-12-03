


![image](https://user-images.githubusercontent.com/15938354/144561118-b636ff3c-ea44-44ef-bbe0-d66cc2f8cf7a.png)

# Short Read와 Long Read 

## Read 
- 유전자를 Sequencing 하는 과정. 이걸 한번에 read하는게 아니라, 여러 번에 걸쳐 진행함. 
- 이때 read 길이에 따라 short이냐 long 이냐를 따지게 된다.  

## Short Read
- Short read는 작은 퍼즐들을 가지고 완성본을 만드는 과정. 
- 아무런 정보가 없기에 각 조각들의 위치를 찾는데 어려움이 있다. 
- 결국 조각들을 맞추다 보면 빈 공간이 생겨버리기도 한다. 
- 저렴하다.
- Illumina 로 생산. 

## Long Read
- 퍼즐 조각이 크다 -> 빈틈없는 완성본을 만드는 데 있어 훨씬 수월하다.
- short read가 할 수 없는 반복적 패턴 파악, 구조적 변이 발견, 백지상태의 sequencing 등이 가능함.
- 비싸다.
- PacBio, Oxford Nanopore 로 생산 


# 기계
- PacBio: Long Read Sequencing 기계 생산.  
- Illumina : Short read sequencing 기계 생산. 

