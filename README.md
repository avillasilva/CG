# Introdução À Computação Gráfica 2018.1

### Introdução:
O objetivo deste projeto é a rasterização de primitivas usando o algoritmo de Brasenham. Para esta tarefa utilizamos um framework desenvolvido pelo Prof. Christian Pagot que emula o acesso direto a memória de vídeo do computador via o ponteiro FBptr.

### Rasterização de um ponto:
Desenvolvemos uma função chamada putPixel que recebe como parâmetro  dois inteiros representando as coordenadas de um pixel e um array de quatro inteiros que representam os valore de RGBA que queremos representar nessas coordenadas.

```C++
void putPixel(int x, int y, color c) {
	FBptr[x*4 + y*4*IMAGE_WIDTH] = c[0];
	FBptr[x*4 + y*4*IMAGE_WIDTH + 1] = c[1];
	FBptr[x*4 + y*4*IMAGE_WIDTH + 2] = c[2];
	FBptr[x*4 + y*4*IMAGE_WIDTH + 3] = c[3];
}
```
Cada pixel é representado por quatro bytes onde cada byte especifíca uma intensidade de uma das cores RGBA nesta ordem. Como esses bytes estão armazenados linearmente na memória de vídeo, cada pixel  está disposto quatro posições a frente do pixel anterior. A posição inicial de cada pixel é dada pela função Offset = 4*x + 4*y*w onde x e y são as coordenadas do pixel e w é o comprmento da tela.


### Rasterização de uma linha:
Para rasterizar linhas, utilizamos o algoritmo de Bresenham generalizando-o para todos octantes do plano cartesiano.

#### Algoritmo de Bresebam:
Esse algoritmo nos da uma função incremental para a rasterização de uma reta mas em sua forma natural ele é limitado ao primeiro octante do plano cartesiano(retas com inclinação entre 0 e 1). Ele é implementado em codigo da seguinte forma:

'''C++
int d = 2*dy - dx;
int e_inc = 2*dy;
int ne_inc = 2*(dy - dx);
			
putPixel(i,c);			
while(x < f.x){
	if(d <= 0){
		x++;
		d += e_inc;			
	}
	else{
		x++;
		y++;
		d += ne_inc;			
	}
	putPixel(x,y,c);
}
'''

#### Como foi feito a generalização:
