# JusCrim-FA

> Assistente de IA para análise de certidões de antecedentes criminais do TJSP, com classificação jurídica de reincidência e maus antecedentes conforme o Código Penal brasileiro.

[![Versão do Prompt](https://img.shields.io/badge/prompt-v3.4-blue)](prompts/system_prompt.md)
[![Licença](https://img.shields.io/badge/licença-CC%20BY--NC%204.0-green)](LICENSE)
[![Uso](https://img.shields.io/badge/uso-exclusivamente%20judicial-red)]()

---

## O que é

O **JusCrim-FA** é um prompt de sistema para modelos de linguagem (LLMs) que atua como assistente especializado na análise de certidões de antecedentes criminais. O sistema classifica cada condenação anterior em:

- **Reincidência** — art. 63 do Código Penal
- **Maus antecedentes** — art. 59 do Código Penal
- **Nenhum dos institutos**

---

## Como usar

### Pré-requisitos

- Acesso a um modelo de linguagem com suporte a upload de arquivos (ex: Claude, GPT-4o)
- Certidão de antecedentes criminais emitida pelo **TJSP** em formato PDF ou imagem
- Conhecimento da **data do fato do crime atual** no formato `dd/mm/aaaa`

### Passo a passo

**1. Copie o prompt do sistema**

Acesse o arquivo [`prompts/system_prompt.md`](prompts/system_prompt.md) e copie todo o conteúdo.

**2. Configure o modelo**

Cole o conteúdo copiado no campo de **system prompt** ou **instruções personalizadas** do modelo de linguagem que estiver utilizando.

**3. Inicie a análise**

Na conversa com o modelo, envie:
- O arquivo PDF/imagem da certidão de antecedentes (máx. 15 páginas)
- A data do fato do crime atual

Exemplo de mensagem:
```
Data do crime atual: 15/03/2022
[anexo: certidão_antecedentes.pdf]
```

**4. Receba o resultado**

O modelo retornará automaticamente:
- Resumo executivo
- Tabela com todos os processos analisados
- Classificação detalhada de cada condenação
- Lista de processos excluídos com justificativa
- Recomendações

---

## Limitações

| Limitação | Detalhe |
|-----------|---------|
| Tribunal | Apenas certidões do **TJSP** |
| Idioma | Documentos em **português** |
| Tamanho | Máximo **15 páginas** por análise |
| Formato | PDF ou imagem legível (não escaneado ilegível) |

---

## Base legal

| Instituto | Artigo | Requisitos |
|-----------|--------|-----------|
| Reincidência | Art. 63, CP | Fato anterior + trânsito anterior ao crime atual + extinção < 5 anos ou sem extinção |
| Maus antecedentes | Art. 59, CP | Fato anterior + qualquer trânsito + extinção > 5 anos |
| Cômputo de prazos | Art. 10, CP | Dia inicial incluído no cômputo |

---

## Aviso legal

> **IMPORTANTE:** Esta ferramenta é um **instrumento de apoio** à atividade judicial e não substitui o juízo humano do magistrado. Os resultados gerados devem ser verificados pelo profissional responsável antes de qualquer utilização em processos judiciais. O uso é restrito a **fins exclusivamente judiciais**.
>
> O sistema não trata dados pessoais diretamente — a responsabilidade pelo tratamento de dados sensíveis de natureza criminal (art. 5º, II e art. 11, LGPD) é do operador que utiliza a ferramenta.

---

## Estrutura do repositório

```
JusCrim-FA/
├── README.md              # Este arquivo
├── LICENSE                # Licença CC BY-NC 4.0
└── prompts/
    └── system_prompt.md   # Prompt de sistema completo (v3.4)
```

---

## Licença

Este projeto está licenciado sob a [Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)](LICENSE).

Você pode compartilhar e adaptar o material para fins **não comerciais**, desde que atribua crédito ao autor original.
