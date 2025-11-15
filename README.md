# Atividade Prática – Revisão de código-fonte

## Tópicos:
- Notação de Grafo de Fluxo
- Complexidade Ciclomática
- Caminhos Básicos

## Notação de Grafo de Fluxo

```
(1) Início
 |
 v
(2) conectarBD()
 |\
 | \ Falha na conexão
 |  \
 |   v
 |  (3) catch conectarBD
 |   |
 |   v
 |   return null
 |
 v
(4) Monta SQL
 |
 v
(5) Executa query
 |\
 | \ Erro ao executar
 |  \
 |   v
 |  (6) catch consulta
 |   |
 |   v
 |   return false
 |
 v
(7) rs.next?
 |\
 | \ NÃO
 |  \
 |   v
 |   return false
 |
 |SIM
 |
 v
(8) nome = rs.getString()
 |
 v
return true
```

## Complexidade Ciclomática
```
Nós identificados = 9
Arestas = 10

V(G) = E - N + 2
V(G) = 10 - 9 + 2 = 3
```

*Complexidade ciclomática = 3*

## Caminhos Básicos

### Caminho 1: erro na conexão

1 → 2 → 3 → return false

### Caminho 2: conexão bem-sucedida, usuário não encontrado

1 → 2 → 4 → 5 → 7 (não) → return false


### Caminho 3: conexão bem-sucedida, usuário encontrado

1 → 2 → 4 → 5 → 7 (sim) → 8 → return true
