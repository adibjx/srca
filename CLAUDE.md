# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Projeto

Landing page estática do escritório SRCA — Squiapati, Romano, Chagas & Afonso Neto, Advocacia Tributária. Uberaba, MG.

Não há bundler, framework ou dependências npm. Para visualizar, abra `SRCA Landing Page.html` diretamente no navegador.

## Estrutura de arquivos

| Arquivo | Função |
|---|---|
| `SRCA Landing Page.html` | Toda a estrutura, copy e JavaScript da página |
| `colors_and_type.css` | Design tokens: cores, tipografia, espaçamento, sombras |
| `styles.css` | Estilos de componentes e layout |
| `form-handler.gs` | Google Apps Script que recebe os dados do formulário e salva no Sheets |

Os SVG icons são inline no HTML via `<symbol>` + `<use>`. Não há sprite externo.

## CSS

`colors_and_type.css` é a fonte de verdade de tokens. Nunca adicione cores ou tamanhos de fonte hardcoded em `styles.css` — use sempre as variáveis CSS definidas ali.

Paleta principal:
- `--color-primary: #08283A` — azul-marinho (fundo dark, header)
- `--color-accent: #A88A45` — dourado fosco (CTAs, ênfases)
- `--color-background: #F7F4EE` — off-white quente (fundo geral)

Fontes: `--font-heading` (Libre Baskerville) para títulos, `--font-body` (Spectral) para corpo, `--font-ui` (Inter Tight) para labels e botões.

## Formulário e integração

O formulário envia JSON via `fetch` com `Content-Type: text/plain` para o Google Apps Script. Esse Content-Type é intencional — evita o preflight CORS que o Apps Script não suporta.

A URL do script está em `SCRIPT_URL` no bloco `<script>` no fim do HTML. Ao reimplantar o Apps Script, atualizar essa constante.

O Apps Script grava na aba ativa da planilha. A ordem das colunas é: Data · Nome · Empresa · E-mail · Telefone · Setor · Faturamento · Regime · Mensagem.

## Estratégia e posicionamento (fonte: `uploads/Posicionamento.md`)

**Tagline aprovada:** "Inteligência tributária para seu negócio e patrimônio." — não alterar.

**Cliente ideal (Tipo B):** empresas com faturamento R$5M–R$50M, Lucro Presumido/Real, sem advogado tributário próprio, no Triângulo Mineiro.

**Tom obrigatório:** direto, educativo, confiante. Sem juridiquês, sem promessas de resultado em percentuais, sem comparações com concorrentes — restrição OAB (Provimento 94/2000).

**Proibido em qualquer copy:** palavras vagas (excelência, jornada, transformação, potencializar), travessões (—), perguntas retóricas óbvias, linguagem motivacional.

**Diferencial central:** o SRCA atua exclusivamente em tributário. Essa especialização deve ser reforçada em qualquer texto novo, nunca diluída.
