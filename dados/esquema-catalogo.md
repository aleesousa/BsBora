# Esquema do catálogo de passeios — BSBora

[← README do projeto](../README.md) · [Semana 1](../documentos/semana-1/README.md)

**Responsável:** Eduarda (cientista de dados) · **Semana:** 1 · **Situação:** rascunho para revisão da equipe

Este documento define **quais informações cada passeio do catálogo deve ter**. O catálogo é a base do sistema: os filtros, o cálculo do orçamento e o RAG (Semana 2) dependem dele.

## Campos de cada passeio

### Identificação

| Campo | Tipo | Obrigatório | Descrição | Exemplo |
| --- | --- | --- | --- | --- |
| `id` | texto | sim | Identificador único. | `psq-0001` |
| `nome` | texto | sim | Nome do passeio ou local. | Parque da Cidade |
| `descricao` | texto | sim | Resumo curto do passeio (usado pelo RAG). | Parque urbano com pistas de caminhada... |
| `categoria` | lista | sim | Uma ou mais categorias (ver [lista abaixo](#categorias)). | `natureza`, `esporte` |

### Localização

| Campo | Tipo | Obrigatório | Descrição | Exemplo |
| --- | --- | --- | --- | --- |
| `regiao_administrativa` | texto | sim | Região Administrativa (RA) do DF onde fica o passeio. | Plano Piloto |
| `endereco` | texto | não | Endereço público do local. | — |
| `latitude` / `longitude` | número | não | Coordenadas do local, para estimar distâncias. | — |

### Custos e horários

| Campo | Tipo | Obrigatório | Descrição | Exemplo |
| --- | --- | --- | --- | --- |
| `preco_por_pessoa` | número (R$) | sim | Valor da entrada por pessoa. `0` quando gratuito. | `0` |
| `preco_infantil` | número (R$) | não | Valor para crianças, quando houver. | — |
| `custos_extras` | texto | não | Gastos comuns não incluídos no preço (estacionamento, alimentação). | Estacionamento pago |
| `horario_funcionamento` | texto | sim | Dias e horários de abertura. | — |
| `duracao_media_horas` | número | sim | Tempo médio de visita, usado para validar a agenda. | `2` |

### Etiquetas (filtros)

| Campo | Tipo | Obrigatório | Descrição |
| --- | --- | --- | --- |
| `adequado_criancas` | sim / não / não informado | sim | Se o passeio é adequado para famílias com crianças. |
| `ambiente` | ao ar livre / coberto / misto | sim | Usado para lembrar o usuário de conferir o clima. |
| `acessibilidade` | texto | não | Informações de acessibilidade confirmadas na fonte. |

### Evidência e qualidade (obrigatório para todo passeio)

| Campo | Tipo | Obrigatório | Descrição |
| --- | --- | --- | --- |
| `fonte_url` | texto | sim | Link da fonte oficial ou da página do atrativo. |
| `fonte_nome` | texto | sim | Nome da fonte (ver [fontes.md](fontes.md)). |
| `data_verificacao` | data | sim | Quando a informação foi conferida. |
| `campos_nao_confirmados` | lista | não | Campos que não puderam ser confirmados na fonte. |

> **Regra de confiabilidade:** se um campo obrigatório não puder ser confirmado em uma fonte, ele é marcado em `campos_nao_confirmados` e o sistema exibe "não confirmado". **Nunca preencher dados por suposição.**

## Categorias

Lista inicial (a validar com a equipe):

`cultura` · `natureza` · `gastronomia` · `esporte` · `lazer infantil` · `vida noturna` · `eventos` · `compras` · `religioso` · `histórico`

## Metas de qualidade do catálogo (Semana 1 → Semana 2)

| Meta | Valor proposto | Ligação |
| --- | --- | --- |
| Tamanho do catálogo | 30 a 50 passeios | [README](../README.md#funcionalidades-planejadas) |
| Passeios com fonte e data de verificação | 100% | Risco "Informações desatualizadas" |
| Passeios gratuitos | Proporção a definir | Respeito ao orçamento |
| Distribuição por Região Administrativa | Evitar concentração no Plano Piloto | Risco "Cobertura desigual do DF" (viés) |
| Categorias diferentes | Ao menos 5 | Métrica "Diversidade do plano" |

## Cuidados (LGPD e viés)

- O catálogo guarda **apenas dados públicos de locais**, nunca dados pessoais.
- Acompanhar a **distribuição por RA e por faixa de preço** para não favorecer só regiões centrais ou passeios caros.

## Próximos passos (Semana 2)

- Revisar este esquema com a equipe, principalmente com o MLOps (Breno) e a engenharia de software (Larissa), que vão criar a tabela no Supabase.
- Coletar os primeiros passeios a partir das fontes de [fontes.md](fontes.md).
