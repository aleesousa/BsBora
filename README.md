# BSBora

**Seu rolê, seu tempo, seu bolso.**

## O que é o BSBora, em poucas palavras

O BSBora é um **site** que ajuda moradores do Distrito Federal a planejar os passeios do mês:

1. Você diz **do que gosta**, **quais dias tem livres** e **quanto pode gastar**.
2. O sistema **sugere passeios** e explica por que escolheu cada um.
3. Ele mostra **quanto vai custar** (incluindo o transporte) e **quanto sobra** do seu orçamento.

Projeto da **Residência em Inteligência Artificial — Challenge 2**, alinhado à Big Idea **Qualidade de Vida**.

> **Status:** fase de definição e planejamento. Ainda não há código implementado. Tudo o que está descrito aqui é **proposta**, sujeita à validação da equipe, dos mentores e dos usuários. O nome e o slogan também são provisórios.

**Foco:** o projeto será um **sistema web** (abre no navegador do computador ou do celular). O aplicativo mobile fica apenas como **plano de backup / evolução futura**.

---

## Sumário

- [Equipe](#equipe)
- [Glossário para iniciantes](#glossário-para-iniciantes)
- [Problema e objetivo](#problema-e-objetivo)
- [Plano do protótipo](#plano-do-protótipo)
- [Funcionalidades planejadas](#funcionalidades-planejadas)
- [Fluxo de uso](#fluxo-de-uso)
- [Arquitetura e tecnologias propostas](#arquitetura-e-tecnologias-propostas)
- [Dados, estimativas e cuidados](#dados-estimativas-e-cuidados)
- [Riscos e métricas](#riscos-e-métricas)
- [Cronograma (roadmap do Challenge)](#cronograma-roadmap-do-challenge)
- [Evoluções futuras](#evoluções-futuras)
- [Decisões em aberto](#decisões-em-aberto)
- [Documentação](#documentação)

---

## Equipe

| Papel | Pessoa |
| --- | --- |
| Cientista de dados | Eduarda |
| MLOps | Breno |
| Engenheira de software | Larissa |
| A definir | Isabel |

---

## Glossário para iniciantes

| Termo | O que significa |
| --- | --- |
| **MVP / protótipo** | A versão mais simples do sistema que já funciona e pode ser demonstrada. |
| **Frontend** | A parte que o usuário vê e usa: telas, botões, formulários. |
| **Backend / API** | A parte "por trás" que recebe os pedidos do site, faz cálculos e acessa o banco de dados. |
| **Banco de dados** | Onde ficam guardadas as informações (usuários, passeios, planos). |
| **Supabase** | Serviço pronto que oferece banco de dados (PostgreSQL) e login de usuários. |
| **LLM** | Modelo de linguagem, a "IA que escreve texto" (ex.: Claude, GPT). |
| **RAG** | Técnica em que a IA primeiro **busca informações em uma base confiável** (o catálogo de passeios) e só depois responde. Reduz respostas inventadas. |
| **Agentes** | Partes da IA com tarefas específicas (ex.: um cuida do orçamento, outro do transporte) que trabalham juntas. |
| **Regras determinísticas** | Cálculos feitos por código comum (somas, limites, datas), sem IA, para garantir que o resultado está sempre certo. |

---

## Problema e objetivo

Descobrir passeios, conciliar preferências e horários, estimar deslocamentos e controlar gastos pode dificultar o aproveitamento dos dias livres. O objetivo do BSBora é transformar essas informações em um plano mensal de lazer explicado, viável e compatível com o limite financeiro definido pelo usuário.

**Pergunta norteadora:** como utilizar inteligência artificial para ajudar moradores de todo o Distrito Federal a planejar momentos de lazer personalizados, respeitando sua disponibilidade de tempo e suas limitações financeiras, de modo a favorecer o bem-estar e a qualidade de vida?

**Público:** moradores do Distrito Federal que buscam passeios de fim de semana, incluindo pessoas sozinhas, casais, famílias e grupos de amigos.

**Cobertura:** **todo o Distrito Federal**, abrangendo todas as suas Regiões Administrativas.

---

## Plano do protótipo

O projeto segue o roadmap de **7 semanas** do Challenge (ver [cronograma](#cronograma-roadmap-do-challenge)). Dentro dele, a construção vai do **mais fácil para o mais difícil**. A ideia é ter algo funcionando cedo e ir melhorando. Esta divisão é uma proposta e deve ser validada pela equipe.

### 🟢 Fácil: base do protótipo (entra com certeza)

- Telas em **HTML + JavaScript simples**: perfil e preferências, lista de passeios em cartões e resumo do plano.
- **Catálogo inicial** de passeios do DF (começando pequeno e crescendo até a meta de 30 a 50).
- **Filtro por categoria** (ex.: cultura, natureza, gastronomia) e por região.
- Etiquetas no catálogo: **adequado para crianças** e **ao ar livre / coberto** (para lembrar o usuário de conferir o clima).
- **Cálculo do orçamento** com regras determinísticas: total planejado e saldo restante.

### 🟡 Médio: deixa o protótipo completo (meta da entrega)

- **Login e banco de dados com Supabase:** o usuário entra, e suas escolhas ficam salvas e passam a filtrar as categorias sugeridas.
- **Agenda simples** para marcar dias e períodos livres.
- **Estimativa de transporte** por fórmula simples (ex.: carro = distância × consumo × combustível; ônibus = tarifa), com aviso de "estimativa".
- **API em Python + FastAPI** ligando as telas ao banco de dados.

### 🔴 Difícil: se der tempo (ou versão mínima)

- **Assistente de IA com RAG**, explicando as sugestões com base no catálogo.
- **Orquestração de sistema multiagentes:** 5 agentes especializados (lazer/eventos, mobilidade, clima via API, financeiro, planejador) reportando para um agente principal orquestrador.
- **Agentes lendo dados de APIs** (mapas e rotas, previsão de clima, fontes de passeios), cada agente com sua integração.

> **Fica para depois:** aplicativo mobile e as demais [evoluções futuras](#evoluções-futuras). Voz está fora do escopo.

---

## Funcionalidades planejadas

| Módulo | Escopo previsto |
| --- | --- |
| Perfil e preferências | Interesses, região de partida aproximada, quantidade de participantes e teto mensal de lazer. Preferências opcionais de acessibilidade e duração máxima do deslocamento. |
| Agenda mensal | Seleção de dias e períodos livres, com inclusão, edição, exclusão e substituição de passeios. |
| Recomendações | Catálogo curado de passeios no Distrito Federal, com sugestões compatíveis com o perfil, justificativas e fontes identificáveis. |
| Transporte | Comparação de custos estimados de ida e volta por ônibus, carro e transporte por aplicativo, mostrando total e custo por pessoa. |
| Orçamento | Cálculo dos gastos planejados e do saldo restante, com possibilidade de reserva para imprevistos e validação do teto mensal. |
| Assistente de IA | Consultas e respostas por texto, com explicação das sugestões e apresentação de alternativas. |
| Transparência | Identificação de fontes, data de verificação, hipóteses de cálculo e informações não confirmadas. |

A meta inicial sugerida para o catálogo é de **30 a 50 passeios**, condicionada à disponibilidade de dados confiáveis.

A interação com o assistente será exclusivamente por texto. Entrada e saída por voz estão fora do escopo do projeto.

---

## Fluxo de uso

1. Informar interesses, região de partida e número de participantes.
2. Definir o orçamento mensal de lazer e, opcionalmente, uma reserva para imprevistos.
3. Marcar dias e períodos livres no calendário.
4. Receber sugestões explicadas e comparar meios de transporte e custos.
5. Aprovar ou substituir passeios e acompanhar o total planejado e o saldo disponível.

---

## Arquitetura e tecnologias propostas

```
[ Site (HTML + JS) ]  →  [ API Python/FastAPI ]  →  [ Supabase: banco + login ]
                                   ↓
                     [ IA: LLM + RAG + agentes ]  →  [ Mapas / fontes de passeios ]
```

| Camada | Tecnologia e responsabilidade |
| --- | --- |
| Frontend web | **HTML + JavaScript simples** no início, com possibilidade de evoluir para um framework se o projeto crescer. Telas responsivas com calendário e cartões de passeios. |
| API e regras | **Python + FastAPI** para perfis, agenda, custos, validações e orquestração. |
| Dados | **Supabase/PostgreSQL** para login, perfis, passeios e planos; **pgvector** para a recuperação vetorial do RAG. |
| Inteligência artificial | **LLM + RAG**, com recuperação de informações verificáveis e coordenação de agentes especializados. |
| Serviços externos | Fontes de passeios e serviços de rotas/mapas, escolhidos conforme cobertura, licença, custo e disponibilidade. |

No fluxo técnico proposto, a interface web consulta a API, o motor de IA recupera informações do catálogo por RAG e os serviços calculam trajetos e custos. Regras de negócio validam datas e orçamento antes da apresentação das opções ao usuário.

### Papéis dos agentes (Semana 5)

O sistema conta com **5 agentes especializados que reportam para um agente principal**, responsável por gerar a resposta final personalizada ao usuário:

- **Agente Principal (Orquestrador):** recebe as preferências e restrições do usuário, distribui as demandas para os especialistas, consolida os resultados e formula o roteiro final personalizado e justificado.
- **Lazer e Eventos:** recupera passeios e eventos do catálogo curado (RAG com `pgvector`), validando categorias (incluindo rotinas para famílias com crianças), horários, preços e regras de visitação.
- **Mobilidade:** consulta distâncias e rotas para estimar custos e opções de deslocamento (ônibus, carro, aplicativo).
- **Clima:** consome uma **API de previsão do tempo** para checar as condições climáticas nas datas planejadas e avaliar a viabilidade de passeios abertos ou cobertos.
- **Financeiro:** valida o cumprimento estrito do teto orçamentário mensal, custos por participante, reserva de imprevistos e saldo restante (regras determinísticas).
- **Planejador:** aloca os passeios nos dias e turnos livres marcados na agenda mensal, propondo substituições viáveis.

Somas, limites financeiros e validações de datas devem ser implementados com **regras determinísticas e testes**. A IA apoia a recuperação, a interpretação e a explicação das opções.

---

## Dados, estimativas e cuidados

- Priorizar fontes verificáveis, como portais oficiais de turismo e cultura do DF, páginas dos atrativos, dados abertos e operadores de transporte.
- Mostrar a origem e a data de verificação das informações, considerando que preços, horários e itinerários podem mudar.
- Para carro, considerar distância de ida e volta, consumo, combustível, estacionamento e pedágios quando aplicáveis.
- Para ônibus, considerar tarifas, embarques e integração quando houver dados disponíveis.
- Para transporte por aplicativo, apresentar faixas **não oficiais**, sem depender de cotação oficial da Uber ou de eventos em tempo real no MVP.
- Exibir “estimativa indisponível” quando faltarem dados confiáveis.
- Usar localização aproximada e coleta mínima de dados; renda e extratos bancários ficam fora do MVP.
- Respeitar o teto definido pelo usuário, oferecendo opções gratuitas ou próximas quando o saldo estiver baixo, sem incentivar endividamento.

O sistema pretende apoiar organização, autonomia e bem-estar percebido. Não há alegação de prevenção ou tratamento de burnout, nem benefício clínico comprovado.

---

## Riscos e métricas

Para manter este README curto, os detalhes estão em arquivos separados:

- **[Riscos e medidas de mitigação](documentos/semana-1/3-riscos.md):** 11 riscos mapeados (informações desatualizadas, custos subestimados, IA inventando dados, privacidade, escopo excessivo, entre outros), cada um com seu impacto e as medidas propostas.
- **[Métricas e avaliação planejada](documentos/semana-1/4-metricas.md):** metas como 100% de respeito ao orçamento e aos dias livres, ≥ 95% de afirmações com fonte e satisfação média ≥ 4/5.

---

## Cronograma (roadmap do Challenge)

O cronograma segue o roadmap oficial do Challenge 2, com **7 semanas**. Cada semana tem um entregável principal.

| Semana | Foco (slide) | Entregável principal | No BSBora |
| --- | --- | --- | --- |
| 1 | Problema, stakeholders, riscos e métricas | Definições do projeto | [Documentos da Semana 1](documentos/semana-1/README.md) e wireframes. |
| 2 | Base de conhecimento e recuperação | Primeiro mecanismo RAG | Catálogo inicial no Supabase com pgvector e telas básicas. |
| 3 | Comparação LLM x RAG | Respostas baseadas em evidências | Mesmo conjunto de perguntas para o LLM com e sem RAG. |
| 4 | Sistema multiagentes | Primeiro sistema multiagentes | Estruturação inicial dos agentes e regras de negócio determinísticas. |
| 5 | Multimodalidade / Multiagentes | Sistema multiagentes completo | 5 agentes especializados (lazer/eventos, mobilidade, clima via API, financeiro, planejador) reportando ao agente principal orquestrador. |
| 6 | Integração completa | Aplicação funcional | Telas, API e IA no fluxo completo do sistema web. |
| 7 | Testes e refinamento | Relatório final + apresentação | Testes de usabilidade, avaliação das métricas e apresentação. |

A entrega planejada inclui **sistema web funcional**, backend acessível, repositório documentado e avaliação das recomendações.

---

## Evoluções futuras

- Aplicativo mobile para Android e iOS, após validação da versão web. React Native, Expo e TypeScript são possibilidades registradas no plano mobile, sem adoção definida para esta etapa.
- Alertas em tempo real de mudança de tempo com sugestão de troca automática do passeio.
- Filtros detalhados de faixa etária e preços específicos/gratuidade infantil por atrativo.
- Integração com Google Calendar e reservas de ingressos.
- Importação de despesas bancárias e histórico de preferências.
- Leitura de cartazes e imagens de eventos, com confirmação das informações críticas.
- Expansão para o Entorno e outras cidades.

Essas evoluções dependem de tempo, disponibilidade de dados e consentimento quando aplicável.

---

## Decisões em aberto

- Priorizar o perfil de usuário para entrevistas e validação.
- Distribuir responsabilidades de dados/RAG, agentes, backend, frontend e avaliação. **Parcialmente decidido:** papéis definidos na seção [Equipe](#equipe); falta definir o papel da Isabel.
- ~~Definir as tecnologias do frontend web.~~ **Decidido:** HTML + JavaScript simples no início, com evolução possível.
- Validar o tamanho do catálogo e as fontes de estimativa de cada transporte.
- Verificar licenças, custos e cotas dos serviços de mapas e IA.
- Definir perguntas e cenários de teste desde a primeira semana.
- Definir as APIs de cada agente (mapas e rotas, clima, fontes de passeios).
- Validar com os mentores a interpretação da multimodalidade (Semana 5) sem voz.

---

## Documentação

- [Proposta preliminar — Challenge 2](documentos/BSBora_Proposta_Challenge_2.pdf): referência para o sistema web, com contexto, público, experiência de uso, arquitetura, riscos, métricas e pontos a validar.
- [Plano resumido do aplicativo mobile](documentos/BSBora_Plano_Resumido_App_Mobile.pdf): estudo de uma possível evolução futura (backup); seu cronograma e suas entregas não representam o escopo atual.
- [Semana 1 — Definições do projeto](documentos/semana-1/README.md): problema, requisitos, stakeholders, riscos e métricas.
- [Riscos e medidas de mitigação](documentos/semana-1/3-riscos.md)
- [Métricas e avaliação planejada](documentos/semana-1/4-metricas.md)

As referências a entrada e saída por voz nos PDFs fazem parte das propostas preliminares e foram descartadas do escopo atual.

As instruções de instalação e execução serão adicionadas quando a estrutura do sistema web e da API estiver implementada.
