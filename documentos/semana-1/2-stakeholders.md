# 2. Mapa de Stakeholders — BSBora

[← Voltar à Semana 1](README.md) · [Ver Personas](personas.md)

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
   │ • Ingestão de APIs   │       │ • Factualidade ≥95%  │       │ • Regras Determiníst.│       │ • Métricas de Aceite │
   │   (Clima/Transporte) │       │                      │       │ • Orquestração Agente│       │ • Conformidade LGPD  │
   │                      │       │                      │       │                      │       │                      │
   │ ENTREGA:             │       │ ENTREGA:             │       │ ENTREGA:             │       │ ENTREGA:             │
   │ Catálogo Estruturado │       │ Recomendações c/Fonte│       │ Fluxo Web Funcional  │       │ Registro de Aceite   │
   └──────────────────────┘       └──────────────────────┘       └──────────────────────┘       └──────────────────────┘
              ▲                                                                                             │
              └───────────────────────── ↻ CICLO COMPLETO: Alinhar → Testar → Corrigir ─────────────────────┘
                                         (ENTREGA: Versão Final Revisada)
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
* **Personas de Referência:** [Marcos (Ceilândia)](personas.md#01) (pai solo) e [Ana (Recanto das Emas)](personas.md#08) (mãe de adolescente e criança).
* **Atuação do BSBora:** Filtra categoria `familia`, checa previsão de chuva via API de clima e calcula despesas totais.

### 🎓 Jovens & Estudantes
* **Foco:** Vida cultural ativa, feiras criativas, eventos independentes e autocuidado com custo mínimo.
* **Personas de Referência:** [Beatriz (Asa Norte)](personas.md#02) (universitária UnB) e [Diego (Gama)](personas.md#10) (jovem aprendiz).
* **Atuação do BSBora:** Centraliza eventos culturais dispersos e cruza com rotas de transporte público (ônibus/metrô).

### 💼 Adultos, Casais & Grupos
* **Foco:** Variedade de experiências, descompressão, divisão de despesas e horários flexíveis.
* **Personas de Referência:** [Camila & Rafael (Águas Claras)](personas.md#05) (casal), [Júlia (Samambaia)](personas.md#06) (amigos) e [Paulo (Planaltina)](personas.md#07) (turnos).
* **Atuação do BSBora:** Cálculo determinístico de custo por participante, acompanhamento de saldo e filtros por horários específicos.

### 👵 Idosos & Melhor Idade
* **Foco:** Tranquilidade, contato com a natureza, caminhadas leves, áreas de descanso e boa legibilidade.
* **Persona de Referência:** [Dona Helena (Taguatinga)](personas.md#04) (aposentada).
* **Atuação do BSBora:** Telas limpas, sem poluição visual, recomendando horários tranquilos e passeios sombreados e planos.

### ♿ Pessoas com Deficiência (PcD - Física e Sensorial)
* **Foco:** Autonomia e segurança com acessibilidade comprovada (rampas, banheiros adaptados, alto contraste e audiodescrição).
* **Personas de Referência:** [Roberto (Guará)](personas.md#03) (cadeirante) e [Lúcia (Sobradinho)](personas.md#09) (baixa visão).
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
> Para ver os detalhes e arquétipos dos usuários mapeados, consulte o catálogo de [personas.md](personas.md).
