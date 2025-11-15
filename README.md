# Atividade Prática – Revisão de código-fonte

## Tópicos:
- Notação de Grafo de Fluxo
- Complexidade Ciclomática
- Caminhos Básicos

## Notação de Grafo de Fluxo

(1) Início <br>
&nbsp; &nbsp; &nbsp; | <br>
&nbsp; &nbsp; &nbsp; v <br>
(2) conectarBD() <br>
&nbsp;  | &nbsp; &nbsp; &nbsp; \ <br>
&nbsp;  | &nbsp; &nbsp; &nbsp; &nbsp; \ Falha na conexão <br>
&nbsp;  | &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \ <br>
&nbsp;  | &nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; v <br>
&nbsp;  | &nbsp;&nbsp; &nbsp; &nbsp; (3) catch conectarBD <br>
&nbsp;  | &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; | <br>
&nbsp;  | &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; v <br>
&nbsp;  | &nbsp; &nbsp; &nbsp; &nbsp; Retorna null <br>
&nbsp;  | <br>
&nbsp;  v <br>
(4) Monta SQL <br>
&nbsp;  | <br>
&nbsp;  v <br>
(5) Executa query <br>
&nbsp;  | &nbsp; &nbsp; &nbsp; \ <br>
&nbsp;  | &nbsp; &nbsp; &nbsp; &nbsp; \ Erro ao executar <br>
&nbsp;  | &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \ <br>
&nbsp;  | &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; v <br>
&nbsp;  | &nbsp; &nbsp; &nbsp; &nbsp; (6) catch consulta <br>
&nbsp;  | &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; | <br>
&nbsp;  | &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; v <br>
&nbsp;  | &nbsp; &nbsp; &nbsp; &nbsp; Retorna false <br>
&nbsp;  | <br>
&nbsp;  v <br>
(7) rs.next? <br>
&nbsp;  | &nbsp; &nbsp; &nbsp; \ <br>
&nbsp;  | &nbsp; &nbsp; &nbsp; &nbsp; \ NÃO <br>
&nbsp;  | &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \ <br>
&nbsp;  | &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; v <br>
&nbsp;  | &nbsp; &nbsp; &nbsp; &nbsp; Retorna false <br>
&nbsp;  | <br>
 SIM <br>
&nbsp;  v <br>
(8) nome = rs.getString() <br>
&nbsp;  | <br>
&nbsp;  v <br>
return true <br>


## Complexidade Ciclomática

Fórmula:

V(G) = E - N + 2

Nós identificados = 9
Arestas = 10

V(G) = 10 - 9 + 2 = 3

**Complexidade ciclomática = 3**

## Caminhos Básicos

### Caminho 1: erro na conexão

1 → 2 → 3 → return false

### Caminho 2: conexão bem-sucedida, usuário não encontrado

1 → 2 → 4 → 5 → 7 (não) → return false


### Caminho 3: conexão bem-sucedida, usuário encontrado

1 → 2 → 4 → 5 → 7 (sim) → 8 → return true