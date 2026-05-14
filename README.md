# Notificador Automático de Faturas

Script de automação desenvolvido em Python para o rastreamento e cobrança proativa de faturas com prazo de validade expirado.

## Objetivo
O projeto foi construído para resolver um gargalo administrativo comum: o monitoramento e a notificação manual de inadimplência. A aplicação consome uma base de dados estruturada, aplica lógicas de verificação temporal e orquestra o envio em lote de e-mails de cobrança personalizados de forma totalmente automatizada.

## Stack Tecnológico
* Linguagem: Python 3
* Processamento de Dados: Pandas
* Manipulação Temporal: biblioteca nativa `datetime`
* Integração de Rede: `smtplib` e `email.message` (Protocolo SMTP)

## Fluxo de Execução e Funcionalidades Principais
O script opera de forma linear, priorizando a eficiência na leitura dos dados e a segurança no envio das mensagens:
* Extração de Dados: Leitura estruturada de registros de clientes a partir de um arquivo `.csv` em memória.
* Filtro Temporal: Cálculo do delta entre a data de execução do script e a data de vencimento (formato AAAA-MM-DD) mapeada na base.
* Isolamento de Inadimplência: Separação eficiente das entidades que configuram atraso de pagamento.
* Orquestração de E-mails: Construção de templates HTML dinâmicos e disparo individualizado via servidor SMTP, injetando valores nominais e monetários específicos de cada registro.

## Estrutura de Dados Esperada
O script requer um arquivo `faturas.csv` no diretório raiz contendo os seguintes cabeçalhos textuais:
`cliente` | `email` | `valor` | `data_vencimento`

## Como Executar Localmente

1. Clone o repositório:
git clone https://github.com/StJ0hn/NotificadorAutomaticoDeFaturasVencidas.git

2. Provisione um ambiente virtual e instale as dependências:
python -m venv venv
source venv/bin/activate (Linux/macOS) ou venv\Scripts\activate (Windows)
pip install pandas

3. Configure o ambiente de disparo:
Edite o arquivo principal inserindo as credenciais de autenticação SMTP (e-mail remetente e Senha de App) nas variáveis designadas.

4. Execute a automação:
python nome_do_script.py
