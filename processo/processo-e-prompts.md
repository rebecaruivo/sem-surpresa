# Processo e engenharia de prompts

Este documento registra como usei IA generativa para construir o case **Sem Surpresa** (Recruta Stone 2027) entre 28/10 e 02/11/2026. O foco é a engenharia de prompts: como formulei os pedidos, quais técnicas funcionaram, onde a IA errou e como corrigi.

> Na versão publicada, os estabelecimentos entrevistados aparecem pelo segmento, sem o nome. O resumo do case está no [README](../README.md).

## Visão geral

**Papel da IA.** O Claude foi meu parceiro de análise e de produção: organizou evidências, propôs e reposicionou a solução, escreveu e revisou o relatório, montou o protótipo e os materiais de apoio. Usei também outras IAs como revisoras independentes, colando as críticas delas no chat para que fossem avaliadas.

**O que ficou comigo.** Fiz as conversas com os lojistas pessoalmente. O levantamento do Reclame Aqui usado na versão final foi feito à mão. Todas as decisões sobre a proposta, a narrativa e o que entrou na entrega foram minhas.

**Fora do escopo deste documento:** a coleta automatizada de dados testada no início, que não foi usada na versão final.

**Entregas produzidas com apoio da IA:** relatório de até 5 páginas, anexo de cálculos, documento de entrevistas, apresentação com protótipo navegável em HTML e um arquivo de contexto para continuar o trabalho em outras ferramentas.

## Trajetória

1. Uma primeira leitura do Reclame Aqui gerou uma ideia inicial, ainda pouco estruturada: o *Radar de Caixa*, uma previsão de caixa para o lojista.
2. Fiz as quatro primeiras entrevistas. Quase ninguém relatou problema, e isso virou a pergunta da pesquisa: onde está a dor?
3. Fiz o levantamento manual do Reclame Aqui, que mostrou o dinheiro bloqueado ou retido como o tema principal.
4. Fiz as outras oito entrevistas.
5. A proposta virou o *Sem Surpresa*.

## Linha do tempo das interações

| # | Etapa | O que pedi (resumo) | Técnica de prompt | Resultado |
|---|---|---|---|---|
| 1 | Enquadramento | Enviei as imagens do enunciado e pedi para avaliar quais dados concretos ajudariam a embasar a proposta | Contexto completo (enunciado) + pedido de avaliação antes da execução | Lista do que coletar e por quê, ligada a cada pergunta do case |
| 2 | Solução | Anexei a planilha de resultados do 2T26 da Stone e pedi "uma solução, ajustando a anterior ou completamente nova" | Pergunta aberta que autoriza descartar a ideia inicial + dado primário da empresa | A previsão de caixa deu lugar a uma central de retenções |
| 3 | Lacunas | Perguntei como ver o app sem login, que perguntas fazer aos comércios e em que fase do protótipo | Pedido de plano de validação, não de conteúdo | Fontes públicas do app e roteiro de entrevistas por fase |
| 4 | Relatório | "Comece o relatório, ainda será incrementado" | Rascunho cedo, com espaços marcados para o que viria do campo | Estrutura pronta para receber entrevistas e telas |
| 5 | IA na proposta | Perguntei se a proposta exige IA ou é facilitada por ela | Validação técnica antes de prototipar | IA só onde agrega (conferência de nota fiscal); o resto é regra e dado |
| 6 | Protótipo | Anexei o HTML da aba Minhas Finanças e pedi a melhor ordem entre interface, back e front | Material de partida real + pedido de sequência | Protótipo navegável com dados fictícios e cenários de teste |
| 7 | Revisão externa | Colei avaliações de outras IAs e pedi: "avalie o que é importante" | Revisão cruzada: a IA julga a crítica antes de aplicar | Cortes para 5 páginas, afirmações atenuadas, números com base |
| 8 | Fragilidades | Colei 8 pontos que a banca exploraria e uma lista de números a corrigir | Checklist explícito | Caso de negócio com premissas, dimensionamento em faixa e limites declarados |
| 9 | Campo | Mandei as entrevistas com a instrução "use apenas os fatos abaixo, sem inventar datas, números, falas" | Restrição de fonte + aviso de risco ("MUITO cuidado") | Documento de entrevistas e trajetória da pesquisa |
| 10 | Narrativa | Corrigi a ordem real: o Reclame Aqui só foi estudado a fundo depois das quatro primeiras entrevistas, feitas com uma ideia inicial ainda pouco estruturada | Correção factual + objetivo de comunicação ("de maneira inteligente") | Trajetória reescrita em todos os materiais |
| 11 | Organização | Esclareci que o documento de entrevistas é um dos materiais de apoio, não todos | Correção de escopo do entregável | Protótipo separado em documento próprio |
| 12 | Passagem de contexto | "Junte toda a trajetória até aqui para que eu forneça de contexto para outra IA" | Arquivo de contexto com regras para quem continuar | Contexto portátil, com o que não pode mudar |
| 13 | Mais campo | Enviei mais entrevistas em PDF e confirmei datas e valores | Atualização incremental com confirmação de ambiguidades | 12 conversas integradas |
| 14 | Atualidade | Pedi para descartar evidências anteriores a 2023 e recalcular com o *n* ao lado | Critério de validade temporal + transparência estatística | Números recentes com contagem |

## Técnicas de engenharia de prompt

1. **Dar o contexto inteiro, não só a tarefa.** Antes de pedir qualquer coisa, enviei o enunciado (entregas, prazo, critérios) e um resumo da minha ideia. Com isso, a IA passou a julgar cada pedido pelo que a banca avalia, e não por critérios genéricos.
2. **Pedir avaliação antes da execução.** Em vez de "colete X", pedi "avalie quais informações e dados concretos seriam úteis". Em vez de "aplique essas críticas", pedi "avalie o que é importante". A IA primeiro dizia o que fazia sentido, e só então eu respondia "sim" ou "aplique". Isso evitou retrabalho e manteve as decisões comigo.
3. **Permitir descartar a própria ideia.** O pedido "qual seria uma solução, ajustando a anterior ou completamente nova" deu espaço para a IA dizer que a previsão de caixa não era o melhor caminho. Prompts que só pedem para "melhorar" a ideia tendem a confirmá-la.
4. **Ancorar em material real.** Anexei a planilha de resultados da Stone, o HTML da aba Minhas Finanças e o PDF das entrevistas. A IA trabalhou sobre o que existe, e o protótipo partiu da interface real em vez de uma tela inventada.
5. **Revisão cruzada com outras IAs.** Colei as avaliações de outras ferramentas e pedi para a IA julgá-las. Ela aceitou parte das críticas, recusou outras com justificativa e encontrou erros que a própria revisão externa tinha cometido.
6. **Restringir a fonte dos fatos.** Ao mandar as entrevistas, escrevi: "use apenas os fatos abaixo, sem inventar datas, números, falas". Quando um trecho veio ambíguo (valores com formatação quebrada no PDF), a IA perguntou antes de usar, em vez de completar por conta própria.
7. **Dizer o objetivo de comunicação, não só o fato.** Na correção da trajetória, além do fato, expliquei a preocupação: "colocado de maneira inteligente para que não prejudique a proposta". A IA reescreveu a história sem esconder nada: as conversas sem problema viraram a pergunta que levou à investigação.
8. **Checklists explícitos.** Quando recebi uma lista de oito fragilidades e cinco números a corrigir, colei a lista inteira. A IA tratou item por item e conferiu os números na base antes de corrigir.
9. **Restrições de formato verificáveis.** O limite de 5 páginas foi conferido exportando o PDF a cada mudança. Quando passava, a IA cortava texto e dizia o que tinha saído.
10. **Critério de validade explícito.** "Reclamações antes de 2023 provavelmente não valem mais", com a regra de mostrar o *n* ao lado de cada percentual. Isso trocou números bonitos por números defensáveis.
11. **Contexto portátil para outras ferramentas.** Pedi um arquivo com toda a trajetória para usar em outra IA. Além dos fatos, ele traz regras do que não pode mudar (ordem da pesquisa, hipóteses que não são fatos), para que a próxima ferramenta não desfaça as correções.
12. **Red team antes da versão final.** Pedi à IA que agisse como um avaliador cético da banca e listasse os pontos fracos por gravidade, com uma mitigação para cada um. As respostas mudaram o escopo do piloto, as proteções e as métricas.

## Fato, hipótese e lacuna

Um cuidado repetido ao longo do processo foi separar três níveis de evidência:

| Nível | Exemplo | Tratamento |
|---|---|---|
| Fato com fonte | Inadimplência acima de 90 dias de 4,7% para 8,6% (2T25 → 2T26, planilha de resultados) | Citado no texto com a fonte |
| Hipótese | O resumo diário e o aviso prévio reduzem a saída por surpresa | Marcada como hipótese, com forma de testar no piloto |
| Lacuna | Churn dos 90 primeiros dias e receita por coorte | Deixada como premissa declarada, sem inventar valor |

## Correções de rota

A IA errou várias vezes, e cada erro gerou uma regra para o próximo prompt.

| O que aconteceu | Como corrigi | O que aprendi |
|---|---|---|
| A IA deduziu a ordem da pesquisa pelos horários dos arquivos e escreveu que o Reclame Aqui veio antes das entrevistas | Disse a ordem real e pedi a correção "em TODOS os materiais" | A IA preenche lacunas com inferências; fatos sobre o meu processo têm de vir de mim, explicitamente |
| Na correção, a IA escreveu que a proposta já estava definida antes das entrevistas | Apontei a frase exata e o fato certo: havia só uma ideia inicial, pouco estruturada, e a proposta se definiu depois do campo | Revisar frase a frase as partes sensíveis; selecionar o trecho e corrigir só ele é mais rápido que reescrever |
| A IA colocou todo o material de apoio num documento só | Esclareci que ele era um dos materiais, não todos | Definir a estrutura dos entregáveis antes de pedir o conteúdo |
| Afirmações sem fonte, como comparação com concorrentes "pelo que apurei" | Uma revisão de outra IA apontou; pedi fonte ou linguagem cautelosa | Perguntar "de onde vem isso?" para toda afirmação factual |
| Percentuais com denominador trocado e dois itens somados apresentados como um só | Colei a lista inteira de números a corrigir | Exigir o *n* ao lado do percentual e dizer o que cada número conta |
| Uma alavanca de negócio (redução de churn) apresentada como ganho principal, sem sustentação | A revisão externa pediu a conta com premissas; a IA refez e mostrou que o valor era pequeno | Pedir a conta, não o adjetivo; um número modesto e honesto convence mais |
| Evidências antigas misturadas com recentes | Pedi para descartar o que era anterior a 2023 e recalcular | Definir o critério de validade dos dados logo no início |
| Um número do rascunho (inadimplência de 3,6% no 2T25) não batia com a fonte | Conferi na planilha e no release oficial: o valor é 4,67% | Conferir cada número na fonte primária antes da entrega |

Um padrão comum: quando o prompt deixava espaço, a IA escolhia a versão mais "forte" da história. As correções mais importantes tornaram o texto mais preciso, mesmo quando isso deixava a proposta mais modesta.

## Modelos de prompt reutilizáveis

Versões genéricas dos pedidos que melhor funcionaram.

**Enquadrar o problema**
```text
Estou resolvendo o case abaixo [enunciado, entregas, prazo, critérios].
Minha ideia inicial é [resumo]. Antes de fazer qualquer coisa, avalie que
informações e dados concretos sustentariam ou derrubariam essa ideia.
```

**Reposicionar a solução com base em dados**
```text
Com base nos dados que levantamos e nos dados da empresa [anexo], qual
seria uma solução que faz sentido, ajustando a anterior ou completamente nova?
```

**Revisão cruzada**
```text
Outra IA avaliou o trabalho assim: [crítica colada]. Avalie o que é
importante, o que não procede e por quê. Não aplique nada ainda.
```

**Red team**
```text
Aja como um avaliador cético da banca. Liste os cinco maiores pontos fracos
desta proposta, em ordem de gravidade, e proponha uma mitigação para cada.
```

**Trabalhar com fatos de campo**
```text
Use apenas os fatos abaixo, sem inventar datas, números ou falas.
Se algo estiver ambíguo, pergunte antes de usar. [entrevistas]
```

**Corrigir a narrativa sem perder credibilidade**
```text
O processo real foi [fato]. Corrija isso em todos os materiais. Conte de
forma que não enfraqueça a proposta, mas sem esconder nem distorcer nada.
```

**Dados com validade e peso**
```text
Considere só dados a partir de [data]. Recalcule cada percentual e escreva
o n ao lado ("33 de 49"). Diga quais padrões se mantêm e quais mudaram.
```

**Passar o contexto adiante**
```text
Junte toda a trajetória até aqui num arquivo para outra IA: fatos, números
com fonte, decisões tomadas e regras do que não pode ser alterado.
```

## Limites e responsabilidades

- **A IA não substitui o campo.** As conversas com lojistas foram feitas por mim, e foram elas que definiram a pergunta da pesquisa. A IA organizou e interpretou o que eu trouxe, sem acrescentar falas ou casos.
- **Verificação humana.** Todo número da entrega foi conferido na fonte antes de entrar, e as afirmações sem base foram retiradas ou atenuadas. Quando a IA e uma revisão externa discordavam, a decisão foi minha.
- **Hipóteses marcadas como hipóteses.** Efeito no churn, proporção de lojistas afetados e efeito no crédito aparecem na proposta como premissas a validar no piloto, não como resultados.
- **Protótipo com dados fictícios.** O protótipo parte da interface pública da aba Minhas Finanças. Não é o app oficial e não usa dados de clientes.

## O que eu faria diferente

Definiria desde o primeiro prompt a estrutura dos entregáveis, o critério de validade dos dados e a regra de citar sempre o *n*. Boa parte das correções veio dessas três coisas terem ficado implícitas no começo.
