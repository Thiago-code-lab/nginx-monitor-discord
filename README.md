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
#sudo nano /var/www/html/index.html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Site pessoal profissional rodando em Nginx no WSL">
    <title>Portfolio Digital</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css">
    <style>
        :root {
            --primary: #3a86ff;
            --primary-light: #5a9cff;
            --primary-dark: #2667cc;
            --dark: #1a1a2e;
            --darker: #0f3460;  /* Azul mais escuro similar à imagem */
            --light: #16213e;    /* Azul escuro para fundo */
            --lighter: #ffffff;
            --success: #2ecc71;
            --text: #f0f0f0;     /* Texto claro para contraste */
            --text-light: #c9d1d9; /* Texto secundário claro */
            --shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
            --transition: all 0.3s ease-in-out;
        }
        
        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 0;
            background-color: var(--light);
            background-image: linear-gradient(135deg, #0f3460 0%, #16213e 100%);  /* Gradiente azul escuro */
            color: var(--text);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            transition: var(--transition);
        }
        
        .container {
            max-width: 680px;
            margin: 2rem;
            padding: 3rem;
            background-color: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 16px;
            box-shadow: var(--shadow);
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: var(--transition);
        }
        
        h1 {
            color: var(--primary-light);
            margin-bottom: 1.75rem;
            font-weight: 700;
            font-size: 2rem;
            line-height: 1.3;
        }
        
        p {
            color: var(--text-light);
            margin-bottom: 2.5rem;
            font-size: 1.2rem;
            line-height: 1.8;
        }
        
        .status {
            display: inline-flex;
            align-items: center;
            gap: 0.75rem;
            padding: 1rem 1.5rem;
            background-color: rgba(46, 204, 113, 0.2);
            color: var(--success);
            border-radius: 9999px;
            font-weight: 600;
            margin-top: 1.5rem;
            border: 1px solid rgba(46, 204, 113, 0.3);
            transition: var(--transition);
            cursor: default;
        }
        
        .status:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(46, 204, 113, 0.3);
        }
        
        .status i {
            font-size: 1rem;
        }
        
        .emoji {
            font-size: 2.5rem;
            margin-bottom: 1.5rem;
            display: inline-block;
            filter: drop-shadow(0 4px 8px rgba(58, 134, 255, 0.4));
        }
        
        .animate-float {
            animation: float 3s ease-in-out infinite;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
        
        .tech-icons {
            display: flex;
            justify-content: center;
            gap: 1.5rem;
            margin: 2rem 0;
            flex-wrap: wrap;
        }
        
        .tech-icon {
            width: 40px;
            height: 40px;
            object-fit: contain;
            transition: var(--transition);
            filter: drop-shadow(0 2px 4px rgba(0,0,0,0.3)) brightness(1.1);
        }
        
        .tech-icon:hover {
            transform: scale(1.15);
            filter: drop-shadow(0 4px 8px rgba(58, 134, 255, 0.5)) brightness(1.2);
        }
        
        @media (max-width: 768px) {
            .container {
                padding: 2rem;
                margin: 1rem;
                backdrop-filter: blur(8px);
            }
            
            h1 {
                font-size: 1.75rem;
            }
            
            p {
                font-size: 1.1rem;
            }
            
            .tech-icons {
                gap: 1rem;
            }
            
            .tech-icon {
                width: 36px;
                height: 36px;
            }
        }
    </style>
</head>
<body>
    <div class="container animate__animated animate__fadeIn">
        <div class="emoji animate-float">🚀</div>
        <h1>Projeto Linux - DevSecOps</h1>
        <p>Ambiente Ubuntu no WSL executando Nginx de alto desempenho com monitoramento contínuo e integração via webhook para envio automático de alertas em tempo real, garantindo alta disponibilidade e rápida detecção de falhas em aplicações web.</p>
        
        <div class="tech-icons">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nginx/nginx-original.svg" class="tech-icon" title="Nginx" alt="Nginx">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg" class="tech-icon" title="Linux" alt="Linux">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/ubuntu/ubuntu-plain.svg" class="tech-icon" title="Ubuntu" alt="Ubuntu">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" class="tech-icon" title="HTML5" alt="HTML5">
        </div>
        
        <div class="status animate__animated animate__pulse animate__infinite">
            <i class="fas fa-circle"></i>
            Status: Operacional
        </div>
    </div>

    <!-- Script para o ícone de círculo no status -->
    <script src="https://kit.fontawesome.com/a076d05399.js" crossorigin="anonymous"></script>
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
## 🔄 Configurando o Reinício Automático do Nginx no Ubuntu (WSL) usando systemd

Para garantir que o serviço do Nginx seja reiniciado automaticamente em caso de falha, siga estes passos:

### 1. Editar o arquivo de serviço do Nginx

```bash
sudo nano /lib/systemd/system/nginx.service
```
### 2. Configurar parâmetros de reinício

Na seção [Service], adicione ou ajuste as seguintes diretivas:

```bash 
[Service]
Type=forking
PIDFile=/run/nginx.pid
ExecStartPre=/usr/sbin/nginx -t -q -g 'daemon on; master_process on;'
ExecStart=/usr/sbin/nginx -g 'daemon on; master_process on;'
ExecReload=/usr/sbin/nginx -g 'daemon on; master_process on;' -s reload
ExecStop=/bin/kill -s TERM $MAINPID

Restart=always
RestartSec=90
```
Explicação das diretivas:

Restart=always → Reinicia o serviço automaticamente em qualquer falha ou término

RestartSec=90 → Aguarda 90 segundos antes de tentar reiniciar

### 3. Aplicar as alterações:
```bash
# Recarregar configurações do systemd
sudo systemctl daemon-reload

# Reiniciar o serviço Nginx
sudo systemctl restart nginx
```
### 4. Verificar o status: 
```bash
sudo systemctl status nginx
```

Aplicar as alterações:
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

### 🌐 Stack Principal
[![Nginx](https://img.shields.io/badge/-Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white)](https://nginx.org)
[![HTML5](https://img.shields.io/badge/-HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/-CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)

### ⚙️ Infraestrutura
[![WSL](https://img.shields.io/badge/-WSL-4D4D4D?style=for-the-badge&logo=windows-terminal&logoColor=white)](https://learn.microsoft.com/en-us/windows/wsl/)
[![Ubuntu](https://img.shields.io/badge/-Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)](https://ubuntu.com)
[![Cron](https://img.shields.io/badge/-Cron-5C5C5C?style=for-the-badge&logo=linux&logoColor=white)](https://man7.org/linux/man-pages/man5/crontab.5.html)

### 🔧 Ferramentas de Desenvolvimento
[![Bash](https://img.shields.io/badge/-Bash-121011?style=for-the-badge&logo=gnu-bash&logoColor=white)](https://www.gnu.org/software/bash/)
[![Shell Script](https://img.shields.io/badge/-Shell_Script-5391FE?style=for-the-badge&logo=shell&logoColor=white)](https://www.shellscript.sh)
[![cURL](https://img.shields.io/badge/-cURL-073551?style=for-the-badge&logo=curl&logoColor=white)](https://curl.se)

### 🤖 Integrações
[![Discord Webhooks](https://img.shields.io/badge/-Discord_Webhooks-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.com)
[![Markdown](https://img.shields.io/badge/-Markdown-000000?style=for-the-badge&logo=markdown&logoColor=white)](https://www.markdownguide.org)

---
