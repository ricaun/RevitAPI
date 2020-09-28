# Seleciona Elementos

Projeto que utiliza [Selection] Class para mostrar os elementos selecionados no [Document].

## Vídeo

[![VideoIma]][Video]

## Código

```C#
#region 02 - Seleciona Elementos

/// <summary>
/// Seleciona o Elemento utilizando o PickObject
/// </summary>
public void SelectElement()
{
    // Document
    var document = ActiveUIDocument.Document;
    // Selection
    var selection = ActiveUIDocument.Selection;

    // Pick Object
    var reference = selection.PickObject(ObjectType.Element);

    // Element
    var elementId = reference.ElementId;
    var element = document.GetElement(elementId);
    
    // Message
    string title = "Revit";
    string message = "";
    message += element.Name;
    message += "\n";
    
    // Task Dialog
    TaskDialog task = new TaskDialog(title);
    task.MainInstruction = message;
    task.Show();
}

/// <summary>
/// Seleciona multiplos Elementos utilizando o PickObjects
/// </summary>
public void SelectElements()
{
    // Document
    var document = ActiveUIDocument.Document;
    // Selection
    var selection = ActiveUIDocument.Selection;

    // Pick Objects
    var reference = selection.PickObjects(ObjectType.Element);
    
    // Reference to Elements
    var elementIds = reference.Select(r => r.ElementId);
    var elements = elementIds.Select(id => document.GetElement(id));
    
    // Message
    string title = "Revit";
    string message = "";
    
    // For Each Element Name
    foreach (var element in elements) {
        message += element.Name;
        message += "\n";
    }
    
    // Task Dialog
    TaskDialog task = new TaskDialog(title);
    task.MainInstruction = message;
    task.Show();
}

#endregion
```

## Licença

<p>Este projeto está licenciado sob <a rel="license" href="https://creativecommons.org/licenses/by-nc-sa/4.0/deed.pt">Atribuição-NãoComercial-CompartilhaIgual 4.0 Internacional</a>.</p>

---

Você gostou deste projeto? Por favor [marque este projeto com estrela no GitHub](https://github.com/ricaun/RevitAPI/stargazers)!

[Video]: https://youtu.be/T6NWrt8mg9k
[VideoIma]: https://img.youtube.com/vi/T6NWrt8mg9k/hqdefault.jpg

[Selection]: https://www.revitapidocs.com/2020/31b73d46-7d67-5dbb-4dad-80aa597c9afc.htm
[Document]: https://www.revitapidocs.com/2020/db03274b-a107-aa32-9034-f3e0df4bb1ec.htm
