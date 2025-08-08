# 🚀 Nginx Monitor Discord

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT) 
![Shell Script](https://img.shields.io/badge/Shell_Script-121011?style=flat&logo=gnu-bash&logoColor=white)

Projeto de monitoramento de sites com Nginx em ambiente Linux (WSL) que envia alertas para Discord quando o serviço fica indisponível.

## 📋 Descrição

Sistema completo que oferece:

✅ **Instalação Automática**
- Configuração do Nginx no WSL
- Setup inicial completo

🖥️ **Página de Status**
- HTML personalizado
- Visual clean e informativo

🔔 **Monitoramento em Tempo Real**
- Verificações minuto a minuto
- Notificações instantâneas

📊 **Logging Detalhado**
- Registro de todas as verificações
- Histórico de disponibilidade

## 🛠️ Pré-requisitos

### 💻 Hardware/Software
- Windows 10/11 com WSL ativado
- Terminal Ubuntu (versão 20.04 ou superior)

### 🔑 Acessos
- Permissões administrativas (sudo)
- Canal do Discord configurado
- Webhook do Discord criado

### 🌐 Rede
- Conexão com internet estável
- Portas 80 (HTTP) liberadas

## 🔧 Instalação Rápida

### 1. Instalação do WSL (Windows Subsystem for Linux)

Execute no **PowerShell como Administrador**:

```powershell
# Comando para instalação completa do WSL
wsl --install

# Verifique a versão instalada
wsl --version
```
## 🐧 Configuração do Nginx no Ubuntu/WSL

### 1. Atualização do Sistema e Instalação

Execute no terminal Ubuntu:

```bash
# Atualizar lista de pacotes e sistema
sudo apt update && sudo apt upgrade -y

# Instalar o Nginx
sudo apt install nginx -y
```
### 2. 📝 Criando a página inicial padrão

Configuração da Página HTML

```bash
sudo tee /var/www/html/index.html <<'EOF'
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Meu Site</title>
</head>
<body>
<h1 style="text-align:center; color:green;">Meu site está online!</h1>
<p style="text-align:center;">Servidor Nginx rodando no WSL</p>
</body>
</html>
EOF

```
## ⚙️ Configuração do Monitoramento

### 📜 Criando o Script de Monitoramento

Crie o arquivo `/usr/local/bin/monitor_site.sh` com o seguinte conteúdo:

```bash
sudo tee /usr/local/bin/monitor_site.sh <<'EOF'
#!/bin/bash

# Configurações básicas
URL="http://localhost"
LOG_FILE="/var/log/monitoramento_site.log"
WEBHOOK="https://discord.com/api/webhooks/URL_DO_SEU_WEBHOOK_AQUI"

# Verificar status do site
STATUS=$(curl -s -o /dev/null -w "%{http_code}" "$URL")
DATA_HORA=$(date "+%Y-%m-%d %H:%M:%S")

# Lógica de notificação
if [ "$STATUS" -ne 200 ]; then
    # Mensagem para Discord
    MENSAGEM="⚠️ **ALERTA**: Site fora do ar!  
    **Código HTTP**: $STATUS  
    **Data/Hora**: $DATA_HORA"
    
    # Enviar para webhook do Discord
    curl -H "Content-Type: application/json" \
         -X POST \
         -d "{\"content\": \"$MENSAGEM\"}" \
         "$WEBHOOK"
    
    # Registrar no log
    echo "$DATA_HORA - ERRO - Código: $STATUS" >> "$LOG_FILE"
else
    echo "$DATA_HORA - OK - Código: $STATUS" >> "$LOG_FILE"
fi
EOF
```
## 🔒 Configuração de Permissões

### 🛠️ Concedendo permissões necessárias

Execute os seguintes comandos no terminal:

```bash
# Tornar o script executável
sudo chmod +x /usr/local/bin/monitor_site.sh

# Criar arquivo de log
sudo touch /var/log/site_monitor.log

# Definir permissões de leitura/escrita
sudo chmod 666 /var/log/site_monitor.log
```
## ⏰ Configuração do Agendamento CRON

### 📅 Adicionando o monitoramento ao CRON

Execute o seguinte comando para configurar a verificação minuto a minuto:

```bash
(crontab -l 2>/dev/null; echo "* * * * * /usr/local/bin/monitor_site.sh") | crontab -
```
## ⚙️ Estrutura da Expressão CRON

### 📋 Formato Básico:
```text
* * * * * comando_a_ser_executado
│ │ │ │ │
│ │ │ │ └─── Dia da semana (0-6) (0=Domingo)
│ │ │ └───── Mês (1-12)
│ │ └─────── Dia do mês (1-31)
│ └───────── Hora (0-23)
└─────────── Minuto (0-59)
```
# 🧪 Como Testar o Monitoramento

## 🔍 Testes Básicos

Execute estes comandos sequencialmente para testar todo o sistema:

```bash
# 1. Verificar status inicial
echo "Teste iniciado em: $(date)"
echo -e "\n➡️ Verificando site..."
curl -I http://localhost

# 2. Simular falha
echo -e "\n➡️ Parando Nginx..."
sudo systemctl stop nginx
curl -I http://localhost || echo "✅ Nginx parado com sucesso"

# 3. Monitorar logs (aguarde 1 minuto)
echo -e "\n➡️ Monitorando logs..."
timeout 75 tail -f /var/log/site_monitor.log

# 4. Restaurar serviço
echo -e "\n➡️ Reiniciando Nginx..."
sudo systemctl start nginx
curl -I http://localhost && echo "✅ Nginx reiniciado com sucesso"

# 5. Verificar notificação no Discord
echo -e "\nVerifique se a notificação chegou no Discord!"
```
# 🛠️ Tecnologias Utilizadas

## 🌐 Stack Principal

[![Nginx](https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white)](https://nginx.org)
[![Bash](https://img.shields.io/badge/Bash-121011?style=for-the-badge&logo=gnu-bash&logoColor=white)](https://www.gnu.org/software/bash/)
[![Discord Webhooks](https://img.shields.io/badge/Discord_Webhooks-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.com)

## ⚙️ Infraestrutura

[![WSL](https://img.shields.io/badge/WSL-4D4D4D?style=for-the-badge&logo=windows-terminal&logoColor=white)](https://learn.microsoft.com/en-us/windows/wsl/)
[![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)](https://ubuntu.com)
[![Cron](https://img.shields.io/badge/Cron-5C5C5C?style=for-the-badge&logo=linux&logoColor=white)](https://man7.org/linux/man-pages/man5/crontab.5.html)

## 📚 Linguagens & Ferramentas

[![Shell Script](https://img.shields.io/badge/Shell_Script-121011?style=for-the-badge&logo=gnu-bash&logoColor=white)](https://www.shellscript.sh)
[![cURL](https://img.shields.io/badge/cURL-073551?style=for-the-badge&logo=curl&logoColor=white)](https://curl.se)
[![Markdown](https://img.shields.io/badge/Markdown-000000?style=for-the-badge&logo=markdown&logoColor=white)](https://www.markdownguide.org)

---
