# Revit API
Códigos em C# para Revit API utilizando Macro e o SharpDevelop.

<a rel="license" href="https://creativecommons.org/licenses/by-nc-sa/4.0/deed.pt"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a>

## Documentação Revit Api

* [Revit API Docs (English)][Revit API Docs]

## Projetos

### 00 - Rotinas Utils

Rotinas utils para facilitar a programação utilizando [Revit API Docs].

* [Código Fonte](code/00-rotinas-utils)

### 01 - Meu primeiro Macro

Projeto que cria um [TaskDialog] que mostra uma mensagem simples utilizando o Macro do Revit.

* [Código Fonte](code/01-meu-primeiro-macro/)

### 02 - Seleciona Elementos

Projeto que utiliza [Selection] Class para mostrar os elementos selecionados no [Document].

* [Código Fonte](code/02-seleciona-elementos/)

### 03 - Elementos e Parâmetros

Projeto que mostra os [Parameter] dos [Element] e edita utilizando [Transaction].

* [Código Fonte](code/03-elementos-e-parametros/)

### 04 - Move Elementos

Projeto que move a posição de [Element] utiliando o [ElementTransformUtils].

* [Código Fonte](code/04-movendo-elementos/)

### 05 - Rotaciona Elementos

Projeto que rotaciona a posição de [Element] utiliando o [ElementTransformUtils].

* [Código Fonte](code/05-rotaciona-elementos/)

### 06 - RevitLookup

[RevitLookup] é uma ferramenta interativa de exploração do banco de dados Revit BIM para visualizar e navegar nas propriedades e relacionamentos dos elementos.

* [Código Fonte](code/06-RevitLookup/)

[RevitLookup]: https://github.com/jeremytammik/RevitLookup

### 07 - Seleciona Parede com Filtro

Projeto que seleciona todos os [Element] da mesma categoria [Wall] utilizando o [FilteredElementCollector].

* [Código Fonte](code/07-seleciona-parede-com-filtro/)

## Licença

<p>Este projeto está licenciado sob <a rel="license" href="https://creativecommons.org/licenses/by-nc-sa/4.0/deed.pt">Atribuição-NãoComercial-CompartilhaIgual 4.0 Internacional</a>.</p>

---

Você gostou deste projeto? Por favor [marque este projeto com estrela no GitHub](https://github.com/ricaun/RevitAPI/stargazers)!

[Revit API Docs]: https://www.revitapidocs.com/

[TaskDialog]: https://www.revitapidocs.com/2020/853afb57-7455-a636-9881-61a391118c16.htm
[Selection]: https://www.revitapidocs.com/2020/31b73d46-7d67-5dbb-4dad-80aa597c9afc.htm
[Document]: https://www.revitapidocs.com/2020/db03274b-a107-aa32-9034-f3e0df4bb1ec.htm
[Element]: https://www.revitapidocs.com/2020/eb16114f-69ea-f4de-0d0d-f7388b105a16.htm
[Parameter]: https://www.revitapidocs.com/2020/333ff41b-e6a7-d959-60bf-c3bfae495581.htm
[Transaction]: https://www.revitapidocs.com/2020/308ebf8d-d96d-4643-cd1d-34fffcea53fd.htm
[ElementTransformUtils]: https://www.revitapidocs.com/2020/781ad017-5ee5-f44b-5db2-e8e1f883ae5d.htm
[Wall]: https://www.revitapidocs.com/2020/b5891733-c602-12df-beab-da414b58d608.htm
[FilteredElementCollector]: https://www.revitapidocs.com/2020/263cf06b-98be-6f91-c4da-fb47d01688f3.htm