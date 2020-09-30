# Rotinas Utils

Rotinas utils para facilitar a programação utilizando [Revit API Docs].

## Código

```C#
#region 00 - Rotinas Utils

/// <summary>
/// Retorna elemento utilizando o PickObject
/// </summary>
/// <returns>Element</returns>
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
/// <returns>Elementos</returns>
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
/// Pega ponto XYZ utilizando o PickPoint
/// </summary>
/// <returns>Ponto XYZ</returns>
private XYZ PickXYZ()
{
    // Selection
    var selection = ActiveUIDocument.Selection;

    try {
        // Pick Object
        var xyz = selection.PickPoint();
    
        // retorna point
        return xyz;		
        
    } catch (Exception) {
        return null;
    }
}

#endregion
```

## Licença

<p>Este projeto está licenciado sob <a rel="license" href="https://creativecommons.org/licenses/by-nc-sa/4.0/deed.pt">Atribuição-NãoComercial-CompartilhaIgual 4.0 Internacional</a>.</p>

---

Você gostou deste projeto? Por favor [marque este projeto com estrela no GitHub](https://github.com/ricaun/RevitAPI/stargazers)!

[Revit API Docs]: https://www.revitapidocs.com/

[Video]: https://youtu.be/XSzhnT5PPnU
[VideoIma]: https://img.youtube.com/vi/XSzhnT5PPnU/hqdefault.jpg

[Rotinas Utils]: code/00-rotinas-utils/