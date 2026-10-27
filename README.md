# BSBora

**Seu rolê, seu tempo, seu bolso.**

Proposta de sistema web para ajudar moradores de todo o Distrito Federal a planejar momentos de lazer a partir de seus interesses, dias livres e orçamento mensal. O BSBora combina sugestões personalizadas, calendário de passeios e comparação de custos de transporte para apoiar decisões informadas sobre o tempo livre.

Projeto da **Residência em Inteligência Artificial — Challenge 2**, alinhado à Big Idea **Qualidade de Vida**, com execução planejada em sete semanas.

## Status do projeto

O projeto está em fase de definição e planejamento. Este repositório contém a documentação inicial; ainda não há sistema web ou API implementados. As funcionalidades, tecnologias e metas descritas abaixo são propostas sujeitas à validação da equipe, dos mentores e dos usuários. O nome e o slogan também são provisórios.

O foco atual é desenvolver um **sistema web responsivo**, acessível pelo navegador. O aplicativo mobile é uma ideia de evolução futura, a ser avaliada após o desenvolvimento e a validação da versão web.

## Problema e objetivo

Descobrir passeios, conciliar preferências e horários, estimar deslocamentos e controlar gastos pode dificultar o aproveitamento dos dias livres. O objetivo do BSBora é transformar essas informações em um plano mensal de lazer explicado, viável e compatível com o limite financeiro definido pelo usuário.

**Pergunta norteadora:** como utilizar inteligência artificial para ajudar moradores de todo o Distrito Federal a planejar momentos de lazer personalizados, respeitando sua disponibilidade de tempo e suas limitações financeiras, de modo a favorecer o bem-estar e a qualidade de vida?

O público inicial são moradores do Distrito Federal que buscam passeios de fim de semana, incluindo pessoas sozinhas, casais, famílias e grupos de amigos. A **cobertura inicial definida é todo o Distrito Federal**, abrangendo todas as suas Regiões Administrativas.

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

## Fluxo de uso

1. Informar interesses, região de partida e número de participantes.
2. Definir o orçamento mensal de lazer e, opcionalmente, uma reserva para imprevistos.
3. Marcar dias e períodos livres no calendário.
4. Receber sugestões explicadas e comparar meios de transporte e custos.
5. Aprovar ou substituir passeios e acompanhar o total planejado e o saldo disponível.

## Arquitetura e tecnologias propostas

| Camada | Tecnologia e responsabilidade |
| --- | --- |
| Frontend web | Aplicação web responsiva com calendário e cartões de passeios; framework e tecnologias de interface ainda a definir. |
| API e regras | **Python + FastAPI** para perfis, agenda, custos, validações e orquestração. |
| Dados | **Supabase/PostgreSQL** para perfis, passeios e planos; **pgvector** para a recuperação vetorial do RAG. |
| Inteligência artificial | **LLM + RAG**, com recuperação de informações verificáveis e coordenação de agentes especializados. |
| Serviços externos | Fontes de passeios e serviços de rotas/mapas, escolhidos conforme cobertura, licença, custo e disponibilidade. |

No fluxo técnico proposto, a interface web consulta a API, o motor de IA recupera informações do catálogo por RAG e os serviços calculam trajetos e custos. Regras de negócio validam datas e orçamento antes da apresentação das opções ao usuário.

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

O sistema pretende apoiar organização, autonomia e bem-estar percebido. Não há alegação de prevenção ou tratamento de burnout, nem benefício clínico comprovado.

## Riscos e medidas de mitigação

Os riscos abaixo foram identificados no planejamento do sistema web. As medidas propostas deverão orientar a implementação e os testes; ainda não representam controles implementados ou resultados verificados.

| Risco | Possível impacto | Medidas propostas |
| --- | --- | --- |
| Informações desatualizadas | Recomendar locais fechados, eventos encerrados ou preços e horários incorretos. | Registrar fonte e data de verificação, definir uma rotina de atualização do catálogo e sinalizar informações não confirmadas. |
| Custos subestimados | O gasto real ultrapassar o orçamento por despesas de transporte, alimentação, estacionamento ou cobrança por participante. | Explicitar os itens incluídos e não incluídos, apresentar faixas de estimativa e permitir reserva para imprevistos. |
| Erros de orçamento e agenda | Somar valores incorretamente, duplicar despesas ou sugerir atividades em horários incompatíveis. | Implementar cálculos e validações com regras determinísticas e testes, considerando duração das atividades, deslocamentos e custos por pessoa. |
| Informações inventadas pela IA | Apresentar preços, horários ou condições de acessibilidade sem evidências. | Usar RAG com fontes verificáveis, conferir afirmações factuais e responder que uma informação não pôde ser confirmada quando faltarem evidências. O RAG não elimina esse risco. |
| Cobertura desigual do Distrito Federal | Concentrar sugestões no Plano Piloto e atender de forma insuficiente moradores de outras Regiões Administrativas. | Medir a distribuição do catálogo e a disponibilidade de recomendações por região, incluindo opções gratuitas e deslocamentos viáveis. |
| Exposição de dados pessoais | Revelar localização, rotina, agenda ou orçamento dos usuários. | Coletar o mínimo necessário, usar localização aproximada, restringir acessos aos dados e definir regras de retenção e exclusão. |
| Manipulação dos agentes por conteúdo externo | Instruções maliciosas em páginas ou documentos recuperados alterarem o comportamento da IA, caracterizando um ataque de prompt injection. | Tratar conteúdo externo como dados, limitar as permissões dos agentes e validar suas saídas antes da execução de ações. |
| Dependência e custo de serviços externos | Falhas, limites de uso ou cobranças de serviços de mapas e IA prejudicarem a disponibilidade e a viabilidade do sistema. | Definir limites de consumo, monitorar custos e permitir funcionamento parcial quando uma integração estiver indisponível, informando as limitações ao usuário. |
| Escopo excessivo em sete semanas | Calendário, RAG, agentes e transporte ficarem incompletos ou pouco testados. | Priorizar um fluxo web completo e simples, integrar desde o início e ampliar funcionalidades conforme os resultados. |
| Baixa utilidade e dificuldade de uso | Sugestões repetitivas, pouco relevantes ou uma configuração trabalhosa reduzirem a adoção. | Testar cedo com moradores de diferentes regiões e medir relevância, tempo de planejamento e conclusão de tarefas sem ajuda. |
| Condições climáticas desfavoráveis | Chuva ou outras condições tornarem um passeio ao ar livre inadequado. | Identificar atividades ao ar livre e orientar a conferência das condições perto da data, sem prometer clima favorável. Quando houver integração meteorológica, informar local, atualização e incerteza da previsão e oferecer alternativas. |

A prioridade inicial é garantir dados confiáveis, cálculos corretos e um fluxo web completo. A meta de 30 a 50 passeios deverá ser validada considerando a cobertura de todo o DF. A integração meteorológica permanece como evolução futura.

Referências de apoio: [guia de segurança da informação da ANPD](https://www.gov.br/anpd/pt-br/assuntos/noticias/anpd-publica-guia-de-seguranca-para-agentes-de-tratamento-de-pequeno-porte), para proteção de dados pessoais, e [orientações da OWASP sobre prompt injection](https://github.com/OWASP/www-project-top-10-for-large-language-model-applications/blob/main/2_0_vulns/LLM01_PromptInjection.md), para riscos de manipulação da IA por conteúdo externo.

## Cronograma proposto

| Semana | Foco e entregas planejadas |
| --- | --- |
| 1 | Definição do problema, público, requisitos, riscos e métricas; wireframes e estrutura inicial da aplicação web. |
| 2 | Telas básicas, banco de dados e catálogo inicial, com preparação da base de recuperação. |
| 3 | Implementação do RAG e comparação controlada entre LLM sem recuperação e LLM com RAG. |
| 4 | Orquestração dos agentes e validação das regras de agenda, orçamento e transporte. |
| 5 | Refinamento do assistente por texto e testes das recomendações, explicações e respostas de incerteza. |
| 6 | Integração das telas com a API e execução do fluxo completo no sistema web. |
| 7 | Testes de usabilidade, ajustes, avaliação das métricas e apresentação do protótipo web. |

A entrega planejada inclui **sistema web funcional**, backend acessível, repositório documentado e avaliação das recomendações.

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

- Aplicativo mobile para Android e iOS, após validação da versão web. React Native, Expo e TypeScript são possibilidades registradas no plano mobile, sem adoção definida para esta etapa.
- Integração com Google Calendar, reservas de ingressos, previsão meteorológica e alertas automáticos.
- Importação de despesas bancárias e histórico de preferências.
- Leitura de cartazes e imagens de eventos, com confirmação das informações críticas.
- Expansão para o Entorno e outras cidades.

Essas evoluções dependem de tempo, disponibilidade de dados e consentimento quando aplicável.

## Decisões em aberto

- Priorizar o perfil de usuário para entrevistas e validação.
- Distribuir responsabilidades de dados/RAG, agentes, backend, frontend e avaliação.
- Definir as tecnologias do frontend web.
- Validar o tamanho do catálogo e as fontes de estimativa de cada transporte.
- Verificar licenças, custos e cotas dos serviços de mapas e IA.
- Definir perguntas e cenários de teste desde a primeira semana.

## Documentação

- [Proposta preliminar — Challenge 2](documentos/BSBora_Proposta_Challenge_2.pdf): referência para o sistema web, com contexto, público, experiência de uso, arquitetura, riscos, métricas e pontos a validar.
- [Plano resumido do aplicativo mobile](documentos/BSBora_Plano_Resumido_App_Mobile.pdf): estudo de uma possível evolução futura para mobile; seu cronograma e suas entregas não representam o escopo atual.

As referências a entrada e saída por voz nos PDFs fazem parte das propostas preliminares e foram descartadas do escopo atual.

As instruções de instalação e execução serão adicionadas quando a estrutura do sistema web e da API estiver implementada.
