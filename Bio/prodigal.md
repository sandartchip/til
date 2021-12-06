

```
prodigal -i my.genome.fna -o my.genes -a my.proteins.faa
prodigal -i my.metagenome.fna -o my.genes -a my.proteins.faa -p meta
prodigal -h
```


- Genome sequence 파일이 있을 때 이로부터 CDS file (coding sequence, gene)을 얻고 싶다면 Prodigal을 사용할 수 있다. 
- 주의해야할 점은 Prodigal은 원핵생물에 한정해서 디자인된 프로그램이므로 진핵생물에 대해서는 다른 프로그램을 사용해야한다.
