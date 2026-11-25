# Laboratório de Programação I

**UFSM · Sistemas de Informação · 2026/1** — Prof. Benhur Stein · Linguagem C

Trabalhos e exercícios da disciplina. Enunciados e material do professor: [BenhurUFSM/l126a](https://github.com/BenhurUFSM/l126a).

## Trabalhos

| | Tema | O que pratica |
|---|---|---|
| [T1](trabalhos/t1-funcoes-matematicas) | Funções matemáticas: potência, fatorial, seno, cosseno, raiz e tabela | funções, seleção, repetição |
| [T2](trabalhos/t2-quebra-cabeca-deslizante) | Quebra-cabeça deslizante 4x4 desenhado no terminal | vetores, matriz em vetor, embaralhamento |
| [T3](trabalhos/t3-gerenciador-de-notas) | Gerenciador de notas: retângulos, cores, etiquetas | registros, ponteiros, arquivos, alocação dinâmica |
| [Final](trabalhos/autoavaliacao.txt) | Autoavaliação da disciplina | |

O histórico do git mostra a evolução: o primeiro commit tem os rascunhos e o segundo as versões entregues.

## Exercícios de aula

Em [`exercicios/`](exercicios): post-it, fibonacci, `putchar` e exercícios semanais.

## Como compilar

```bash
# T1
gcc -Wall -std=c99 -o t1 trabalhos/t1-funcoes-matematicas/l1-t1-diego-kelme.c -lm
# T2
gcc -Wall -std=c99 -o t2 trabalhos/t2-quebra-cabeca-deslizante/l1-t2-diego-kelme.c
# T3 (usa tela.c/tela.h, fornecidos pelo professor)
cd trabalhos/t3-gerenciador-de-notas
gcc -Wall -std=c99 -o t3 l1-t3-diego-kelme.c tela.c && ./t3 notas.txt
```

O T3 tem testes automatizados em [`testes/`](trabalhos/t3-gerenciador-de-notas/testes): `drv.py` roda o programa num pseudo-terminal (Linux).
