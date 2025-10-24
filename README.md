<img width="800" height="200" alt="Image" src="https://github.com/user-attachments/assets/bc251934-6e76-47f8-99ef-af6788691611" />
<div align="center">
    
# 🔔 Nginx Monitor Discord!


<div align="center">

[![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)](https://www.linux.org/)
[![Nginx](https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white)](https://nginx.org/)
[![Bash](https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnu-bash&logoColor=white)](https://www.gnu.org/software/bash/)
[![Discord](https://img.shields.io/badge/Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

**🚨 Sistema de monitoramento automatizado para serviços web com notificações em tempo real via Discord**

*Projeto DevOps demonstrando automação, observabilidade e integração de sistemas*

[🎯 Visão Geral](#-visão-geral) • [🏗️ Arquitetura](#️-arquitetura) • [⚡ Instalação](#-instalação-completa) • [📊 Demonstração](#-demonstração-prática) • [📞 Contato](#-contato)

---

</div>

## 🎯 Visão Geral

> **Sistema completo de monitoramento e alertas para serviços Nginx em ambiente WSL, com notificações instantâneas via Discord Webhooks**

Este projeto implementa uma solução profissional de **Site Reliability Engineering (SRE)** que monitora continuamente a disponibilidade de aplicações web, detecta falhas em tempo real e notifica a equipe através de webhooks do Discord. Perfeito para demonstrar competências em DevOps, automação e observabilidade de sistemas.

### ✨ Características Principais

<table>
<tr>
<td align="center" width="25%">
<h3>🔄 Monitoramento</h3>
<p>Verificações automáticas a cada minuto</p>
</td>
<td align="center" width="25%">
<h3>⚡ Alertas Instantâneos</h3>
<p>Notificações via Discord Webhook</p>
</td>
<td align="center" width="25%">
<h3>📊 Logging Completo</h3>
<p>Histórico detalhado de uptime</p>
</td>
<td align="center" width="25%">
<h3>🔄 Auto-Recovery</h3>
<p>Reinício automático do Nginx</p>
</td>
</tr>
<tr>
<td align="center" width="25%">
<h3>🌐 Interface Web</h3>
<p>Dashboard personalizado</p>
</td>
<td align="center" width="25%">
<h3>⚙️ Cron Automation</h3>
<p>Agendamento inteligente</p>
</td>
<td align="center" width="25%">
<h3>🛡️ Systemd Integration</h3>
<p>Gestão robusta de serviços</p>
</td>
<td align="center" width="25%">
<h3>📈 Health Checks</h3>
<p>Verificação HTTP completa</p>
</td>
</tr>
</table>

### 🏆 Métricas de Performance

<div align="center">

| **Métrica** | **Valor** | **Impacto** |
|-------------|-----------|-------------|
| ⏱️ **Tempo de Resposta** | < 5 segundos | Alta velocidade de detecção |
| 🔄 **Frequência** | 60 segundos | Monitoramento contínuo |
| 📊 **Uptime Target** | 99.9% SLA | Confiabilidade empresarial |
| 🚨 **MTTR** | ~90 segundos | Recovery automático rápido |

</div>

---

## 🏗️ Arquitetura

### 📊 Diagrama de Sistema

```mermaid
graph TB
    subgraph WSL["💻 Windows Subsystem for Linux"]
        subgraph Services["🔧 Serviços"]
            A[🌐 Nginx Web Server<br/>Port 80]
            B[📜 Monitor Script<br/>/usr/local/bin/]
            C[⏰ Cron Scheduler<br/>Execução Minuto a Minuto]
            D[📊 Systemd<br/>Auto-restart Service]
        end
        
        subgraph Storage["💾 Armazenamento"]
            E[📝 Log Files<br/>/var/log/]
            F[🌐 HTML Files<br/>/var/www/html/]
        end
    end
    
    G[👤 Usuário<br/>Browser] -->|HTTP Request| A
    C -->|Executa| B
    B -->|Verifica| A
    B -->|Registra| E
    A -->|Serve| F
    B -->|HTTP 200?| H{Status Check}
    H -->|❌ Falha| I[🚨 Discord Webhook]
    H -->|✅ OK| E
    D -->|Monitora| A
    D -->|Reinicia se necessário| A
    I -->|Notifica| J[📱 Discord Channel]
    
    style A fill:#009639,stroke:#fff,stroke-width:2px,color:#fff
    style B fill:#4EAA25,stroke:#fff,stroke-width:2px,color:#fff
    style C fill:#FCC624,stroke:#000,stroke-width:2px,color:#000
    style D fill:#E34F26,stroke:#fff,stroke-width:2px,color:#fff
    style I fill:#5865F2,stroke:#fff,stroke-width:2px,color:#fff
    style J fill:#5865F2,stroke:#fff,stroke-width:2px,color:#fff
```

### 🔧 Stack Tecnológica

<div align="center">

| **Camada** | **Tecnologia** | **Função** |
|------------|---------------|-----------|
| **🌐 Web Server** | ![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat&logo=nginx&logoColor=white) | Servidor HTTP de alto desempenho |
| **🖥️ Sistema** | ![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=flat&logo=ubuntu&logoColor=white) ![WSL](https://img.shields.io/badge/WSL-4D4D4D?style=flat&logo=windows-terminal&logoColor=white) | Linux subsystem no Windows |
| **🔧 Automação** | ![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat&logo=gnu-bash&logoColor=white) ![Cron](https://img.shields.io/badge/Cron-5C5C5C?style=flat&logo=linux&logoColor=white) | Scripts e agendamento |
| **📊 Monitoramento** | ![cURL](https://img.shields.io/badge/cURL-073551?style=flat&logo=curl&logoColor=white) ![Systemd](https://img.shields.io/badge/Systemd-E34F26?style=flat&logo=systemd&logoColor=white) | Health checks e gestão de serviços |
| **🔔 Alertas** | ![Discord](https://img.shields.io/badge/Discord-5865F2?style=flat&logo=discord&logoColor=white) | Notificações em tempo real |
| **🎨 Frontend** | ![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white) ![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white) | Interface web moderna |

</div>

### 🏛️ Estrutura de Arquivos

```
📦 nginx-monitor-discord/
├── 🌐 /var/www/html/
│   └── 📄 index.html                    # Dashboard web customizado
├── 📜 /usr/local/bin/
│   └── 🔧 monitor_site.sh              # Script de monitoramento
├── 📊 /var/log/
│   └── 📝 monitoramento_site.log       # Logs de uptime/downtime
├── ⚙️ /lib/systemd/system/
│   └── 🛡️ nginx.service                # Configuração systemd
├── ⏰ Crontab
│   └── 🕐 */1 * * * *                  # Job de monitoramento
└── 📖 README.md                         # Esta documentação
```

---

## ⚡ Instalação Completa

### 📋 Pré-requisitos

<div align="center">

| **Requisito** | **Versão** | **Status** |
|---------------|-----------|-----------|
| ![Windows](https://img.shields.io/badge/Windows-0078D6?style=flat&logo=windows&logoColor=white) | 10/11 | ✅ Requerido |
| ![WSL](https://img.shields.io/badge/WSL-4D4D4D?style=flat&logo=windows-terminal&logoColor=white) | 2.0+ | ✅ Requerido |
| ![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=flat&logo=ubuntu&logoColor=white) | 20.04+ | ✅ Requerido |
| ![Discord](https://img.shields.io/badge/Discord-5865F2?style=flat&logo=discord&logoColor=white) | Webhook | ✅ Requerido |
| 🔑 **Sudo Access** | - | ✅ Requerido |

</div>

### 🚀 Instalação em 5 Etapas

#### **1️⃣ Instalar WSL**

Execute no **PowerShell como Administrador**:

```powershell
# Instalar WSL com Ubuntu
wsl --install

# Verificar instalação
wsl --version

# Iniciar Ubuntu
wsl
```

#### **2️⃣ Instalar e Configurar Nginx**

```bash
# Atualizar sistema
sudo apt update && sudo apt upgrade -y

# Instalar Nginx
sudo apt install nginx -y

# Verificar status
sudo systemctl status nginx

# Iniciar Nginx
sudo systemctl start nginx

# Habilitar inicialização automática
sudo systemctl enable nginx
```

#### **3️⃣ Criar Dashboard Web Profissional**

```bash
sudo tee /var/www/html/index.html <<'EOF'
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Nginx Monitoring Dashboard">
    <title>Projeto Linux - DevSecOps</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css">
    <style>
        :root {
            --primary: #3a86ff;
            --success: #2ecc71;
            --dark: #0f3460;
            --light: #16213e;
            --text: #f0f0f0;
        }
        
        * { margin: 0; padding: 0; box-sizing: border-box; }
        
        body {
            font-family: 'Inter', -apple-system, sans-serif;
            background: linear-gradient(135deg, #0f3460 0%, #16213e 100%);
            color: var(--text);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        
        .container {
            max-width: 680px;
            margin: 2rem;
            padding: 3rem;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 16px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .emoji {
            font-size: 2.5rem;
            margin-bottom: 1.5rem;
            animation: float 3s ease-in-out infinite;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
        
        h1 {
            color: var(--primary);
            margin-bottom: 1.5rem;
            font-size: 2rem;
        }
        
        p {
            color: var(--text);
            margin-bottom: 2rem;
            font-size: 1.1rem;
            line-height: 1.8;
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
            filter: drop-shadow(0 2px 4px rgba(0,0,0,0.3)) brightness(1.1);
            transition: transform 0.3s;
        }
        
        .tech-icon:hover {
            transform: scale(1.2);
        }
        
        .status {
            display: inline-flex;
            align-items: center;
            gap: 0.75rem;
            padding: 1rem 1.5rem;
            background: rgba(46, 204, 113, 0.2);
            color: var(--success);
            border-radius: 9999px;
            font-weight: 600;
            border: 1px solid rgba(46, 204, 113, 0.3);
        }
    </style>
</head>
<body>
    <div class="container animate__animated animate__fadeIn">
        <div class="emoji">🚀</div>
        <h1>Projeto Linux - DevSecOps</h1>
        <p>Ambiente Ubuntu no WSL executando Nginx de alto desempenho com monitoramento contínuo e integração via webhook para envio automático de alertas em tempo real, garantindo alta disponibilidade e rápida detecção de falhas em aplicações web.</p>
        
        <div class="tech-icons">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nginx/nginx-original.svg" class="tech-icon" alt="Nginx">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg" class="tech-icon" alt="Linux">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/ubuntu/ubuntu-plain.svg" class="tech-icon" alt="Ubuntu">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" class="tech-icon" alt="HTML5">
        </div>
        
        <div class="status">
            ● Status: Operacional
        </div>
    </div>
</body>
</html>
EOF

# Verificar criação
cat /var/www/html/index.html
```

#### **4️⃣ Configurar Script de Monitoramento**

```bash
# Criar script de monitoramento
sudo tee /usr/local/bin/monitor_site.sh <<'EOF'
#!/bin/bash

# ====================================
# Nginx Monitor - Discord Integration
# ====================================

# Configurações
URL="http://localhost"
LOG_FILE="/var/log/monitoramento_site.log"
WEBHOOK="https://discord.com/api/webhooks/SEU_WEBHOOK_AQUI"

# Verificar status HTTP
STATUS=$(curl -s -o /dev/null -w "%{http_code}" "$URL")
DATA_HORA=$(date "+%Y-%m-%d %H:%M:%S")

# Lógica de alertas
if [ "$STATUS" -ne 200 ]; then
    # Mensagem de erro para Discord
    MENSAGEM="🚨 **ALERTA CRÍTICO**
    
**Status**: Site Indisponível
**Código HTTP**: $STATUS
**URL**: $URL
**Timestamp**: $DATA_HORA
**Servidor**: $(hostname)

⚠️ Verificação necessária!"
    
    # Enviar notificação
    curl -H "Content-Type: application/json" \
         -X POST \
         -d "{\"content\": \"$MENSAGEM\"}" \
         "$WEBHOOK" 2>/dev/null
    
    # Log de erro
    echo "$DATA_HORA - ERRO - Código: $STATUS" >> "$LOG_FILE"
else
    # Log de sucesso
    echo "$DATA_HORA - OK - Código: $STATUS" >> "$LOG_FILE"
fi
EOF

# Tornar executável
sudo chmod +x /usr/local/bin/monitor_site.sh

# Criar arquivo de log
sudo touch /var/log/monitoramento_site.log
sudo chmod 666 /var/log/monitoramento_site.log
```

**⚠️ IMPORTANTE**: Substitua `SEU_WEBHOOK_AQUI` pela URL do seu webhook do Discord!

#### **5️⃣ Configurar Agendamento Cron**

```bash
# Adicionar job ao crontab
(crontab -l 2>/dev/null; echo "* * * * * /usr/local/bin/monitor_site.sh") | crontab -

# Verificar crontab
crontab -l

# Verificar serviço cron
sudo service cron status

# Iniciar cron se necessário
sudo service cron start
```

### 🛡️ Configurar Auto-Recovery do Nginx

```bash
# Editar serviço systemd
sudo nano /lib/systemd/system/nginx.service

# Adicionar na seção [Service]:
# Restart=always
# RestartSec=90

# Recarregar configurações
sudo systemctl daemon-reload

# Reiniciar Nginx
sudo systemctl restart nginx

# Verificar status
sudo systemctl status nginx
```

---

## 📊 Demonstração Prática

### 🎬 Fluxo de Monitoramento

<div align="center">

```mermaid
sequenceDiagram
    participant C as ⏰ Cron
    participant S as 📜 Script
    participant N as 🌐 Nginx
    participant L as 📝 Log
    participant D as 📱 Discord
    
    C->>S: Executa (a cada minuto)
    S->>N: curl http://localhost
    
    alt Status 200 OK
        N-->>S: HTTP 200
        S->>L: Registra: OK - 200
    else Status != 200
        N-->>S: HTTP 000/500/etc
        S->>L: Registra: ERRO - XXX
        S->>D: POST Webhook
        D-->>D: Notifica canal
    end
```

</div>

### 🧪 Teste Completo do Sistema

Execute este script de teste automatizado:

```bash
#!/bin/bash
echo "🔍 INICIANDO TESTE DE MONITORAMENTO"
echo "===================================="

# 1. Verificar status inicial
echo -e "\n1️⃣ Verificando status inicial do Nginx..."
sudo systemctl status nginx | grep "Active:"

# 2. Testar acesso ao site
echo -e "\n2️⃣ Testando acesso HTTP..."
curl -I http://localhost

# 3. Simular falha
echo -e "\n3️⃣ Simulando falha (parando Nginx)..."
sudo systemctl stop nginx
sleep 2
curl -I http://localhost 2>&1 | head -n 1

# 4. Aguardar verificação do cron
echo -e "\n4️⃣ Aguardando verificação do cron (75 segundos)..."
echo "Monitorando logs em tempo real:"
timeout 75 tail -f /var/log/monitoramento_site.log

# 5. Restaurar serviço
echo -e "\n5️⃣ Restaurando Nginx..."
sudo systemctl start nginx
sleep 2
sudo systemctl status nginx | grep "Active:"

# 6. Verificar logs
echo -e "\n6️⃣ Últimas 10 entradas do log:"
tail -n 10 /var/log/monitoramento_site.log

echo -e "\n✅ TESTE CONCLUÍDO!"
echo "Verifique se recebeu a notificação no Discord!"
```

### 📸 Evidências Visuais

<div align="center">

**🖥️ Dashboard Web em Produção**

<img width="1919" height="946" alt="Image" src="https://github.com/user-attachments/assets/fb83862f-e82b-49c0-9b3b-f000c89c9b89" />

---

**📊 Sistema de Logs Funcionando**

<img width="1517" height="788" alt="Image" src="https://github.com/user-attachments/assets/34725bce-de78-47db-b77f-becca1749f8e" />

---

**🔔 Alertas no Discord**

<img width="1502" height="781" alt="Image" src="https://github.com/user-attachments/assets/1926b8cc-304f-4a4c-9618-8b7da2857658" />

---

**⚙️ Script de Automação**

<img width="1332" height="363" alt="Image" src="https://github.com/user-attachments/assets/1ba17402-eafb-4065-841c-3edce8b626d0" />

---

</div>

---

## 🔧 Comandos Úteis

### 🌐 Gerenciar Nginx

```bash
# Status detalhado
sudo systemctl status nginx

# Iniciar serviço
sudo systemctl start nginx

# Parar serviço
sudo systemctl stop nginx

# Reiniciar serviço
sudo systemctl restart nginx

# Recarregar configuração
sudo systemctl reload nginx

# Testar configuração
sudo nginx -t

# Ver logs de erro
sudo tail -f /var/log/nginx/error.log

# Ver logs de acesso
sudo tail -f /var/log/nginx/access.log
```

### 📊 Monitorar Logs

```bash
# Ver últimas 20 linhas
tail -n 20 /var/log/monitoramento_site.log

# Seguir logs em tempo real
tail -f /var/log/monitoramento_site.log

# Filtrar apenas erros
grep "ERRO" /var/log/monitoramento_site.log

# Contar registros OK vs ERRO
echo "OK: $(grep -c 'OK' /var/log/monitoramento_site.log)"
echo "ERRO: $(grep -c 'ERRO' /var/log/monitoramento_site.log)"

# Calcular uptime
echo "Uptime: $(echo "scale=2; $(grep -c 'OK' /var/log/monitoramento_site.log) * 100 / $(wc -l < /var/log/monitoramento_site.log)" | bc)%"
```

### ⏰ Gerenciar Cron

```bash
# Listar jobs
crontab -l

# Editar crontab
crontab -e

# Remover todos os jobs
crontab -r

# Status do serviço cron
sudo service cron status

# Ver logs do cron
grep CRON /var/log/syslog | tail -n 20
```

### 🧪 Teste Manual

```bash
# Executar script manualmente
sudo /usr/local/bin/monitor_site.sh

# Testar webhook diretamente
curl -H "Content-Type: application/json" \
     -X POST \
     -d '{"content": "🧪 Teste manual do webhook!"}' \
     "https://discord.com/api/webhooks/SEU_WEBHOOK"
```

---

## 🔍 Troubleshooting

### ❌ Problemas Comuns e Soluções

| **Problema** | **Causa Possível** | **Solução** |
|--------------|-------------------|------------|
| Nginx não inicia | Porta 80 ocupada | `sudo lsof -i :80` e matar processo |
| Cron não executa | Serviço parado | `sudo service cron start` |
| Webhook não funciona | URL inválida | Verificar URL no Discord |
| Script sem permissão | Chmod incorreto | `sudo chmod +x /usr/local/bin/monitor_site.sh` |
| Logs não gravam | Sem permissão | `sudo chmod 666 /var/log/monitoramento_site.log` |

### 🐛 Debug Avançado

```bash
# Verificar se script tem erros de sintaxe
bash -n /usr/local/bin/monitor_site.sh

# Executar com debug
bash -x /usr/local/bin/monitor_site.sh

# Verificar permissões
ls -la /usr/local/bin/monitor_site.sh
ls -la /var/log/monitoramento_site.log

# Testar conectividade
curl -v http://localhost

# Ver processos do Nginx
ps aux | grep nginx
```

---

## 📚 Conceitos DevOps Aplicados

### 🎓 Práticas Demonstradas

<div align="center">

| **Conceito** | **Implementação** | **Benefício** |
|--------------|------------------|---------------|
| **🔄 Monitoring** | Health checks via cURL | Detecção proativa de falhas |
| **🚨 Alerting** | Discord Webhooks | Notificação em tempo real |
| **📊 Logging** | Arquivo de log estruturado | Auditoria e troubleshooting |
| **⚙️ Automation** | Cron + Bash scripts | Redução de trabalho manual |
| **🛡️ Resilience** | Systemd auto-restart | Alta disponibilidade |
| **📈 Observability** | Métricas de uptime | Visibilidade do sistema |

</div>

### 🏗️ Arquitetura SRE

Este projeto demonstra os **4 Pilares do SRE**:

1. **🎯 Service Level Objectives (SLO)**: Uptime target de 99.9%
2. **📊 Monitoring**: Verificações contínuas de saúde
3. **🚨 Alerting**: Notificações instantâneas de incidentes
4. **🔄 Automation**: Scripts para detecção e recovery

---

## 🚀 Evolução do Projeto

### 🎯 Roadmap de Melhorias

- [ ] **📊 Grafana Dashboard**: Visualização avançada de métricas
- [ ] **🔔 Múltiplos Canais**: Slack, Telegram, Email
- [ ] **📈 Prometheus Integration**: Métricas detalhadas
- [ ] **🤖 ChatOps**: Comandos via Discord
- [ ] **🔐 HTTPS Monitoring**: Verificação de certificados
- [ ] **🌍 Multi-site**: Monitorar vários endpoints
- [ ] **📱 Mobile App**: Notificações push nativas
- [ ] **🧪 Chaos Engineering**: Testes de resiliência

### 💡 Ideias para Contribuir

- Adicionar verificação de latência
- Implementar métricas de performance
- Criar dashboard React/Vue
- Integrar com PagerDuty
- Adicionar testes de carga

---

## 🤝 Contribuição

<div align="center">

**💡 Contribuições são bem-vindas! Este projeto é open-source e educacional.**

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=for-the-badge)](http://makeapullrequest.com)
[![Issues](https://img.shields.io/badge/Issues-Open-red?style=for-the-badge)](https://github.com/seu-usuario/nginx-monitor-discord/issues)

</div>

---

## 📞 Contato

<div align="center">

### 👨‍💻 **Thiago Cardoso Davi**
*DevOps Engineer | SRE Specialist | Cloud Architect*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/analyticsthiagocardoso)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Thiago-code-lab)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:analyticsdev.thiago@gmail.com)

**📧 analyticsdev.thiago@gmail.com**

</div>

---

## 📄 Licença

<div align="center">

**Este projeto é open-source sob a Licença MIT**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

*Use, modifique e aprenda livremente!*

</div>

---

## 🎓 Recursos de Aprendizado

### 📚 Documentação Oficial

- [Nginx Documentation](https://nginx.org/en/docs/)
- [Cron Manual](https://man7.org/linux/man-pages/man5/crontab.5.html)
- [Systemd Documentation](https://www.freedesktop.org/software/systemd/man/)
- [Discord Webhook Guide](https://discord.com/developers/docs/resources/webhook)
- [Bash Scripting Guide](https://www.gnu.org/software/bash/manual/)

### 🎥 Tutoriais Recomendados

- [DevOps Bootcamp](https://www.udemy.com/course/devops-bootcamp/)
- [Linux Administration](https://www.udemy.com/course/linux-administration/)
- [Site Reliability Engineering](https://sre.google/books/)

---

<div align="center">

### ⭐ **Se este projeto foi útil, considere dar uma estrela!** ⭐

