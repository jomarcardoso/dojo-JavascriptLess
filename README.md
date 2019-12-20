# JavascriptLess

A ideia é que a marcação e o estilo funcione o máximo possível sem o Javascript.

Imagine um ecommerce deixar de vender porque o botão de compra não está liberado, porque o JavaScript:
- não tenha carregado ainda;
- dado algum erro.

Ou então o usário tem uma péssima experiência de ver um carrossel quebrado até o JS fazer efeito.

## Componentes

Algumas trechos de código contando menos com o Javascript.

### Formulário

```html
<form action="https://test.com/register" method="post"> 
  <label>Nome: <input type="text" name="name"/> </label> <br>
  <label>Email: <input type="text" name="email/> </label> <br>
  <input type="hidden" name="feature" value="new"> <br>
  <input type="submit" value="submit">
</form>
```

Se não tiver javascript ainda assim o formulário será submetido.

input[type="hidden"] para enviar os valores que não são editáveis.

No `form` há outros [atributos](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/form) que podem auxiliar, como enctype (semelhante ao content-type) e target.

**O que não deveria ser feito: (e eu ja vi)**

- `<button type="button" />` no evento de "click" fazer submit. Dependente do Javascript.
- Campos do formulário com qualquer "name" que são trocados ao submeter o formulário. Dependente do Javascript.
- Seletores por "id" pegando os valores dos campos. Se o formulário foi construído corretamento com [FormData](https://developer.mozilla.org/pt-BR/docs/Web/API/FormData/FormData) da para pegar eles.

## Accordion

``` html
<article class="accordion" data-js="accordion">
  <input type="checkbox" class="accordion__control" id="accordion-test" data-js="accordion-control" hidden>
  <label class="accordion__label" for="accordion-test" role="button" aria-expanded="false" data-js="accordion-label">accordion label</label>
  <div class="accordion__content">
    <%-- ... --%>
  </div>
</article>
```

```javascript
const elAccordions = document.querySelectorAll('[data-js="accordion"]');

Array.from(elAccordions).forEach((el) => {
  const elControl = el.querySelector('[data-js="accordion-control"]');
  const elLabel = el.querySelector('[data-js="accordion-label"]');

  function handleChange({ currentTarget: { checked: opened } }) {
    if (opened) {
      el.setAttribute('expanded', '');
      if (elLabel) elLabel.setAttribute('aria-expanded', 'true');

      return;
    }

    el.removeAttribute('expanded');
    if (elLabel) elLabel.setAttribute('aria-expanded', 'false');
  }

  if (elControl) elControl.addEventListener('change', handleChange);
});
```

O javascript está apenas complementando.

## Referências

- [jo-CSSComponents](https://github.com/jomarcardoso/jo-CSSComponents)

