# Neo
<h1> Desenvolvimento de um compilador </h1> </br>

• Deve ter, no mínimo, 3 tipos de variáveis </br>
- keywords.put("intx", Token.TokenType.INTX); </br>
  keywords.put("flx", Token.TokenType.FLX); </br>
  keywords.put("strx", Token.TokenType.STRX); </br>
  keywords.put("bool", Token.TokenType.BOOL); </br>
  
• Deve ter a estrutura de controle if . . . else; </br>
- keywords.put("InCase", Token.TokenType.IN_CASE); </br>
  keywords.put("Other", Token.TokenType.OTHER); </br>
  keywords.put("Else", Token.TokenType.ELSE); </br>
   
• Deve possibilitar ifs encadeados </br>
```
  Fx intx main() { 
    intx x = 3; 
    intx y = 4; 
    intx c = 2;

InCase (x > y){ 
	InCase(x > c) 
    		goOut("x é maior");
	} 
    } 
}
```
</br>
• Deve ter ao menos duas estruturas de repetição (while, do . . . while, for); </br>

- keywords.put("Echo", Token.TokenType.ECHO); </br>
  keywords.put("Play", Token.TokenType.PLAY); </br>
  keywords.put("Over", Token.TokenType.OVER); </br>
  </br>
• Deve possibilitar laços encadeados </br>

```
  Fx intx main() { 
    intx x = 3; 
    intx y = 4; 
    InCase (x > y){ 
    Play{ 
        y--; 
        } 
    Over(y == 0); 
    }    
```

</br>
• A parte de expressões envolvendo os operadores matemáticos deve ser realizada de maneira
correta, respeitando a precedência. </br>

```
    Fx intx main() { 
    intx x = 3; 
    intx y = 4; 
    intx c = 2; 
    intx conta = x + y * c; 
       goOut(conta); 
} 
```
</br>
• As atribuições também devem ser realizadas; </br>

```
    Fx intx main() { 
    intx x = 3;
    intx y = 4;
    intx c = 2;
    }
    
```


</br>
    
• Os comandos de leitura do teclado (Scanner, scanf, input, etc) e de impressão na tela (print)
devem ser disponibilizados. </br>

  - keywords.put("goOut", Token.TokenType.GO_OUT); </br>
    keywords.put("goOutln", Token.TokenType.GO_OUTLN); </br>
    keywords.put("plugIn", Token.TokenType.PLUG_IN); </br>
    
• O compilador tem que aceitar números decimais. </br>

```
 private Token number() {
        while (Character.isDigit(peek())) advance();
        if (peek() == '.' && Character.isDigit(peekNext())) {
            advance(); // Consume the '.'
            while (Character.isDigit(peek())) advance();
            return makeToken(Token.TokenType.LITERAL_FLOAT);
        }
        return makeToken(Token.TokenType.LITERAL_INT);
    }
```
    
</br>
• O compilador deve ter mensagens de erros. 
</br>
• A cada utilização de uma variável, é necessário verificar se ela já foi declarada.
</br>
• É necessário verificar se é possível realizar as operações, devido aos tipos das variáveis e ao
seu escopo.


| Tipo em NEO | Categoria | Descrição                         |
| ----------- | --------- | --------------------------------- |
| `intx`      | Numérico  | Número inteiro com sinal          |
| `flx`       | Numérico  | Número decimal em ponto flutuante |
| `strx`      | Texto     | Cadeia de caracteres (string)     |
| `bool`      | Booleano  | Tipo lógico (booleano)            |


-----

| Palavra-chave | Função                           |
| ------------- | -------------------------------- |
| `Fx`          | Declaração de função             |
| `InCase`      | Início de bloco condicional (if) |
| `Other`       | Bloco `else if`                  |
| `Else`        | Bloco `else`                     |
| `Echo`        | Laço de repetição (`for`)        |
| `Play`        | Início de bloco `loopEcho`       |
| `Over`        | Condição final de um `Play`      |
| `reply`       | Retorno de função                |
| `goOut`       | Impressão sem quebra de linha    |
| `goOutln`     | Impressão com quebra de linha    |
| `plugIn`      | Leitura de entrada do usuário    |

