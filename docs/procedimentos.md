# Procedimentos de Análise Técnica

Guia oficial para diagnósticos e *troubleshooting* da equipe de Sustentação.

!!! tip "Dica de Navegação"
    Use o menu lateral direito **(Índice)** para pular direto para o tópico desejado ou aperte `Ctrl + F` para buscar nesta página.

---

## 1. Banco de Dados (Database)

### 1.1. Query de Locks (Travamentos)
Procedimento para identificar sessões travadas no banco.

??? example "Ver Query SQL"
    ```sql
    SELECT * FROM performance_schema.events_waits_current 
    WHERE TIMER_WAIT > 10000000000;
    ```

### 1.2. Reset de Senha de Serviço
Passo a passo para rotacionar credenciais de aplicação.
1. Acesse o Vault.
2. Gere nova credencial.
3. Atualize a variável de ambiente `DB_PASSWORD`.

---

## 2. Integrações (APIs)

### 2.1. Erro 504 (Gateway Timeout)
Ocorre quando o backend demora mais de 30s para responder.
* **Causa Provável:** Query lenta ou serviço travado.
* **Ação:** Verificar logs de APM (Datadog/Dynatrace).

### 2.2. Erro 401 (Unauthorized)
Geralmente expirou o Token JWT.
* **Ação:** Solicitar novo token no endpoint `/auth`.

---

## 3. Infraestrutura

### 3.1. Reinício de Pods (Kubernetes)
!!! danger "Cuidado"
    Nunca reinicie mais de 50% dos pods de uma vez.

Comando seguro para *rolling update*:
```bash
kubectl rollout restart deployment/nome-do-app