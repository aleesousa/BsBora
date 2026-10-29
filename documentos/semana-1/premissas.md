# 3. Premissas do Projeto — BSBora

[← Voltar à Semana 1](README.md) · [Mapa de Stakeholders](2-stakeholders.md) · [Personas](personas.md)

**Responsável:** Eduarda (Cientista de Dados) · **Semana:** 1 · **Situação:** Oficial

> **Objetivo:** Registrar as premissas fundamentais (suposições assumidas como verdadeiras) que norteiam o desenvolvimento do BSBora, conectadas diretamente aos stakeholders e às categorias de público atendidas.

---

## 📌 Mapa Conceitual das Premissas

```
┌────────────────────────────────────────────────────────────────────────┐
│                        PREMISSAS DO BSBORA                             │
├─────────────────┬──────────────────┬─────────────────┬─────────────────┤
│  POR CATEGORIA  │  DADOS & RAG     │    OPERAÇÃO     │   PRIVACIDADE   │
│ • Crianças      │ • Fontes Ofic.   │ • Clima 5-7d    │ • Coleta Mínima │
│ • Jovens/Adulto │ • Verificação    │ • Rotas Semob   │ • Localiz. RA   │
│ • Idosos / PcD  │ • pgvector       │ • Determinístico│ • Sem Extrato   │
└─────────────────┴──────────────────┴─────────────────┴─────────────────┘
```

---

## 1. Premissas por Categoria de Público

As premissas abaixo garantem que o sistema atenda com equidade a diversidade de moradores do DF:

### 🧒 Crianças & Família
* **Gratuidade e Meia-Entrada:** Assume-se que grande parte dos parques e atrativos culturais públicos do DF possui entrada gratuita ou meia para crianças até certa faixa etária.
* **Infraestrutura Crítica:** Toda recomendação `familia` assume a necessidade prioritária de banheiros, segurança e opções de alimentação próximas.
* **Vulnerabilidade Climática:** Famílias com crianças são as mais sensíveis a chuvas repentinas; o sistema prioriza locais cobertos quando a probabilidade de chuva for alta.

### 🎓 Jovens & Estudantes
* **Dependência de Transporte Público:** Assume-se que grande parte dos estudantes depende de ônibus ou metrô; o custo e o horário de retorno são fatores decisivos.
* **Cultura Viva e Espaços Livres:** Jovens priorizam eventos alternativos, feiras criativas e parques públicos com custo zero ou simbólico.

### 💼 Adultos & Casais
* **Planejamento Mensal Consciente:** Adultos buscam conciliar compromissos profissionais e momentos de lazer a dois, exigindo previsibilidade de saldo mensal.
* **Divisão de Custos:** Assume-se que os custos do passeio são compartilhados, exigindo cálculo determinístico claro de custo total e per capita.

### 👵 Idosos & Melhor Idade
* **Conforto e Usabilidade:** Idosos priorizam passeios com áreas de sombra, bancos para descanso, caminhadas leves e baixo ruído.
* **Simplicidade Visual:** A interface deve ser direta e legível, sem formulários cansativos ou sobrecarga de informações.

### ♿ Pessoas com Deficiência (PcD)
* **Tolerância Zero para Informação Duvidosa:** Acessibilidade não pode ser estimada por IA; se o local não comprovar rampa e banheiro adaptado na fonte, o sistema **deve** avisar que a condição não foi confirmada.
* **Autonomia e Dignidade:** As recomendações para PcD assumem que a pessoa deseja ter previsibilidade total antes de sair de casa.

---

## 2. Premissas de Dados e Catálogo (RAG)

* **Disponibilidade de Dados Públicos:** Assume-se que o Distrito Federal possui ampla oferta de eventos e atrativos públicos documentados em portais governamentais (Setur-DF, Secult-DF, Dados Abertos).
* **Curadoria Factual (Meta ≥ 95%):** Nenhuma informação de horário ou preço será inventada pela LLM. Se faltar evidência, o campo é explicitamente marcado como "não confirmado".
* **Base Demo Inicial:** A base inicial de 30 a 50 passeios cobrirá equilibradamente o Plano Piloto e as demais Regiões Administrativas (Ceilândia, Taguatinga, Guará, Sobradinho, etc.).

---

## 3. Premissas Técnicas, Mobilidade e Clima

* **Precisão Meteorológica:** Assume-se que previsões meteorológicas de 5 a 7 dias (via API Open-Meteo / INMET) possuem confiabilidade suficiente para classificar passeios abertos vs. cobertos.
* **Estimativas de Deslocamento:** Fórmulas paramétricas simples (tarifa oficial de ônibus e consumo médio km/litro para carro) são aproximações suficientes e válidas para o protótipo.
* **Cálculos Determinísticos (100% Exatos):** O saldo orçamentário e a soma dos custos nunca são delegados à inteligência artificial criativa; rodam sempre via código Python/JS.

---

## 4. Premissas de Governança e Privacidade (LGPD)

* **Coleta Mínima Estrita:** O sistema não necessita de extrato bancário, CPF ou dados financeiros sensíveis.
* **Localização Aproximada:** Apenas a Região Administrativa (RA) de partida declarada pelo usuário é necessária para estimar o trajeto.
* **Transparência com o Cidadão:** O usuário sempre saberá a fonte da informação, a data de verificação e a justificativa de cada sugestão de passeio.

---

## 📊 Matriz de Rastreabilidade (Premissa ➔ Stakeholder ➔ Entrega)

| Premissa | Stakeholder Impactado | Como o BSBora cumpre |
| :--- | :--- | :--- |
| **Passeios Acessíveis Auditados** | PcD (Roberto) / Idosos (D. Helena) | Filtro de acessibilidade com selo de verificação oficial. |
| **Previsão Climática Integrada** | Famílias com Crianças (Marcos) | Agente de clima alerta risco de chuva e sugere locais cobertos. |
| **Rotas de Transporte Público** | Jovens e Estudantes (Beatriz) | Cruzamento com linhas e tarifas da Semob. |
| **Respeito Estrito ao Teto Mensal**| Adultos e Casais (Camila & Rafael) | Algoritmo determinístico de teto e saldo restante. |
| **Coleta Mínima e Ética** | ANPD / Reguladores | Zero solicitação de dados bancários ou confidenciais. |
