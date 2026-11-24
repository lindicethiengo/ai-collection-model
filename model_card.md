# Model Card | Priorização de cobrança

**Status:** documentação preliminar para revisão técnica e de governança.  
**Versão do modelo:** não informada.  
**Situação de uso:** modelo proposto; piloto não executado e não aprovado formalmente; implantação geral não aprovada formalmente.  
**Natureza do material:** contexto de simulação para capacitação, sem dados de clientes no documento de contexto. Não há comprovação da origem dos dados que produziram os indicadores. [C; A: B16; E: §5]

Documentos complementares: [Evidence Register](evidence_register.md) e [Decision Record](decision_record.md).

## 1. Finalidade e escopo

| Item | Descrição | Fonte |
| --- | --- | --- |
| Problema de negócio | A equipe de cobrança possui capacidade limitada de contato. | C: Contexto |
| Processo vigente (baseline) | Ordenação da fila de contratos em atraso por tempo de atraso e valor devido. A ponderação e a implementação da regra não foram detalhadas. | C: Contexto |
| Finalidade do modelo | Estimar a chance de regularização em até 30 dias após o contato e apoiar a ordenação da fila. | C: Proposta |
| Objetivo de negócio | Aumentar a taxa de regularização em 30 dias sem elevar custos operacionais nem ampliar riscos para os clientes. | C: Objetivo de negócio |
| População de referência | Contratos em atraso da carteira de cobrança. Segmentos, critérios de elegibilidade e exclusão não informados. | C: Contexto; Condições para avaliação |
| Saída esperada | Recomendação de priorização, sujeita à revisão da equipe de cobrança. Formato do score, escala, regras de ordenação e desempate não informados. | C: Escopo e restrições |
| Restrição operacional | Capacidade de atendimento comparável à do processo atual. A capacidade efetiva não foi quantificada. | C: Proposta; E: §5 |
| Usuário operacional previsto | Equipe de cobrança. Responsáveis nominais, perfis de acesso e operador técnico não informados. | C: Contexto; Escopo e restrições |

A unidade de ordenação é a fila de contratos em atraso. A unidade de observação do modelo e da avaliação (contrato, cliente ou contato) não foi formalmente definida no material recebido.

## 2. Identificação, dados e rastreabilidade

| Elemento | Informação disponível | Fonte ou pendência |
| --- | --- | --- |
| Nome descritivo | Modelo de priorização de cobrança. | C: Proposta |
| Versão do modelo e artefato treinado | Não informados/disponibilizados. | E: §3; nenhum artefato de modelo anexado |
| Origem, sistemas e bases de dados utilizadas | Não informados. | Ausente em C, A e E |
| Identificador e período do snapshot de dados | Não informados. | E: §3 |
| Hash do snapshot | Não informado. | E: §3 |
| Variáveis de entrada, dicionário de dados e tipos | Não informados. Tempo de atraso e valor devido são critérios da regra atual, não atributos confirmados do modelo. | C: Contexto; demais detalhes ausentes em C, A e E |
| Variável-alvo | Regularização em até 30 dias após o contato, como objetivo preditivo. Definição operacional do evento, denominador e tratamento de casos sem seguimento não informados. | C: Proposta; A: D5:D6 |
| Quantidade de registros e composição das amostras | Não informadas. | A: B12; E: §2 |
| Partições de treino, validação e teste | Não informadas. | Ausente em C, A e E |
| Autorização e qualidade dos dados | Exige-se o uso de dados autorizados para a finalidade; comprovação da autorização, controles de acesso e relatórios de qualidade não disponibilizados. | C: Escopo e restrições; E: §4 |
| Código e execução experimental | Commit do experimento e Run ID do MLflow, quando disponível, não encaminhados. | E: §3 |

O arquivo de resultados contém indicadores agregados, não uma base de treinamento ou de avaliação em nível de registro. O documento de contexto é identificado como material de simulação; isso não comprova que o modelo tenha sido treinado com dados sintéticos nem que os indicadores tenham origem em um experimento real. Os identificadores dos arquivos recebidos, calculados no Evidence Register, não substituem a versão do modelo, o hash do snapshot ou o commit de código.

## 3. Metodologia

### 3.1 O que está documentado

- Abordagem proposta: modelo preditivo para estimar a chance de regularização após o contato e apoiar a priorização de contratos em atraso. [C: Proposta]
- Comparador: regra operacional vigente por tempo de atraso e valor devido. [C: Contexto; Objetivo de negócio]
- Resultado de avaliação apresentado: comparação agregada da taxa de regularização em até 30 dias, com diferença estimada e intervalo de confiança de 95% informado para a diferença. [A: A4:D9; E: §1–2]

### 3.2 O que precisa ser recuperado ou definido

| Componente | Status |
| --- | --- |
| Família de algoritmo, arquitetura, hiperparâmetros, bibliotecas e versões | Não informados. |
| Preparação dos dados, seleção de atributos e tratamento de ausências | Não informados. |
| Protocolo de treinamento, validação, divisão temporal, prevenção de vazamento de dados e sementes | Não informado. |
| Desenho da avaliação (retrospectiva, simulação ou experimento), comparabilidade das populações, denominadores e método de cálculo do IC | Não informado. |
| Definição da capacidade de contato, política de seleção dos contratos e tratamento das revisões humanas | Não informada em nível operacional. |
| Estratégia de calibração e conversão da estimativa em ordenação da fila | Não informada. |

**Fonte das lacunas:** C, A e E não detalham esses componentes. A: B12:B13 e E: §2 confirmam especificamente a ausência de tamanho de amostra e metodologia de avaliação.

Não é possível reproduzir o treinamento, verificar a validade do protocolo de avaliação ou atribuir o resultado a uma versão específica do modelo com os arquivos disponibilizados.

## 4. Métricas e resultados da avaliação

| Indicador | Resultado informado | Fonte |
| --- | ---: | --- |
| Taxa de regularização em até 30 dias: regra atual (baseline) | 12% | A: B5, C5, D5 |
| Taxa de regularização em até 30 dias: modelo proposto | 14% | A: B6, C6, D6 |
| Diferença estimada (modelo menos baseline) | +2,0 p.p. | A: B7, C7, D7 |
| IC de 95% da diferença: limite inferior | −0,4 p.p. | A: B8:D8 |
| IC de 95% da diferença: limite superior | +4,4 p.p. | A: B9:D9 |

*IC: intervalo de confiança. p.p.: pontos percentuais.*

**Verificação aritmética:** a diferença de 2,0 p.p. é consistente com as taxas informadas. A célula B7 contém a fórmula `=(B6-B5)*100`. Os limites do IC são valores registrados na planilha, sem fórmula de estimação associada. Não houve recálculo independente do IC.

**Interpretação técnica:** a estimativa pontual favorece o modelo. Contudo, o intervalo informado contém zero e valores negativos, portanto também é compatível com ausência de ganho ou com redução da taxa. Caso o IC tenha sido validamente construído para a diferença, ele não sustenta uma conclusão de superioridade em um teste bilateral ao nível de 5%. Essa interpretação é condicional à validade metodológica, que ainda precisa ser verificada. Não demonstra equivalência ou não inferioridade, tampouco um efeito causal do contato ou da mudança na fila. [Análise técnica de A: B5:B9; E: §2]

### Métricas e avaliações ausentes

| Avaliação | Situação atual | Validação recomendada (proposta) |
| --- | --- | --- |
| Tamanho das amostras e método do IC | Não informados. [A: B12:B13] | Recuperar numeradores, denominadores, desenho amostral, cálculo da incerteza e relatório metodológico. |
| Desempenho por segmentos | Não disponibilizado. [A: B14] | Avaliar resultados, cobertura e incerteza por segmentos relevantes e autorizados. |
| Custos e capacidade | Avaliação de custos não disponibilizada; comparabilidade de capacidade não demonstrada. [A: B15; C: Proposta] | Medir volume de contatos, esforço de revisão, custos totais e custo por regularização, sob capacidade comparável. |
| Discriminação, calibração e qualidade do ranking | Não informadas. [Ausente em C, A e E] | Avaliar métricas adequadas ao ranking sob a capacidade disponível (ex. taxa de regularização no top-K), qualidade preditiva e calibração se a saída representar probabilidade. |
| Impactos sobre clientes | Avaliação requerida, resultados não disponibilizados. [C: Condições para avaliação] | Verificar diferenças de tratamento, exposição a contatos, reclamações e outros efeitos relevantes, com critérios aprovados por Risco/Compliance. |
| Piloto controlado | Não executado. [A: B16] | Definir e submeter um desenho controlado para autorização, com protocolo de acompanhamento e revisão humana. |

Não há metas quantitativas de aceite, margem de não inferioridade ou limiares de monitoramento aprovados nos anexos. Nenhum valor deve ser presumido a partir do resultado de 14%.

## 5. Limitações e riscos

As limitações explicitamente comunicadas estão indicadas como documentadas. Os demais riscos são hipóteses técnicas para validação, não ocorrências comprovadas. Os controles são propostas, salvo as restrições expressas do contexto.

| Limitação ou risco | Base | Consequência e controle |
| --- | --- | --- |
| Mudança no perfil da carteira (possível drift) | Documentado em E: §4 | Pode comprometer a qualidade das previsões. Proposta: monitorar composição da carteira e desempenho ao longo do tempo. |
| Lacunas nos dados | Documentado em E: §4 | Podem deteriorar previsões. Proposta: testes de completude, consistência e regras de tratamento de falhas. |
| Incerteza estatística e atribuição causal indevida | A: B7:B13; E: §2 | Benefício não demonstrado. Proposta: avaliação reprodutível e piloto controlado antes de considerar ampliação. |
| Seleção histórica de contratos e possível viés de contato | Hipótese técnica baseada em C: Contexto; Proposta; E: §2 | Probabilidade de regularização após contato não é necessariamente ganho incremental causado pelo contato. Proposta: verificar seleção, comparabilidade e desenho causal. |
| Segmentos com desempenho desigual ou efeitos adversos | Hipótese técnica baseada em C: Condições para avaliação; A: B14 | Risco de priorização inadequada, exclusão de determinados contratos ou tratamento desproporcional. Proposta: avaliação segmentada e revisão de impactos. |
| Aumento de custo ou sobrecarga operacional | C: Objetivo de negócio; A: B15 | A economia/eficiência não foi demonstrada. Proposta: contabilizar recursos e custos, inclusive revisão humana. |
| Uso de dados não autorizados ou extrapolação de finalidade | Restrição em C: Escopo e restrições; hipótese quanto à ocorrência | Proposta: verificar autorização, necessidade, acesso e retenção de dados antes do uso. |
| Falta de rastreabilidade e de reprodutibilidade | Documentado em E: §3 | Impede vincular os resultados a dados, código e modelo específicos. Proposta: recuperar os identificadores e preservar artefatos. |
| Dependência indevida da recomendação | Hipótese técnica baseada em C: Escopo e restrições | Proposta: manter revisão humana efetiva, registrar alterações na fila e prever retorno à regra vigente em caso de falha. |

## 6. Usos permitidos e usos não autorizados

**Escopo de uso previsto, condicionado à autorização aplicável:** estimar a chance de regularização em até 30 dias após contato; apoiar a ordenação da fila de contratos em atraso; fornecer recomendação sujeita à revisão da equipe de cobrança, usando somente dados autorizados e capacidade comparável à atual. [C: Proposta; Escopo e restrições]

Esses usos são compatíveis com a finalidade prevista, mas não constituem autorização para executar o piloto ou implantar o modelo. A autorização formal de ambas as etapas não foi concedida segundo a equipe técnica. [E: §5]

**Usos expressamente não autorizados:** [C: Escopo e restrições]

- Disparar contatos automaticamente.
- Aplicar sanções.
- Alterar contratos.
- Decidir condições de negociação.
- Utilizar dados não autorizados para a finalidade.

**Outras restrições propostas para revisão:** não empregar o modelo em outras populações, finalidades ou decisões automatizadas sem nova avaliação; não utilizar a recomendação como substituto da revisão humana; não ampliar volume de contato com base apenas no score. Essas restrições adicionais são recomendações de governança, não novas aprovações ou políticas já estabelecidas.

## 7. Situação de governança e próximos passos

- **Recomendação registrada pela Engenharia de IA:** preparar um piloto controlado, com mesma capacidade de contato, revisão humana da fila e critérios de acompanhamento. [E: §5]
- **Condições de negócio:** avaliar desempenho agregado e segmentado, capacidade, custos e potenciais efeitos nos clientes. [C: Condições para avaliação]
- **Instâncias de análise:** Negócio, Dados e IA e Risco/Compliance. A equipe de cobrança realiza a revisão da fila. Não há nomes de responsáveis, pareceres individuais ou registros formais de aprovação. [C: Escopo e restrições; Condições para avaliação; E: §5]
- **Proposta desta documentação:** manter a regra atual para operação e tratar o modelo como candidato à avaliação; condicionar qualquer piloto a critérios e autorizações formais e qualquer implantação a nova decisão baseada em evidências do piloto.

Consultar o [Decision Record](decision_record.md) para as condições recomendadas e o [Evidence Register](evidence_register.md) para a rastreabilidade e as pendências.

## 8. Fontes e convenções

- **C:** `Contexto_Projeto.docx`, documento de Operações de Cobrança, seções indicadas neste card e nota final sobre simulação.
- **A:** `Resultados_Avaliacao.xlsx`, única aba `Avaliação`, células e intervalos indicados neste card.
- **E:** `Email_Equipe_Tecnica.txt`, de Engenharia de IA, assunto `Priorização de cobrança | Pendências da avaliação`. §1: linha 7; §2: linha 9; §3: linha 11; §4: linha 13; §5: linha 15 (parágrafos substantivos do e-mail).

C, A e E são referências documentais locais, não identificadores de experimentos. As interpretações e propostas explicitamente sinalizadas foram elaboradas para esta documentação, sem evidência de que tenham sido executadas ou aprovadas. Não foram utilizadas fontes externas.
