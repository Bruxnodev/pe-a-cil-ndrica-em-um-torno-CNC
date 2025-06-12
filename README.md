# Peça Cilíndrica em um Torno CNC

Este repositório contém programas CNC (código G) para a usinagem completa de uma peça em um torno. O projeto inclui não apenas os códigos executáveis, mas também documentação em PDF e análises detalhadas para cada método de roscamento.

O principal objetivo é demonstrar e comparar diferentes abordagens para a execução de roscas externas, utilizando os ciclos `G76`, `G78` e o comando fundamental `G33`.

## Visão Geral da Peça Usinada

Todos os programas visam usinar um eixo a partir de um material em tarugo. O perfil final da peça inclui:
* Um diâmetro de $25 \, \text{mm}$ com um chanfro de $1.5 \times 45^\circ$.
* Uma seção para a rosca M25 com passo de 1.5.
* Um canal com $3 \, \text{mm}$ de largura.
* Uma seção cônica na extremidade da peça.

## Variações de Roscamento

Este repositório oferece três implementações distintas para a operação de roscamento. Cada método possui seus próprios arquivos de código, documentação e análise, conforme descrito abaixo.

### 1. `G76` - Ciclo Automático de Roscamento
Esta abordagem utiliza o ciclo `G76`, um dos mais eficientes para roscamento automático em controles Fanuc. Os arquivos para este método são:
* **Código G:** `v1.00100_comciclorosca_g76.nc`
* **Documentação:** `v1.00100_comciclorosca_g76.pdf`
* **Análise:** `G76-Análise-do-Ciclo-de-Roscamento-Automatico.md`

### 2. `G33` - Roscamento Síncrono (Passe a Passe)
Este método representa a forma mais fundamental de usinar uma rosca, programando cada passe individualmente com o comando `G33`. Os arquivos relacionados são:
* **Código G:** `v2.00100_passoapasso_g33.nc`
* **Documentação:** `v2.00100_passoapasso_g33.pdf`
* **Análise:** `G33_-Análise-Detalhada-do-Ciclo-de-Roscamento.md`

### 3. `G78` - Ciclo Automático de Roscamento (Simplificado)
Uma alternativa ao `G76`, o ciclo `G78` também executa o roscamento de forma automática e é encontrado em diversos comandos. Os arquivos são:
* **Código G:** `v3.00100_comciclorosca_g78.nc`
* **Documentação:** `v3.00100_comciclorosca_g78.pdf`
* **Análise:** `G78-Análise-Detalhada-do-Ciclo-de-Roscamento.md`

---

## Estrutura do Código Principal (`v1.00100_comciclorosca_g76.nc`)

O programa é dividido em seções lógicas, utilizando diferentes ferramentas para cada operação:

* **Preparação e Faceamento (`T0101`):** Usa `G96` para velocidade de corte constante e `G75` para facear a peça.
* **Desbaste e Acabamento do Perfil (`T0101`, `T0303`):** Usa `G71` para o desbaste do perfil e `G70` para o passe de acabamento.
* **Usinagem de Canal (`T0505`):** Usa interpolações lineares (`G1`) para mergulhar a ferramenta e criar o canal.
* **Roscamento (`T0909`):** Usa `G97` para rotação constante e o ciclo `G76` para executar a rosca.

---

## Como Utilizar

1.  Faça o clone ou o download deste repositório.
2.  Escolha a versão do programa (`.nc` file) que deseja estudar ou executar.
3.  Carregue o arquivo em um simulador CNC (ex: CIMCO Edit, G-Wizard Editor) ou diretamente no controle da máquina.
4.  **Atenção:** Sempre verifique e ajuste os parâmetros (corretores de ferramenta, zero peça, velocidades) de acordo com a sua máquina e material antes da execução real.

## Contribuições

Contribuições são bem-vindas! Se você tiver uma otimização, uma versão para outro tipo de comando CNC ou uma correção, sinta-se à vontade para abrir uma *Pull Request*.
