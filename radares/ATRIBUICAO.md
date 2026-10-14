# Base de radares do Ohm Maps: atribuição e licenças

Esta pasta (`radares/`) é publicada automaticamente por uma tarefa semanal do projeto Ohm Maps e lida pelo aplicativo
para manter a base de radares atualizada. Não edite os arquivos à mão: o próximo ciclo os sobrescreve.

## Arquivos

| Arquivo | O que é |
|---|---|
| `radares.bin` | A base: binário little-endian, cabeçalho `RDR1` + versão + quantidade + data, depois 24 bytes por radar, em ordem de latitude e longitude. |
| `radares.meta.json` | De onde veio cada fonte (URL, sha256, data), contagens por tipo e por fonte. |
| `catalogo.json` | Índice que o aplicativo consulta: `formato`, `sha256` e `bytes` do `radares.bin`, `quantidade`, `geradoEm` (data da base), `meta` e `fontes`. |

O aplicativo só troca a base depois de conferir o `sha256` e o tamanho de cada arquivo e de ler o binário por inteiro.

## Fontes e licenças

A base é uma obra derivada de dados abertos, publicada aqui sob a mesma licença de seus dados de origem.

- **Pardal** (`github.com/Murkiriel/pardal`, `brasil/radares.csv`), que reúne dados do OpenStreetMap e de órgãos de trânsito.
  Licença **ODbL 1.0** (Open Database License): https://opendatacommons.org/licenses/odbl/1-0/
  Contém informações de © colaboradores do OpenStreetMap (https://www.openstreetmap.org/copyright).
- **ANTT**, dados abertos de radares em rodovias concedidas (`dados.antt.gov.br`, conjunto `radar`).
  Licença **Creative Commons Atribuição (CC BY)**.
- **CET-SP**, fiscalização eletrônica do trânsito de São Paulo (`dados.prefeitura.sp.gov.br`,
  conjunto `fiscalizacao-eletronica-do-transito`). Licença **Creative Commons Atribuição (CC BY)**.
  Os endereços da CET-SP foram convertidos em coordenadas por geocodificação; só entram onde casam com um ponto já conhecido.

Por causa da cláusula de compartilhamento pela mesma licença da ODbL, esta base (`radares.bin`) também é distribuída sob a
**ODbL 1.0**. Se você a reutilizar, mantenha esta atribuição e distribua a obra derivada sob a mesma licença.

## Limites

A base é um auxílio, não uma garantia. Pontos podem estar desatualizados ou imprecisos, e lombadas e radares fixos não são
distinguidos em parte dos dados nacionais. Sempre vale a sinalização da via.
