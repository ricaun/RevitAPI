# Move Elementos

Projeto que move a posição de [Element] utiliando o [ElementTransformUtils].

## Vídeo

[![VideoIma]][Video]

## Código

```C#
#region 04 - Move Elementos 

/// <summary>
/// Retorna elemento utilizando o PickObject
/// </summary>
/// <returns>Elemento Selecionado</returns>
private Element PickElement()
{
    // Document
    var document = ActiveUIDocument.Document;
    // Selection
    var selection = ActiveUIDocument.Selection;

    try {
        // Pick Object
        var reference = selection.PickObject(ObjectType.Element);
    
        // Element
        var elementId = reference.ElementId;
        var element = document.GetElement(elementId);
        
        // Retorna Elemento
        return element;		
        
    } catch (Exception) {
        return null;
    }
}

/// <summary>
/// Retorna elementos utilizando o PickObjects
/// </summary>
/// <returns>Lista de Elementos Selecionados</returns>
private List<Element> PickElements()
{
    // Document
    var document = ActiveUIDocument.Document;
    // Selection
    var selection = ActiveUIDocument.Selection;

    try {
        // Pick Object
        var reference = selection.PickObjects(ObjectType.Element);
    
        // Reference to Elements
        var elementIds = reference.Select(r => r.ElementId);
        var elements = elementIds.Select(id => document.GetElement(id));
    
        // Retorna Elemento
        return elements.ToList();
        
    } catch (Exception) {
        return null;
    }
}

/// <summary>
/// Seleciona elemento e move para o lado
/// </summary>
public void ElementMove()
{
    // Document
    var document = ActiveUIDocument.Document;
    
    // Pick Element
    var element = PickElement();
    
    // Se Element for valido
    if (element != null)
    {
        // Cria Transaction
        Transaction transaction = new Transaction(document);
        transaction.Start("ElementMove");
        
        // Valor para mover
        var move = new XYZ(1.0,0.0,0.0);
        
        // Pés para metros
        move = move.Divide(0.3048);
        
        // Move Element
        ElementTransformUtils.MoveElement(document, element.Id, move);
        
        // Envia todas as modificações
        transaction.Commit();
    }
}

/// <summary>
/// Seleciona elemento e move para o lado até apertar esc para sair do comando
/// </summary>
public void ElementMoveWhile()
{
    // Document
    var document = ActiveUIDocument.Document;
    
    // Pick Element
    var element = PickElement();

    // Se Element for valido
    while (element != null) {
        
        // Cria Transaction
        Transaction transaction = new Transaction(document);
        transaction.Start("ElementMove");
        
        // Valor para mover
        var move = new XYZ(1.0,0.0,0.0);
        
        // Pés para metros
        move = move.Divide(0.3048);
        
        // Move Element
        ElementTransformUtils.MoveElement(document, element.Id, move);
        
        // Envia todas as modificações
        transaction.Commit();
        
        // Pick outro Element
        element = PickElement();
    }
}

/// <summary>
/// Seleciona elementos e move para o lado
/// </summary>
public void ElementMoveAll()
{
    // Document
    var document = ActiveUIDocument.Document;
    
    // Pick Elements
    var elements = PickElements();

    // Se Element for valido
    if (elements != null) {
        
        // Cria Transaction
        Transaction transaction = new Transaction(document);
        transaction.Start("ElementMove");
        
        // Valor para mover
        var move = new XYZ(1.0,0.0,0.0);
        
        // Pés para metros
        move = move.Divide(0.3048);
        
        // Move Element
        ElementTransformUtils.MoveElements(document, elements.Select(e => e.Id).ToList(), move);
        
        // Envia todas as modificações
        transaction.Commit();
    }
}
}

#endregion
```

## Licença

<p>Este projeto está licenciado sob <a rel="license" href="https://creativecommons.org/licenses/by-nc-sa/4.0/deed.pt">Atribuição-NãoComercial-CompartilhaIgual 4.0 Internacional</a>.</p>

---

Você gostou deste projeto? Por favor [marque este projeto com estrela no GitHub](https://github.com/ricaun/RevitAPI/stargazers)!

[Video]: https://youtu.be/LODrbyzhEz0
[VideoIma]: https://img.youtube.com/vi/LODrbyzhEz0/hqdefault.jpg

[Element]: https://www.revitapidocs.com/2020/eb16114f-69ea-f4de-0d0d-f7388b105a16.htm
[ElementTransformUtils]: https://www.revitapidocs.com/2020/781ad017-5ee5-f44b-5db2-e8e1f883ae5d.htm
[Transaction]: https://www.revitapidocs.com/2020/308ebf8d-d96d-4643-cd1d-34fffcea53fd.htm
