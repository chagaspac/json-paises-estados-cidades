# JSON com Todos os Países + Estados + Cidades de todo o Brasil

JSON Registros de Todos os **Países e Nações** (c/ Código do Portal do Comércio Exterior ou BACEN) + **Estados e Federações Brasileiras** (c/ DDD e Código do IBGE) + **Cidades e Municípios Brasileiros** (c/ Código do IBGE), incluindo as 31 regiões administrativas do DF, Ilhas e Áreas Remotas do Mundo.

**Obrigado ao chinnonsantos**, se quiser a mesma estrutura de dados para MySQL, PostgreSQL ou SQL Server, acesse https://github.com/chinnonsantos/sql-paises-estados-cidades

## Como Atualizar (Para quem já faz uso do projeto...)

Apenas substituir o JSON

## Dicas e Sugestões de Uso

\*Todos os Estados/Distritos e Cidades/Municípios Brasileiros possui um código único de identificação do IBGE, porem nem todos os Países e Nações do mundo possui um código único de identificação do BACEN, devido o BACEN só catalogar Países dos quais ele possui ligação financeira (Agencias Bancarias ou Correspondente bancário), geralmente esses países (ou espaços governados por outras nações) são ilhas inabitadas ou regiões inabitadas próximas das Antártida, não se preocupe com isso, provavelmente sua aplicação nunca irá precisar utilizar essa localização.

\*A tabela de 'pais' possui todos os Países e Nações possíveis com ou sem Sigla, ~~com ou sem Código do BACEN~~, com Nome Original e Nome Traduzido para o Português.

## Validações

#### Validação do Código de Município

O Código de Município do IBGE tem a composição que segue:

- Composição: UUNNNND
  Onde:
  UU = Código da UF do IBGE
  NNNN = Número de ordem dentro da UF;
  D = Dígito de Controle módulo 10

Validação possível:

- Extensão máxima: 7 dígitos;
- Extensão mínima: 7 dígitos;
- Código da UF: deve ser válido, conforme Tabela de UF do IBGE;
- Número de ordem dentro da UF: não pode ser zero;
- Dígito de Controle: módulo 10 (pesos 2 e 1)

Obs 1: Considerar a soma dos algarismos no somatório dos produtos dos pesos. Ou seja, se o produto for superior a 9 os dois algarismos devem ser somados.

Obs 2: Se o resto da divisão for zero, considerar o dígito verificador igual a zero.

O código de Município do IBGE dos seguintes Municípios tem o DV - dígito verificador inválido:

```
4305871 - Coronel Barros/RS;
2201919 - Bom Princípio do Piauí/PI;
2202251 - Canavieira /PI;
2201988 - Brejo do Piauí/PI;
2611533 - Quixaba/PE;
3117836 - Cônego Marinho/MG;
3152131 - Ponto Chique/MG;
5203939 - Buriti de Goiás/GO;
5203962 - Buritinópolis/GO;
```

#### Validação do Código de País

Composição do Código de País:

- NNND
  Onde:
  NNN = Número de ordem do Código do País;
  D = Dígito de Controle módulo 11.

Validação possível:

- Extensão máxima: 4 dígitos;
- Extensão mínima: 2 dígitos;
- Dígito de Controle: módulo 11, pesos 2 a 9

Obs.: Se o resto da divisão for zero ou 1, considerar o dígito verificador igual a zero.

O código de País do BACEN dos seguintes países tem o DV - dígito verificador inválido:

```
1504 - GUERNSEY, ILHA DO CANAL (INCLUI ALDERNEY E SARK);
1508 - JERSEY, ILHA DO CANAL;
3595 - MAN, ILHA DE;
4985 - MONTENEGRO;
6781 - SAINT KITTS E NEVIS;
7370 - SERVIA;
```

## Fontes

- [x] [Tabela de Países do Portal do Comércio Exterior](http://www.nfe.fazenda.gov.br/portal/listaConteudo.aspx?tipoConteudo=Iy/5Qol1YbE=)
- [x] [Códigos BACEN](http://www.bcb.gov.br/rex/Censo2000/port/manual/pais.asp?idpai=censo2000inf)
- [x] [Instruções de Preenchimento do Banco Central - Março de 2016 - PDF](http://www.bcb.gov.br/fis/pstaw10/DLO_2061_e_2071_instrucoesComplementares_ACP_v201603.pdf)
- [x] [Código de Unidade da Federação](http://www.ibge.gov.br/home/geociencias/areaterritorial/principal.shtm)
- [x] [Código do Município](http://www.ibge.gov.br/home/geociencias/areaterritorial/area.shtm)
- [x] [Cidades IBGE](http://www.cidades.ibge.gov.br/v3/cidades/home-cidades)
