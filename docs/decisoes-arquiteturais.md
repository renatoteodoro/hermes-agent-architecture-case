# Registro de decisões arquiteturais

## 1. API Server em vez de acesso direto à máquina

A interface web conversa com um endpoint autenticado. O usuário externo não recebe terminal, acesso ao sistema de arquivos ou credenciais da VPS.

## 2. HTTPS em um túnel dedicado

O serviço continua escutando apenas em loopback. O túnel publica somente a rota necessária e evita abrir diretamente a porta do processo na máquina.

## 3. Chaves fora da configuração versionada

O arquivo de configuração referencia variáveis de ambiente. A chave não aparece no repositório, no prompt do agente nem nos logs de aplicação.

## 4. Ferramentas mínimas por identidade

Sessões externas recebem uma identidade separada. Um guardrail filtra o catálogo de ferramentas antes da execução e nega a chamada quando a regra não pode ser comprovada.

## 5. MCP como contrato de integração

O agente não conhece detalhes internos da plataforma conectada. Ele descobre ferramentas MCP e chama operações com entradas estruturadas, o que reduz acoplamento e facilita auditoria.

## 6. Aprovação humana como estado do fluxo

A revisão não é uma mensagem informal. Cada entrega assume um estado: aguardando aprovação, aprovada, recusada ou em ajuste. Apenas o estado aprovado libera o arquivamento.

## 7. Entrega por link, não por caminho local

A interface externa não acessa o disco da VPS. A saída visual é publicada em uma central protegida e o agente devolve um link verificável.
