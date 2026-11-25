# Laboratório de Programação I

> Os três trabalhos e os exercícios de aula de Laboratório de Programação I, em C: funções matemáticas, um quebra-cabeça deslizante e um gerenciador de notas no terminal.

**Contexto:** UFSM · Sistemas de Informação · Laboratório de Programação I · Prof. Benhur Stein · 2026/1

## Sobre

O repositório guarda o que foi entregue na disciplina. São três trabalhos, cada um mais difícil que o anterior, mais a autoavaliação final e os exercícios feitos em aula.

- **T1, funções matemáticas:** potência, fatorial, seno pela série de Taylor, raiz quadrada pelo método de Heron, cosseno pela identidade sen² + cos² = 1 e uma tabela de senos e cossenos. Tudo sem `math.h`. Pratica funções, seleção e repetição.
- **T2, quebra-cabeça deslizante:** o jogo de 15 peças (15-puzzle) em uma matriz 4x4 guardada em um vetor de 16 posições, jogado no terminal. Pratica vetores, indexação de matriz em vetor e testes de unidade feitos à mão.
- **T3, gerenciador de notas:** notas coloridas desenhadas como retângulos no terminal, com etiquetas, busca e edição, lidas e gravadas em arquivo. Pratica registros aninhados, ponteiros, alocação dinâmica (vetor que cresce e encolhe), arquivos e um programa organizado em modos.

Os enunciados estão no repositório do professor, [BenhurUFSM/l126a](https://github.com/BenhurUFSM/l126a/tree/main/Trabalhos).

## Funcionalidades

### T1: funções matemáticas (`l1-t1-diego-kelme.c`)

- `potencia(x, n)` aceita expoente negativo, que vira o inverso de `x` elevado a `-n`.
- `fatorial(n)` retorna `double`, porque `long` não comporta os fatoriais usados na série do seno. Para `n` negativo, retorna `-1`.
- `seno(x)` usa a série de Taylor e para quando o termo fica abaixo de `1e-10`.
- `raiz(x)` usa o método de Heron e para quando a diferença entre dois chutes seguidos fica abaixo de `1e-10`.
- `cosseno(x)` calcula `raiz(1 - seno²(x))`. Quando o arredondamento deixa o radicando um pouco negativo, ele é tratado como zero.
- Imprime uma tabela ASCII de seno e cosseno de 0 a 89 graus, cinco ângulos por linha e quatro casas decimais.
- A `main` chama uma função de teste por questão e mostra cada resultado ao lado do valor esperado.

### T2: quebra-cabeça deslizante (`l1-t2-diego-kelme.c`)

- O tabuleiro é um vetor `int v[16]` que representa a matriz 4x4 linha a linha. O valor `15` é a casa vazia.
- O embaralhamento faz 200 movimentos aleatórios a partir do tabuleiro resolvido, então o resultado sempre tem solução.
- Os movimentos respeitam as bordas: a casa vazia nunca sai do tabuleiro.
- O tabuleiro é desenhado com `+`, `-` e `|`, e a casa vazia aparece em branco.
- Uma bateria de testes (`roda_testes`) roda antes de o jogo começar e imprime `ERRO ...` se alguma função falhar.
- O jogo detecta quando o quebra-cabeça foi resolvido e dá parabéns.

### T3: gerenciador de notas (`l1-t3-diego-kelme.c`)

- Cada nota tem uma etiqueta de 3 caracteres (`A`-`Z`, `0`-`9`), uma cor RGB, um retângulo (posição e tamanho) e um texto de até 100 caracteres.
- As notas ficam em um vetor alocado dinamicamente. A capacidade começa em 8, dobra quando o vetor enche e cai pela metade quando a ocupação fica abaixo de 30%.
- As notas são desenhadas como retângulos coloridos. O texto ocupa as linhas do retângulo uma após a outra, e a cor da letra (clara ou escura) é escolhida para contrastar com o fundo. A nota sob o cursor ganha uma moldura.
- A ordem no vetor define o empilhamento: a última nota fica por cima. Dá para mandar uma nota para o início ou para o fim do vetor.
- Dá para mover, aumentar e diminuir o retângulo sem deixá-lo sair da tela.
- Remover uma nota guarda essa nota como "última removida", e ela pode ser reinserida na posição do cursor.
- Há modos para editar o texto, a etiqueta e a cor. Etiqueta e cor podem ser aplicadas a todas as notas visíveis de uma vez.
- A busca filtra por trecho do texto (diferencia maiúsculas de minúsculas) e por prefixo da etiqueta.
- As notas são lidas de um arquivo ao iniciar e gravadas com `g` e ao sair. Linhas mal formatadas, e linhas cujo texto teve de ser cortado, são copiadas para `notas-problemas.txt`. Cores fora de 0-255 são ajustadas ao limite, e largura ou altura menor que 1 vira 1.

## Tecnologias

- C (C99), compilado com GCC
- Biblioteca padrão: `stdio.h`, `stdlib.h`, `string.h`, `stdbool.h`
- T3: `tela.c`/`tela.h`, fornecidos pelo professor, que usam `stty` e sequências de escape ANSI para o terminal em modo cru, cores RGB e posição do cursor
- Python 3 (só os scripts de teste do T3, com `pty`)

## Estrutura do projeto

| Caminho | Descrição |
|---|---|
| `trabalhos/t1-funcoes-matematicas/l1-t1-diego-kelme.c` | T1 entregue: todas as questões em um arquivo |
| `trabalhos/t1-funcoes-matematicas/{potencia,fatorial,seno,raiz,cosseno,tabela}.c` | Rascunhos do T1, uma questão por arquivo, cada um com a própria `main` de teste |
| `trabalhos/t2-quebra-cabeca-deslizante/l1-t2-diego-kelme.c` | T2 entregue |
| `trabalhos/t3-gerenciador-de-notas/l1-t3-diego-kelme.c` | T3 entregue |
| `trabalhos/t3-gerenciador-de-notas/tela.c`, `tela.h` | Biblioteca de tela e teclado do professor (não é de minha autoria) |
| `trabalhos/t3-gerenciador-de-notas/notas.txt` | Arquivo de notas de exemplo |
| `trabalhos/t3-gerenciador-de-notas/testes/drv.py`, `drv2.py` | Scripts que abrem o T3 em um pseudo-terminal e enviam teclas |
| `trabalhos/t3-gerenciador-de-notas/testes/notas-problemas.txt` | Exemplo de saída com uma linha rejeitada |
| `trabalhos/autoavaliacao.txt` | Texto de autoavaliação da entrega final |
| `exercicios/` | Exercícios de aula (rascunhos) |

Os exercícios de `exercicios/`:

| Arquivo | Conteúdo |
|---|---|
| `2026-03-26-exercicio.cpp` | "Pa-pum": de 1 a 20, troca múltiplos de 3 por `pa`, números terminados em 5 por `pum` e os dois casos por `papum` |
| `2026-04-02-putchar.cpp` | Leitura de um número (rascunho, usa `system("cls")`) |
| `benhur-post-it.c`, `benhur-post-it.cpp` | Post-its coloridos no terminal com cores ANSI, feitos a partir do exemplo do professor |
| `fibonacci.cpp` | Tabela ASCII com os termos da sequência de Fibonacci |
| `semana-3-exercicio-1.cpp` | Desenho de uma caixa com `putchar` |
| `semana-3-exercicio-2.cpp` | Impressão de um inteiro dígito a dígito com `putchar`, recursiva |

Os arquivos `.cpp` são código C com extensão de C++. Por serem rascunhos de aula, alguns não compilam sem ajustes (veja [Observações](#observações)).

## Como rodar

### Pré-requisitos

- GCC
  - Linux: `sudo apt install gcc` (Debian/Ubuntu) ou equivalente
  - Windows: [MSYS2](https://www.msys2.org/) com MinGW-w64, ou WSL
- T3: um terminal POSIX com `stty` (Linux, macOS ou WSL no Windows). O console do Windows não serve.
- Scripts de teste do T3: Python 3 em Linux, macOS ou WSL (o módulo `pty` não existe no Windows)

### Passo a passo

Clone o repositório:

```bash
git clone https://github.com/itskelme/ufsm-si-lab-prog-1.git
cd ufsm-si-lab-prog-1
```

**T1:**

```bash
gcc -Wall -std=c99 -o t1 trabalhos/t1-funcoes-matematicas/l1-t1-diego-kelme.c
./t1          # no Windows: .\t1.exe
```

Cada rascunho também compila sozinho, por exemplo `gcc -Wall -std=c99 -o seno trabalhos/t1-funcoes-matematicas/seno.c`.

**T2:**

```bash
gcc -Wall -std=c99 -o t2 trabalhos/t2-quebra-cabeca-deslizante/l1-t2-diego-kelme.c
./t2          # no Windows: .\t2.exe
```

**T3** (Linux, macOS ou WSL):

```bash
cd trabalhos/t3-gerenciador-de-notas
gcc -Wall -o l1-t3 l1-t3-diego-kelme.c tela.c
./l1-t3 notas.txt
```

O argumento é opcional. Sem ele, o programa usa `notas.txt`, e se o arquivo não existir começa sem nenhuma nota. O `notas-problemas.txt` é criado na pasta em que o programa foi executado.

**Testes do T3:** os scripts executam `./l1-t3 notas.txt` a partir da pasta atual, por isso compile o binário com o nome `l1-t3` e rode-os de dentro de `trabalhos/t3-gerenciador-de-notas`:

```bash
python3 testes/drv.py    # grava, cria uma nota, grava de novo e sai
python3 testes/drv2.py   # cria uma nota, move 5 casas para a esquerda e 3 para baixo, grava e sai
cat notas.txt            # confira o resultado
```

Os scripts não verificam nada sozinhos: eles só mandam as teclas. O resultado é conferido abrindo o `notas.txt`, que eles alteram.

## Como usar

### T1

Não pede entrada. Imprime os testes das questões 1 a 5 e, no fim, a tabela:

```
+-----+---------------+---------------+---------------+---------------+---------------+
| ang |  seno cosseno |  seno cosseno |  seno cosseno |  seno cosseno |  seno cosseno |
+-----+---------------+---------------+---------------+---------------+---------------+
|   0 | 0.0000 1.0000 | 0.0175 0.9998 | 0.0349 0.9994 | 0.0523 0.9986 | 0.0698 0.9976 |
...
```

### T2

As peças são numeradas de 0 a 14, e o objetivo é deixá-las em ordem com a casa vazia no canto inferior direito. Digite o comando e tecle Enter (a entrada é lida com `scanf`, então dá para mandar vários comandos na mesma linha).

| Tecla | Ação |
|---|---|
| `w` ou `c` | move uma peça para cima (a que está abaixo da casa vazia) |
| `s` ou `b` | move uma peça para baixo |
| `a` ou `e` | move uma peça para a esquerda |
| `d` | move uma peça para a direita |
| setas + Enter | também funcionam, porque o código reconhece as letras `A`/`B`/`C`/`D` das sequências de escape das setas |
| `Q` (maiúsculo) | sai |

```
+----+----+----+----+
|  0 |  1 |  2 |  3 |
+----+----+----+----+
|  4 |  5 |  6 |  7 |
+----+----+----+----+
|  8 |  9 | 10 | 11 |
+----+----+----+----+
| 12 | 13 | 14 |    |
+----+----+----+----+
```

### T3

A tela mostra as notas e uma barra de status na última linha, com o número de notas visíveis e total e os filtros ativos.

**Modo principal**

| Tecla | Ação |
|---|---|
| `h` `j` `k` `l` ou setas | move o cursor |
| `H` `J` `K` `L` ou Shift+setas | move o retângulo da nota sob o cursor |
| Ctrl+`H`/`J`/`K`/`L` ou Ctrl+setas | aumenta o retângulo para a esquerda/baixo/cima/direita |
| Ctrl+`Y`/`U`/`I`/`O` ou Alt+setas | diminui o retângulo pela esquerda/baixo/cima/direita |
| `n` | cria uma nota nova no cursor (etiqueta `AAA`, 10x4, cor 200 200 120) |
| `d` ou Delete | remove a nota sob o cursor |
| `I` ou Insert | reinsere a última nota removida na posição do cursor |
| `i` / `f` | manda a nota para o início do vetor (fica por baixo) / para o fim (fica por cima) |
| `p` | leva o cursor até a nota visível que está mais acima na pilha |
| `e` / `t` / `c` | edita o texto / a etiqueta / a cor da nota sob o cursor |
| `b` / `B` | busca por texto / por etiqueta |
| `g` | grava o arquivo |
| `q` ou Esc | sai (e grava) |

**Editar texto (`e`) e busca por texto (`b`):** caracteres ASCII imprimíveis, menos aspas duplas. Setas ou Ctrl+`H`/`L` andam pelo texto, Home/End ou Ctrl+`K`/`J` vão ao início e ao fim, Backspace ou Ctrl+`B` apaga para trás e Delete ou Ctrl+`D` apaga sob o cursor. Enter confirma. Esc cancela a edição de texto e, na busca, limpa o filtro.

**Etiqueta (`t`) e busca por etiqueta (`B`):** `A`-`Z` e `0`-`9`, até 3 caracteres. Na edição, Enter aplica à nota sob o cursor e Ctrl+`T` (ou Alt+Enter) aplica a todas as notas visíveis, e os dois só funcionam com os 3 caracteres preenchidos. Na busca, Enter aplica o que foi digitado como prefixo e Esc limpa.

**Cor (`c`):** `r`/`g`/`b` (ou `e`/`v`/`a`) escolhem o componente, `h`/`l` ou ←/→ trocam de componente, `k`/`j` ou ↑/↓ somam ou subtraem 1, `K`/`J` ou Shift+↑/↓ somam ou subtraem 16 e os dígitos digitam o valor (até 255). Enter aplica à nota, Ctrl+`T` ou Alt+Enter aplica a todas as visíveis e Esc ou Ctrl+`B` cancela.

Alguns terminais reservam combinações como Ctrl+`H` (Backspace) e Ctrl+`I` (Tab). Se uma não funcionar, use a alternativa com setas.

**Formato do arquivo de notas:** uma nota por linha.

```
ETQ R G B X Y LARGURA ALTURA "texto"
123 192 65 120 66 15 10 4 "oi seu lindo ta funcionando sem utf-8"
```

`X` é a coluna e `Y` é a linha do canto superior esquerdo, contadas a partir de 1. Caracteres fora do ASCII imprimível (acentos, por exemplo) são descartados na leitura.

## Observações

Pontos encontrados ao revisar o código para este README:

- **T2:** o programa não chama `srand`, então o embaralhamento é igual em toda execução. Se a entrada acabar (EOF), o laço principal não termina, porque o retorno do `scanf` não é verificado.
- **T3:** no modo de cor, Ctrl+`B` cancela, enquanto nos outros modos Ctrl+`B` apaga e Ctrl+`C` cancela. Se o modo de cor for aberto sem nenhuma nota sob o cursor, ele mostra a última cor editada, que na primeira vez não está inicializada.
- **Exercícios:** `benhur-post-it.c` define `acha_postit` duas vezes (uma sem corpo) e não compila assim. `semana-3-exercicio-1.cpp` passa a string `"J"` para uma função que espera um caractere. `semana-3-exercicio-2.cpp` lê um `int` com `%f`.

## Referências

- Enunciados da disciplina: [T1](https://github.com/BenhurUFSM/l126a/blob/main/Trabalhos/t1.md), [T2](https://github.com/BenhurUFSM/l126a/blob/main/Trabalhos/t2.md), [T3](https://github.com/BenhurUFSM/l126a/blob/main/Trabalhos/t3.md), [entrega final](https://github.com/BenhurUFSM/l126a/blob/main/Trabalhos/final.md)
- Material de aula do Prof. Benhur Stein: [BenhurUFSM/l126a](https://github.com/BenhurUFSM/l126a)
- [Série de Taylor](https://pt.wikipedia.org/wiki/S%C3%A9rie_de_Taylor) e [método de Heron (babilônico)](https://en.wikipedia.org/wiki/Methods_of_computing_square_roots#Heron's_method), usados no T1
- [15-puzzle](https://en.wikipedia.org/wiki/15_puzzle), base do T2
- [Sequências de escape ANSI](https://en.wikipedia.org/wiki/ANSI_escape_code), usadas por `tela.c` e pelos post-its

## Autores

- Diego Kelme Santos da Silva ([@itskelme](https://github.com/itskelme)), autor dos trabalhos e exercícios
- Prof. Benhur Stein, docente da disciplina e autor de `tela.c`/`tela.h` e dos enunciados

## Licença

Este projeto está sob a licença [CC BY-NC 4.0](LICENSE): uso pessoal e modificação permitidos com atribuição; uso comercial proibido. Material de terceiros (enunciados, código fornecido pelo professor) pertence aos respectivos autores.
