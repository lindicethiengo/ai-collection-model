# Decision Record | Priorização de cobrança

**Decisão em análise:** autorizar ou não um piloto controlado e, posteriormente, decidir sobre eventual implantação geral do modelo.  
**Status:** recomendação técnica preliminar; decisão formal pendente. Piloto não executado e sem aprovação formal. Implantação geral sem aprovação formal. [A: B16; E: linha 15]  
**Identificador oficial da decisão, data da deliberação e versão do modelo:** não informados.  
**Responsáveis nominais e instância formal de decisão:** não informados. As áreas requeridas para análise estão descritas na seção 6.

Documentos complementares: [Model Card](model_card.md) e [Evidence Register](evidence_register.md).

## 1. Contexto da decisão

A equipe de cobrança possui capacidade limitada de contato. A fila vigente de contratos em atraso é ordenada por tempo de atraso e valor devido. A proposta é utilizar um modelo preditivo para estimar a chance de regularização em até 30 dias após o contato e apoiar a ordenação da fila, mantendo capacidade de atendimento comparável à atual. [C: Contexto; Proposta]

O objetivo de negócio é aumentar a taxa de regularização em 30 dias sem elevar custos operacionais ou ampliar riscos para os clientes. A saída do modelo é apenas uma recomendação sujeita à revisão da equipe de cobrança. [C: Objetivo de negócio; Escopo e restrições]

A decisão precisa considerar a incerteza dos resultados preliminares, a ausência de rastreabilidade técnica, a viabilidade operacional, os custos e os potenciais impactos sobre os clientes. O contexto é material de simulação para capacitação; não comprova operação real do modelo. [C: Condições para avaliação; nota final; E: linhas 9, 11 e 13]

## 2. Evidências que sustentam a análise

| Evidência | Resultado / situação | Fonte |
| --- | --- | --- |
| Regularização em até 30 dias com a regra atual | 12% | A: B5 |
| Regularização em até 30 dias com o modelo proposto | 14% | A: B6 |
| Diferença estimada | +2,0 p.p. | A: B7; fórmula conferida |
| IC de 95% da diferença | −0,4 a +4,4 p.p. | A: B8:B9; método não informado |
| Tamanho das amostras e método do IC | Não informados | A: B12:B13; E: linha 9 |
| Avaliação segmentada e de custos | Não disponibilizada | A: B14:B15; E: linha 9 |
| Capacidade equivalente e efeitos sobre clientes | Requisitos de avaliação; resultados não disponibilizados | C: Proposta; Condições para avaliação |
| Versão, snapshot, hash, commit e Run ID do MLflow (quando disponível) | Não encaminhados | E: linha 11 |
| Piloto | Não executado | A: B16 |
| Aprovação formal do piloto e da implantação geral | Não houve | E: linha 15 |

**Análise técnica:** a diferença aritmética está correta. O intervalo informado contém zero e admite diferenças negativas. Se o IC for válido para a diferença estimada, o resultado não demonstra superioridade estatística bilateral a 5%. Sem relatório metodológico, amostras e protocolo comparável, não se pode reproduzir o IC nem concluir que a mudança de fila causará aumento de regularização. Tampouco há comprovação de que o objetivo de custo e risco tenha sido atingido. [A: B5:B15; E: linha 9; C: Objetivo de negócio]

## 3. Alternativas consideradas

A comparação numérica documentada refere-se à regra atual e ao modelo proposto. A recomendação de preparar um piloto consta do e-mail. As alternativas de encaminhamento abaixo foram estruturadas nesta análise para apoiar a decisão; não há evidência de que tenham sido formalmente deliberadas pelas áreas.

| Alternativa | Vantagem esperada | Limitações e riscos | Avaliação nesta documentação |
| --- | --- | --- | --- |
| Manter a regra atual (baseline) enquanto as evidências são completadas | Preserva a continuidade operacional e evita introduzir riscos do modelo ainda não avaliados. | Não explora imediatamente o possível ganho; desempenho e custos da própria regra atual também não estão detalhados. | Recomendada como situação operacional provisória. Base: C: Contexto; A: B5; E: linhas 9 e 15. |
| Preparar e, somente se autorizado, executar piloto controlado | Permite testar a priorização em capacidade comparável e produzir evidências mais robustas. | Exige desenho válido, rastreabilidade, revisão humana, controle de custos e impactos. Pode não confirmar o ganho. | Encaminhamento recomendado pela Engenharia de IA; execução ainda não autorizada. Base: E: linha 15; C: Condições para avaliação. |
| Implantar o modelo de forma geral sem piloto | Possibilidade de explorar mais rapidamente o ganho estimado. | Benefício não demonstrado, custos e impactos desconhecidos, rastreabilidade incompleta, risco de deterioração e ausência de aprovação. | Não recomendada com as evidências atuais. Base: A: B7:B16; E: linhas 9, 11, 13 e 15. |

Nenhuma família de algoritmo ou alternativa técnica de modelagem (ex. modelos diferentes) foi descrita ou comparada nos anexos. Não se presume que essa seleção tenha ocorrido.

## 4. Recomendação técnica e justificativa

**Recomendação registrada na fonte:** a Engenharia de IA recomenda preparar um piloto controlado, com a mesma capacidade de contato, revisão humana da fila e critérios de acompanhamento. A área explicita que não houve aprovação formal do piloto nem da implantação geral e que a decisão deve ser registrada após manifestação das áreas responsáveis. [E: linha 15]

**Encaminhamento proposto nesta documentação:** manter a regra atual em operação enquanto se recuperam as evidências e se estrutura o piloto. Submeter a autorização de um piloto controlado à análise das áreas de Negócio, Dados e IA e Risco/Compliance. Executar somente após autorização formal e cumprimento das condições estabelecidas. Não recomendar implantação geral antes de avaliação dos resultados do piloto e de nova decisão formal.

Justificativa:

- Existe uma diferença pontual preliminar de +2,0 p.p. a favor do modelo, suficiente para justificar investigação, não para comprovar benefício. [A: B5:B9]
- O IC informado não exclui ausência de ganho ou redução na taxa de regularização, e a metodologia não está disponível. [A: B8:B13; E: linha 9]
- Não há rastreabilidade entre os resultados e a versão de dados, modelo, código e execução experimental. [E: linha 11]
- Custos, capacidade, segmentos e efeitos sobre os clientes precisam ser avaliados antes de concluir atendimento ao objetivo de negócio. [C: Objetivo de negócio; Condições para avaliação; A: B14:B15]
- Mudança de perfil da carteira e lacunas de dados podem comprometer previsões. [E: linha 13]

A recomendação não autoriza uso, teste com clientes ou implantação. Trata-se de uma proposta de encaminhamento para deliberação.

## 5. Riscos, condições para aprovação e critérios de acompanhamento

### 5.1 Riscos relevantes à decisão

Os controles listados são propostas de mitigação, salvo restrições expressamente estabelecidas em C. Não há avaliação formal de severidade ou risco residual nos anexos.

| Risco | Base documental / interpretação | Condição ou controle proposto |
| --- | --- | --- |
| Aprovar com base em ganho não demonstrado | IC inclui zero; método e amostras ausentes. [A: B7:B13; E: linha 9] | Validar a avaliação e definir hipótese, métricas e regra de decisão antes do piloto. |
| Alteração do perfil da carteira e dados incompletos | Limitações explicitamente comunicadas. [E: linha 13] | Avaliar qualidade, estabilidade e desempenho; definir monitoramento e interrupção. |
| Custo adicional ou capacidade não equivalente | Avaliações insuficientes para verificar o objetivo. [C: Proposta; Objetivo de negócio; A: B15] | Fixar capacidade comparável e contabilizar custos e esforço humano. |
| Efeitos desiguais ou adversos sobre clientes | Risco potencial; avaliação segmentada e de impactos requerida. [C: Condições para avaliação; A: B14] | Avaliar segmentos autorizados, tratamento dos clientes e critérios de proteção definidos por Risco/Compliance. |
| Uso indevido da recomendação e dos dados | Restrições expressas em C: Escopo e restrições; ocorrência não demonstrada. | Revisão humana, autorização de dados, controles de acesso e impedimento de ações fora do escopo. |
| Impossibilidade de reproduzir ou auditar resultado | Identificadores ausentes. [E: linha 11] | Recuperar e vincular modelo, dados, código e execução ao relatório. |
| Confundir propensão com benefício incremental do contato | Hipótese técnica decorrente da finalidade em C: Proposta e do alerta causal em E: linha 9. | Usar desenho de avaliação que possibilite comparar políticas de priorização e controlar diferenças de seleção. |

### 5.2 Condições para autorizar a execução de um piloto

O contexto exige análise de desempenho, segmentos, capacidade, custos e efeitos nos clientes, além da manifestação das áreas responsáveis. [C: Condições para avaliação] A forma específica de operacionalizar essas exigências abaixo é uma **proposta de governança**, ainda não aprovada. Não foram definidos limiares numéricos no material original.

| Condição proposta | Evidência requerida | Status com base nos anexos |
| --- | --- | --- |
| Identidade e rastreabilidade | Versão do modelo, snapshot identificado e datado, hash, commit, Run ID se disponível, artefatos e vínculo aos resultados. | Pendente. E: linha 11. |
| Metodologia e avaliação preliminar validadas | Relatório com desenho da avaliação, amostras, definição de regularização, denominadores, cálculo do IC e resultados reproduzíveis; avaliação inicial por segmentos e custos para instruir a decisão. | Pendente. A: B12:B15; E: linha 9. |
| Autorização e qualidade dos dados | Documentação das fontes, finalidade autorizada, controles de qualidade e avaliação de lacunas de dados. | Pendente de comprovação. C: Escopo e restrições; E: linha 13. |
| Protocolo de piloto | População elegível, comparador, capacidade de contato, horizonte de avaliação, desenho, tamanho de amostra, métricas, critérios de aceite e plano de acompanhamento definidos previamente. | Não disponibilizado. C: Proposta; Condições para avaliação; E: linha 15. |
| Controle humano e proteção de clientes | Revisão da fila, registro de alterações, prevenção de ações não autorizadas e critérios de interrupção/retorno à regra atual. | Revisão exigida; implementação e critérios não demonstrados. C: Escopo e restrições; E: linha 15. |
| Manifestação e autorização formal | Registro de decisão com responsáveis identificados, pareceres, escopo e condições de execução. | Não houve aprovação formal. E: linha 15. |

A preparação documental e metodológica não deve ser confundida com autorização para iniciar o piloto.

### 5.3 Desenho e acompanhamento do piloto (proposta)

- Comparar a política vigente com a política baseada na recomendação do modelo, sob capacidade de contato equivalente e regras operacionais comparáveis. Considerar alocação aleatória quando viável e aprovada; caso contrário, justificar o desenho e suas limitações de inferência causal.
- Definir previamente a unidade de alocação e análise, critérios de elegibilidade, numerador e denominador da taxa, janela de 30 dias após contato, tratamento de contatos não realizados, seguimento incompleto e possíveis contaminações entre grupos. Definir estimando apropriado para avaliar o efeito da política, além da métrica operacional de regularização após contato.
- Fixar critérios de aceite, tamanho amostral, método estatístico, margem de risco, critérios de interrupção e responsáveis antes de observar o resultado do piloto. Não usar os +2,0 p.p. preliminares como meta de aceite automaticamente.
- Acompanhar desempenho agregado e por segmentos, volume e capacidade de contato, custos totais e por regularização, revisão humana, qualidade dos dados, reclamações e potenciais efeitos adversos sobre clientes.
- Preservar as restrições do contexto: não disparar contatos automaticamente, não aplicar sanções, não alterar contratos, não decidir condições de negociação e não usar dados não autorizados. [C: Escopo e restrições]
- Registrar recomendações, intervenções humanas, ocorrências e desvios de protocolo. Prever interrupção e retorno à regra vigente se os critérios de segurança, qualidade ou capacidade forem violados.

**Base da proposta:** C: Proposta; Objetivo de negócio; Escopo e restrições; Condições para avaliação; E: linhas 9, 13 e 15. Nenhum desenho experimental ou limiar específico foi formalizado nos anexos.

### 5.4 Condições para futura aprovação de implantação geral

| Condição proposta | Evidência esperada |
| --- | --- |
| Benefício demonstrado conforme critérios previamente estabelecidos | Relatório do piloto com comparação válida, resultados agregados e segmentados, intervalos de incerteza e conclusão conforme a regra de decisão aprovada. |
| Custos e capacidade compatíveis com o objetivo | Comprovação de que a operação permanece em capacidade comparável e não eleva os custos operacionais, conforme o critério de mensuração aprovado. |
| Risco aos clientes avaliado e aceitável | Evidências dos impactos, análise por segmentos, medidas de proteção e manifestação de Risco/Compliance compatíveis com o objetivo de não ampliar riscos aos clientes. |
| Rastreabilidade, monitoramento e operação preparados | Artefatos versionados e reproduzíveis, responsáveis, métricas, limites de monitoramento, rotina de revisão humana e procedimento de contingência. |
| Nova deliberação formal | Decisão datada de implantação, rejeição ou revisão, com escopo, versão avaliada, responsáveis e condições registradas. |

**Status atual de todas as condições de implantação:** não demonstradas no material recebido. O piloto consta como não executado e a implantação geral como não aprovada formalmente. [A: B16; E: linha 15]

## 6. Responsáveis e status das aprovações

As áreas de Negócio, Dados e IA e Risco/Compliance são expressamente indicadas para análise de eventual autorização de piloto. [C: Condições para avaliação] A Engenharia de IA é a área remetente da recomendação de piloto; o e-mail não estabelece autoridade de aprovação para ela. [E: cabeçalho e linha 15]

| Área | Papel documentado ou proposto | Responsável nominal | Manifestação / aprovação registrada |
| --- | --- | --- | --- |
| Negócio / Operações de Cobrança | Documentado: requisitos operacionais, análise da autorização e revisão humana da fila. Proposto: validar capacidade, custos, execução e critérios operacionais. | Não informado | Parecer individual não disponibilizado; aprovação formal não evidenciada. |
| Dados e IA | Documentado: área indicada para análise. Proposto: validar metodologia, dados, modelo, rastreabilidade, desempenho e monitoramento. | Não informado | Parecer individual não disponibilizado; aprovação formal não evidenciada. |
| Engenharia de IA | Documentado: comunica lacunas e recomenda preparar piloto. Proposto: apoiar recuperação dos artefatos e reprodução da avaliação. | Não informado | Recomendação técnica disponível (E: linha 15); não constitui aprovação. |
| Risco/Compliance | Documentado: área indicada para análise. Proposto: validar finalidade dos dados, impactos aos clientes, controles, restrições e riscos. | Não informado | Parecer individual não disponibilizado; aprovação formal não evidenciada. |
| Instância/autoridade final de decisão | Não definida nos anexos. Proposto: formalizar autoridade competente e responsáveis por etapa. | Não informado | Não identificado registro formal de decisão. |

O e-mail estar endereçado às áreas não comprova ciência, concordância ou aprovação individual. Não há nomes, assinaturas, datas de parecer ou atas disponibilizadas.

## 7. Registro do status da decisão

| Marco | Status documentado ou recomendado |
| --- | --- |
| Continuidade da regra vigente durante instrução da decisão | Recomendada nesta documentação; não constitui nova deliberação. |
| Preparação do piloto controlado | Recomendada pela Engenharia de IA; execução da preparação não comprovada. [E: linha 15] |
| Autorização do piloto | Não houve aprovação formal. [E: linha 15] |
| Execução do piloto | Não executado. [A: B16] |
| Implantação geral | Não houve aprovação formal; não recomendada com as evidências atuais. [E: linha 15; análise técnica] |
| Registro oficial da decisão final | Pendente de manifestação das áreas responsáveis. [E: linha 15] |

Quando a decisão for formalizada, acrescentar o identificador real do registro (se utilizado), a data efetiva da deliberação, a versão do modelo, as referências às evidências avaliadas, os responsáveis nominais, os pareceres, o resultado da decisão, suas condições, o prazo de revisão e o tratamento das pendências. Não preencher esses campos como aprovados antes da manifestação competente.

## 8. Fontes e convenções

- **C:** `Contexto_Projeto.docx`, Operações de Cobrança, seções Contexto, Proposta, Objetivo de negócio, Escopo e restrições, Condições para avaliação e nota final de simulação.
- **A:** `Resultados_Avaliacao.xlsx`, aba `Avaliação`, células indicadas no texto.
- **E:** `Email_Equipe_Tecnica.txt`, Engenharia de IA, assunto `Priorização de cobrança | Pendências da avaliação`: linhas 1–3 (cabeçalho), 7 (consolidação), 9 (limitações de avaliação), 11 (rastreabilidade), 13 (limitações das previsões), 15 (recomendação e aprovações).

As referências C, A e E são rótulos documentais locais. As alternativas, critérios, controles e papéis explicitamente descritos como propostas foram estruturados nesta documentação; não representam fatos já implementados ou aprovação institucional. Nenhuma fonte externa foi utilizada.
