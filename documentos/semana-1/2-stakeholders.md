# 2. Mapa de Stakeholders — BSBora

[← Voltar à Semana 1](README.md) · [README do projeto](../../README.md)

**Responsável:** Eduarda (Cientista de Dados) · **Semana:** 1 · **Situação:** Oficial

> **Objetivo:** Mapear de forma clara e visual todas as pessoas, organizações e sistemas que impactam ou são impactados pelo **BSBora**.

---

## 1. Grupos de Stakeholders

```
                     ┌───────────────────────────────────────────┐
                     │           STAKEHOLDERS DO BSBORA          │
                     └─────────────────────┬─────────────────────┘
                                           │
         ┌───────────────────┬─────────────┴───────┬───────────────────┐
         ▼                   ▼                     ▼                   ▼
┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│   PRIMÁRIOS     │ │   SECUNDÁRIOS   │ │  REGULATÓRIOS   │ │ EQUIPE INTERNA  │
│(Usuários Finais)│ │(Dados e Serviços│ │ (Mentores e LGPD│ │ (Desenvolvedores│
│ - Famílias      │ │ - Setur / Secult│ │ - Residência IA │ │ - Eng. de Dados │
│ - Jovens/Casais │ │ - Eventbrite    │ │ - ANPD          │ │ - Cientista     │
│ - Moradores RAs │ │ - APIs Clima/Map│ │                 │ │ - Arquiteta/Ops │
└─────────────────┘ └─────────────────┘ └─────────────────┘ └─────────────────┘
```

---

## 2. Detalhamento por Categoria

### 🟢 Grupo 1: Stakeholders Primários (Usuários Finais)

Pessoas que utilizam o sistema para planejar seu tempo livre e gastos.

* **Famílias e Pais/Mães com Crianças:**
  * **Interesse:** Lazer seguro, rotina familiar viável e passeios com estrutura infantil.
  * **Dor central:** Dificuldade em achar opções baratas e medo de chuva estragar o passeio ao ar livre.
  * **Ação no projeto:** Validar a categoria `familia` e campos de gratuidade/meia-entrada infantil.

* **Jovens, Adultos e Casais (Lazer & Autocuidado):**
  * **Interesse:** Descobrir novos rolês culturais e gastronômicos sem ultrapassar o teto financeiro do mês.
  * **Dor central:** Informações espalhadas em redes sociais e surpresas com custos de transporte.
  * **Ação no projeto:** Validar filtros de orçamento rigorosos e sugestões perto de transporte público.

* **Moradores de Regiões Administrativas fora do Plano Piloto:**
  * **Interesse:** Opções de lazer descentralizadas (Ceilândia, Taguatinga, Samambaia, Planaltina, etc.).
  * **Dor central:** Sensação de que eventos de qualidade só acontecem no centro de Brasília.
  * **Ação no projeto:** Evitar viés geográfico mantendo o catálogo distribuído por todo o DF.

* **Pessoas com Deficiência (PcD) ou Mobilidade Reduzida:**
  * **Interesse:** Saber previamente se o atrativo possui rampas, banheiros acessíveis e piso tátil.
  * **Ação no projeto:** Exibir apenas informações de acessibilidade comprovadas na fonte oficial.

---

### 🟡 Grupo 2: Stakeholders Secundários (Fornecedores de Dados e APIs)

Entidades e serviços que fornecem a base de informações para os agentes de IA.

* **Órgãos Públicos de Turismo e Cultura do DF (Setur-DF, Secult-DF, IPE-DF):**
  * **Papel:** Fontes confiáveis para o catálogo de atrativos históricos, parques e centros culturais.
  * **Como tratar:** Usar dados abertos oficiais e sempre citar fonte e data de verificação.

* **Plataformas de Eventos e Ingressos (Eventbrite, Sympla, etc.):**
  * **Papel:** Fornecimento de feiras, peças teatrais e eventos temporários no DF.
  * **Como tratar:** Priorizar plataformas com APIs públicas ou catálogo verificado.

* **Provedores de Mobilidade e Tarifas (Semob-DF, Google Routes, OpenStreetMap):**
  * **Papel:** Dados de linhas de ônibus, distâncias e consumo de combustível.
  * **Como tratar:** Calcular estimativas com fórmulas determinísticas transparentes.

* **Provedores de Previsão Meteorológica (Open-Meteo, INMET):**
  * **Papel:** Previsão do tempo para alertar sobre chuva em passeios ao ar livre.
  * **Como tratar:** Integrar via API de clima para apoiar a recomendação de locais cobertos.

---

### 🔵 Grupo 3: Stakeholders Regulatórios e Acadêmicos

Entidades que avaliam e auditam a qualidade e a conformidade do projeto.

* **Mentores e Avaliadores da Residência em IA:**
  * **Interesse:** Garantir rigor metodológico, entregáveis semanais e foco na *Qualidade de Vida*.
  * **Como atender:** Apresentações semanais, documentação viva no GitHub e métricas objetivas.

* **Autoridade Nacional de Proteção de Dados (ANPD) / LGPD:**
  * **Interesse:** Garantir privacidade e segurança dos dados dos cidadãos.
  * **Como atender:** Coleta mínima (apenas RA aproximada e teto de gastos; sem extratos bancários).

---

### 🟣 Grupo 4: Equipe Interna de Desenvolvimento

Responsáveis pela construção e entrega do sistema web e da IA.

| Integrante | Papel Oficial | Foco no Repositório |
| --- | --- | --- |
| **Alexandre Sousa** | Engenheiro de Dados | Banco de dados Supabase, extensão `pgvector` e pipelines de APIs. |
| **Eduarda (Duda)** | Cientista de Dados | Curadoria do catálogo de passeios, RAG, factualidade e stakeholders. |
| **Larissa** | Arquiteta de Software | Contratos de API, integração Frontend/Backend e regras determinísticas. |
| **Isabela** | Operação | Validação com usuários, acompanhamento de riscos e métricas de aceitação. |
| **Breno** | Operação | Apoio a métricas, conformidade de processos e governança do roadmap. |

---

## 3. Matriz de Priorização e Engajamento

Tabela sintética para orientar as ações da equipe:

| Stakeholder | Grau de Impacto | Nível de Influência | Estratégia de Engajamento |
| --- | :---: | :---: | --- |
| **Famílias com crianças** | Alto | Alto | Envolver em questionários de teste e validar categoria `familia`. |
| **Moradores fora do Plano Piloto** | Alto | Alto | Garantir cotas mínimas de atrativos em suas RAs no catálogo. |
| **Mentores da Residência** | Alto | Alto | Apresentar entregas semanais conforme o roadmap de 7 semanas. |
| **Órgãos de Turismo (Setur/Secult)** | Médio | Alto | Consumir portais oficiais e registrar fontes com transparência. |
| **APIs Externas (Clima e Rotas)** | Médio | Médio | Monitorar limites de requisição (*quotas*) e manter plano B. |
| **ANPD / LGPD** | Crítico | Regulatório | Aplicar coleta mínima estrita desde o primeiro formulário. |

---

## 4. Diretriz para a Validação da Semana

* **Foco prioritário:** Moradores do DF com restrição orçamentária mensal, englobando ao menos um perfil familiar (com crianças) e um perfil individual/casal residente fora do Plano Piloto.
* **Formato:** Pesquisa documental e consultas com perguntas objetivas para validar se as dores mapeadas coincidem com os requisitos levantados.
