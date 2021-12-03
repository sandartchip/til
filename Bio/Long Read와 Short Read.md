


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
- 롱 리드 시퀀싱 플랫폼들은 short read 시퀀싱 기술에 가까운 정확도를 보이며 수십에서 수천 킬로 베이스 가량의 긴 길이를 생산함.
- 기존에는 접근하기 어려웠던 구조 변이의 탐지와 최초로 텔로미어-텔로미어까지의 전체 염색체 조립을 가능하게 하였다.
- 롱리드를 이용한 조립은 빠르지만(?) 정확도가 낮다는 문제점이 있었다.

#### Polishing 
- 폴리싱을 거치지 않으면 조립이 작은 삽입과 결실 오류를 많이 보인다.
- 


# 기계
- PacBio: Long Read Sequencing 기계 생산.  
- Illumina : Short read sequencing 기계 생산. 

## 현재의 동향
- 현재의 시퀀싱 시장은, 높은 정확도와 가성비를 장점으로 하는 Short Read 시퀀싱이 대세임. 그러나 Human Genome Reference 수립을 위한 De novo assembly를 하기 위해서 Long read 시퀀싱은 필수로 이용되고 있다. Short Read는 Depth가 높아서 Error Rate가 낮고, 같은 Read를 읽을 때 가격적으로 훨씬 저렴하다.

- 반복 서열이 많거나, Polymorphism이 많이 존재하는 영역, GC 비율이 높아서 시퀀싱이 어려운 영역, 구조 변이 검출 등에서는 Long read 시퀀싱이 훨씬 우수함. 



참고 자료 :https://2wordspm.com/2019/04/28/pacbio-smrt-sequencing-long-reads-sequencing%EC%9D%98-%EC%9B%90%EB%A6%AC%EC%99%80-%EC%9E%A5%EB%8B%A8%EC%A0%90/
https://www.ibric.org/myboard/read.php?Board=report&id=3637
