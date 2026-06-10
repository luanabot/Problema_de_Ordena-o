# Relatório – Comparação entre Bubble Sort e Merge Sort

## 1. Introdução

A ordenação de dados é um dos problemas fundamentais da Ciência da Computação. Seu objetivo é organizar um conjunto de elementos em uma determinada ordem, geralmente crescente ou decrescente, facilitando operações como busca, análise e processamento de informações.

Neste trabalho foram implementados e comparados dois algoritmos de ordenação:

- **Bubble Sort** – algoritmo simples, porém menos eficiente para grandes volumes de dados.
- **Merge Sort** – algoritmo mais eficiente, baseado na estratégia de Divisão e Conquista (*Divide and Conquer*).

Os testes foram realizados utilizando arquivos contendo diferentes distribuições de dados (melhor caso, caso médio e pior caso), permitindo avaliar o comportamento de cada algoritmo em diferentes cenários.

---

## 2. Funcionamento dos Algoritmos

### 2.1 Bubble Sort

O Bubble Sort percorre o vetor diversas vezes comparando elementos adjacentes.

Quando dois elementos estão fora de ordem, eles são trocados de posição. A cada passagem, os maiores elementos são movidos para o final da lista.

#### Exemplo

Vetor inicial:

```text
[5, 3, 8, 1]
```

Primeira passagem:

```text
[3, 5, 8, 1]
[3, 5, 8, 1]
[3, 5, 1, 8]
```

Segunda passagem:

```text
[3, 5, 1, 8]
[3, 1, 5, 8]
```

Terceira passagem:

```text
[1, 3, 5, 8]
```

#### Pseudocódigo

```text
para i de 0 até n-1
    para j de 0 até n-i-1
        se vetor[j] > vetor[j+1]
            trocar posições
```

#### Complexidade

| Caso | Complexidade |
|--------|-------------|
| Melhor | O(n) |
| Médio | O(n²) |
| Pior | O(n²) |

---

### 2.2 Merge Sort

O Merge Sort utiliza a técnica de **Divisão e Conquista**.

Primeiramente, o vetor é dividido em partes menores até que cada parte possua apenas um elemento. Em seguida, essas partes são reunidas novamente de forma ordenada.

#### Exemplo

Vetor inicial:

```text
[8, 3, 5, 1]
```

Divisão:

```text
[8, 3] [5, 1]

[8] [3] [5] [1]
```

Junção ordenada:

```text
[3, 8] [1, 5]

[1, 3, 5, 8]
```

#### Pseudocódigo

```text
mergeSort(vetor)

se tamanho <= 1
    retornar

dividir vetor em duas partes

mergeSort(esquerda)
mergeSort(direita)

intercalar as partes ordenadas
```

#### Complexidade

| Caso | Complexidade |
|--------|-------------|
| Melhor | O(n log n) |
| Médio | O(n log n) |
| Pior | O(n log n) |

---

## 3. Resultados

### Arquivos com 1.000 elementos

| Caso | Bubble Sort | Merge Sort |
|--------|------------|------------|
| Melhor Caso | 0 ms | 1 ms |
| Caso Médio | 14 ms | 2 ms |
| Pior Caso | 10 ms | 2 ms |

### Arquivos com 1.000.000 elementos

| Caso | Bubble Sort | Merge Sort |
|--------|------------|------------|
| Melhor Caso | 11 ms | 144 ms |
| Caso Médio | 14 ms | 2 ms |
| Pior Caso | 10.274.609 ms | 126 ms |

### Tabela Comparativa Geral

| Tamanho da Entrada | Caso | Bubble Sort | Merge Sort |
|-------------------|-------|------------|------------|
| 1.000 | Melhor | 0 ms | 1 ms |
| 1.000 | Médio | 14 ms | 2 ms |
| 1.000 | Pior | 10 ms | 2 ms |
| 1.000.000 | Melhor | 11 ms | 144 ms |
| 1.000.000 | Médio | 14 ms | 2 ms |
| 1.000.000 | Pior | 10.274.609 ms | 126 ms |

---

## 4. Análise Crítica

Os resultados demonstram claramente a diferença de desempenho entre os algoritmos analisados.

O **Bubble Sort** possui complexidade **O(n²)**. Isso significa que, à medida que a quantidade de elementos aumenta, o número de comparações cresce de forma quadrática. Consequentemente, para grandes conjuntos de dados, o tempo de execução torna-se extremamente elevado.

No pior caso com 1.000.000 de elementos, o algoritmo levou aproximadamente **10.274.609 ms** (cerca de 171 minutos), evidenciando sua baixa eficiência para grandes volumes de dados.

Por outro lado, o **Merge Sort** possui complexidade **O(n log n)**. Embora também apresente aumento no tempo de execução quando o tamanho da entrada cresce, esse crescimento ocorre de forma muito mais controlada.

Mesmo processando um arquivo com 1.000.000 de elementos, o Merge Sort concluiu a ordenação em aproximadamente **126 ms**, demonstrando excelente desempenho.

### Comparação dos comportamentos

- O Bubble Sort realiza muitas comparações e trocas repetidas.
- O Merge Sort divide o problema em partes menores e resolve cada uma delas de forma eficiente.
- Quanto maior o volume de dados, maior a diferença de desempenho entre os dois algoritmos.
- Algoritmos com complexidade **O(n log n)** são mais adequados para aplicações reais que manipulam grandes quantidades de informações.

---

## 5. Conclusão

A comparação realizada demonstrou a importância da escolha adequada do algoritmo de ordenação.

Embora o Bubble Sort seja simples de implementar e compreender, seu desempenho torna-se inviável para grandes conjuntos de dados devido à sua complexidade quadrática.

Já o Merge Sort apresentou tempos de execução muito inferiores, mantendo boa eficiência mesmo com o aumento significativo da entrada.

Dessa forma, conclui-se que o Merge Sort é uma alternativa muito mais adequada para aplicações que exigem processamento de grandes volumes de dados, oferecendo melhor escalabilidade e desempenho.
