JavascriptLess

A ideia é que a marcação funcione sem o Javascript.

Imagine um ecommerce deixar de vender porque o botão de compra não está liberado.

Caso o Javascript:
- não tenha carregado ainda;
- dado algum erro.

### Formulário

```html
<form action="https://test.com/register" method="post"> 
  <label>Nome: <input type="text" name="name"/></label> <br>
  <input type="hidden" name="feature" value="new">
  <input type="submit" value="submit"> <br>
</form>
```

Se não tiver javascript ainda assim o formulário será submetido.

input[type="hidden"] para enviar os valores que não são visíveis.

