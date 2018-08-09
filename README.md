# Introdução À Computação Gráfica 2018.1

### Introdução:
O objetivo deste projeto é a rasterização de primitivas usando o algoritmo de Brasenham. Para esta tarefa utilizamos um framework desenvolvido pelo Prof. Christian Pagot que emula o acesso direto a memória de vídeo do computador.

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
