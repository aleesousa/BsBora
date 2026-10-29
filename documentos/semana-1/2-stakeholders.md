# 2. Mapa de Stakeholders — BSBora

[← Voltar à Semana 1](README.md) · [Ver Personas](personas.md) · [Ver Premissas](premissas.md)

**Responsável:** Eduarda (Cientista de Dados) · **Semana:** 1 · **Situação:** Oficial

> **Objetivo:** Mapear de forma visual, enxuta e estruturada todas as partes envolvidas no **BSBora**: quem usa, quem fornece dados, quem regula e quem constrói o sistema.

---

## 📐 1. Pipeline Geométrico das Funções da Equipe

Fluxo de trabalho integrado da equipe para as entregas do projeto:

```
╔═════════════════════════════════════════════════════════════════════════════════════════════════╗
║                 PIPELINE GEOMÉTRICO: FLUXO DE TRABALHO DA EQUIPE BSBORA                         ║
╚═════════════════════════════════════════════════════════════════════════════════════════════════╝

   [ 1. INGESTÃO & BANCO ]        [ 2. CURADORIA & RAG ]        [ 3. ARQUITETURA & REGRAS ]     [ 4. OPERAÇÃO & TESTES ]
    Alexandre Sousa                Eduarda (Duda)                Larissa Giffoni                 Isabela & Breno
    Engenharia de Dados            Ciência de Dados              Arquiteta de Software           Operação & Governança
   ┌──────────────────────┐       ┌──────────────────────┐       ┌──────────────────────┐       ┌──────────────────────┐
   │ • Banco Supabase     │       │ • Catálogo de 30-50  │       │ • API FastAPI        │       │ • Validação Usuários │
   │ • Extensão pgvector  │ ────► │ • Embeddings / Busca │ ────► │ • Contratos de Dados │ ────► │ • Matriz de Riscos   │
   │ • Ingestão APIs Clima│       │ • Factualidade ≥95%  │       │ • Regras Determiníst.│       │ • Métricas de Aceite │
   │   e Transporte       │       │ • Personas / Premissa│       │ • Orquestração Agente│       │ • Conformidade LGPD  │
   └──────────────────────┘       └──────────────────────┘       └──────────────────────┘       └──────────────────────┘
              ▲                                                                                             │
              └───────────────────────────── Feedback Contínuo ─────────────────────────────────────────────┘
```

---

## 👥 2. Stakeholders Primários por Categoria de Público

Usuários finais do sistema, representados em detalhe no documento de [Personas](personas.md):

```
┌────────────────────────────────────────────────────────────────────────┐
│                        PÚBLICO ATENDIDO NO DF                          │
├──────────────┬──────────────┬──────────────┬─────────────┬─────────────┤
│ 🧒 CRIANÇAS  │  🎓 JOVENS   │  💼 ADULTOS  │  👵 IDOSOS  │   ♿ PcD     │
│  & Famílias  │ & Estudantes │   & Casais   │Melhor Idade │Mobilidade R.│
└──────────────┴──────────────┴──────────────┴─────────────┴─────────────┘
```

### 🧒 Crianças & Família
* **Foco:** Passeios seguros, rotina familiar viável e infraestrutura adequada (banheiros, alimentação, segurança).
* **Persona de Referência:** [Marcos (Ceilândia)](personas.md#persona-1-marcos-34-anos--família--crianças).
* **Atuação do BSBora:** Filtra categoria `familia`, evita passeios abertos em dias de chuva e calcula despesas totais.

### 🎓 Jovens & Estudantes
* **Foco:** Vida cultural ativa, feiras criativas, eventos independentes e autocuidado com custo mínimo.
* **Persona de Referência:** [Beatriz (Asa Norte)](personas.md#persona-2-beatriz-22-anos--jovens--estudantes).
* **Atuação do BSBora:** Centraliza eventos culturais dispersos e cruza com rotas de transporte público (ônibus/metrô).

### 💼 Adultos & Casais
* **Foco:** Variedade de experiências no mês, descompressão e controle orçamentário compartilhado.
* **Persona de Referência:** [Camila & Rafael (Águas Claras)](personas.md#persona-3-camila-29-e-rafael-31--adultos--casais).
* **Atuação do BSBora:** Cálculo determinístico de custo por participante e acompanhamento do saldo do teto mensal.

### 👵 Idosos & Melhor Idade
* **Foco:** Tranquilidade, contato com a natureza, caminhadas leves, áreas de descanso e boa legibilidade.
* **Persona de Referência:** [Dona Helena (Sobradinho)](personas.md#persona-4-dona-helena-68-anos--idosos--melhor-idade).
* **Atuação do BSBora:** Telas limpas, sem poluição visual, recomendando horários tranquilos e passeios sombreados.

### ♿ Pessoas com Deficiência (PcD)
* **Foco:** Autonomia e segurança física através de acessibilidade comprovada (rampas, piso tátil, banheiros adaptados).
* **Persona de Referência:** [Roberto (Guará)](personas.md#persona-5-roberto-42-anos--pessoas-com-deficiência-pcd).
* **Atuação do BSBora:** Exibe apenas dados auditados; se não houver confirmação oficial, sinaliza *"Não confirmado"*.

---

## 🌐 3. Stakeholders Secundários (Dados e Serviços)

| Stakeholder | Tipo | O que Fornece ao Projeto |
| --- | --- | --- |
| **Setur-DF / Secult-DF** | Órgãos Públicos | Dados oficiais de pontos turísticos, museus e atrativos culturais. |
| **Eventbrite / Sympla** | Plataformas | Agendas de feiras criativas, peças teatrais e eventos temporários no DF. |
| **Semob-DF / Google Routes**| Mobilidade | Itinerários de ônibus, metrô, distâncias e estimativas de tempo/custo. |
| **Open-Meteo / INMET** | Meteorologia | Previsão climática para validação de atividades ao ar livre vs. cobertas. |

---

## ⚖️ 4. Stakeholders Regulatórios e Acadêmicos

* **Mentores e Residência em IA:** Avaliam o rigor técnico, o avanço semanal e a aplicabilidade para *Qualidade de Vida*.
* **ANPD / LGPD:** Garantem a conformidade regulatória. O sistema aplica **coleta mínima** (apenas RA aproximada e teto de gastos; sem extratos).

---

## 📊 5. Matriz de Priorização Rápida

| Stakeholder | Impacto | Influência | Ação Prioritária |
| :--- | :---: | :---: | :--- |
| **Famílias com Crianças** | Alto | Alto | Validar infraestrutura e cálculo conjunto de ingressos/transporte. |
| **Moradores fora do Plano** | Alto | Alto | Garantir passeios descentralizados em todas as RAs no catálogo. |
| **Pessoas com Deficiência** | Alto | Médio | Sinalizar com rigor itens de acessibilidade verificados. |
| **Mentores da Residência** | Alto | Alto | Apresentar entregas semanais conforme o roadmap de 7 semanas. |
| **APIs de Clima e Rotas** | Médio | Médio | Monitorar limites de uso e manter alternativas de contingência. |
| **ANPD (Privacidade)** | Crítico | Regulatório | Não coletar dados bancários ou informações sensíveis. |

---

> [!TIP]
> Para ver os detalhes humanos dos usuários mapeados, consulte [personas.md](personas.md). Para ver as premissas operacionais assumidas pela equipe, consulte [premissas.md](premissas.md).
