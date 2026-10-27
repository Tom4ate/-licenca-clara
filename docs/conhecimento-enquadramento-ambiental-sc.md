# Enquadramento ambiental em Santa Catarina (CONSEMA)

Base de conhecimento para o motor de regras do Licença Clara. O documento explica **como uma atividade é enquadrada no licenciamento ambiental em SC** e o que o sistema precisa perguntar para chegar a esse enquadramento.

> **Status:** pesquisa feita em 26/10/2026 a partir do texto das resoluções publicado no LegisWeb e de páginas oficiais (links em [Fontes](#14-fontes)). As faixas numéricas de porte copiadas aqui **são incompletas** (ver [§6](#6-porte-do-empreendimento)). Antes de transformar qualquer número em regra no código, confira no texto oficial do DOE/SC e nas correções da Resolução CONSEMA 259/2024.
>
> O que motivou este documento está em [`feedback-especialista-enquadramento.md`](./feedback-especialista-enquadramento.md).

---

## 1. Resumo em uma página

1. **Quem define a lista:** o CONSEMA (Conselho Estadual do Meio Ambiente de SC). A lista diz quais atividades dependem de licença, com qual porte e com qual estudo.
2. **Normas vigentes:** **Resolução CONSEMA 250/2024** (lista geral do Estado) e **Resolução CONSEMA 251/2024** (lista de impacto local, licenciada pelos municípios). As duas **revogaram as Resoluções 98/2017 e 99/2017**, que ainda aparecem em muitos sites de prefeituras.
3. **O que define o enquadramento:** a atividade e a operação. Para cada código de atividade, a lista traz:
   - o **potencial poluidor** (ar, água, solo e geral, em P/M/G);
   - as faixas de **porte**, medidas por um parâmetro físico, em geral área útil em hectares;
   - a **modalidade** resultante (AuA, LAC ou LAP/LAI/LAO) e o **estudo** exigido (RAP, EAS ou EIA).
4. **Documentos da empresa não mudam o enquadramento.** Alvará, Bombeiros, contrato social e similares não entram nessa conta. Eles só servem para montar o processo, e portanto o orçamento.
5. **Resultados possíveis:**
   - atividade **não listada**: DANC;
   - atividade listada, mas **abaixo do porte**: CCA;
   - porte **mínimo ou único**: AuA;
   - alguns códigos: LAC;
   - demais casos: licenciamento trifásico (LAP, LAI e LAO) com RAP, EAS ou EIA/RIMA;
   - empresa **já operando sem licença**: LAO de regularização com ECA.
6. **Quem licencia:** um único órgão por empreendimento, o competente para a atividade de maior impacto. É o município, se a atividade for de impacto local e o município estiver habilitado no nível exigido. Caso contrário, é o IMA. Itajaí, Balneário Camboriú e Camboriú estão habilitados no nível III (§3).

---

## 2. Normas que importam

| Norma | O que faz | Observação para o sistema |
|---|---|---|
| **LC federal 140/2011** | Divide as competências de licenciamento entre União, Estados e Municípios. Atribui aos conselhos estaduais a tipologia de impacto local. | Base da divisão entre IMA e município. |
| **Lei estadual 14.675/2009** (Código Estadual do Meio Ambiente) | Prevê as modalidades LAP, LAI, LAO, AuA e LAC. | Referência legal das modalidades. |
| **CONAMA 237/1997** | Conceitos gerais de licença e licenciamento. | Citada pelas prefeituras. |
| **CONSEMA 250/2024** (08/08/2024) | Procedimentos, definições, estudos e **lista estadual de atividades licenciáveis (Anexo VI)**, mais os parâmetros técnicos (Anexo VII). Revoga a 98/2017 e a 99/2017 (art. 43). | **Fonte principal do motor de regras.** |
| **CONSEMA 251/2024** (12/08/2024) | Lista de atividades de **impacto local**, licenciadas pelo município, em **3 níveis de complexidade** (Capítulos I, II e III do Anexo I). Usa as definições da 250. | Define se o município pode licenciar. |
| **CONSEMA 259/2024** (15/10/2024) | Corrige portes e potenciais poluidores de atividades da 250 e da 251. | **As faixas precisam vir do texto já corrigido.** |
| **CONSEMA 309/2026** (08/05/2026, DOE 11/05/2026) | Critérios para o município exercer o licenciamento de impacto local: estrutura técnica, conselho, sistema eletrônico e fiscalização. Revoga as Resoluções 117/2017 e 167/2020. | Pode mudar quais municípios estão habilitados. Acompanhar. |
| **Portaria IMA 229/2019** e **Portaria IMA 106/2020** | Lista de **CNAEs** ligados às atividades licenciáveis e as exclusões posteriores. | Ponte CNAE → atividade. Confirmar se ainda vale depois da 250/2024. |

---

## 3. Competência: quem licencia

- **Um único órgão por empreendimento** (art. 6º da 250): o competente para a atividade de **maior impacto**. Há exceções para alguns códigos e para condomínios industriais (71.21.11) e complexos turísticos (71.70.10).
- **Impacto local** (art. 2º, XXXIV): a área de intervenção e a área de influência direta ficam **dentro de um único município**, e a atividade consta da tipologia da 251/2024.
- **Proibição de protocolar no Estado** (art. 5º): uma atividade de impacto local, em município apto a licenciá-la, não pode ser protocolada no IMA.
- **Níveis de complexidade da 251/2024:** o município é habilitado em um nível, e as listas são cumulativas.
  - Exemplo: **12.80.00** (usinagem e solda) e **71.00.00** (manutenção com pintura) aparecem já no **nível I**.
  - **11.60.02** (serralheria **sem** pintura) aparece a partir do **nível II**.
  - **11.60.01** (serralheria **com** pintura ou tratamento químico) aparece **só no nível III**.
  - Consequência: **uma pergunta sobre pintura pode mudar até o órgão competente**.

### Órgãos nos municípios atendidos

| Município | Órgão municipal | Habilitação (lista SEMAE/CONSEMA, atualizada até 26/08/2026) | Como tramita (segundo as fontes) | A confirmar |
|---|---|---|---|---|
| **Itajaí** | FAMAI (fundação municipal de meio ambiente) | **Nível III** (Res. CONSEMA 008/08) | SinFAT (sistema do IMA). Segundo a imprensa, o sistema indica sozinho se a análise é estadual ou municipal. | Lista de documentos. |
| **Balneário Camboriú** | SEMAM (Secretaria de Meio Ambiente) | **Nível III** (Res. CONSEMA 088/16; desabilitado pela 131/19 e habilitado de novo pela 193/22) | Instruções normativas próprias por código de atividade, já citando a 251/2024 (ex.: condomínios e hotelaria, 71.11.x). Licenças trifásicas (LAP, LAI e LAO). | Lista de documentos. |
| **Camboriú** | FUCAM (órgão ambiental municipal) | **Nível III** (Res. CONSEMA 64/15) | SinFAT. Supressão de vegetação pelo SINAFLOR, e terraplanagem em processo físico (Lei municipal 3.260/2020). Emite DANC e CCA. | O site ainda cita a 99/2017 (revogada). |

> Os três municípios estão habilitados no **nível III**, o mais alto, que inclui os níveis I e II. A habilitação foi concedida na vigência da 99/2017, mas o parágrafo único do art. 2º da 251/2024 diz que toda menção à resolução revogada passa a valer para a 251. **Na prática:** atividade que consta da 251/2024, em qualquer nível, é licenciada pelo município. Atividade fora da 251 vai para o IMA, e leva junto o empreendimento inteiro (órgão único, art. 6º da 250). A lista de habilitados muda com o tempo: conferir a versão atual antes de abrir o processo.

---

## 4. Anatomia de um código de atividade

Exemplo real do Anexo VI da 250/2024:

```
11.60.01 - Serralheria, fabricação de tanques, reservatórios e outros recipientes metálicos
           e de artigos de caldeireiro COM tratamento químico superficial ou galvanotécnico
           ou pintura por aspersão ou esmaltação ou imersão.
Pot. Poluidor/Degradador: Ar: M  Água: G  Solo: P  Geral: G
Porte Mínimo: ... - será licenciado por meio da expedição de autorização ambiental - AuA
Porte Médio: 0,2 < AU(3) < 1 (RAP)
...
```

| Parte | Significado |
|---|---|
| `11.60.01` | Código CONSEMA no formato `GG.SS.VV`: grupo, subgrupo e variante. **Não é o CNAE.** |
| Descrição | Pode trazer condições como "com/sem pintura" ou "com geração de efluentes". **São essas condições que as perguntas da etapa "Operação" precisam responder.** |
| Potencial poluidor | Característica fixa da atividade, em P, M ou G para ar, água, solo e geral. |
| Linhas de porte | Para cada porte (Mínimo, Pequeno, Médio, Grande ou Único): a faixa do parâmetro e o estudo ou modalidade resultante. |

### Grupos de atividades do Anexo VI (250/2024)

| Grupo | Título |
|---|---|
| 00 | Extração de minerais |
| 01 e 03 | Atividades agropecuárias (ex.: 01.70.02, uso múltiplo da pequena propriedade rural) e aquicultura (03.3x). O texto consultado não trouxe os títulos do grupo 01. |
| 10 | Indústria de produtos minerais não metálicos |
| 11 | Indústria metalúrgica (inclui **serralheria**) |
| 12 | Indústria mecânica (inclui **usinagem e solda**) |
| 13 | Material elétrico e comunicações |
| 14 | Material de transporte (inclui embarcações) |
| 15 | Madeira |
| 16 | Mobiliário (inclui **marcenaria**) |
| 17 | Papel e papelão |
| 18 | Borracha |
| 19 | Couros e peles |
| 20 | Química (inclui **tintas**) |
| 21 | Produtos farmacêuticos e veterinários |
| 22 | Refino de petróleo e destilação de álcool |
| 23 | Matérias plásticas |
| 24 | Têxtil (inclui **lavanderia e tinturaria industrial**) |
| 25 | Vestuário e artefatos têxteis |
| 26 | Produtos alimentares |
| 27 | Bebidas e álcool etílico |
| 28 | Fumo |
| 29 | Editorial e gráfica |
| 30 | Indústrias diversas (concreto, argamassa…) |
| 33 | Construção civil |
| 34 | Serviços de infraestrutura (saneamento, energia, antenas…) |
| 42 | Comércio varejista (**só combustíveis e agrotóxicos**) |
| 43 | Comércio atacadista e depósitos (produtos químicos perigosos, combustíveis, agrotóxicos…) |
| 47 | Transportes e terminais |
| 53 | Serviços diversos (coleta de efluentes, aplicação aérea de agrotóxicos) |
| 56 | Serviços médico-hospitalares, laboratoriais e veterinários |
| 71 | Atividades diversas (**oficinas com pintura**, laboratórios, condomínios, hotelaria, resíduos, cemitérios…) |

---

## 5. Potencial poluidor

- É **intrínseco à atividade**: não depende da empresa (art. 2º, XLIV).
- É dado separadamente para **ar, água e solo**, mais um **geral**, cada um em P, M ou G.
- Serve para a priorização e para a ficha técnica do resultado. **Não é perguntado ao cliente**: vem da tabela.
- Atividades parecidas mudam de potencial conforme a operação. Exemplo: serralheria sem pintura (11.60.02) tem potencial geral **M**, e com pintura ou tratamento químico (11.60.01) passa a **G**.

---

## 6. Porte do empreendimento

> ⚠️ **Não confundir com o porte da empresa (MEI, ME, EPP).** O porte CONSEMA é físico e operacional, não fiscal. A especialista confirmou que a natureza jurídica e o porte fiscal **não são usados** no enquadramento ambiental.

- **Categorias:** Mínimo (Mín), Pequeno (P), Médio (M), Grande (G) ou Único (U) (art. 2º, XLIII).
- **Cada código usa um parâmetro.** Os mais comuns para empresas urbanas estão abaixo.

| Sigla | Parâmetro | Unidade | Onde aparece |
|---|---|---|---|
| **AU(3)** | **Área útil geral**: soma das áreas usadas na atividade licenciada, **incluindo** setores de apoio, estocagem, circulação, manobra e estacionamento de veículos pesados, e áreas de tratamento ou disposição de efluentes e resíduos. | **hectare (ha)** | Maioria das indústrias e serviços |
| AE(1) | Área edificada dentro da área útil | m² | Condomínios comerciais, alguns serviços |
| AE(2) | Área edificada usada só para depósito de produtos | m² | Depósitos de agrotóxico e similares |
| AD | Área de depósito | m² | 43.20.00, depósito de produtos químicos perigosos |
| VT | Volume total de tancagem (soma dos tanques) | m³ | Postos e tanques de combustível (42.32.x) |
| NL | Número de leitos | un. | Hotelaria e hospitais |
| NH | Número de unidades habitacionais | un. | Condomínios residenciais |
| NV | Número de veículos | un. | Transporte de efluentes |
| CN | Capacidade nominal de produção | t/h | Algumas indústrias |
| CmedA | Média de animais abatidos por dia | cab./dia | Abatedouros |

**Implicação para o formulário:** a pergunta "área ocupada (m²)" precisa virar **área útil**, separada por componente: produção, administrativo e apoio, estoque, pátio e circulação, e tratamento de efluentes. O sistema converte para hectare.

**Conversão de m² para ha** (1 ha = 10.000 m²):

| ha | m² |
|---|---|
| 0,05 | 500 |
| 0,1 | 1.000 |
| 0,2 | 2.000 |
| 0,5 | 5.000 |
| 1 | 10.000 |
| 3 | 30.000 |
| 5 | 50.000 |

> ⚠️ **Dados incompletos:** o texto de referência (LegisWeb) perdeu, em muitos códigos, as linhas de porte Pequeno e Grande. Para a maioria das atividades só aparecem o Mínimo e o Médio. Por isso este documento **não afirma** onde começa o licenciamento de cada código. Esses limites são o que decide entre CCA e licença, e precisam vir da tabela oficial, com as correções da 259/2024.

---

## 7. Do enquadramento ao resultado

| Situação | Documento | Base (250/2024) | Observações |
|---|---|---|---|
| A atividade **não consta** da lista | **DANC** (Declaração de Atividade Não Constante) | art. 15 | O órgão analisa **todas** as atividades da empresa. Validade máxima de **1 ano**. **Não autoriza** instalação nem operação, nem dispensa outras exigências ambientais ou florestais. No SinFAT: modalidade "Atividade não licenciável", com busca por CNAE ou descrição. |
| A atividade consta, mas está **abaixo do limite de porte** | **CCA** (Certidão de Conformidade Ambiental) | art. 14 | Exige uma Declaração de Conformidade Ambiental assinada por profissional habilitado, **com ART**. Validade igual à da declaração. Também não autoriza a operação. Camboriú emite CCA em nível municipal. |
| Porte **Mínimo** ou **Único** | **AuA** (Autorização Ambiental) | arts. 2º, XIV, e 9º, II | Ato único que cobre localização, instalação e operação. **Dispensa estudos ambientais** (art. 22). Validade de 4 a 10 anos. |
| Código que prevê **LAC** | **LAC** (Licença por Compromisso) | arts. 9º, III, e 12 | Eletrônica, em etapa única, baseada em declaração de compromisso. Documentos técnicos com ART. Validade de 3 a 5 anos. Costuma exigir "sem supressão de vegetação". |
| Demais portes | **LAP → LAI → LAO** (trifásico) | art. 9º, I | As três licenças podem ser isoladas, sucessivas ou concomitantes. Estudo: **RAP** (simplificado), **EAS** ou **EIA/RIMA** (impacto significativo), conforme o porte. LAP até 5 anos, LAI até 6 anos, LAO de 4 a 10 anos. |
| Empresa **já operando sem licença** | **LAO de regularização** com **ECA** (Estudo de Conformidade Ambiental) | art. 20 | Cobre as três fases de uma vez. O ECA é proporcional ao estudo que seria exigido na LAP. Pode haver sanções. |
| **Ampliação** de atividade já licenciada | Nova LAP, LAI direta ou ofício | art. 11 | Muda o tipo de estudo: nova LAP. Muda o porte ou o parâmetro: LAI. Não muda nada: basta ofício. |

**Licença não substitui alvarás** (art. 41): a licença ambiental, ou sua dispensa, não exime a empresa de alvarás e certidões municipais, estaduais ou federais. Por isso o escopo de alvarás é **separado** do enquadramento.

---

## 8. Empresas com várias atividades ou CNAEs

Regras do art. 10 da 250/2024:

- **Todas** as atividades licenciáveis precisam ser informadas no pedido.
- O estudo segue a atividade de **maior complexidade** e considera os impactos de todas.
- Se o empreendimento como um todo **não é licenciável**, mas tem **uma atividade licenciável** na estrutura, licencia-se essa atividade sozinha, **pelo porte dela**.
- Atividades de pessoas físicas ou jurídicas **distintas** têm processos próprios, vinculados entre si.
- Em **área compartilhada**, por exemplo um galpão dividido, os processos são distintos, mas os estudos consideram todas as atividades da área. Para o enquadramento, cada processo soma a área individual e a compartilhada.

**Implicação:** a análise não pode parar no CNAE principal. Como observou a especialista, muitas empresas registram **comércio como CNAE principal e fabricação como secundário**. O motor precisa avaliar **todos** os CNAEs e a descrição real da operação.

### "Comércio não entra no enquadramento"

Vale para o comércio em geral. A lista só contém comércio nos seguintes casos:

- **42.32.x**: postos e tancagem de combustíveis (parâmetro VT);
- **42.40.00**: depósito de agrotóxico em casas agropecuárias;
- **43.xx**: comércio atacadista **com depósito** de produtos minerais em bruto, de **produtos químicos perigosos** (43.20.00, parâmetro AD), de agrotóxicos, de combustíveis e lubrificantes, e postos ou centrais de recolhimento de embalagens de agrotóxicos.

**Regra para o motor:** um CNAE de comércio é descartado, **a menos que** a operação tenha estoque de combustível, agrotóxico ou produto químico perigoso.

---

## 9. Variáveis da operação que mudam o código

No Anexo VI da 250/2024 há **37 códigos** cuja descrição traz **"com" ou "sem"** tratamento químico superficial, galvanoplastia ou pintura por aspersão, esmaltação ou imersão. Quase todos formam pares, em que essa é a única diferença. Isso confirma o que a especialista disse: perguntas de sim/não sobre a operação **eliminam ou escolhem** enquadramentos.

| Pergunta (sim/não) | O que ela decide | Exemplos de códigos afetados |
|---|---|---|
| Faz **pintura** por aspersão (pistola), esmaltação ou imersão? | Troca o código sem pintura pelo código com pintura, de potencial maior. No caso de oficinas, **faz a atividade entrar na lista**. | 11.60.01/02, 11.30.01/02, 11.40.01/02, 11.50.01/02, 11.70.01/02, 11.90.01/02, 12.10.00/12.11.00/12.20.00, 12.80.00/12.80.10, **71.00.00** |
| Faz **tratamento químico superficial** ou **galvanoplastia** (zincagem, cromagem, fosfatização, decapagem)? | Igual ao anterior. Existe também um serviço exclusivo de tratamento (11.80.02). | Grupo 11, 12.10.00, 11.80.02 |
| Tem **fundição** ou forno (cubilô ou outro)? | Seleciona os códigos de fundidos. | 11.00.09–12, 11.11.08–11 |
| Gera **efluente líquido de processo**, **resíduos perigosos** ou **emissões atmosféricas**? | Em gráficas, por exemplo, **só entra na lista com pelo menos um desses três**. | **29.10.00**, 17.40.00 |
| Tem **lavagem** (lavanderia, tinturaria, estamparia com lavagem)? | Estamparia por sublimação ou digital **sem lavagem** fica fora. | 24.70.00, **24.80.00**, **25.20.00** |
| **Manipula ou fabrica alimentos?** De qual tipo (origem animal ou vegetal, laticínios, sorvetes, pescado, bebidas, ração)? | Seleciona o subgrupo do grupo 26 ou 27. | 26.00.00, 26.50.01/02, 26.60.00, 26.70.00, **26.91.00** (sorvetes), 27.x |
| **Armazena** combustível (tanque) ou produto químico perigoso? Qual volume ou área? | Pode tornar licenciável até um comércio, uma transportadora ou uma indústria. | 42.32.20/40 (VT), **43.20.00** (AD) |
| **Atividade com animais?** | Hospitais veterinários e abate têm códigos próprios. Atividades rurais ficam nos grupos 01–03. | 56.20.00, 26.50.2x, 26.94.00 |
| O imóvel tem **rede coletora de esgoto** ou **sistema próprio de tratamento** (fossa e filtro)? | Para condomínios, hotelaria e uso misto, o código só se aplica onde **não há** coleta e tratamento de esgoto ou plano diretor. Em geral, também muda as exigências do processo. | 71.11.01, 71.11.02, 71.11.06, 71.11.07 |

### Sobre ruído

**Ruído não é critério para escolher código** no Anexo VI. Ele aparece no conteúdo dos estudos (RAP e EAS pedem a avaliação de "emissão de ruídos") e no controle ambiental. Por isso a especialista pediu que **ruído, emissão e animais sejam perguntas separadas**: elas têm efeitos diferentes. Ruído ajuda a descrever a operação e a orçar o estudo, enquanto emissão e animais podem mudar o código.

---

## 10. Exemplos práticos

Os valores são do texto de referência. Consulte o aviso no [§6](#6-porte-do-empreendimento).

| Atividade comum | Código CONSEMA | Pot. geral | Faixa vista | Resultado vista | Nível municipal (251) |
|---|---|---|---|---|---|
| Serralheria **sem** pintura ou tratamento químico | 11.60.02 | M | Médio: 0,2 < AU(3) < 1 ha | RAP | II e III |
| Serralheria **com** pintura ou tratamento químico | 11.60.01 | G | Há AuA para porte mínimo. Médio: 0,2 < AU(3) < 1 ha | AuA / RAP | III |
| Usinagem e solda | 12.80.00 | P | Mín: AU(3) < 0,1 ha. Médio: 0,2 < AU(3) < 1 ha | AuA / RAP | I, II e III |
| Usinagem e solda **com pintura** | 12.80.10 | M | Mín: AU(3) < 0,05 ha. Médio: 0,2 < AU(3) < 1 ha | AuA / RAP | II e III |
| Manutenção de máquinas ou veículos **com pintura** (ex.: funilaria e pintura) | 71.00.00 | M | Porte único | **AuA** | I, II e III |
| Marcenaria (móveis de madeira) | 16.10.00 | M | Médio: 1 < AU(3) < 5 ha | RAP | II e III |
| Gráfica com resíduo perigoso, efluente ou emissão | 29.10.00 | M | Médio: 0,5 < AU(3) < 3 ha | RAP | II e III |
| Lavanderia, tinturaria ou estamparia industrial | 24.80.00 | G | Mín: AU(3) < 0,1 ha. Médio: 0,3 < AU(3) < 2 ha | AuA / EAS | III |
| Confecção com lavanderia, tinturaria ou estamparia | 25.20.00 | G | Mín: AU(3) < 0,3 ha. Médio: 0,5 < AU(3) < 1 ha | AuA / EAS | III |
| Fabricação de produtos alimentares (geral) | 26.00.00 | M | Médio: 0,2 < AU(3) < 1 ha | RAP | II e III |
| Fabricação de sorvetes | 26.91.00 | P | Médio: 0,5 < AU(3) < 1 ha | RAP | I, II e III |
| Depósito de produtos químicos perigosos | 43.20.00 | M | Mín: AD < 200 m². Médio: 1.000 < AD < 2.000 m² | AuA / RAP | II e III |
| Posto de combustível | 42.32.00 | M | Médio: 60 < VT < 125 m³ | EAS | II e III |
| Hospital veterinário | 56.20.00 | M | Médio: 0,1 < AU(3) < 0,2 ha | RAP | II e III |
| Laboratório de análises (saúde) | 56.11.01 | M | Porte único | AuA | II e III |

Na coluna "Nível municipal", a atividade consta da 251/2024 nos níveis indicados. Um código ausente da 251 não é de impacto local: quem licencia é o IMA.

### Caso 1: serralheria de Camboriú que trabalha mais na obra do cliente

Exemplo citado pela especialista.

1. **CNAE provável:** 2542-0/00 (artigos de serralheria, exceto esquadrias) ou 2512-8/00 (esquadrias de metal).
2. **Pergunta decisiva:** pinta com pistola, esmalta ou faz tratamento químico na oficina?
   - **Sim:** 11.60.01, potencial G. Na 251, só aparece no nível III.
   - **Não:** 11.60.02, potencial M, nível II.
3. **Porte:** depende da AU(3) **da oficina**, ou seja, do endereço fixo. Uma oficina de 300 m² tem AU(3) de 0,03 ha.
   - Se isso fica abaixo do limite de licenciamento (CCA) ou dentro do porte mínimo (AuA), depende da tabela oficial.
4. **Forma de atuação "os dois"** (endereço fixo e serviço externo): o enquadramento recai sobre o local fixo.
   - A confirmar com a especialista: como tratar o serviço feito na obra do cliente.

### Caso 2: comércio como CNAE principal e fabricação como secundário

- O CNAE principal de comércio é descartado, salvo as exceções do [§8](#comércio-não-entra-no-enquadramento).
- O CNAE secundário de fabricação é enquadrado normalmente, pela área útil **da parte produtiva**, conforme o art. 10, §2º.

### Caso 3: oficina mecânica

| Situação | CNAE | Enquadramento |
|---|---|---|
| Funilaria e pintura | 4520-0/02 | 71.00.00, **AuA**, porte único |
| Só mecânica, sem pintura | 4520-0/01 | Não encontramos código específico. Provável DANC, **a confirmar**. |

Lavagem de peças, troca de óleo e caixa separadora de água e óleo podem trazer exigências próprias. Validar com a especialista.

---

## 11. Ligação entre CNAE e código CONSEMA

- O CNAE **não corresponde 1:1** ao código CONSEMA.
  - Um CNAE pode levar a vários códigos, conforme a operação (ex.: serralheria com ou sem pintura).
  - Muitos CNAEs não levam a código nenhum (comércio e serviços em geral), e o resultado é DANC.
- **Fontes da ponte:**
  - SinFAT (IMA): permite buscar por CNAE ao pedir DANC;
  - a tabela do IMA de "Atividades não sujeitas ao licenciamento", por CNAE;
  - a Portaria IMA 229/2019, alterada pela Portaria 106/2020.

  Confirmar qual delas está atualizada para a 250/2024.
- **Estratégia sugerida para o motor:**
  1. O CNAE gera uma **lista de candidatos** (códigos CONSEMA possíveis) e uma marcação **"não listado"**.
  2. As perguntas de operação ([§9](#9-variáveis-da-operação-que-mudam-o-código)) **eliminam** candidatos.
  3. A área útil ou outro parâmetro define o **porte**, e com ele a modalidade e o estudo.
  4. O código, o município e o nível de habilitação definem o **órgão**.
  5. Com várias atividades, aplicam-se as regras do [§8](#8-empresas-com-várias-atividades-ou-cnaes): o órgão é o da atividade de maior impacto, e o estudo é o de maior complexidade.

---

## 12. Modelo de dados sugerido para a tabela de atividades

```jsonc
{
  "codigo": "11.60.01",
  "descricao": "Serralheria ... com tratamento químico superficial ou galvanotécnico ou pintura ...",
  "grupo": "11",
  "potencialPoluidor": { "ar": "M", "agua": "G", "solo": "P", "geral": "G" },
  "parametro": "AU3",            // AU3 | AE1 | AE2 | AD | VT | NL | NH | NV | CN | CmedA | UNICO
  "unidade": "ha",
  "faixas": [                    // preencher com o texto OFICIAL (250/2024 + 259/2024)
    { "porte": "MIN", "max": null, "resultado": "AuA" },
    { "porte": "P",   "min": null, "max": null, "estudo": "RAP" },
    { "porte": "M",   "min": 0.2,  "max": 1,    "estudo": "RAP" },
    { "porte": "G",   "min": null, "estudo": null }
  ],
  "abaixoDoLimite": "CCA",
  "permiteLAC": false,
  "condicoes": { "pintura": true, "tratamentoQuimico": true },   // o que as perguntas precisam confirmar
  "exclusivoDe": null,           // ex.: { "semRedeEsgoto": true } para 71.11.x
  "cnaes": ["2542-0/00", "2512-8/00"],                           // candidatos, não equivalência
  "nivelMunicipal251": ["III"],
  "fonte": "CONSEMA 250/2024, Anexo VI"
}
```

---

## 13. Glossário

- **AuA (Autorização Ambiental):** licenciamento simplificado, em ato único, para porte mínimo ou único.
- **AU(3) (área útil geral):** em hectares. Ver o [§6](#6-porte-do-empreendimento).
- **ART (Anotação de Responsabilidade Técnica):** registro no conselho de classe do profissional responsável.
- **CCA (Certidão de Conformidade Ambiental):** atividade listada, mas abaixo do porte.
- **CONSEMA (Conselho Estadual do Meio Ambiente de SC):** nos áudios aparece como "Concema".
- **DANC (Declaração de Atividade Não Constante):** a atividade não está na lista.
- **EAS (Estudo Ambiental Simplificado):** estudo intermediário, feito por equipe multidisciplinar.
- **ECA (Estudo de Conformidade Ambiental):** usado na regularização de quem já opera.
- **EIA/RIMA (Estudo e Relatório de Impacto Ambiental):** para impacto significativo, com audiência pública obrigatória.
- **FAMAI, SEMAM e FUCAM:** órgãos ambientais de Itajaí, Balneário Camboriú e Camboriú.
- **IMA (Instituto do Meio Ambiente de SC):** órgão licenciador estadual.
- **LAC (Licença Ambiental por Compromisso):** eletrônica, por autodeclaração.
- **LAP, LAI e LAO:** licenças prévia, de instalação e de operação (trifásico).
- **RAP (Relatório Ambiental Prévio):** o estudo mais simples, pode ser feito por um profissional.
- **SinFAT:** sistema eletrônico de licenciamento do IMA, também usado por municípios.

---

## 14. Fontes

- Resolução CONSEMA 250/2024 (texto integral): <https://www.legisweb.com.br/legislacao/?id=463083>
- Resolução CONSEMA 251/2024 (impacto local, níveis I a III): <https://www.legisweb.com.br/legislacao/?id=463084>
- Resolução CONSEMA 309/2026 (critérios para o licenciamento municipal): <https://www.legisweb.com.br/legislacao/?id=495646>
- Notícia sobre a 309/2026: <https://www.portaltela.com/noticias/geral/2026/05/21/santa-catarina-adota-novos-criterios-de-licenciamento-ambiental-para-municipios/>
- Pedido de informação da ALESC sobre a 259/2024: <https://portalelegis.alesc.sc.gov.br/documentos/zEaQ9>
- Resolução CONSEMA 98/2017 (revogada): <https://www.legisweb.com.br/legislacao/?id=345935>
- Resolução CONSEMA 99/2017 (revogada): <https://www.legisweb.com.br/legislacao/?id=345931>
- Portaria IMA 106/2020 (CNAEs excluídos da Portaria 229/2019): <https://consultas.ima.sc.gov.br/portarias/pdf/2645>
- Instrução Normativa do IMA (CCA e DANC): <https://in.ima.sc.gov.br/instrucaoNormativa/gerarPDF/332>
- IMA, atividades não licenciáveis e manual da DANC no SinFAT: <https://www.ima.sc.gov.br/atividades-nao-sujeitas-ao-licenciamento-ambiental/> (PDF: <https://www.ima.sc.gov.br/wp-content/uploads/2026/07/Manual-DANC.pdf>)
- Camboriú (FUCAM), orientações de licenciamento: <https://camboriu.sc.gov.br/wp-content/uploads/2025/02/SITE-licenciamento.pdf>
- Itajaí (FAMAI), licença 100% eletrônica no SinFAT: <https://www.nsctotal.com.br/?p=6222928>
- Itajaí, diretrizes ambientais da PPP (cita a 251/2024): <https://ppp.itajai.sc.gov.br/wp-content/uploads/2026/07/1.7.-Anexo-VII-do-Contrato-Diretrizes-Ambientais.pdf>
- Balneário Camboriú (SEMAM): instruções normativas por código de atividade, publicadas em `bc.sc.gov.br/arquivos/conteudo_downloads/`. Encontradas via busca; o documento específico não foi aberto.
- CONSEMA (SEMAE/SC): <https://www.semae.sc.gov.br/consema/>
- Municípios habilitados para o licenciamento de impacto local (SEMAE/CONSEMA, atualizado até 26/08/2026): <https://www.semae.sc.gov.br/download/municipios-habilitados-compilado-por-ordem-alfabetica/>
