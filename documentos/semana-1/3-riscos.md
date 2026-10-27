# Riscos e medidas de mitigação — BSBora

[← Voltar à Semana 1](README.md) · [README do projeto](../../README.md)

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

A prioridade inicial é garantir dados confiáveis, cálculos corretos e um fluxo web completo. A meta de 30 a 50 passeios deverá ser validada considerando a cobertura de todo o DF. A integração com API de clima será realizada pelo Agente de Clima como parte do desenvolvimento do sistema multiagentes.

Referências de apoio: [guia de segurança da informação da ANPD](https://www.gov.br/anpd/pt-br/assuntos/noticias/anpd-publica-guia-de-seguranca-para-agentes-de-tratamento-de-pequeno-porte), para proteção de dados pessoais, e [orientações da OWASP sobre prompt injection](https://github.com/OWASP/www-project-top-10-for-large-language-model-applications/blob/main/2_0_vulns/LLM01_PromptInjection.md), para riscos de manipulação da IA por conteúdo externo.
