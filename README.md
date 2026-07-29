# Portfólio API - Postman (Suporte N1)

Projeto de estudo criado para praticar e demonstrar conhecimentos básicos de **API e Postman**, voltado para vagas de **Suporte Técnico N1**.

##  Objetivo

Mostrar na prática:
- Uso dos métodos HTTP (GET, POST, PUT, DELETE)
- Leitura de status codes e respostas JSON
- Organização de requisições em uma Collection
- Testes básicos automatizados no Postman

##  APIs utilizadas

- **[JSONPlaceholder](https://jsonplaceholder.typicode.com)** — API fake gratuita, usada para simular abertura, atualização e encerramento de "chamados" (posts).
- **[ViaCEP](https://viacep.com.br)** — API pública brasileira de consulta de CEP, usada como exemplo extra de integração nacional.

##  Requisições da Collection

| # | Método | Endpoint | O que faz | Status esperado |
|---|--------|----------|-----------|------------------|
| 1 | GET | `/posts/1` | Busca um "chamado" pelo ID | 200 |
| 2 | POST | `/posts` | Cria um novo "chamado" | 201 |
| 3 | PUT | `/posts/1` | Atualiza um "chamado" existente | 200 |
| 4 | DELETE | `/posts/1` | Remove/encerra um "chamado" | 200 |
| 5 | GET | ViaCEP `01001000` | Consulta um CEP (bônus) | 200 |

Cada requisição já vem com uma descrição e um teste automático (aba **Tests**) validando o status code da resposta.

##  Como usar

1. Abra o Postman
2. Clique em **Import**
3. Selecione o arquivo `Suporte-N1-API-Portfolio.postman_collection.json`
4. Execute as requisições uma a uma e veja os resultados na aba **Test Results**

##  Como isso se aplica no dia a dia de Suporte N1

Além de estudar os métodos HTTP, o principal valor do Postman no suporte é **diagnosticar problemas antes de escalar ou responder o cliente**. Alguns cenários práticos:

### Cenário 1: Cliente diz "não consigo fazer login"
- **Testo no Postman:** `POST /login` com o e-mail e senha
- **Resposta:** `401 Unauthorized` → `{ "erro": "Credenciais inválidas" }`
- **Conclusão:** não é bug, é credencial errada
- **Resposta ao cliente:** "Testei aqui e o sistema retornou 'credenciais inválidas'. Pode confirmar e-mail e senha? Posso te ajudar a redefinir se precisar."

### Cenário 2: Cliente diz "o sistema tá fora do ar"
- **Testo no Postman:** `GET /status`
- **Resposta:** `500 Internal Server Error`
- **Conclusão:** confirmado, é erro geral do servidor
- **Escalando pro time de dev:** "Reproduzi o problema relatado pelo cliente X. O endpoint /status está retornando 500. Print em anexo. Podem verificar os logs?"

### Cenário 3: Dev avisa "já corrigi o bug do cadastro, pode validar?"
- **Testo no Postman:** `POST /cadastro` com dados de teste
- **Resposta:** `201 Created`
- **Conclusão:** correção confirmada
- **Resposta ao dev:** "Validado! Retorna 201 normalmente agora. Pode fechar o chamado, vou avisar o cliente."

**Resumo da lógica:** testar antes de afirmar, ter prova em mãos (print da requisição/resposta), e traduzir entre a linguagem técnica (status code) para o time de dev e a linguagem simples para o cliente.

##  O que eu aprendi com esse projeto

- Diferença entre GET, POST, PUT e DELETE e quando usar cada um
- Como interpretar status codes (200, 201, 404, 500...)
- Como estruturar uma Collection organizada com variáveis de ambiente (`base_url`)
- Como escrever testes simples para validar respostas de API

---
*Projeto feito como parte de preparação para vaga de Suporte Técnico N1.*
