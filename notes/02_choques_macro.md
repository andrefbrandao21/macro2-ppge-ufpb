# Notas de Aula: Macroeconomia II – Choques Macroeconômicos e sua Propagação
### Baseado em: Ramey, V.A. (2016). "Macroeconomic Shocks and Their Propagation". *Handbook of Macroeconomics*, Vol. 2A.

---

## 1. Introdução: O Problema dos Impulsos e da Propagação

A macroeconomia moderna distingue dois conceitos centrais no estudo dos ciclos econômicos:

- **Choque (impulso):** Uma perturbação exógena e primitiva que inicia o movimento do sistema.
- **Mecanismo de propagação:** A estrutura do modelo que amplifica e transmite o choque ao longo do tempo.

A intuição seminal vem de Slutsky (1927) e Frisch (1933): somas de causas aleatórias podem gerar séries temporais que se assemelham a ciclos econômicos. A questão empírica central é: **quais são essas causas aleatórias?**

> **Intuição:** O modelo macroeconômico é como uma caixa de ressonância. O choque é a pancada; o mecanismo de propagação determina como o som ecoa e se dissipa.

---

## 2. Métodos de Identificação de Choques

### 2.1 O que é um Choque Macroeconômico?

Um choque macroeconômico deve satisfazer três propriedades:

1. **Exogeneidade:** Ser exógeno às variáveis endógenas contemporâneas e defasadas do modelo.
2. **Ortogonalidade:** Não ser correlacionado com outros choques exógenos.
3. **Surpresa ou Notícia:** Representar movimentos não antecipados em variáveis exógenas, ou *news* sobre movimentos futuros.

> **Importante:** Choques são distintos de *inovações* (resíduos de um VAR em forma reduzida) e de *instrumentos*. A identificação consiste em mapear uns nos outros com restrições econômicas críveis.

### 2.2 Framework Ilustrativo

Considere um sistema estático com três variáveis — impostos ($\tau$), gastos do governo ($g$) e produto ($y$):

$$\tau_t = b_{\tau g} g_t + b_{\tau y} y_t + \varepsilon_t^\tau$$
$$g_t = b_{g\tau} \tau_t + b_{gy} y_t + \varepsilon_t^g$$
$$y_t = b_{y\tau} \tau_t + b_{yg} g_t + \varepsilon_t^y$$

Os $\varepsilon$'s são os **choques estruturais** que buscamos identificar. O problema: as variáveis são mutuamente determinadas, tornando MQO viesado. Precisamos de **restrições adicionais** para identificar os parâmetros $b$ e os choques $\varepsilon$.

**Versão dinâmica (SVAR):** O modelo geral é:

$$Y_t = B(L)Y_t + \Omega\varepsilon_t$$

onde $B(L)$ é um polinômio no operador de defasagem. A forma reduzida equivalente é:

$$A(L)Y_t = \eta_t$$

A ligação entre inovações da forma reduzida ($\eta_t$) e choques estruturais ($\varepsilon_t$) é:

$$\eta_t = H\varepsilon_t, \quad \text{onde } H = (I - B_0)^{-1}\Omega$$

Escrito explicitamente para um sistema trivariado:

$$\eta_{1t} = b_{12}\eta_{2t} + b_{13}\eta_{3t} + \varepsilon_{1t}$$
$$\eta_{2t} = b_{21}\eta_{1t} + b_{23}\eta_{3t} + \varepsilon_{2t}$$
$$\eta_{3t} = b_{31}\eta_{1t} + b_{32}\eta_{2t} + \varepsilon_{3t}$$

São necessárias **pelo menos 3 restrições adicionais** para identificar todos os três choques.

### 2.3 Métodos de Identificação

#### 2.3.1 Decomposição de Cholesky

O método mais comum. Impõe restrições recursivas de zeros contemporâneos. Duas alternativas:

**A. Variável de política não responde a outras variáveis no período corrente** (política ordenada primeiro):
$$b_{12} = b_{13} = 0$$

**B. Outras variáveis não respondem ao choque de política no período corrente** (política ordenada por último):
$$b_{21} = b_{31} = 0$$

> **Cuidado:** A *recursiveness assumption* não é inocente. Modelos DSGE neo-keynesianos estimados (Smets–Wouters, 2007) implicam resposta imediata de produto e inflação ao choque monetário, contradizendo a restrição $b_{12} = 0$.

#### 2.3.2 SVAR com Restrições Contemporâneas Gerais

Generalização do Cholesky. Usa teoria econômica ou estimativas externas para restringir parâmetros. Exemplo: Blanchard e Perotti (2002) impõem $b_{13} = 2{,}08$ (elasticidade cíclica dos impostos líquidos ao produto, estimada externamente).

#### 2.3.3 Métodos Narrativos

Constroem séries de choques a partir de documentos históricos (atas do Fed, legislação, cobertura jornalística). Exemplos clássicos: Friedman e Schwartz (1963), Romer e Romer (1989, 2004, 2010), Ramey e Shapiro (1998).

> **Atenção:** A narrativa por si só **não garante exogeneidade**. Se a série narrativa inclui eventos motivados por deterioração econômica futura, ela captura resposta endógena — não choque exógeno.

#### 2.3.4 High-Frequency Identification (HFI)

Usa dados de alta frequência (diários ou intra-diários) em torno de anúncios de política monetária (reuniões do FOMC) e movimentos em contratos futuros de juros para identificar surpresas de política. A identificação por timing de alta frequência é mais plausível do que a mensal ou trimestral.

#### 2.3.5 Instrumentos Externos / Proxy SVARs

Método de Stock e Watson (2008) e Mertens e Ravn (2013). O instrumento externo $Z_t$ é válido se:

$$E[Z_t \varepsilon_{1t}] \neq 0 \quad \text{(relevância)}$$
$$E[Z_t \varepsilon_{it}] = 0, \quad i = 2, 3 \quad \text{(exogeneidade)}$$

**Procedimento:**
1. Estimar o sistema em forma reduzida para obter $\hat{\eta}_t$.
2. Regredir $\eta_{2t}$ e $\eta_{3t}$ em $\eta_{1t}$ usando $Z_t$ como instrumento → estima $b_{21}$ e $b_{31}$.
3. Regredir $\eta_{1t}$ em $\eta_{2t}$ e $\eta_{3t}$ usando resíduos da etapa 2 como instrumentos → estima $b_{12}$ e $b_{13}$.

#### 2.3.6 Restrições de Longo Prazo

Identifica choques por restrições no horizonte infinito. Galí (1999): choque de tecnologia é o único com efeito permanente sobre produtividade do trabalho. Formalmente, impõe $D_{12}(1) = 0$ e $D_{13}(1) = 0$ na representação de médias móveis:

$$Y_t = D(L)\varepsilon_t$$

**Problemas:** sensibilidade a premissas sobre raízes unitárias; distorções em amostras pequenas.

**Alternativa de horizonte finito** (Francis et al., 2014): identifica o choque que **maximiza** a parcela da variância do erro de previsão da produtividade do trabalho num horizonte finito $h$.

#### 2.3.7 Restrições de Sinal

Uhlig (1997, 2005): identifica o choque monetário contracionista como aquele que **não aumenta** os preços. Permite identificação parcial sem restringir as variáveis de interesse (produto). Produz conjuntos de confiança em vez de estimativas pontuais.

#### 2.3.8 FAVARs

Bernanke, Boivin e Eliasz (2005): inclui fatores latentes extraídos de mais de 100 séries no VAR, reduzindo o problema de omissão de variáveis relevantes. Continua usando Cholesky na maioria das implementações.

#### 2.3.9 Modelos DSGE Estimados

Smets e Wouters (2003, 2007): estima um modelo DSGE neo-keynesiano completo por métodos bayesianos e extrai o conjunto completo de choques implícitos. A identificação vem da estrutura teórica do modelo.

### 2.4 Estimação de Funções de Impulso-Resposta

**Método padrão (VAR):** As FIRs são funções não-lineares dos parâmetros da forma reduzida:

$$\frac{\partial Y_{i,t+h}}{\partial \varepsilon_{j,t}} = d_{ij,h}$$

onde $D(L) = C(L)H$ e $C(L) = [A(L)]^{-1}$.

**Método de Projeção Local (Jordà, 2005):** Estima diretamente a regressão para cada horizonte $h$:

$$Y_{i,t+h} = \theta_{i,h} \cdot \varepsilon_{1t} + \text{controles} + \xi_{t+h}$$

O coeficiente $\theta_{i,h}$ é a FIR no horizonte $h$. Vantagens: mais robusto a má-especificação do VAR; permite incorporar dependência de estado. Desvantagem: menos preciso (confidence bands mais largas).

> **Correção de erros-padrão:** Como $\xi_{t+h}$ é serialmente correlacionado (MA de ordem $h$), usar correção de Newey–West.

**Combinando Proxy SVAR com Projeção Local:**

$$Y_{i,t+h} = \theta_{i,h} Y_{1,t} + \text{controles} + \zeta_{t+h}$$

usando $Z_t$ como instrumento para $Y_{1,t}$ (variável de política).

### 2.5 O Problema da Previsibilidade (Foresight)

Dois tipos de *foresight* ameaçam a identificação:

**1. Foresight dos agentes privados:** Políticas frequentemente são antecipadas. Se o choque narrativo $\hat{\varepsilon}_{ft}$ contém a antecipação dos agentes, o VAR produz representação de médias móveis não-fundamental — os resíduos da forma reduzida não são invertíveis nos choques verdadeiros.

Exemplo (Leeper et al., 2013): com antecipação de 2 períodos, a acumulação ótima de capital segue:
$$k_t = \alpha k_{t-1} + \varepsilon_{A,t} - \bar{k}\{\varepsilon_{\tau,t-1} + \theta\varepsilon_{\tau,t}\}$$
onde $\theta = (\alpha\beta)^{1-\tau} < 1$. A representação **não é invertível**, e regredir $k_t$ em seus próprios defasados recupera "notícias velhas".

**2. Foresight do policymaker:** O Banco Central ou governo usa mais informação do que o VAR captura. O choque identificado $\tilde{\varepsilon}_{ft}$ confunde o verdadeiro choque com a resposta sistemática à informação superior:

$$\tilde{\varepsilon}_{ft} = \varepsilon_{ft} + \alpha_1\left(E_t^f[\Delta_h y_{t+h}] - E_t^p[\Delta_h y_{t+h}]\right) + \alpha_2\left(E_t^f[\Delta_h\pi_{t+h}] - E_t^p[\Delta_h\pi_{t+h}]\right)$$

**Soluções:** medir expectativas diretamente (previsões Greenbook, futuros de taxa de juros, spreads de títulos); incluir séries narrativas de notícias (news); usar EVARs (*Expectational VARs*, Perotti, 2011).

### 2.6 O Problema das Tendências

Variáveis macroeconômicas são não-estacionárias. Sims, Stock e Watson (1990): estimar em log-níveis fornece estimativas consistentes mesmo com raízes unitárias e cointegração. Impor raízes unitárias aumenta eficiência, mas pode causar distorções sérias (Elliott, 1998; Gospodinov et al., 2013). Recomendação geral: estimar em log-níveis com tendências determinísticas.

---

## 3. Choques de Política Monetária

### 3.1 Definição e Relevância

Choques monetários são **desvios da regra sistemática de política**. Se a política monetária é bem conduzida, esses choques são raros. Seu valor empírico é como **instrumento** para identificar o efeito causal da política monetária — não como fonte primária de flutuações.

### 3.2 O Benchmark de Christiano, Eichenbaum e Evans (1999)

**Especificação:** VAR com blocos recursivos:
- Bloco 1 (não responde ao choque no período): produção industrial, preços, preços de commodities.
- Bloco 2 (variável de política): *federal funds rate* (FFR).
- Bloco 3: agregados monetários (M1, reservas).

**Hipótese de Recursividade:** $b_{12} = b_{13} = 0$ — produto e preços não respondem ao choque monetário no mesmo período.

**Resultado principal (amostra 1965–1995):** Um choque contracionista que eleva a FFR em 100 pb causa queda de $\approx 0{,}7\%$ na produção industrial com defasagem de $\approx 8$ trimestres. Resultado robusto a diversas especificações.

**Problema com amostras recentes (1983–2007):** Os resultados se invertem — choques contracionistas parecem ter efeitos expansionistas. Interpretação: a política monetária passou a ser conduzida de forma mais sistemática, tornando os verdadeiros choques raros e difíceis de identificar.

### 3.3 Romer e Romer (2004): Identificação Narrativa + Greenbook

**Construção do choque:**
1. Derivar série de mudanças intencionadas na FFR nas reuniões do FOMC (método narrativo).
2. Regredir a mudança intencional nas previsões Greenbook do Fed para inflação e produto:

$$\Delta ff_t^{meta} = \alpha + \beta \cdot E_t^{Fed}[\Delta_h y_{t+h}] + \gamma \cdot E_t^{Fed}[\Delta_h \pi_{t+h}] + \hat{\varepsilon}_t^{RR}$$

O resíduo $\hat{\varepsilon}_t^{RR}$ é o choque monetário — movimento na FFR ortogonal às previsões do Fed sobre o estado futuro da economia.

**Resultado:** efeito sobre a produção industrial de $\approx 4{,}3\%$ de queda no vale (muito maior que CEE). Coibion (2012) mostra que parte da diferença deve-se à maior persistência do choque R&R na FFR e à sensibilidade ao período 1979–82.

**Reconciliação (Coibion, 2012):** Usando o VAR híbrido de R&R, a queda da produção industrial é de $\approx 2\%$ no vale a $\approx 18$ meses — resultado "médio", consistente com outras especificações.

### 3.4 Gertler e Karadi (2015): HFI + Proxy SVAR

**Instrumento:** Variação em futuros de FFR em janelas estreitas em torno de reuniões do FOMC (3 meses à frente, $ff4\_tc$).

**Modelo:** VAR com produção industrial, CPI, *excess bond premium* (Gilchrist–Zakrajšek, 2012) e taxa de juros de 1 ano, estimado de 1979–2012; instrumento disponível a partir de 1991.

**Resultado (Proxy SVAR):** Choque que eleva a FFR em 100 pb reduz a produção industrial em $\approx 2{,}2\%$ em 18 meses.

**Resultado (Projeção Local de Jordà):** Muito diferente — produção não cai por um ano, depois sobe. Possível explicação: *forward guidance* crescente torna o VAR mal-especificado (representação de médias móveis não-fundamental).

### 3.5 Síntese: Choques Monetários

| Método | Amostra | Queda pico (produção) | Puzzle de Preço |
|:---|:---|:---|:---|
| CEE (1999) — Cholesky | 1965–1995 | 0,7% em 8T | Sim |
| Romer–Romer (2004) | 1970–1996 | 4,3% em 24M | Não (com Greenbook) |
| Coibion (2012) — VAR híbrido | 1970–1996 | 2% em 18M | Parcial |
| Gertler–Karadi (2015) — Proxy SVAR | 1991–2012 | 2,2% em 18M | Não |
| Uhlig (2005) — Sign restrictions | 1965–1996 | Positiva (n.s.) | Não |
| Smets–Wouters (2007) — DSGE | 1966–2004 | 1,8% em 4T | Não |

> **Conclusão:** Choques monetários provavelmente **não são fonte primária de instabilidade macroeconômica** nos dados recentes. Seu valor principal é como instrumento para identificar o canal causal da política monetária sobre o produto.

---

## 4. Choques Fiscais

### 4.1 Choques de Gastos do Governo

#### 4.1.1 Métodos de Identificação

**Método de Blanchard–Perotti (2002):** SVAR com gastos ordenados primeiro no Cholesky ($b_{21} = b_{23} = 0$) — premissa: gastos não respondem a movimentos contemporâneos do produto ou impostos.

**Método Narrativo (Ramey–Shapiro, 1998; Ramey, 2011):** Séries de notícias sobre gastos militares construídas a partir de documentos históricos. A variável captura o **valor presente esperado** de mudanças nos gastos governamentais causadas por eventos militares — identificando o componente não antecipado e exógeno ao ciclo econômico.

**Argumento central de Ramey (2011):** A maioria dos gastos públicos é antecipada com vários trimestres de antecedência. Os choques Blanchard–Perotti são Granger-causados pela variável de notícias militares — evidência de que o SVAR padrão identifica choques já antecipados, não surpresas.

**Ben Zeev e Pappa:** Identificação por horizonte médio — choque de gastos em defesa que: (i) é ortogonal ao nível corrente de gastos; e (ii) maximiza a explicação dos movimentos futuros de defesa num horizonte de 5 anos.

#### 4.1.2 Cálculo do Multiplicador Fiscal

O multiplicador correto não é pico-a-impacto, mas a **razão de integrais**:

$$m_h = \frac{\sum_{i=0}^{h} \hat{Y}_{t+i}}{\sum_{i=0}^{h} \hat{G}_{t+i}}$$

Em termos de estimação por IV (método de uma etapa):

$$\sum_{i=0}^{h} z_{t+i} = \beta_h + m_h \sum_{i=0}^{h} g_{t+i} + \chi_h(L)y_{t-1} + \text{tendência} + \nu_{t+h}$$

usando o choque identificado como instrumento para a soma dos gastos. O coeficiente $m_h$ é o **multiplicador no horizonte** $h$ com erro-padrão direto.

**Relevância dos instrumentos:** A estatística $F$ de primeiro estágio deve superar os limiares de Montiel Olea e Pflueger (2013): 23 (nível 10%) e 37 (nível 5%), que corrigem para correlação serial.

#### 4.1.3 Resultados Empíricos dos Gastos

**Resposta qualitativa:**
- Blanchard–Perotti: produto, horas e **consumo** sobem; salário real sobe. Inconsistente com modelos neoclássicos/NK padrão.
- Ramey news e Ben Zeev–Pappa: produto e horas sobem; consumo **cai**; salário real **cai**. Consistente com modelos neoclássicos.

A discrepância é explicada pelo problema de *foresight*: tratar um choque antecipado como não antecipado produz artificialmente uma alta no consumo (Ramey, 2009 — simulação DSGE).

**Multiplicadores estimados:**

| Identificação | Horizonte | Multiplicador |
|:---|:---|:---|
| Blanchard–Perotti | 8–20T | 0,37–0,44 |
| Ramey news | 8T | 0,80 |
| Ramey news | 16T | 0,60 |
| Ben Zeev–Pappa news | 8T | 1,41 |
| Ben Zeev–Pappa news | 16T | 1,10 |

> **Metanálise (Gechert, 2015):** Multiplicadores de gastos públicos próximos a 1; investimento público próximo a 1,5. A maioria dos estudos encontra multiplicadores entre 0,6 e 1,5.

> **Nota metodológica:** Multiplicadores estimados em estados ou regiões (cross-state) são sistematicamente maiores que os agregados porque diferenciam o financiamento federal — não são diretamente comparáveis.

### 4.2 Choques de Impostos

#### 4.2.1 Choques Não Antecipados

**Blanchard–Perotti (2002):** Impõe elasticidade dos impostos líquidos ao produto $b_{13} = 2{,}08$ (estimada externamente). Multiplicador implícito: 0,78–1,33.

**Romer e Romer (2010):** Identificação narrativa baseada em documentos legislativos. Seleciona mudanças tributárias motivadas por redução de déficit ou crescimento de longo prazo (exógenas ao ciclo). Multiplicador: 2,5–3 em 3 anos.

**Mertens e Ravn (2014) — Proxy SVAR para impostos:** Usa série narrativa de R&R como instrumento externo. Estima $b_{13} = 3{,}13$ (I.C. 95%: $[2{,}73;\; 3{,}55]$) — Blanchard–Perotti subestimava a elasticidade, viesando o multiplicador para baixo.

**Mecanismo:** Subestimar a elasticidade dos impostos ao produto deixa o choque identificado contaminado por causalidade reversa (expansão do produto → maiores receitas tributárias), gerando viés de atenuação no multiplicador.

#### 4.2.2 Choques Antecipados (News Fiscais)

Mertens e Ravn (2011, 2012): separam choques R&R em antecipados (legislados mais de 90 dias antes da implementação) e não antecipados. Resultado: evidência forte de **substituição intertemporal**.

Resposta a uma **antecipação de aumento de impostos futuro**:
- **Antes da implementação (período de notícia):** produto, horas, investimento e consumo de duráveis **sobem** (agentes intertemporalmente substituem atividade tributável para o presente).
- **Após a implementação:** todas as variáveis **caem**.

> Este é um dos resultados mais robustos do capítulo: notícias sobre impostos futuros geram expansão presente seguida de contração — evidência direta de que *news* dirigem flutuações econômicas.

**Leeper, Richter e Walker (2012):** constroem medida alternativa de expectativas de impostos futuros usando spread entre títulos federais e municipais (AFTR15). Resultados qualitativamente idênticos.

| Método | Multiplicador de impostos |
|:---|:---|
| Blanchard–Perotti (2002) | 0,78–1,33 |
| Mountford–Uhlig (2009) | 5 (corte financiado por déficit) |
| Romer–Romer (2010) | 2,5–3 |
| Barro–Redlick (2011) | 1,1 |
| Mertens–Ravn (2014) — Proxy SVAR | 3 em 6 trimestres |

---

## 5. Choques de Tecnologia

### 5.1 Tecnologia Neutra (TFP)

Função de produção agregada padrão:
$$Y_t = A_t F(L_t, K_t)$$

Kydland e Prescott (1982): choques à TFP ($A_t$) podem replicar flutuações do ciclo econômico.

**Problemas com o Resíduo de Solow como proxy de TFP:**
- É Granger-causado por variáveis de política (Evans, 1992).
- Captura variações de utilização de capital e trabalho — componente endógeno.
- Basu et al. (2006): após ajustar para utilização, TFP positiva **reduz** horas trabalhadas (resultado contracionista a curto prazo).

**Identificação por restrição de longo prazo (Galí, 1999):** Tecnologia é o único choque com efeito permanente sobre produtividade do trabalho. VAR bivariado com produtividade e horas, impondo $D_{12}(1) = 0$.

**Debate sobre horas:**
- Galí (1999), Basu et al. (2006): choque tecnológico positivo **reduz** horas no curto prazo (compatível com modelos NK com rigidez de preços).
- Christiano, Eichenbaum e Vigfusson (2003): assumindo horas estacionárias (sem raiz unitária), choque tecnológico **eleva** horas.
- Francis e Ramey (2009): controlando por efeito demográfico (baby boom), retorna ao resultado de queda nas horas.

**Identificação por horizonte médio (Francis et al., 2014):** Identifica choque que maximiza a parcela da variância do erro de previsão da produtividade no horizonte $h$. Mais robusto às controvérsias sobre raízes unitárias. Contribuição para variância de produto: 15–40%.

### 5.2 Tecnologia Específica ao Investimento (IST) e Eficiência Marginal do Investimento (MEI)

**Distinção conceitual:** Em Justiniano, Primiceri e Tambalotti (2011):

$$I_t = \Psi_t Y_t^I \quad \text{(IST: transforma bem final em bem de investimento)}$$
$$K_{t+1} = (1-\delta)K_t + \mu_t I_t \quad \text{(MEI: transforma investimento em capital instalado)}$$

$\Psi_t$ é IST — identificável pelo preço relativo do investimento. $\mu_t$ é MEI — não diretamente observável nos preços.

**Resultado:** Choques de MEI (não antecipados) explicam $\approx 60\%$ da variância do produto nos ciclos — a maior contribuição individual em modelos DSGE estimados.

**Ben Zeev e Khan (2015):** IST news shocks — identificados pelo método de horizonte médio de Barsky–Sims combinado com restrições sobre o preço relativo do investimento — explicam $\approx 73\%$ da variância do produto a 8 trimestres. São o candidato mais promissor para explicar comovimentos do ciclo (produto, horas, consumo e investimento sobem juntos).

### 5.3 Notícias sobre Tecnologia Futura (News Shocks)

Beaudry e Portier (2006): identificam choque que move preços de ações imediatamente mas não afeta TFP no impacto. Encontram que *news* explicam $\approx 50\%$ das flutuações. **Controvérsia:** Barsky e Sims (2011) e outros usam restrições de horizonte médio e encontram que *news* de TFP **reduzem** horas — não geram comovimento típico do ciclo. A questão permanece em aberto.

### 5.4 Correlações entre Choques Estimados

A tabela de correlações entre diferentes estimativas do mesmo tipo de choque revela um problema sério:

- Choques de TFP estimados por métodos distintos têm correlação elevada ($r > 0{,}6$) entre si.
- Mas choques de TFP *news* têm correlações próximas de **zero** entre diferentes métodos (Beaudry–Portier vs. Barsky–Sims: $r = 0{,}25$; ambos vs. Miyamoto–Nguyen DSGE: $r \approx 0$).
- Choques de IST e MEI de diferentes métodos têm correlações geralmente baixas.

> **Implicação:** Não há consenso sobre a natureza e importância dos choques de tecnologia. A baixa correlação entre estimativas sugere que ou os métodos de identificação capturam fenômenos distintos, ou muitos são contaminados por componentes endógenos.

**Teste de exogeneidade:** Vários choques estimados são serialmente correlacionados ou Granger-causados por produto, consumo e preços de ações — violando a propriedade fundamental de que um choque deve ser não antecipado.

---

## 6. Choques Adicionais

### 6.1 Choques de Petróleo

Hamilton (1983): choques de oferta de petróleo são causa importante de recessões. Debate subsequente sobre assimetrias (aumentos vs. quedas) e sobre a decomposição oferta/demanda. Kilian (2009): muitas variações no preço do petróleo são **choques de demanda** — identificação com petróleo ordenado primeiro no Cholesky é incorreta. Após identificação adequada, choques de oferta de petróleo explicam fração modesta da variância do produto.

### 6.2 Choques de Crédito

Gilchrist e Zakrajšek (2012): inovações no *excess bond premium* (EBP) — prêmio de risco dos títulos corporativos ortogonal ao estado corrente da economia — têm efeitos macroeconômicos significativos. Interpretado como choque à capacidade de absorção de risco do setor financeiro.

### 6.3 Choques de Incerteza

Papel crescente na literatura recente. Questão central: incerteza como mecanismo de propagação endógeno ou como choque exógeno independente?

### 6.4 Choques de Oferta de Trabalho (Wage Markup)

Em modelos DSGE estimados, *news* sobre markup de salários explicam parte expressiva da variância das horas (Schmitt-Grohé e Uribe, 2012; Khan e Tsoukalas, 2012). Questão aberta: são choques primitivos ou mecanismo de propagação mal identificado?

---

## 7. Síntese: Decomposição da Variância do Produto

Usando um VAR combinando os principais choques identificados (amostra 1954–2005):

| Choque | Produto (8T) | Horas (8T) |
|:---|:---|:---|
| Gastos militares (Ben Zeev–Pappa news) | 1,4% | 0,9% |
| Impostos futuros (Leeper–Richter–Walker) | 4,8% | 6,3% |
| Impostos não antecipados (Romer–Romer) | 1,5% | 0,9% |
| TFP (Francis et al., horizonte médio) | 13,9% | 2,4% |
| IST news (Ben Zeev–Khan) | **26,9%** | **39,5%** |
| MEI (Justiniano et al., DSGE) | 16,3% | 14,2% |
| Taxa de juros (FFR) | 6,1% | 10,9% |
| **Total** | **~71%** | **~75%** |

> **Conclusão principal:** Os três choques fiscais, os três choques de tecnologia e o choque monetário conjuntamente explicam 63–79% da variância de produto e horas em horizontes de 4 a 20 trimestres. Estamos substantivamente mais próximos de entender as "causas aleatórias" de Slutsky do que há 20 anos — mas há muito trabalho a fazer na verificação da plausibilidade das premissas de identificação.

---

## 8. Síntese Metodológica

| Método | Premissa central | Vulnerabilidade principal |
|:---|:---|:---|
| Cholesky | Ordenação recursiva contemporânea | *Recursiveness assumption* implausível em modelos NK |
| SVAR com restrições externas | Elasticidades calibradas externamente | Sensibilidade ao valor assumido (Caldara–Kamps, 2012) |
| Narrativo | Exogeneidade do evento histórico | Narrativa ≠ exogeneidade; contaminação endógena |
| HFI | Timing de alta frequência elimina antecipação | Informação superior do Fed; *forward guidance* |
| Proxy SVAR | Instrumento externo válido (relevância + exogeneidade) | Fraca relevância em muitas aplicações |
| Longo prazo | Choque de tecnologia único com efeito permanente | Dependência de premissas sobre raízes unitárias |
| Horizonte médio | Maximização da variância em horizonte finito | Resultado sensível à escolha do horizonte |
| Sign restrictions | Incorpora priors razoáveis sem circularidade | Identificação parcial; conjuntos de confiança largos |
| FAVARs | Condiciona em grande conjunto de informação | Ainda usa Cholesky; exige estacionariedade |
| DSGE estimado | Identificação pela estrutura teórica | Identificação indireta; sensível à especificação do modelo |

---

[^1]: A condição de Marshall-Lerner — presente nas notas IS-LM-BP — estabelece que a soma das elasticidades das exportações e importações ao câmbio real deve ser maior que a unidade para que uma depreciação melhore o saldo comercial. É análoga à condição $(X_\epsilon - M_\epsilon) > 0$ usada nas notas anteriores.