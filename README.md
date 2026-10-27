# BSBora

**Seu rolê, seu tempo, seu bolso.**

Proposta de aplicativo para ajudar moradores de Brasília a planejar momentos de lazer a partir de seus interesses, dias livres e orçamento mensal. O BSBora combina sugestões personalizadas, calendário de passeios e comparação de custos de transporte para apoiar decisões informadas sobre o tempo livre.

Projeto da **Residência em Inteligência Artificial — Challenge 2**, alinhado à Big Idea **Qualidade de Vida**, com execução planejada em sete semanas.

## Status do projeto

O projeto está em fase de definição e planejamento. Este repositório contém a documentação inicial; ainda não há aplicativo ou API implementados. As funcionalidades, tecnologias e metas descritas abaixo são propostas sujeitas à validação da equipe, dos mentores e dos usuários. O nome e o slogan também são provisórios.

A proposta original apresenta uma aplicação web responsiva. O plano mobile adapta essa base para Android e iOS; este README segue essa direção para a implementação planejada.

## Problema e objetivo

Descobrir passeios, conciliar preferências e horários, estimar deslocamentos e controlar gastos pode dificultar o aproveitamento dos dias livres. O objetivo do BSBora é transformar essas informações em um plano mensal de lazer explicado, viável e compatível com o limite financeiro definido pelo usuário.

**Pergunta norteadora:** como utilizar inteligência artificial para ajudar moradores de Brasília a planejar momentos de lazer personalizados, respeitando sua disponibilidade de tempo e suas limitações financeiras, de modo a favorecer o bem-estar e a qualidade de vida?

O público inicial são moradores de Brasília que buscam passeios de fim de semana, incluindo pessoas sozinhas, casais, famílias e grupos de amigos. O recorte geográfico dentro do Distrito Federal ainda será definido.

## Funcionalidades planejadas

| Módulo | Escopo previsto |
| --- | --- |
| Perfil e preferências | Interesses, região de partida aproximada, quantidade de participantes e teto mensal de lazer. Preferências opcionais de acessibilidade e duração máxima do deslocamento. |
| Agenda mensal | Seleção de dias e períodos livres, com inclusão, edição, exclusão e substituição de passeios. |
| Recomendações | Catálogo curado de Brasília, com sugestões compatíveis com o perfil, justificativas e fontes identificáveis. |
| Transporte | Comparação de custos estimados de ida e volta por ônibus, carro e transporte por aplicativo, mostrando total e custo por pessoa. |
| Orçamento | Cálculo dos gastos planejados e do saldo restante, com possibilidade de reserva para imprevistos e validação do teto mensal. |
| Assistente de IA | Consulta por texto, explicação das sugestões e apresentação de alternativas. Entrada e saída por voz como evolução priorizada no cronograma. |
| Transparência | Identificação de fontes, data de verificação, hipóteses de cálculo e informações não confirmadas. |

A meta inicial sugerida para o catálogo é de **30 a 50 passeios**, condicionada à disponibilidade de dados confiáveis.

## Fluxo de uso

1. Informar interesses, região de partida e número de participantes.
2. Definir o orçamento mensal de lazer e, opcionalmente, uma reserva para imprevistos.
3. Marcar dias e períodos livres no calendário.
4. Receber sugestões explicadas e comparar meios de transporte e custos.
5. Aprovar ou substituir passeios e acompanhar o total planejado e o saldo disponível.

## Arquitetura e tecnologias propostas

| Camada | Tecnologia e responsabilidade |
| --- | --- |
| Aplicativo | **React Native + Expo + TypeScript** para telas, navegação e calendário em Android e iOS. |
| API e regras | **Python + FastAPI** para perfis, agenda, custos, validações e orquestração. |
| Dados | **Supabase/PostgreSQL** para perfis, passeios e planos; **pgvector** para a recuperação vetorial do RAG. |
| Inteligência artificial | **LLM + RAG**, com recuperação de informações verificáveis e coordenação de agentes especializados. |
| Serviços externos | Fontes de passeios e serviços de rotas/mapas, escolhidos conforme cobertura, licença, custo e disponibilidade. |

No fluxo técnico proposto, o aplicativo consulta a API, o motor de IA recupera informações do catálogo por RAG e os serviços calculam trajetos e custos. Regras de negócio validam datas e orçamento antes da apresentação das opções ao usuário.

### Papéis dos agentes

- **Orquestrador:** divide as tarefas e consolida a resposta.
- **Lazer:** recupera passeios e evidências de horários, preços e regras de visitação.
- **Mobilidade:** consulta rotas e estima alternativas de deslocamento.
- **Financeiro:** verifica o teto mensal, o saldo e o custo por pessoa.
- **Planejador:** combina passeios nos dias livres e propõe substituições.

Somas, limites financeiros e validações de datas devem ser implementados com **regras determinísticas e testes**. A IA apoia a recuperação, a interpretação e a explicação das opções.

## Dados, estimativas e cuidados

- Priorizar fontes verificáveis, como portais oficiais de turismo e cultura do DF, páginas dos atrativos, dados abertos e operadores de transporte.
- Mostrar a origem e a data de verificação das informações, considerando que preços, horários e itinerários podem mudar.
- Para carro, considerar distância de ida e volta, consumo, combustível, estacionamento e pedágios quando aplicáveis.
- Para ônibus, considerar tarifas, embarques e integração quando houver dados disponíveis.
- Para transporte por aplicativo, apresentar faixas **não oficiais**, sem depender de cotação oficial da Uber ou de eventos em tempo real no MVP.
- Exibir “estimativa indisponível” quando faltarem dados confiáveis.
- Usar localização aproximada e coleta mínima de dados; renda e extratos bancários ficam fora do MVP.
- Respeitar o teto definido pelo usuário, oferecendo opções gratuitas ou próximas quando o saldo estiver baixo, sem incentivar endividamento.

O aplicativo pretende apoiar organização, autonomia e bem-estar percebido. Não há alegação de prevenção ou tratamento de burnout, nem benefício clínico comprovado.

## Cronograma proposto

| Semana | Foco e entregas planejadas |
| --- | --- |
| 1 | Definição do problema, público, requisitos, riscos e métricas; wireframes e estrutura inicial do Expo. |
| 2 | Telas básicas, banco de dados e catálogo inicial, com preparação da base de recuperação. |
| 3 | Implementação do RAG e comparação controlada entre LLM sem recuperação e LLM com RAG. |
| 4 | Orquestração dos agentes e validação das regras de agenda, orçamento e transporte. |
| 5 | Interação por voz e testes de multimodalidade. |
| 6 | Integração das telas com a API e execução do fluxo completo no celular. |
| 7 | Testes de usabilidade, ajustes, avaliação das métricas e geração de APK de demonstração. |

A entrega sugerida inclui **APK Android demonstrável**, backend acessível, repositório documentado e avaliação das recomendações. O iOS poderá compartilhar a base de código, mas sua distribuição exige etapas próprias da Apple.

## Avaliação planejada

As metas abaixo são hipóteses iniciais de aceitação e ainda precisam ser revisadas e medidas.

| Indicador | Meta proposta | Forma de avaliação |
| --- | --- | --- |
| Respeito ao orçamento | 100% | Cenários automatizados com diferentes tetos. |
| Respeito aos dias livres | 100% | Testes de datas, horários e conflitos. |
| Afirmações sustentadas por fontes | ≥ 95% | Checagem de uma amostra anotada. |
| Erro de estimativa de transporte | Mediana < 20%, quando houver referência | Comparação com rotas e preços observados. |
| Satisfação | Média ≥ 4/5 | Questionário após tarefas de uso. |
| Diversidade do plano | ≥ 3 categorias, quando viável | Análise dos passeios sugeridos no mês. |

A comparação entre LLM e RAG deve usar o mesmo conjunto de perguntas e avaliar factualidade, suporte das respostas, omissões e respostas indevidas. Ainda não há resultados empíricos registrados.

## Evoluções futuras

- Integração com Google Calendar, reservas de ingressos, previsão meteorológica e alertas automáticos.
- Importação de despesas bancárias e histórico de preferências.
- Leitura de cartazes e imagens de eventos, com confirmação das informações críticas.
- Expansão para o Entorno e outras cidades.

Essas evoluções dependem de tempo, disponibilidade de dados e consentimento quando aplicável.

## Decisões em aberto

- Definir a cobertura inicial: Plano Piloto, Regiões Administrativas selecionadas ou todo o DF.
- Priorizar o perfil de usuário para entrevistas e validação.
- Distribuir responsabilidades de dados/RAG, agentes, backend, frontend e avaliação.
- Validar o tamanho do catálogo e as fontes de estimativa de cada transporte.
- Verificar licenças, custos e cotas dos serviços de mapas e IA.
- Definir perguntas e cenários de teste desde a primeira semana.

## Documentação

- [Plano resumido do aplicativo mobile](documentos/BSBora_Plano_Resumido_App_Mobile.pdf): adaptação técnica para mobile, funcionalidades, cronograma e entrega sugerida.
- [Proposta preliminar — Challenge 2](documentos/BSBora_Proposta_Challenge_2.pdf): contexto, público, experiência de uso, arquitetura, riscos, métricas e pontos a validar.

As instruções de instalação e execução serão adicionadas quando a estrutura do aplicativo e da API estiver implementada.
