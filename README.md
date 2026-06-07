⚙️ A&R Performance Reward
> Sistema de Premiação Automática por Desempenho para o Time de Análise e Reparo (A\&R)
HackWeb · Residência em TIC 29 · Web 3.0 · 2026
---
👤 Autor
Rogério Marques
GitHub: @rogeriomarques087
---
📋 Apresentando o Projeto
O A&R Performance Reward é um sistema descentralizado de premiação automática desenvolvido com smart contracts na blockchain Ethereum (rede de testes Sepolia).
O sistema elimina a necessidade de aprovações manuais e intermediários na distribuição de recompensas para o time de Análise e Reparo (A&R), tornando o processo mais transparente, rastreável e justo.
🔗 Links
Interface Web: https://rogeriomarques087.github.io/ar-performance-reward/ar-performance-reward-v3.html
Contrato na Sepolia: https://sepolia.etherscan.io/address/0x51D550f4c66098244Bd3B98EF5276095eAb2836c
Endereço do Contrato: `0x51D550f4c66098244Bd3B98EF5276095eAb2836c`
---
🎯 Contexto e Objetivos
O Problema
No time de A&R (Análise e Reparo), a distribuição de prêmios por desempenho depende de:
✗ Aprovações manuais de gestores
✗ Processos burocráticos e demorados
✗ Falta de transparência nos critérios
✗ Risco de favoritismo ou erros humanos
✗ Dificuldade de auditoria dos pagamentos
A Solução
Um smart contract que automatiza todo o fluxo:
Gestor registra métricas de desempenho de cada técnico
Contrato calcula automaticamente a pontuação
Prêmio é liberado diretamente para a carteira do técnico
Tudo registrado on-chain — transparente e auditável por qualquer pessoa
Contexto de Aplicação
Área	Aplicação
Indústria	Times de manutenção e reparo em fábricas
Telecom	Técnicos de campo e suporte
TI	Times de suporte e infraestrutura
Logística	Equipes de operação e reparo
---
🏗️ Arquitetura da Solução
```
Gestor (Owner)
    │
    ├── depositarFundos() ──► Contrato recebe ETH
    ├── cadastrarTecnico() ──► Registra técnico na blockchain
    ├── registrarMetricas() ──► Calcula pontuação automaticamente
    └── liberarPremio() ──► Transfere ETH para técnico
                                    │
                              Técnico recebe
                              prêmio direto
                              na carteira
```
🏆 Tabela de Premiação
Nível	Pontuação Mínima	Prêmio
🥉 Bronze	60 pontos	0.01 ETH
🥈 Prata	75 pontos	0.025 ETH
🥇 Ouro	90 pontos	0.05 ETH
📊 Fórmula de Pontuação
```
Pontuação = (Reparos × 40%) + (Qualidade × 40%) + (Tempo × 20%)
```
Métrica	Peso	Critério
Reparos realizados	40%	1 reparo = 2pts (máx 100)
Taxa de qualidade	40%	Valor direto 0-100%
Tempo médio	20%	≤30min=100 / ≤60min=80 / ≤90min=60 / ≤120min=40 / >120min=20
---
🛠️ Tecnologias Utilizadas
Tecnologia	Uso
Solidity ^0.8.20	Smart contract
OpenZeppelin (Ownable)	Controle de acesso seguro
Sepolia Testnet	Rede de deploy
Remix IDE	Desenvolvimento e deploy
MetaMask	Carteira e assinatura de transações
Ethers.js v6	Integração frontend-blockchain
HTML/CSS/JS	Interface web
GitHub Pages	Hospedagem da interface
---
🚀 Como Executar
Pré-requisitos
Navegador Chrome ou Firefox
Extensão MetaMask instalada
Conta configurada na rede Sepolia Testnet
ETH de teste (obtenha em sepoliafaucet.com)
Passo a Passo
Acesse a interface: https://rogeriomarques087.github.io/ar-performance-reward/ar-performance-reward-v3.html
Clique em "Conectar Carteira" e aprove na MetaMask
Deposite fundos na aba "Depositar"
Cadastre técnicos na aba "Cadastrar"
Registre métricas na aba "Métricas"
Libere prêmios na aba "Premiar"
Consulte resultados na aba "Consultar"
Verificar no Etherscan
Acesse: https://sepolia.etherscan.io/address/0x51D550f4c66098244Bd3B98EF5276095eAb2836c
---
📁 Estrutura do Repositório
```
ar-performance-reward/
├── ar-performance-reward-v3.html   # Interface web completa
└── README.md                        # Documentação do projeto
```
---
🔐 Funções do Smart Contract
```solidity
// Depositar ETH para financiar prêmios
function depositarFundos() external payable onlyOwner

// Cadastrar técnico no sistema
function cadastrarTecnico(address \_endereco, string \_nome) external onlyOwner

// Registrar métricas e calcular pontuação automaticamente
function registrarMetricas(address \_tecnico, uint256 \_reparos, uint256 \_qualidade, uint256 \_tempoMedio) external onlyOwner

// Liberar prêmio individual
function liberarPremio(address \_tecnico) external onlyOwner

// Liberar prêmios para todos os elegíveis
function liberarTodosOsPremios() external onlyOwner

// Consultar dados de um técnico
function consultarTecnico(address \_tecnico) external view returns (...)

// Sacar fundos remanescentes
function sacarFundos() external onlyOwner
```
---
🔄 Fluxo de Execução Demonstrado
```
1. Gestor deposita 0.1 ETH no contrato
         ↓
2. Gestor cadastra técnico (nome + carteira)
         ↓
3. Gestor registra métricas (reparos, qualidade, tempo)
         ↓
4. Contrato calcula pontuação automaticamente
         ↓
5. Contrato determina nível (Bronze/Prata/Ouro)
         ↓
6. Gestor aciona liberação do prêmio
         ↓
7. ETH transferido direto para carteira do técnico
         ↓
8. Transação registrada e verificável on-chain
```
---
💡 Diferenciais do Projeto
Automação total — sem aprovação manual, sem intermediários
Transparência — todas as transações verificáveis no Etherscan
Imutabilidade — regras gravadas no contrato, não podem ser alteradas arbitrariamente
Segurança — uso de OpenZeppelin Ownable, proteção contra duplo pagamento
Interface intuitiva — qualquer gestor pode operar sem conhecimento técnico de blockchain
Log em tempo real — todas as ações registradas na interface
---
🤖 Uso de Inteligência Artificial
Conforme política do HackWeb, declaro o uso das seguintes ferramentas de IA como apoio no desenvolvimento:
Claude (Anthropic) — auxílio na estruturação do smart contract, revisão de lógica e desenvolvimento da interface web
A autoria intelectual, as decisões de arquitetura, os testes e a execução do projeto são de minha responsabilidade.
---
📝 Processo de Criação e Dificuldades
Como foi desenvolvido
Definição do problema real no contexto A&R
Modelagem das regras de negócio e fórmula de pontuação
Desenvolvimento do smart contract em Solidity com OpenZeppelin
Deploy na Sepolia Testnet via Remix IDE
Desenvolvimento da interface web com Ethers.js
Hospedagem via GitHub Pages
Testes completos do fluxo
Principais dificuldades
Configuração da MetaMask com arquivos locais — resolvido com GitHub Pages
Integração Ethers.js v6 — sintaxe diferente das versões anteriores
Gestão de múltiplas carteiras para teste — necessário para simular técnicos diferentes
---
Projeto desenvolvido para o HackWeb · Residência em TIC 29 · 2026
