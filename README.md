# Elipse E3/Power Console Log
Janela de saída de mensagens para Elipse E3/Power.

## Como usar

### Configuração
- Adicione a biblioteca `consolelog.lib` ao seu domínio.
- Instancie o xobject `Console` a um `DataServer` presente em algum `.prj` do domínio.
- Instancie o xcontrol `Output` a uma tela e, associe a propriedade `.Console` presente na janela de propriedades do xcontrol ao xobject adicionado no passo anterior, por exemplo, `Dados.Console1`.

### Utilização
Para escrever um *log* na janela de saída, basta escrever a mensagem desejada na propriedade `.WriteLine` do xobject `Console`, exemplo:
```vbs
Sub Foo()
  Dim xo
  Set xo = Application.GetObject("Dados.Console1") 
  xo.WriteLine = "Minha mensagem"
End Sub
```
Ou crie uma `Sub`:
```vbs
Sub Foo()
  WriteLine "Foo..."
End Sub

Sub Bar()
  WriteLine "Bar..."
End Sub

Sub WriteLine( ByVal s )
  Dim xo
  Set xo = Application.GetObject("Dados.Console1") 
  xo.WriteLine = s
End Sub
```
