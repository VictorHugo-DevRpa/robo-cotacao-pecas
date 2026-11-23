# Robô de Cotação de Peças (RPA)

Robô feito no **Rocketbot Studio** que consulta o preço de autopeças no site da Auto Peças Molina e grava o resultado numa planilha Excel, sem ninguém precisar copiar e colar.

Autor: Victor Hugo

---

## O problema

Em uma loja de autopeças, cotar o preço de várias peças em sites de fornecedores é um trabalho manual e repetitivo: abrir o site, procurar a peça, copiar título, marca e preço, colar na planilha, e repetir para cada item.

## O que o robô faz

1. Abre a planilha e vai na aba **lista**.
2. Lê o **código** e o **link** de uma peça.
3. Abre o link no Chrome.
4. Lê da página o **título**, o **preço** e a **marca**.
5. Limpa a marca (o site escreve "MARCA: TEC FIL", o robô guarda só "TEC FIL").
6. Volta para a aba **Cotacao** e grava uma linha com código, título, marca, preço e fornecedor.
7. Fecha o navegador e passa para a próxima peça.
8. Repete até acabar a lista e salva a planilha.

## Arquivos do projeto

| Arquivo | O que é |
|---|---|
| `cotacao_pecas.json` | O robô exportado do Rocketbot Studio |
| `cotacao_pecas_modelo.xlsx` | A planilha, com a aba **lista** (entrada) e a aba **Cotacao** (resultado) |
| `prints/` | Imagens usadas neste README |

## A planilha

**Aba lista** (o que o robô lê):

| Codigo | Marca | Link | Peca |
|---|---|---|---|
| GI04 | Tec Fil | link da página do produto | Filtro de combustível |

O robô usa as colunas **Codigo** e **Link**. As colunas Marca e Peca servem para conferência.

**Aba Cotacao** (o que o robô escreve): Código, Título, Marca, Preço (R$) e Fornecedor.

## Como usar

1. Instale o Rocketbot Studio e importe o arquivo `cotacao_pecas.json`.
2. Preencha a aba **lista** com o código e o link de cada peça.
3. No comando **Open Workbook**, ajuste o caminho da planilha para o lugar onde ela está no seu computador.
4. Se a lista tiver mais ou menos peças, ajuste a condição do **While**. Hoje ela é `{linha} <= 6`, ou seja, a lista termina na linha 6.
5. Feche o Excel e clique em **Run**.

## Exemplo de resultado (cotação de 22/11/2026)

| Código | Marca | Preço |
|---|---|---|
| GI04 | TEC FIL | R$ 28,10 |
| N252 | COBREQ | R$ 184,60 |
| BD1650 | FREMAX | R$ 378,80 |
| 6203019000 | LUK | R$ 883,60 |
| PSL55 | TEC FIL | R$ 28,10 |

## Prints

**1. A planilha de entrada (aba lista)**

Cada linha tem o código da peça, a marca e o link da página do produto.

![Aba lista](prints/01_aba_lista.png)

**2. O robô no Rocketbot Studio**

Começo do robô: abre a planilha, define a linha inicial e entra no laço (While) que repete para cada peça.

![Início do robô e laço While](prints/02_robo_inicio.png)

Dentro do laço: abre o link da peça e lê o preço e o título da página.

![Leitura da página](prints/03_robo_leitura.png)

Fim do laço: fecha o navegador e, depois que todas as peças foram cotadas, salva a planilha e fecha o Excel.

![Fim do laço](prints/04_robo_fim_do_laco.png)

**3. O resultado (aba Cotacao)**

![Resultado na aba Cotacao](prints/05_resultado_cotacao.png)

## O que aprendi no projeto

- Ler dados de páginas web com o Rocketbot (por id, classe e XPath).
- Usar variáveis e um contador de linha para repetir o mesmo fluxo em várias peças.
- Tratar texto com um comando de Python (tirar o "MARCA: ").
- Ler e escrever em Excel pelo robô, em abas diferentes.
- Converter o preço de texto para número com `=VALUE(...)`.

## Limitações e próximos passos

- Os **links** são copiados à mão, um por peça. Uma versão futura pode buscar a peça pelo código no site.
- Hoje o robô cota em **um fornecedor** (Molina). A ideia é incluir mais fornecedores e comparar preços.
- Ideia futura: ler **notas fiscais (XML)** para dar entrada nos produtos automaticamente.
