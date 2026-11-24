# Evidence Register | Priorização de cobrança

**Status:** registro preliminar de evidências e lacunas de rastreabilidade.  
**Cobertura:** três arquivos recebidos para análise. Nenhum dado em nível de registro, código experimental, artefato de modelo ou log de execução foi fornecido.  
**Conclusão:** é possível verificar o conteúdo dos documentos e a aritmética da diferença reportada; não é possível reproduzir os resultados da avaliação ou comprovar eficácia, custos, segurança de uso ou aprovação formal.

Documentos complementares: [Model Card](model_card.md) e [Decision Record](decision_record.md).

## 1. Inventário e integridade das fontes

| Referência local | Arquivo original | Origem declarada no material | Conteúdo |
| --- | --- | --- | --- |
| C | `Contexto_Projeto.docx` | Operações de Cobrança | Contexto, objetivo, proposta, escopo, restrições e condições de avaliação. Nota final: material de simulação para capacitação; não contém dados de clientes. |
| A | `Resultados_Avaliacao.xlsx` | Autor não identificado no conteúdo; a Engenharia de IA menciona a consolidação preliminar no e-mail E | Indicadores agregados, diferença estimada, IC de 95% informado e status de itens complementares. Uma aba: `Avaliação`. |
| E | `Email_Equipe_Tecnica.txt` | Remetente declarado: Engenharia de IA. Destinatários: Operações de Cobrança; Dados e IA; Risco e Compliance. | Consolidação preliminar, limitações metodológicas, identificadores não encaminhados, recomendação de piloto e ausência de aprovações formais. |

Versão formal e data de emissão dos documentos não foram identificadas no conteúdo substantivo. O e-mail foi recebido como arquivo de texto, sem cabeçalho de data, Message-ID ou cadeia de respostas. A autoria e a autenticidade não foram verificadas fora dos anexos. Não se inferem datas de experimentos a partir de metadados de arquivos.

### 1.1 Impressões digitais dos arquivos recebidos

SHA-256 calculado diretamente sobre os bytes de cada anexo nesta análise, para permitir verificar futuramente a identidade da cópia consultada.

| Arquivo | Tamanho em bytes | SHA-256 calculado |
| --- | ---: | --- |
| `Contexto_Projeto.docx` | 37454 | `961b5a29d2c728f706983d1545bde525d97c8dc353a1af39308852224f3b7862` |
| `Resultados_Avaliacao.xlsx` | 9026 | `747149ede3ae202e6aaa586f88e759013fa38b5fe6deedb7a69f59af9871c8d3` |
| `Email_Equipe_Tecnica.txt` | 1476 | `781583b160a02882889c8421f1e7910e9e1e905574ea390667bdf5d59e7467fd` |

**Atenção:** são hashes dos anexos, não do snapshot de dados, do código ou do modelo treinado. Não comprovam autenticidade, autoria, origem dos resultados ou validade do experimento. As referências C, A e E foram atribuídas apenas para organização documental e não correspondem a IDs de experimentos, tickets ou registros existentes.

## 2. Evidências disponíveis e grau de verificação

Convenções de status:

- **Documentado:** afirmação presente na fonte; não equivale a comprovação independente do fato operacional.
- **Reportado:** resultado ou status apresentado na fonte, ainda sem comprovação metodológica independente.
- **Verificado aritmeticamente:** cálculo conferido a partir dos valores fornecidos.
- **Não informado:** informação não encontrada no material; não significa que inexista.
- **Não disponibilizado:** artefato ou avaliação não encaminhado.
- **Não executado / não aprovado formalmente:** situação explicitamente informada na fonte.

| Evidência | Localização exata | Conteúdo disponível | Status e limite da evidência |
| --- | --- | --- | --- |
| Contexto operacional e baseline | C: Contexto | Capacidade limitada; fila ordenada por tempo de atraso e valor devido. | Documentado. Regra de cálculo e capacidade numérica não fornecidas. |
| Objetivo e finalidade | C: Proposta; Objetivo de negócio | Estimar chance de regularização em até 30 dias após contato; melhorar a taxa sem elevar custos ou ampliar riscos aos clientes. | Documentado como objetivo, não como resultado atingido. |
| Restrições e revisão humana | C: Escopo e restrições | Recomendação de priorização sujeita à revisão; restrições a contatos automáticos, sanções, alteração de contratos, condições de negociação e dados não autorizados. | Documentado como requisito; controles implantados não comprovados. |
| Critérios gerais de avaliação e instâncias de análise | C: Condições para avaliação | Desempenho agregado e segmentado, capacidade operacional, custos e efeitos nos clientes; análise de Negócio, Dados e IA e Risco/Compliance. | Documentado; critérios quantitativos e pareceres não fornecidos. |
| Comparação agregada | A: `Avaliação!A4:D9`; E: linhas 7 e 9 | Baseline 12%, modelo 14%, diferença +2,0 p.p., IC 95% de −0,4 a +4,4 p.p. | Reportado; diferença verificada aritmeticamente; IC não reproduzido. |
| Lacunas de avaliação | A: `Avaliação!A11:B16`; E: linha 9 | Ausência de tamanho das amostras, método de cálculo do IC, resultados por segmentos e custos; piloto não executado. | Status explicitamente reportados. |
| Identificadores técnicos ausentes | E: linha 11 | Versão do modelo, identificação e período do snapshot, hash, commit e Run ID do MLflow quando disponível. | Não encaminhados, conforme a Engenharia de IA. |
| Limitações do modelo | E: linha 13 | Mudanças no perfil da carteira e lacunas de dados podem comprometer previsões. | Documentado como risco; sem teste ou medição anexados. |
| Recomendação e situação de aprovações | E: linha 15; A: `Avaliação!B16` | Preparação de piloto controlado; sem aprovação formal do piloto ou da implantação geral; piloto não executado. | Recomendação documentada, não autorização nem execução. |
| Natureza do material | C: nota final | Simulação para capacitação; documento sem dados de clientes. | Documentado; não estabelece a procedência dos dados da avaliação. |

## 3. Registro de resultados

Fonte única dos valores: `Resultados_Avaliacao.xlsx`, aba `Avaliação`. A leitura incluiu conteúdo, valores e a fórmula da diferença. As taxas de 12% e 14% correspondem aos valores numéricos 0,12 e 0,14 exibidos em percentual.

| Indicador | Célula de valor | Valor | Unidade | Verificação |
| --- | --- | ---: | --- | --- |
| Regra atual (baseline) | B5 | 12 | % | Valor armazenado; não há numerador, denominador ou consulta de origem fornecidos. |
| Modelo proposto | B6 | 14 | % | Valor armazenado; não há identificação da versão do modelo avaliado ou registros subjacentes. |
| Diferença estimada | B7 | +2,0 | p.p. | Fórmula `=(B6-B5)*100`, conferida: 14% menos 12% = 2,0 p.p. |
| IC 95%: limite inferior | B8 | −0,4 | p.p. | Valor registrado diretamente; não há fórmula de estimação ou método fornecido. |
| IC 95%: limite superior | B9 | +4,4 | p.p. | Valor registrado diretamente; não há fórmula de estimação ou método fornecido. |

**Observação da planilha:** ambos os indicadores de taxa referem-se a regularização em até 30 dias (D5:D6); o IC refere-se à diferença (D8:D9). O contexto explicita a janela após o contato (C: Proposta). Não há protocolo que confirme a aplicação uniforme dessa janela na avaliação.

**Interpretação técnica:** o IC informado contém zero, logo a diferença pontual positiva não estabelece superioridade estatística se interpretada sob um procedimento bilateral válido. Não se pode afirmar causalidade, equivalência ou não inferioridade. A avaliação não pode ser reproduzida com as fontes atuais. [Análise de A: B5:B13; E: linha 9]

### 3.1 Itens complementares, conforme a planilha

| Item | Célula | Status literal da fonte |
| --- | --- | --- |
| Tamanho das amostras | B12 | Não informado |
| Método de cálculo do IC | B13 | Não informado |
| Avaliação por segmentos | B14 | Não disponibilizada |
| Avaliação de custos | B15 | Não disponibilizada |
| Piloto controlado | B16 | Não executado |

Não disponibilizado não significa necessariamente que a atividade não tenha sido realizada; apenas o piloto consta explicitamente como não executado.

## 4. Rastreabilidade de dados, código e experimentos

| Elemento necessário | Valor ou status atual | Fonte | Evidência a recuperar |
| --- | --- | --- | --- |
| Versão do modelo | Não informada | E: linha 11 | Identificador oficial da versão e vínculo com o artefato do modelo avaliado. |
| Artefato do modelo, URI e hash | Não disponibilizados | Nenhum artefato correspondente entre C, A e E | Referência ao artefato e mecanismo de integridade, quando aplicável. |
| Origem e versão das bases / snapshot | Não informadas | E: linha 11; C, A e E não identificam as bases | Manifesto das fontes, identificador e versão da extração. |
| Período do snapshot e janelas de treino, validação e teste | Não informados | E: linha 11; demais períodos ausentes em C, A e E | Datas de referência e janelas de observação e desfecho. |
| Hash do snapshot de dados | Não informado | E: linha 11 | Hash e algoritmo de integridade do snapshot efetivamente utilizado. |
| Dicionário, atributos, alvo e qualidade dos dados | Não disponibilizados em nível técnico | C: Proposta; Escopo e restrições; E: linha 13 | Dicionário, regras de elegibilidade, definição da regularização, relatório de qualidade e evidência de autorização dos dados. |
| Repositório e versão do código | Não informados | E: linha 11 menciona commit ausente; repositório não identificado nos anexos | Repositório e commit exato do código de treinamento e/ou avaliação usado. |
| Commit do código do experimento | Não informado | E: linha 11 | SHA do commit que reproduza a avaliação, vinculado à execução. |
| Experiment ID, nome do experimento e Run ID | Não informados | E: linha 11 confirma ausência do Run ID do MLflow, quando disponível; demais IDs não constam dos anexos | Identificação real do experimento e execução no sistema de rastreamento, se utilizado. Não presumir uso efetivo do MLflow. |
| Ambiente, dependências, configuração e sementes | Não informados | Ausente em C, A e E | Manifesto de dependências, ambiente e parâmetros necessários à reprodução. |
| Relatório metodológico e amostras | Não disponibilizados; tamanho não informado | E: linha 9; A: B12:B13 | Protocolo, numeradores e denominadores, critérios de seleção, cálculo do IC e resultados reproduzíveis. |
| Data de execução e responsável nominal pelo experimento | Não informados | Ausente em C, A e E | Registro de execução datado e responsável identificado. |
| Vínculo planilha → execução → modelo/código/dados | Não comprovado | A: A4:D9; E: linha 11 | Evidência que associe cada resultado à execução e aos respectivos artefatos versionados. |

A planilha isolada não é um registro de execução experimental. Não foi criado nenhum identificador de modelo, snapshot, commit ou experimento para preencher essas lacunas.

## 5. Consistências, inconsistências e questões abertas

| Ponto analisado | Diagnóstico | Fonte / ação requerida |
| --- | --- | --- |
| Aritmética das taxas | Consistente: 14% menos 12% = +2,0 p.p. | A: B5:B7; conferência realizada nesta análise. |
| IC e diferença pontual | Não há contradição numérica evidente: o IC contém a estimativa de +2,0 p.p. Sua validade estatística permanece desconhecida. | A: B7:B9, B12:B13; recuperar método, amostras e cálculo. |
| Resultado favorável versus evidência de ganho | Não é uma inconsistência aritmética. É uma limitação de interpretação: ganho pontual não equivale a eficácia comprovada. | A: B5:B9; E: linha 9; validar protocolo e incerteza. |
| Origem dos indicadores e piloto não executado | O valor de 14% não pode ser atribuído a um piloto controlado executado; o desenho que o produziu não está identificado. | A: B6, B16; E: linhas 7 e 9; recuperar natureza e período da avaliação. |
| Objetivo de negócio versus escopo avaliado | Custos, capacidade comparável, desempenho segmentado e efeitos sobre clientes são requisitos, mas não foram demonstrados nos anexos. | C: Objetivo de negócio; Condições para avaliação; A: B14:B15; E: linha 9. |
| Modelo preditivo versus impacto do contato | Estimar chance de regularização após contato não comprova que o contato ou a alteração da fila produzam ganho incremental. | C: Proposta; E: linha 9; definir hipótese e desenho de avaliação. |
| Material de capacitação versus procedência da avaliação | C é material de simulação, porém A e E não identificam a base que gerou os números. Não é possível afirmar que se trata de dados reais ou sintéticos. | C: nota final; A e E; recuperar origem dos indicadores. |
| Recomendação versus aprovação | Coerente: a Engenharia recomenda preparar piloto, declara não haver aprovação formal, e a planilha registra piloto não executado. | E: linha 15; A: B16. |

Não foram identificadas contradições materiais diretas entre os três anexos. A insuficiência está principalmente na cadeia de evidência, no desenho da avaliação e na ausência de validações complementares.

## 6. Pendências priorizadas de rastreabilidade e validação

A priorização, os responsáveis por área e a forma de encerramento abaixo são **propostas desta documentação**. Não representam atribuições formalizadas ou compromissos assumidos. P0: necessário para instruir adequadamente uma decisão de autorização de piloto; P1: evidência requerida antes de decisão sobre ampliação/implantação. Os critérios de aceite devem ser estabelecidos antes de iniciar o piloto.

| Prioridade | Pendência | Área sugerida | Evidência de encerramento |
| --- | --- | --- | --- |
| P0 | Identificar versão do modelo, dados, snapshot, período, hash, commit e execução experimental; recuperar artefatos. | Dados e IA / Engenharia de IA | Cadeia de rastreabilidade íntegra, com valores reais e referências aos artefatos. |
| P0 | Recuperar metodologia, amostras, desenho, definição de regularização e recálculo do IC. | Dados e IA | Relatório reproduzível que explique os valores de A e as condições de comparação. |
| P0 | Confirmar finalidade e autorização dos dados, qualidade e avaliação inicial de riscos aos clientes e segmentos. | Dados e IA; Risco/Compliance; Operações de Cobrança | Documentação dos dados, avaliação de qualidade e parecer sobre os riscos e medidas aplicáveis. |
| P0 | Definir população, capacidade de contato comparável, desenho, métricas, limites de aceite, acompanhamento e interrupção. | Operações de Cobrança; Dados e IA; Risco/Compliance | Protocolo de piloto formalmente submetido, com revisão humana e controles operacionais previstos. |
| P0 | Registrar manifestação e autorização explícita das áreas responsáveis. | Negócio; Dados e IA; Risco/Compliance | Registro datado, com decisores identificados, escopo e condições da autorização, ou decisão de não autorizar. |
| P1 | Executar piloto somente após autorização; medir resultados agregados e por segmentos, custos, capacidade e efeitos sobre clientes. | Operações de Cobrança; Dados e IA; Risco/Compliance | Relatório do piloto com denominadores, incerteza, custos, impactos e critérios de aceite avaliados. |
| P1 | Avaliar comportamento sob mudança de carteira, lacunas de dados, qualidade das previsões e sustentabilidade operacional. | Dados e IA; Operações de Cobrança | Testes, evidências de monitoramento e procedimento de interrupção/retorno à regra atual. |
| P1 | Obter nova decisão formal sobre eventual implantação geral, com condições de governança. | Negócio; Dados e IA; Risco/Compliance | Pareceres e decisão formal vinculados às evidências e versões efetivamente avaliadas. |

**Status de encerramento:** pendências abertas no material recebido. Não há comprovação de execução dessas ações. As condições de autorização e expansão são detalhadas no [Decision Record](decision_record.md).

## 7. Convenção de referência e manutenção

- **C:** `Contexto_Projeto.docx`, seção de mesmo nome indicada no registro.
- **A:** `Resultados_Avaliacao.xlsx`, aba `Avaliação`, células/ranges explicitados.
- **E:** `Email_Equipe_Tecnica.txt`, assunto `Priorização de cobrança | Pendências da avaliação`, com numeração de linhas físicas: 7 (consolidação), 9 (metodologia e causalidade), 11 (rastreabilidade), 13 (limitações), 15 (recomendação e aprovações).

Na atualização futura, registrar a fonte original, localização, versão real, resultado, data de coleta, responsável e status da validação. Preservar o histórico dos resultados e da decisão. A publicação deste registro não deve ser tratada como aprovação do modelo. Nenhuma fonte externa foi utilizada.
