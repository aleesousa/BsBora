# 2.5 Personas | Públicos do BSBora

[← Voltar à Semana 1](README.md) · [Mapa de Stakeholders](2-stakeholders.md)

**Responsável:** Eduarda (Cientista de Dados) · **Semana:** 1 · **Situação:** Oficial (Alinhado ao Google Docs)

> **Objetivo:** Perfis representativos dos moradores do Distrito Federal para orientar o desenvolvimento e validar requisitos. Cobrem **10 Regiões Administrativas** e todas as categorias centrais: famílias, jovens, adultos, idosos, PcD, trabalhadores por turno e grupos de amigos.

---

## ⚡ Tabela Rápida das 10 Personas

| # | Persona | Perfil & RA | Objetivo e Dificuldade | Como o BSBora Responde |
| :---: | :--- | :--- | :--- | :--- |
| **01** | **Marcos** (34) | Pai solo • Ceilândia | Lazer infantil barato. Pouco tempo; infraestrutura e custos incertos. | Filtrar por faixa etária e categoria `familia`. Estimar transporte e gastos totais. |
| **02** | **Beatriz** (22) | Estudante • Asa Norte | Feiras, saraus e oficinas. Eventos dispersos; retorno de ônibus difícil. | Reunir eventos culturais alternativos e cruzar com rotas de transporte público. |
| **03** | **Roberto** (42) | Cadeirante • Guará | Lazer cultural com autonomia. Acessibilidade mal documentada na internet. | Mostrar apenas rampas, banheiros e vagas com confirmação oficial na fonte. |
| **04** | **Helena** (67) | Aposentada • Taguatinga | Passeios culturais tranquilos. Dificuldade com apps complexos e caminhadas longas. | Roteiros com trajetos simples, pausas, sombras e informações claras de acesso. |
| **05** | **Camila e Rafael** (29/31) | Casal • Águas Claras | Lazer a dois após o trabalho. Agenda apertada e preços pouco claros. | Sugerir passeios por horário livre, custo total do casal e distância viável. |
| **06** | **Júlia** (26) | Grupo de amigos • Samambaia | Encontros em grupo no DF. Preferências diferentes e divisão de despesas. | Filtrar atividades coletivas, sugerir ponto de encontro e calcular custo por pessoa. |
| **07** | **Paulo** (45) | Turnos alternativos • Planaltina | Busca lazer em horários atípicos (folgas durante a semana). Poucas opções próximas. | Filtrar por período livre específico, proximidade geográfica e custo total. |
| **08** | **Ana** (38) | Mãe de adolescente • Recanto das Emas | Conciliar lazer para diferentes idades. Ingressos e deslocamento pesam no bolso. | Comparar preço por pessoa, opções gratuitas e atrativos multigeracionais. |
| **09** | **Lúcia** (52) | Baixa visão • Sobradinho | Cultura com autonomia. Informações visuais e orientação de acesso limitadas. | Interface com textos legíveis, alto contraste e dados confirmados de acessibilidade. |
| **10** | **Diego** (19) | Jovem aprendiz • Gama | Esportes e eventos gratuitos. Depende 100% de ônibus e tem renda muito baixa. | Priorizar passeios com custo zero e rotas diretas de transporte público. |

---

## 🎯 Detalhamento dos Arquétipos por Categoria

### 🧒 Crianças & Família

* **Marcos (34 anos) — Ceilândia (Pai Solo):**
  * *Contexto:* Vive com seu filho Enzo (7 anos). Orçamento apertado e tempo livre restrito aos fins de semana.
  * *Dores:* Medo de chuva estragar passeios abertos; falta de tempo para pesquisar; incerteza sobre sanitários infantis e segurança.
  * *Solução:* Filtro `familia` com infraestrutura checada e agente de clima alertando sobre chuva.

* **Ana (38 anos) — Recanto das Emas (Mãe de Adolescente):**
  * *Contexto:* Precisa conciliar o lazer de uma filha de 14 anos e um filho de 6 anos.
  * *Dores:* O que diverte a criança entedia a adolescente; custos de ingressos multiplicados por 3 pesam muito.
  * *Solução:* Comparativo de custo por pessoa e indicação de parques e centros culturais híbridos.

---

### 🎓 Jovens & Vida Cultural

* **Beatriz (22 anos) — Asa Norte (Estudante UnB / Estagiária):**
  * *Contexto:* Depende de transporte público e busca cultura alternativa, feiras e saraus.
  * *Dores:* Informações dispersas em redes sociais e medo de ficar sem transporte tarde da noite.
  * *Solução:* Agrupamento de eventos temporários integrado a rotas seguras de ônibus e metrô.

* **Diego (19 anos) — Gama (Jovem Aprendiz):**
  * *Contexto:* Renda inicial de aprendiz; busca rolês esportivos, parques e encontros ao ar livre.
  * *Dores:* Qualquer gasto acima de R$ 20 compromete a semana; distância do Gama até a área central.
  * *Solução:* Filtro rigoroso de gratuidade e destaque para atrativos no próprio Gama ou RAs vizinhas.

---

### 💼 Adultos & Socialização em Grupo

* **Camila (29) e Rafael (31) — Águas Claras (Casal):**
  * *Contexto:* Vida profissional ativa; querem descompressão aos fins de semana sem estourar o orçamento doméstico.
  * *Dores:* Monotonia de ir sempre aos mesmos locais; dificuldade de calcular despesas combinadas com antecedência.
  * *Solução:* Distribuição mensal na agenda e controle determinístico de saldo disponível.

* **Júlia (26 anos) — Samambaia (Organizadora do Grupo de Amigos):**
  * *Contexto:* É quem sempre toma a iniciativa de juntar a turma (5 a 8 amigos).
  * *Dores:* Dificuldade de encontrar um local que agrade quem pode gastar muito e quem está sem dinheiro.
  * *Solução:* Filtros por custo por pessoa e indicação de atrativos com espaços abertos para piqueniques e convivência.

---

### ⏰ Rotinas Flexíveis & Horários Alternativos

* **Paulo (45 anos) — Planaltina (Trabalhador por Turnos):**
  * *Contexto:* Trabalha em escala (12x36 ou plantões noturnos); costuma ter folgas em terças ou quartas-feiras.
  * *Dores:* Muitos museus e parques fecham para manutenção no início da semana; poucas opções perto de Planaltina.
  * *Solução:* Filtro por dia da semana e período específico (manhã/tarde), evitando viagens perdidas a locais fechados.

---

### 👵 Idosos & Melhor Idade

* **Dona Helena (67 anos) — Taguatinga (Aposentada):**
  * *Contexto:* Gosta de passeios culturais, feiras de artesanato e caminhadas pela manhã.
  * *Dores:* Telas com letras pequenas ou difíceis de mexer; cansaço físico em locais sem sombra e sem bancos.
  * *Solução:* Interface com visual limpo e direto, destacando locais planos, arborizados e de fácil circulação.

---

### ♿ Acessibilidade & PcD (Mobilidade e Sensorial)

* **Roberto (42 anos) — Guará (Cadeirante):**
  * *Contexto:* Usuário de cadeira de rodas motorizada, ativo e apreciador de artes e gastronomia.
  * *Dores:* Acessibilidade "no papel" que não existe na prática (degraus ocultos, banheiros trancados ou sem barra).
  * *Solução:* Apenas dados de acessibilidade física auditados em fontes oficiais. Se não houver certeza, o sistema avisa.

* **Lúcia (52 anos) — Sobradinho (Pessoa com Baixa Visão):**
  * *Contexto:* Gosta de música, teatro e passeios ao ar livre, mas precisa de apoio de contraste visual.
  * *Dores:* Páginas web com baixo contraste e falta de informações sonoras ou orientação tátil nos atrativos.
  * *Solução:* Design web compatível com leitores de tela, alto contraste e sinalização de atrativos com audiodescrição.

---

## 🗺️ Cobertura Geográfica das 10 Personas no DF

```
                        [ Planaltina (Paulo) ]
                                 │
                         [ Sobradinho (Lúcia) ]
                                 │
                 ┌───────────────┴───────────────┐
                 ▼                               ▼
       [ Asa Norte (Beatriz) ]        [ Guará (Roberto) ]
                 │                               │
       [ Águas Claras (C. & R.) ]     [ Taguatinga (Helena) ]
                 │                               │
       [ Ceilândia (Marcos) ]         [ Samambaia (Júlia) ]
                 │                               │
       [ Recanto das Emas (Ana) ]     [ Gama (Diego) ]
```
*(Garante 100% de conformidade com a meta de evitar a concentração exclusiva no Plano Piloto).*
