# Feedback da especialista: foco no enquadramento ambiental

Análise dos áudios de uma profissional de licenciamento ambiental que testou o protótipo (`index.html`). O documento registra **o que ela pediu** e **o que muda no produto**.

- **Origem:** 7 áudios de WhatsApp de 24/10/2026, em [`docs/feedback/`](./feedback/).
  - Seis foram transcritos manualmente.
  - O último (`17.00.49`) foi transcrito automaticamente em 26/10/2026 e precisa de revisão.
- **Conhecimento técnico de apoio:** [`conhecimento-enquadramento-ambiental-sc.md`](./conhecimento-enquadramento-ambiental-sc.md). Explica CONSEMA, porte, potencial poluidor, modalidades e exemplos.

---

## 1. Mensagem central

> *"A ideia é deixar só o enquadramento ambiental, sabe? Porque os documentos de alvará, dessas coisas, não influenciam no enquadramento ambiental, e sim a atividade e a operação do estabelecimento."* (áudio 17.00.23)

> *"Mas a base está interessante, agora é meio que aprimorar só por enquadramento."* (áudio 17.00.49)

1. **Mudança de escopo:** o Licença Clara deixa de ser um pré-diagnóstico geral (alvará, Bombeiros, Vigilância Sanitária, inscrições, viabilidade) e passa a ser uma **ferramenta de enquadramento ambiental**. A pergunta que ele responde é: **a atividade precisa de licenciamento ambiental? Se sim, em qual enquadramento?**
2. **O enquadramento depende só da atividade e da operação.** Não depende dos documentos que a empresa já tem.
3. **Regularizar não depende de documentos.** Primeiro é preciso saber **se** precisa de licenciamento. Os documentos e projetos são importantes, mas vêm depois.
   - A Resolução CONSEMA 250/2024 confirma isso: a regularização é feita por uma LAO de regularização com Estudo de Conformidade Ambiental (art. 20).
4. **Documentos ficam para uma fase posterior, a de elaborar o orçamento.** São documentos "básicos para qualquer tipo de licenciamento", muito parecidos entre si.
5. **A estrutura atual foi aprovada:** etapas, perguntas de sim/não que eliminam enquadramentos e rótulos de status como "analisar", "pendências" e "conferir". A estrutura fica; o conteúdo muda.
6. **O filtro de regras é o coração do produto.** As atividades e o CNAE geram o filtro, e as características da operação eliminam enquadramentos.
   - Exemplo dela: *"se não tem alimento, exclui esses enquadramentos"*.
7. **A tabela de referência é a do CONSEMA**, que separa as atividades por categoria (indústria, alimentos, fabricação…).
   - As normas vigentes são as **Resoluções 250/2024 e 251/2024**, que revogaram a 98/2017 e a 99/2017.

---

## 2. Feedback por etapa do formulário

Os nomes entre crases são os `id`/`name` dos campos em `index.html`.

### Etapa 01: Empresa

| Item atual | O que ela disse | Mudança proposta |
|---|---|---|
| Razão social (`companyName`), CNPJ (`cnpj`), município (`municipality`) | Servem para entender a empresa. | **Manter.** |
| Natureza jurídica (`legalNature`) e porte (`companySize`) | *"Essas duas coisas a gente não utiliza para a parte do licenciamento ambiental, mas é interessante."* | **Tirar do enquadramento.** Deixar opcional ou remover. **Atenção:** o porte fiscal (MEI, ME, EPP) **não é** o porte CONSEMA, que é físico (área útil, volume, leitos…). A interface não pode sugerir que são a mesma coisa. |
| "O que você está verificando?" (`processType`: abertura, regularização, alteração, renovação) | A regularização não depende de outros documentos. O que se quer descobrir é **se** a atividade precisa de licenciamento. | **Reformular** como situação da operação: *ainda vai instalar*, *já opera sem licença ambiental* ou *já tem licença e vai ampliar ou renovar*. Muda o caminho do processo (LAP/LAI/LAO, LAO de regularização com ECA, ou ampliação pelo art. 11), mas **não** o código. *Proposta nossa, a validar com ela.* |

### Etapa 02: Estabelecimento

| Item atual | O que ela disse | Mudança proposta |
|---|---|---|
| Endereço, CEP, inscrição imobiliária | Servem para saber onde a atividade está. | **Manter.** O endereço define o município e, com ele, o órgão. A inscrição imobiliária pode ir para a fase de documentos. |
| Área ocupada (`area`, m²) | O tamanho é importante. Sugeriu *"destrinchar a área ocupada"*, por exemplo uma parte administrativa e outra de operação, com maquinário. | **Separar a área por uso:** produção ou operação, administrativo e apoio, estoque, pátio e circulação, e tratamento de efluentes e resíduos. Somar como **área útil AU(3)** e converter para hectare. AU(3) é o parâmetro de porte da maioria dos códigos ([conhecimento §6](./conhecimento-enquadramento-ambiental-sc.md#6-porte-do-empreendimento)). Perguntar também a **área construída**, que alguns códigos usam (AE1). |
| Número de pavimentos (`floors`) | Foi citado de passagem, sem conclusão. | Manter como opcional até confirmar com ela. |
| Tipo de unidade (`unitType`) | *"Pode ser correlacionado com a parte do CONSEMA… é uma indústria, é de alimentos, é de fabricação."* | **Trocar as opções** (loja, depósito, residência…) por **categorias que conversem com os grupos do CONSEMA**: indústria ou fabricação, alimentos e bebidas, oficina ou manutenção, serviços de saúde ou veterinários, depósito ou armazenamento, comércio, escritório. |
| Situação do imóvel (`propertyUse`: alugado, próprio, compartilhado, residencial…) | *"Destrincha muito… é só se é próprio ou se é alugado."* Isso define o documento anexado ao processo. | **Reduzir a Próprio / Alugado.** Avaliar "cedido" com ela. **Exceção que vale guardar:** área compartilhada com outra empresa muda a soma das áreas no enquadramento (art. 10, §3º, da 250/2024). Pode virar uma pergunta separada: "divide o espaço com outra empresa?". |
| Endereço fixo (`fixedPlace`) | Gostou, mas com as opções **sim, não e os dois**. Exemplo: um cliente com serralheria em Camboriú, que às vezes trabalha lá, mas na maior parte do tempo trabalha fora. | **Manter com 3 opções:** só no local fixo, só externo e os dois. |
| Clientes vão ao local (`customerVisit`) | *"É interessante, mas não é aplicável para a parte de enquadramento."* | **Remover.** |
| Maquinário | Sugeriu perguntar se há maquinário e se as máquinas geram ruído, o que *"já entra no outro item"*. | Levar para a etapa 03 (ver abaixo). |

### Etapa 03: Atividade e operação

| Item atual | O que ela disse | Mudança proposta |
|---|---|---|
| CNAE principal e secundários (`mainCnae`, `otherCnaes`) | Achou interessante. É daqui que sai o filtro de regras. **Ponto-chave:** *"geralmente eles colocam o comércio como o primeiro e depois a fabricação… porque comércio não entra em enquadramento."* | **Manter e analisar todos os CNAEs**, não só o principal. Comércio em geral é descartado, exceto combustíveis, agrotóxicos e depósitos de produtos químicos perigosos ([conhecimento §8](./conhecimento-enquadramento-ambiental-sc.md#comércio-não-entra-no-enquadramento)). |
| "O que a empresa realmente faz?" (`activityDescription`) | *"É interessante, o que a empresa realmente faz."* Sugeriu perguntas de detalhe: **tem equipamentos? Quais?** Se manipula alimentos, **qual tipo de alimento?** | **Manter**, com perguntas guiadas: lista de equipamentos (texto livre ou checklist) e tipo de alimento. Os tipos de alimento seguem os subgrupos do CONSEMA: origem animal, origem vegetal, laticínios, pescado, sorvetes, bebidas, ração. |
| Características da operação (8 perguntas de sim/não) | *"Seria um checklist muito maior… é muito bom porque é sim e não, ele vai eliminando dentro das regras."* | **Ampliar o checklist** (ver a seção 3 abaixo). |
| "Há atividade com animais, ruído relevante ou emissão?" (`impact`) | *"Tem coisas que estão misturadas… animais, ruídos e emissão não têm coisas parecidas… ia destrinchar em três."* Lembrou também que *"basicamente qualquer fabricação gera ruído"*. | **Separar em 3 perguntas:** animais, ruído e emissão atmosférica. |
| Pintura e tratamento químico (não existem hoje) | *"Trabalha com pintura, que é uma coisa muito interessante. Tem tratamento químico."* | **Criar.** No CONSEMA, 37 códigos mudam conforme "com" ou "sem" pintura ou tratamento químico. Em oficinas, a pintura é o que **faz a atividade entrar na lista** (código 71.00.00). |
| "Dados adicionais" (`inscriptionState`, `municipalRegistration`, `buildingPermit`, `viabilityStatus`) | Servem para saber quais documentos a empresa tem para anexar ao processo, mas *"são documentos básicos para qualquer tipo de licenciamento"*. | **Tirar do enquadramento.** Mover para a fase de documentos e orçamento, ou remover. |

### Etapa 04: Documentos e licenças existentes

| Item atual | O que ela disse | Mudança proposta |
|---|---|---|
| "Licença / dispensa ambiental" (`environmentDoc`) | *"Não é o que a gente está tentando descobrir? Não tem como ter uma pergunta se a pessoa tem ou não tem."* | **Remover** do diagnóstico. Só cabe na situação "já tem licença e vai renovar ou ampliar", e aí como número e validade da licença existente. |
| Checklist geral (CNPJ, contrato social, Bombeiros, alvará sanitário, CCM, habite-se, fotos…) | Não influencia o enquadramento. Os documentos *"só vão ser necessários para a fase posterior, que é elaborar o orçamento"*. | **Trocar pelos documentos do licenciamento ambiental** e transformar a etapa em "Preparação para orçamento", opcional e depois do resultado. |
| Documentos mais difíceis | *"Deixar destrinchado documentos mais difíceis, tipo projeto arquitetônico, projeto hidrossanitário."* | Itens próprios: **projeto arquitetônico** e **projeto hidrossanitário** (tem / não tem / em elaboração). |
| Esgoto | *"É importante perguntar se passa rede coletora, se tem um sistema de tratamento de efluente, uma fossa no caso, que aí varia."* | Duas perguntas: **"Passa rede coletora de esgoto na rua?"** e **"Qual o sistema de tratamento: rede pública, fossa e filtro, outro, não sei?"**. Em condomínios e hotelaria, isso **muda inclusive o enquadramento** (códigos 71.11.x). |

### Etapa 05: Diagnóstico

| Item atual | O que ela disse | Mudança proposta |
|---|---|---|
| Resultado com viabilidade, alvará municipal, Bombeiros, Vigilância Sanitária, ambiental e checklist de documentos | *"Está bem abrangente para todas as áreas… Isso viraria um software para a empresa conferir o que ela precisa fazer quando quiser abrir."* É interessante, porque mostra o que fazer agora, mas não é o objetivo. | **O resultado passa a ser só o enquadramento ambiental** (formato na seção 4). Os blocos de viabilidade, alvará, CBMSC e sanitário saem. Se o produto quiser oferecer isso no futuro, deve ser um módulo separado. |
| Rótulos de status ("Análise prioritária", "Consultar / confirmar", pendências) | *"Seria um plus a mais… para entender a realidade do empreendimento."* | **Manter** os rótulos, aplicados ao enquadramento. Exemplo: "enquadramento provável", "depende de confirmação: pintura?", "faltou área útil". |

---

## 3. Novo checklist de operação

Cada pergunta é de sim / não / não sei. A coluna "Efeito" diz como a resposta muda o enquadramento. A base normativa está em [conhecimento §9](./conhecimento-enquadramento-ambiental-sc.md#9-variáveis-da-operação-que-mudam-o-código).

| # | Pergunta | Efeito no enquadramento | Pedido por ela? |
|---|---|---|---|
| 1 | Fabrica, transforma, monta ou conserta produtos? | Separa indústria e serviços de comércio e escritório. | Já existe (`production`) |
| 2 | Tem máquinas ou equipamentos? **Quais?** | Ajuda a escolher o código: usinagem, solda, forno, caldeira, cabine de pintura, compressor… | ✅ |
| 3 | Faz **pintura** com pistola, esmaltação ou imersão? | Escolhe entre código com e sem pintura. Faz oficina entrar na lista (71.00.00). Muda até o nível municipal: serralheria com pintura só aparece no nível III. | ✅ |
| 4 | Faz **tratamento químico** de superfície ou galvanoplastia (zincagem, cromagem, decapagem, fosfatização)? | Igual à pergunta 3. Também pode ser um serviço próprio (11.80.02). | ✅ |
| 5 | Tem forno, fundição ou caldeira? Usa gás, chama ou calor no processo? | Códigos de fundição. Emissão atmosférica. | Parcial (`gasHeat`) |
| 6 | Gera **emissão atmosférica** (fumaça, pó, vapores, odor)? | Em alguns códigos é condição de entrada (ex.: gráfica, 29.10.00). | ✅ (separar de `impact`) |
| 7 | Gera **ruído** relevante? | Não escolhe código, mas entra no estudo (RAP/EAS) e nos controles. Informativo. | ✅ (separar de `impact`) |
| 8 | Tem **atividade com animais**? Qual (clínica ou hospital veterinário, criação, abate…)? | Códigos próprios: 56.20.00, 26.50.2x, grupos 01 e 03. | ✅ (separar de `impact`) |
| 9 | **Manipula ou fabrica alimentos?** Qual tipo? | Escolhe o subgrupo dos grupos 26 e 27. Sem alimentos, esses códigos são excluídos. | ✅ |
| 10 | Gera **efluente líquido de processo** (lavagem de peças, pisos, tanques, água de processo)? | Condição de entrada em alguns códigos e controle no estudo. | Parcial (`environmental`) |
| 11 | Tem **lavanderia, tinturaria ou estamparia com lavagem**? | Códigos 24.70.00, 24.80.00 e 25.20.00. Sublimação ou digital sem lavagem fica fora. | — (derivado da norma) |
| 12 | Gera **resíduos perigosos** (óleo, solvente, borra de tinta, embalagens contaminadas)? | Condição de entrada em alguns códigos (ex.: gráfica) e controle no estudo. | Parcial (`environmental`) |
| 13 | **Armazena combustível** em tanque ou **produto químico perigoso**? Quantos m³ ou m²? | Pode tornar licenciável até um comércio (42.32.x, 43.20.00). Parâmetros VT e AD. | Parcial (`storage`) |
| 14 | Atividade de saúde (hospital, laboratório de análises)? | Códigos 56.11.00 (por leitos) e 56.11.01. Salões e estética **não** aparecem no texto consultado. | Já existe (`healthBeauty`); restringir |

Perguntas atuais que **saem** do enquadramento:

- `customerVisit`;
- `employees`: o número de empregados não aparece como parâmetro de porte no texto consultado;
- `storage` genérico: vira a pergunta 13, mais específica.

---

## 4. Como o resultado deve ficar

Para **cada atividade** (CNAE ou descrição), mostrar:

1. **Código e descrição CONSEMA** prováveis (ex.: `11.60.02 – Serralheria… sem pintura`), ou "atividade não listada → DANC".
2. **Potencial poluidor**: ar, água, solo e geral.
3. **Porte**, com o parâmetro usado e o valor informado (ex.: "AU(3) = 0,03 ha"), e o enquadramento resultante:
   - abaixo do limite → **CCA**;
   - mínimo ou único → **AuA**;
   - LAC, quando o código permite;
   - P/M/G → **LAP/LAI/LAO + RAP, EAS ou EIA**.
4. **Órgão provável:** município (FAMAI, SEMAM ou FUCAM) ou IMA, conforme a 251/2024 e o nível de habilitação.
5. **Pendências** que podem mudar o enquadramento. Exemplos: "confirmar se há pintura por aspersão" ou "informar área de estoque".
6. **Situação do processo:** nova instalação, regularização (LAO com ECA) ou ampliação.

Ao final, um **resumo do empreendimento**: atividade de maior impacto, órgão único, estudo de maior complexidade (art. 6º e 10 da 250/2024) e lista de documentos para o orçamento (fase seguinte).

---

## 5. Backlog derivado

Prioridade: **P1** (essencial para o novo escopo), **P2** (melhoria importante), **P3** (depois).

| ID | Prio | Requisito | Critério de aceite |
|---|---|---|---|
| R1 | P1 | Remover do diagnóstico os blocos de viabilidade, alvará municipal, CBMSC, Vigilância Sanitária, CCM e habite-se. | O resultado só traz itens de enquadramento ambiental. |
| R2 | P1 | Montar a **tabela de atividades** CONSEMA 250/2024, com as correções da 259/2024 (código, descrição, potencial, parâmetro, faixas, modalidade, estudo, condições, níveis da 251), começando pelos grupos mais comuns no litoral: 11, 12, 16, 24 a 26, 29, 42, 43, 56 e 71. | Estrutura conforme [conhecimento §12](./conhecimento-enquadramento-ambiental-sc.md#12-modelo-de-dados-sugerido-para-a-tabela-de-atividades). Faixas copiadas do texto **oficial**. |
| R3 | P1 | Ligação **CNAE → candidatos CONSEMA**, avaliando **todos** os CNAEs e descartando comércio, salvo as exceções. | Empresa com comércio no CNAE principal e fabricação no secundário é enquadrada pela fabricação. |
| R4 | P1 | Novo **checklist de operação** (seção 3), que elimina candidatos. | Responder "não" para alimentos remove os códigos 26 e 27 sugeridos pela descrição. Se o próprio CNAE for de alimentos, o código vira alternativa a confirmar ("sem fabricação no local"), em vez de sumir sem aviso. "Sim" para pintura escolhe a variante "com pintura". |
| R5 | P1 | **Área útil por componente**, somada em AU(3) e convertida para hectare. | O resultado mostra o valor em m² e em ha e o porte resultante. |
| R6 | P1 | Separar "animais / ruído / emissão" em 3 perguntas. | Três campos independentes no formulário e no JSON exportado. |
| R7 | P1 | Remover a pergunta "tem licença ou dispensa ambiental?" do enquadramento. | Ela só aparece no fluxo de renovação ou ampliação. |
| R8 | P2 | Simplificar a situação do imóvel para próprio / alugado, mais a pergunta "divide área com outra empresa?". | — |
| R9 | P2 | Forma de atuação com 3 opções (fixo / externo / os dois). Remover `customerVisit`. | — |
| R10 | P2 | Reformular `processType` como situação da operação (nova / sem licença / ampliação ou renovação). | Uma empresa que já opera sem licença recebe a indicação "LAO de regularização + ECA". |
| R11 | P2 | Tipo de unidade alinhado aos grupos CONSEMA. | — |
| R12 | P2 | Determinar o **órgão competente**: município × IMA, pelo código e pelo nível de habilitação de Itajaí, BC e Camboriú. | Os três estão no nível III (lista SEMAE/CONSEMA atualizada até 26/08/2026). |
| R13 | P3 | Etapa "Preparação para orçamento": projeto arquitetônico, projeto hidrossanitário, rede coletora, sistema de tratamento (fossa e filtro), documento do imóvel (matrícula ou contrato de locação). | Aparece depois do resultado e não altera o enquadramento. |
| R14 | P3 | Atualizar as fontes no app: trocar a referência genérica "Resoluções CONSEMA vigentes" por links para a 250/2024 e a 251/2024. Hoje o `sources.env` aponta só para a página do CONSEMA. | — |
| R15 | P3 | Manter rótulos de status (provável / depende de confirmação / faltou dado) por atividade. | — |

### Status de implementação (27/10/2026, `index.html`)

- **Implementado:** R1, R3 a R15.
  - **R12:** Itajaí, Balneário Camboriú e Camboriú estão habilitados no nível III. O app mostra "FAMAI (municipal)", "SEMAM (municipal)" ou "FUCAM (municipal)" quando o código consta da 251/2024. Quando não consta, mostra o IMA, e pelo art. 6º o empreendimento inteiro vai junto.
  - **R13:** a etapa de orçamento ficou como etapa 04, opcional, antes do resultado. Ela não altera o enquadramento e aparece de novo no resultado, como "Preparação para orçamento".
- **Parcial:**
  - **R2:** base piloto com 64 códigos dos grupos 11, 12, 14 a 16, 20, 23 a 27, 29, 30, 42, 43, 53, 56 e 71. As faixas foram copiadas do texto consolidado, que está incompleto, e ainda não foram conferidas contra a 259/2024.
- **Validação (27/10/2026):**
  - **Dados:** os 64 códigos foram conferidos por script contra o texto consultado da 250/2024 (potencial poluidor, parâmetro e faixas) e da 251/2024 (nível mínimo). Não houve divergência.
  - **Revisão de código:** uma revisão independente achou 12 problemas, todos corrigidos e cobertos por testes. Os principais eram:
    - CNAE no formato do cartão CNPJ (`25.42-0-00`) lido errado;
    - CNAEs secundários separados por vírgula ou espaço sendo perdidos;
    - dois CNAEs da mesma família reduzidos a um item só;
    - revenda virando fabricação por palavra-chave ("cervejas, chopes");
    - campos escondidos ainda influenciando o resultado;
    - relatório antigo continuando na tela depois de editar ou reiniciar;
    - números no formato brasileiro ("1.500") lidos como 1,5.
  - **Palavra-chave da descrição:** atividade encontrada só pela descrição aparece como "Depende da operação", com o pedido de confirmar se ela é exercida no local.
- **Como o motor funciona:**
  1. Cada CNAE é ligado a uma família de atividade pelo prefixo mais longo.
  2. A descrição da operação também é lida por palavra-chave, para achar a fabricação que o CNAE não mostra.
  3. As respostas de sim/não escolhem o código.
  4. "Não sei" mantém as alternativas na tela, com a pergunta pendente.
- **Arquivo antigo:** `docs/diagnostico-licenciamento-sc.html` continua com a versão anterior do protótipo.

---

## 6. Pontos em aberto para validar com a especialista

1. **Faixas de porte:** ela trabalha com a tabela oficial da 250/2024 e da 259/2024? Pode passar a versão em PDF ou planilha que usa? O texto que consultamos perdeu várias linhas de porte (detalhe em [conhecimento §6](./conhecimento-enquadramento-ambiental-sc.md#6-porte-do-empreendimento)).
2. **CNAE → código CONSEMA:** ela usa a tabela de CNAEs do IMA, a busca do SinFAT ou a experiência própria?
3. **Serviço externo** (ex.: serralheria que trabalha na obra do cliente): o enquadramento considera só a oficina?
4. ~~**Níveis de habilitação**~~ **Respondido:** os três municípios estão no nível III, conforme a [lista da SEMAE](https://www.semae.sc.gov.br/download/municipios-habilitados-compilado-por-ordem-alfabetica/) atualizada até 26/08/2026. Ainda vale perguntar a ela se a Resolução 309/2026 (novos critérios para o município licenciar) mudou algo na prática para esses órgãos.
5. **Número de pavimentos:** é usado em algum caso?
6. **Imóvel:** além de próprio e alugado, existem casos de cedido ou comodato?
7. **Resultado:** ela quer ver até a modalidade e o estudo (AuA, RAP, EAS…) ou só "licenciável sim/não + código"?
8. **Documentos para orçamento:** qual a lista padrão que ela usa e quais variam conforme o órgão?
9. **Oficina sem pintura** (só mecânica): no entendimento dela, é DANC?
10. **Trecho ininteligível** do último áudio: *"pire ir para o aró"*. Talvez se refira aos rótulos de prioridade do resultado.

---

## 7. Notas sobre as transcrições

Correções prováveis de termos que a transcrição errou:

| Transcrito | Provável |
|---|---|
| "Concema" | **CONSEMA** (Conselho Estadual do Meio Ambiente de SC) |
| "a Nike vai fazer aquele filtro" | "a gente vai fazer aquele filtro" |
| "o ruído, o relevante, a omissão" | "ruído relevante ou emissão" (texto da pergunta atual `impact`) |
| "tratamento de fluente" | "tratamento de efluente" |
| "rede de coletor" | "rede coletora (de esgoto)" |
| "pire ir para o aró" (áudio 17.00.49) | ininteligível |

| Arquivo | Assunto |
|---|---|
| `16.53.13` | Etapa 1 e objetivo: saber se precisa de licenciamento. |
| `16.55.27` | Etapa 2: local, área, tipo de unidade, imóvel, maquinário, forma de atuação. |
| `16.56.31` | Etapa 3: CNAEs, comércio × fabricação, equipamentos, tipo de alimento. |
| `16.57.53` | Características da operação: checklist maior, separar animais, ruído e emissão; pintura e tratamento químico; dados adicionais. |
| `16.58.39` | Etapa 4: remover a pergunta "tem licença", documentos difíceis, rede coletora e fossa. |
| `17.00.23` | Etapa 5: diagnóstico amplo demais; foco só no enquadramento; documentos são para o orçamento. |
| `17.00.49` | Rótulos de status são um plus; a base está boa; aprimorar o enquadramento. *Transcrição automática.* |
