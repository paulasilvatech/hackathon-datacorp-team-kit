---
applyTo: "src/auth/**,src/crypto/**,**/config/**"
---

# Convenções de Segurança

## Auth: bcrypt/argon2, rate limiting, MFA para admin
## Authz: toda requisição, menor privilégio, nível de recurso
## Entrada: consultas parametrizadas, sanitizar HTML, validar uploads
## Agent: sem permissões autoconcedidas, sem banco de produção sem aprovação
