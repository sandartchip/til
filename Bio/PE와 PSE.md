##  Single End Sequencing
- 시퀀싱 기계가 서열의 조각을 오직 한 쪽 끝에서부터 읽어서 염기쌍 서열을 생성한다.

## paired-end squencing
- 우선 한쪽 끝에서 특정 길이까지 읽고, 그다음 다른 쪽 끝에서 서열을 읽는다. Paired-end sequencing은 유전체 상에서 다양한 read들의 상대적인 위치를 찾는데 더 용이하다.
- 원본 없이 하나하나 맞춰 보면서 연결되는 것 끼리 쭉 잇는다. 이어서 원래의 genome 서열을 알아내야 한다. 따라서 한 종류의 read들만 가지고 assemble을 하기란 쉽지 않다. 그래서, short, long, paired-end, mate-paired-end 등 여러 종류의 read들을 가지고 assembly를 해야 결과가 좋아진다. 


## Strand Specific
- Strand-specific은 양 말단의 adapter sequence를 다르게 붙임으로써 reads의 앞뒤를 구분해주는 방식. 

- Single-end, Paired-end와 Stranded, Unstranded는 별개의 개념이라는 것을 알아야 한다. Single-end이더라도 Stranded일 수도 있고 Unstranded일 수도 있으며 Paired-end도 마찬가지이다

## Depth of coverage 
- depth of coverage는 시퀀싱 중 유전체의 특정 위치가 시퀀싱되는 횟수를 나타낸다. 예를 들어 Exome sequencing을 하는데 목표 coverage를 60X라고 한다면, 그 뜻은 목표로 하는 각 염기들이 평균적으로 60번 정도 시퀀싱된다는 것이다. 



https://bgreat.tistory.com/100
