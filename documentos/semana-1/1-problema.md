# 1. Problema, público e requisitos — BSBora

[← Voltar à Semana 1](README.md) · [README do projeto](../../README.md)

## O problema

Descobrir passeios, conciliar preferências e horários, estimar deslocamentos e controlar gastos pode dificultar o aproveitamento dos dias livres. Hoje essas informações ficam espalhadas (sites de turismo, redes sociais, aplicativos de transporte, planilhas pessoais), e cada pessoa precisa juntá-las sozinha.

**Pergunta norteadora:** como utilizar inteligência artificial para ajudar moradores de todo o Distrito Federal a planejar momentos de lazer personalizados, respeitando sua disponibilidade de tempo e suas limitações financeiras, de modo a favorecer o bem-estar e a qualidade de vida?

**Ligação com a Big Idea (Qualidade de Vida):** o BSBora apoia a **tomada de decisão** sobre o tempo livre: o que fazer, quando e quanto gastar.

## Público

- Moradores do Distrito Federal que buscam passeios de fim de semana: pessoas sozinhas, casais, famílias (com ou sem crianças) e grupos de amigos.
- **Cobertura:** todo o Distrito Federal, abrangendo todas as Regiões Administrativas.

## Requisitos funcionais

| ID | Requisito | Prioridade |
| --- | --- | --- |
| RF01 | Cadastro e login do usuário (Supabase). | Média |
| RF02 | Perfil com interesses, região de partida aproximada, número de participantes e teto mensal de lazer. | Alta |
| RF03 | Catálogo de passeios do DF com categoria, região, preço, horário, fonte e data de verificação. | Alta |
| RF04 | Filtro por categoria e região, incluindo a categoria de **família / adequado para crianças** e etiqueta **ao ar livre / coberto**. | Alta |
| RF05 | Cálculo do total planejado e do saldo restante, com reserva opcional para imprevistos. | Alta |
| RF06 | Agenda para marcar dias e períodos livres. | Média |
| RF07 | Estimativa de custo de transporte (ônibus, carro e aplicativo), com aviso de que é estimativa. | Média |
| RF08 | Assistente por texto que explica as sugestões com base no catálogo (RAG). | Média |
| RF09 | 5 agentes especializados (lazer/eventos, mobilidade, clima via API, financeiro, planejador) reportando a um agente principal orquestrador. | Média |

## Requisitos não funcionais

| ID | Requisito |
| --- | --- |
| RNF01 | Sistema web responsivo, acessível pelo navegador do computador e do celular. |
| RNF02 | Somas, limites de orçamento e validações de datas feitos por **regras determinísticas e testes**, nunca pela IA. |
| RNF03 | Toda informação factual exibida deve ter **fonte e data de verificação**; sem evidência, o sistema informa "não confirmado". |
| RNF04 | Coleta mínima de dados pessoais e localização aproximada, em conformidade com a **LGPD**. |
| RNF05 | Funcionamento parcial quando uma API externa estiver indisponível, avisando o usuário. |
| RNF06 | Conteúdo vindo de fontes externas tratado como dado, nunca como instrução (proteção contra *prompt injection*). |

## Decisões técnicas e justificativas

| Decisão | Justificativa |
| --- | --- |
| **Sistema web** (mobile como backup) | Mais rápido de desenvolver e demonstrar em 7 semanas; funciona em qualquer dispositivo com navegador. |
| **HTML + JavaScript simples** no frontend | Curva de aprendizado baixa para a equipe; pode evoluir para um framework se o projeto crescer. |
| **Python + FastAPI** no backend | Python é a linguagem principal de IA e dados; o FastAPI é leve e gera documentação automática da API. |
| **Supabase (PostgreSQL + pgvector + login)** | Reúne banco, login e busca vetorial do RAG em um único serviço gratuito para protótipos. |
| **LLM + RAG** | Reduz respostas inventadas, porque a IA responde a partir do catálogo verificado. A Semana 3 compara LLM com e sem RAG. |
| **Agentes que leem dados de APIs** | Cada agente tem uma fonte de dados própria, o que facilita testar e trocar integrações. As APIs candidatas ainda serão definidas. |
| **Início com o Agente Principal** | O desenvolvimento começa só pelo agente principal, com uma base demo de 30 passeios (divisão da pesquisa a definir na Semana 2) para avaliar a eficiência das respostas. Os agentes especialistas são desenvolvidos um a um a partir da Semana 4 (multiagentes). O Agente de Clima tem duas opções de arquitetura (Lazer + Clima ou Mobilidade + Clima), decididas nessa etapa; ver [README](../../README.md#papéis-dos-agentes-semanas-4-e-5). |
| **Sem voz** | O protótipo foca em ler dados das APIs e responder por texto. A multimodalidade da Semana 5 é tratada como a combinação de várias fontes de dados pelos agentes (interpretação a validar com os mentores). |

## Fora do escopo

- Entrada e saída por voz.
- Aplicativo mobile (fica como backup e evolução futura).
- Integração com renda ou extratos bancários.
- Cotação oficial de transporte por aplicativo em tempo real.
- Alegações de benefício clínico (por exemplo, prevenção de burnout).
