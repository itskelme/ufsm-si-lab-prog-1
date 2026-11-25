# Laboratório de Programação I — Prof. Benhur Stein

UFSM · Ciência da Computação · 2026/1 · Linguagem C

Enunciados e material da disciplina: [BenhurUFSM/l126a](https://github.com/BenhurUFSM/l126a)

## Trabalhos

| Trabalho | Tema | Pasta |
|---|---|---|
| T1 | Funções matemáticas (potência, fatorial, seno, cosseno, raiz, tabela) | [`trabalhos/t1-funcoes-matematicas`](trabalhos/t1-funcoes-matematicas) |
| T2 | Quebra-cabeça deslizante 4x4 no terminal | [`trabalhos/t2-quebra-cabeca-deslizante`](trabalhos/t2-quebra-cabeca-deslizante) |
| T3 | Gerenciador de notas (retângulos, cor, arquivo, alocação dinâmica) | [`trabalhos/t3-gerenciador-de-notas`](trabalhos/t3-gerenciador-de-notas) |
| Final | Autoavaliação | [`trabalhos/autoavaliacao.txt`](trabalhos/autoavaliacao.txt) |

O histórico do git guarda os rascunhos (primeiro commit) e as versões entregues (segundo commit).

## Exercícios de aula

[`exercicios/`](exercicios): post-it, fibonacci, putchar e exercícios semanais.

## Compilar

```bash
gcc -Wall -std=c99 -o t1 trabalhos/t1-funcoes-matematicas/l1-t1-diego-kelme.c -lm
gcc -Wall -std=c99 -o t3 trabalhos/t3-gerenciador-de-notas/l1-t3-diego-kelme.c trabalhos/t3-gerenciador-de-notas/tela.c
```
