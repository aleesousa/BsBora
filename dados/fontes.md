# Fontes de dados candidatas — BSBora

[← README do projeto](../README.md) · [Semana 1](../documentos/semana-1/README.md)

**Responsável:** Eduarda (cientista de dados) · **Semana:** 1 · **Situação:** rascunho para revisão da equipe

Esta é a lista de **fontes candidatas** para o catálogo e para os agentes. **Nenhuma fonte foi verificada ainda.** Antes de usar cada uma, é preciso confirmar se ela existe e está atualizada, qual é a licença, se tem custo ou limite de uso e qual é a forma de acesso (API, download ou consulta manual).

## Critérios para aceitar uma fonte

1. **Confiável:** fonte oficial ou página do próprio atrativo.
2. **Atualizada:** informa ou permite registrar a data da informação.
3. **Licença compatível:** o uso no projeto é permitido.
4. **Acessível:** por API, dados abertos ou consulta manual viável.
5. **Custo viável:** gratuita ou com cota suficiente para o protótipo.

## Fontes por agente

### Agente de Lazer (passeios)

| Fonte candidata | Tipo | O que pode fornecer | Situação |
| --- | --- | --- | --- |
| Secretaria de Turismo do DF | Portal oficial | Atrativos turísticos do DF | A verificar |
| Secretaria de Cultura e Economia Criativa do DF | Portal oficial | Equipamentos culturais e agenda | A verificar |
| Portal de Dados Abertos do DF | Dados abertos | Conjuntos de dados públicos (parques, equipamentos) | A verificar |
| Páginas oficiais dos atrativos | Sites oficiais | Preços, horários e regras de visitação | A verificar, uma a uma |

### Agente de Mobilidade (rotas e transporte)

| Fonte candidata | Tipo | O que pode fornecer | Situação |
| --- | --- | --- | --- |
| Secretaria de Transporte e Mobilidade do DF (Semob) | Portal oficial | Tarifas e linhas de ônibus | A verificar |
| OpenStreetMap (com serviço de rotas, ex.: OSRM) | Dados abertos / API | Distâncias e trajetos de carro | A verificar licença e cota |
| Google Maps Platform | API paga | Rotas e tempo de deslocamento | A verificar custo |
| ANP — levantamento de preços de combustíveis | Dados oficiais | Preço médio da gasolina no DF | A verificar |

### Agente de Clima (etiqueta "ao ar livre")

| Fonte candidata | Tipo | O que pode fornecer | Situação |
| --- | --- | --- | --- |
| INMET | Dados oficiais | Previsão e dados meteorológicos | A verificar a forma de acesso |
| Open-Meteo | API | Previsão do tempo por coordenada | A verificar licença e cota |

### Agente Financeiro

Não usa API externa. Trabalha com **regras determinísticas** sobre os dados do catálogo, da mobilidade e do perfil do usuário.

### Regiões Administrativas

| Fonte candidata | Tipo | O que pode fornecer | Situação |
| --- | --- | --- | --- |
| Governo do DF / IPEDF | Dados oficiais | Lista oficial das Regiões Administrativas | A verificar |

## Transporte por aplicativo

Não há fonte oficial pública de preços. Conforme o README, o sistema apresenta **faixas não oficiais**, sempre sinalizadas como estimativa.

## Próximos passos

- [ ] Verificar cada fonte (existência, licença, custo, forma de acesso) e atualizar a coluna "Situação".
- [ ] Escolher as APIs de cada agente junto com o MLOps (Breno), que cuida de custos e cotas.
- [ ] Registrar as fontes aprovadas no campo `fonte_nome` do [esquema do catálogo](esquema-catalogo.md).
