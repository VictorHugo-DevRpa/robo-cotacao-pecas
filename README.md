# 🤖 Robô de Cotação de Peças (RPA)

Robô desenvolvido no **Rocketbot Studio** que consulta preços de autopeças no site da **Auto Peças Molina** e registra automaticamente os resultados em uma planilha Excel, eliminando tarefas manuais e repetitivas.

**Autor:** Victor Hugo

---

## 📌 O problema

Em uma loja de autopeças, consultar preços de vários produtos em sites de fornecedores é um trabalho manual e repetitivo: abrir o site, procurar a peça, copiar título, marca e preço, inserir na planilha e repetir o processo para cada item.

## ⚙️ O que o robô faz

1. Abre a planilha e acessa a aba **lista**.
2. Lê o código e o link de uma peça.
3. Abre o link no Google Chrome.
4. Captura o título, o preço e a marca do produto.
5. Trata o texto da marca, removendo o prefixo "MARCA:".
6. Acessa a aba **Cotacao** e registra código, título, marca, preço e fornecedor.
7. Fecha o navegador e passa para a próxima peça.
8. Repete o processo até finalizar a lista e salva a planilha.

## 📂 Arquivos do projeto

| Arquivo | Descrição |
|---|---|
| `cotacao_pecas.json` | Robô exportado do Rocketbot Studio |
| `cotacao_pecas_modelo.xlsx` | Planilha modelo com as abas lista e Cotacao |
| `lista_pecas.xlsx` | Lista de peças para consulta |
| `01_aba_lista.png` | Print da planilha de entrada |
| `
