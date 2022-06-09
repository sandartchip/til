
## energy function 

energy function 
-> penalizing? 주어진 dataset의 label과, 분석 결과의 label이 match가 되지 않는걸 penalizing함. 

- penalizing 할 떄 고려가 되는 부분이, data term 그리고 smoothness term.

- pixel이 foreground 맞는데 레이블링이 맞음-> penalize 안함.

energy function에 대해서, 잘못 분류되면 penalty를 얼마나 줘야할까.? 

--각 point마다 data term, smoothness term을 계산함.

data term은 intensity value만.  (unary cost)

smoothness term은, 주변의 값을 고려. (spatial한 relationship, coherence를)
-> smoothness term은, pairwise를 본다.
-> node의 pair을 보고 cost를 계산. 

새 부리에서 중간쪽의 한 점을 찍으면.. 주변이 다 비슷함 -> smoothness가 잘 되고 있음..
-> 페널티 낮음(??)

(새 사진)
하얀색=0... 페널티 없음.
새와 배경 사이 boundary 영역에서 -> 페널티가 크다. 
뭔가가 변하는 부분, spatial한 영역들을 보고 변화가 되는 부분에 대해서는 에너지로 표현을 해 줌. = pairwise cost 
spatial한 영역을 보고, 변화가 큰 곳(boundary)에서 .

--> Energy Function : unary cost(data term) + pairwise cost (boundary에 해당하는 - smoothness)

dot 나오는 그림 -> pairwise cost. 

두 개의 임의의 연결된 pixel에 대해서, function으로 표현. 둘 사이에 pairwise cost를 계산.


각 location에 label을 assign했을 때 (non negative) penalty를 어떻게 정의해야 할까.

neighbor 관계에 있는 p와 q를 봤을 때, 그 때 assign되는 Lable fp, fq를 비교를 해서, non negative penalty를 assign함.

두 노드사이의 adjacency를 정의할 때의 직관적 방법 = graph 

pixel 하나하나 = node. 
각 node간의 관계를 edge로 표현. 

격자 형태로 edge를 연결. 여기서 smoothness term을 효율적으로 표현해보자..

--위의 edge간의 관계를..
random variable을 node로 표현하고, 그들의 dependency로 표현하는거 =MRF(Markov Random Field)
->edge간의 관계를 확률적 측면에서 정의해볼 수도 잇다.!


< Energy 정의 >

data term -> MRF (probability )로 표현하는거는.. (중간에 좀 뛰어넘은 부분이 있음)

(시간부족으로) 바로 정리된 내용만 살펴 보면, 두 edge간의 관계를 log로 표현 가능. 

label이 background(0)이다. 그렇게 assign이 되있는데, 그럼 penalty를 줘야 한다.
penalty를 줄 때, penalty를 계산한다. 0이 assign된 p가 실제로 background가 될 확률을 계산한다.

결국은 0일 때, background가 되면 좋음.

error가 거의 없다.
p가 0일 때 background가 될 확률을 최대로 높인다.

--intensity

어떤 pixel에 대해서 0을 assgin했는데, 어떤 point가 background가 될 확률이 낮다
-> 그 경우에 penalty를 많이 준다. 

마이너스 로그 function -> 역행한다.

0이었는데 background-> 잘 된거-> 0 (그래프의 맨끝)
0이라고 읽었는데 background가 될 확률이 굉장히 낮다-> penalty를 많이!

p가 1일 때(foreground일 때) 그렇게 assign을 했는데 실제로 foreground->페널티 적게
p가 1일 떄 assign되었는데 실제로 background-> 페널티 많게 

결국은, data term을 낮추는 것이 labeling function을 데이터 측면에서는, 최대한 낮추는 게 좋은 방법.


--smoothness 

intensity의 historygram이 나옴 
이런 normalized histogram(0~1)을 integral 했을 떈 1이 나옴.-> probability function임.

p와 q 둘의 관계가 주어짐 -> p와 q가 다를 때 







## graph cut 
![image](https://user-images.githubusercontent.com/15938354/172552178-498b4932-aea5-42a2-ac8b-f9c8f8dafd92.png)

- 일반적인 컷을 형성했을 때, 그 컷 간의 간선 값들의 합은 작게 된다.

- 픽셀의 최소 변화량이 그 이미지를 영역별로 나누는 경계가 될 것이라는 생각에서 나온 방법
- 간선(edge)의 weight : intensity의 변화량에 반비례함



