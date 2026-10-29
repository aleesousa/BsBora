# Personas do Projeto — BSBora

[← Voltar à Semana 1](README.md) · [Mapa de Stakeholders](2-stakeholders.md) · [Premissas](premissas.md)

**Responsável:** Eduarda (Cientista de Dados) · **Semana:** 1 · **Situação:** Oficial

> **Objetivo:** Representar em arquétipos humanos reais os diferentes públicos de Brasília, cobrindo todas as categorias centrais do projeto: **crianças/famílias**, **jovens**, **adultos/casais**, **idosos** e **pessoas com deficiência (PcD)**.

---

## 🎯 Visão Geral das Personas

```
┌────────────────────────────────────────────────────────────────────────┐
│                        ARQUÉTIPOS DE USUÁRIOS                          │
├──────────────┬──────────────┬──────────────┬─────────────┬─────────────┤
│   FAMÍLIA    │    JOVENS    │   ADULTOS    │   IDOSOS    │    PcD      │
│  👶 Marcos   │  🎓 Beatriz  │ 💼 C. & R.   │ 👵 D. Helena│ ♿ Roberto   │
│ (Ceilândia)  │ (Asa Norte)  │  (Guará/AC)  │ (Sobradinho)│   (Guará)   │
└──────────────┴──────────────┴──────────────┴─────────────┴─────────────┘
```

---

## 🧒 Persona 1: Marcos (34 anos) — Família & Crianças
> *"Quero que meu filho tenha fins de semana incríveis sem que isso comprometa o aluguel do mês."*

* **Perfil:** Técnico de suporte e pai solo. Mora em **Ceilândia** com seu filho Enzo (7 anos).
* **Rotina & Orçamento:** Orçamento financeiro apertado; tempo livre estritamente nos fins de semana.
* **Objetivos:**
  * Encontrar parques, oficinas infantis, feiras e passeios culturais gratuitos ou baratos no DF.
  * Garantir passeios seguros, divertidos e com estrutura para crianças.
* **Dores:**
  * Falta de tempo para pesquisar opções adequadas.
  * Incerteza se o local tem banheiros limpos, segurança e opções acessíveis de alimentação.
  * Medo de chuvas repentinas estragarem passeios em áreas abertas.
* **Como o BSBora ajuda:**
  * Filtra opções na categoria `familia` com infraestrutura adequada.
  * Checa a previsão do tempo via API de clima para evitar passeios abertos em dias de chuva.
  * Calcula custos totais (transporte + ingressos) a partir de Ceilândia.

---

## 🎓 Persona 2: Beatriz (22 anos) — Jovens & Estudantes
> *"Quero viver a cultura de Brasília sem gastar o que não tenho e sem ficar ilhada na volta para casa."*

* **Perfil:** Estudante de Comunicação na UnB e estagiária. Mora na **Asa Norte** e depende 100% de transporte público (ônibus e metrô).
* **Rotina & Orçamento:** Orçamento muito restrito; busca descompressão e autocuidado entre as aulas e o estágio.
* **Objetivos:**
  * Descobrir feiras criativas, saraus, teatro independente, oficinas e eventos alternativos.
  * Aproveitar espaços públicos com amigos sem custos elevados.
* **Dores:**
  * Eventos culturais alternativos ficam dispersos em múltiplos perfis de redes sociais.
  * Medo de não ter ônibus ou metrô para voltar tarde da noite.
  * Gastos imprevistos com transporte por aplicativo que estouram o mês.
* **Como o BSBora ajuda:**
  * Centraliza eventos do catálogo e plataformas integradas (Eventbrite/Setur).
  * Cruza a localização do evento com as linhas de transporte público da Semob.
  * Garante roteiros 100% compatíveis com um teto orçamentário estudantil.

---

## 💼 Persona 3: Camila (29) e Rafael (31) — Adultos & Casais
> *"Nosso objetivo é ter momentos de lazer a dois todo fim de semana, com previsibilidade financeira."*

* **Perfil:** Analista de RH e Desenvolvedor Júnior. Moram em **Águas Claras**.
* **Rotina & Orçamento:** Renda estável, mas com meta rígida de economia para comprar um imóvel.
* **Objetivos:**
  * Conhecer novos cafés, trilhas ecológicas, exposições no CCBB e experiências gastronômicas com bom custo-benefício.
  * Distribuir os passeios pelos 4 fins de semana do mês com equilíbrio.
* **Dores:**
  * Dificuldade de controlar os gastos somados do casal ao longo das semanas.
  * Monotonia de ir sempre aos mesmos locais por falta de planejamento prévio.
* **Como o BSBora ajuda:**
  * Agente financeiro calcula o gasto por pessoa e o saldo restante do teto mensal.
  * Agente planejador distribui os eventos nos fins de semana livres marcados na agenda.

---

## 👵 Persona 4: Dona Helena (68 anos) — Idosos & Melhor Idade
> *"Procuro tranquilidade, passeios agradáveis durante o dia e locais onde eu possa caminhar com segurança."*

* **Perfil:** Professora aposentada, moradora de **Sobradinho**. Vive com seu marido.
* **Rotina & Orçamento:** Dias de semana e fins de semana disponíveis; prioriza conforto, segurança e socialização.
* **Objetivos:**
  * Fazer caminhadas matinais em parques ecológicos, visitar museus e feiras de artesanato com calma.
  * Passeios com sombra, bancos para descanso e fácil acesso a sanitários.
* **Dores:**
  * Dificuldade em navegar em sistemas complexos ou com excesso de propagandas.
  * Falta de informações claras sobre acessibilidade para quem tem mobilidade reduzida por idade.
  * Atrativos com trânsito confuso ou estacionamento muito distante.
* **Como o BSBora ajuda:**
  * Interface web limpa, com cartões simples e de fácil leitura.
  * Recomendações de horários mais tranquilos e passeios arborizados/estruturados.
  * Detalhamento claro de distâncias e pontos de apoio no local.

---

## ♿ Persona 5: Roberto (42 anos) — Pessoas com Deficiência (PcD)
> *"Não aceito surpresas de acessibilidade. Preciso saber antes se o lugar me respeita como cidadão."*

* **Perfil:** Analista de sistemas e usuário de cadeira de rodas motorizada. Mora no **Guará**.
* **Rotina & Orçamento:** Ativo, sociável e financeiramente independente. Gosta de artes visuais, gastronomia e parques.
* **Objetivos:**
  * Explorar a vida cultural de Brasília com plena autonomia, segurança e dignidade.
  * Confirmar de antemão a existência de rampas adequadas, piso nivelado, elevadores e banheiros adaptados.
* **Dores:**
  * Informações de acessibilidade na internet são genéricas, desatualizadas ou falsas ("acessível", mas com 3 degraus na porta).
  * Chegar ao destino e ser obrigado a voltar para casa por falta de infraestrutura física.
* **Como o BSBora ajuda:**
  * Exibe **apenas dados de acessibilidade verificados e auditados** no catálogo.
  * Caso o atrativo não confirme acessibilidade na fonte oficial, o BSBora avisa explicitamente: *"Condição de acessibilidade não confirmada"*.
  * Sugere trajetos planos e locais com vagas reservadas garantidas.

---

## 📊 Matriz Comparativa das Personas

| Persona | Categoria Principal | Região (RA) | Foco Central | Principal Restrição |
| --- | :--- | :--- | :--- | :--- |
| **Marcos** | Família / Crianças | Ceilândia | Custo total e infraestrutura infantil | Orçamento apertado e tempo livre |
| **Beatriz** | Jovens / Estudantes | Asa Norte | Cultura alternativa e autocuidado | Renda de estágio e transporte público |
| **Camila & Rafael**| Adultos / Casal | Águas Claras | Variedade e planejamento mensal | Teto rígido de poupança |
| **Dona Helena** | Idosos / Melhor Idade | Sobradinho | Conforto, natureza e tranquilidade | Mobilidade física e usabilidade simples |
| **Roberto** | PcD / Mobilidade Red. | Guará | Autonomia cultural e acessibilidade | Barreiras arquitetônicas |
