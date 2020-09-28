# Elementos e Parâmetros

Projeto que mostra os [Parameter] dos [Element] e edita utilizando [Transaction].

## Vídeo

[![VideoIma]][Video]

## Código

```C#
#region 03 - Elementos e Parâmetros

/// <summary>
/// Seleciona o elemento e mostra o valor do parâmetro de Comentário
/// </summary>
public void SelectElementParameter()
{
    // Nome do Parâmetro
    var parameterName = "Comments";
    
    // Document
    var document = ActiveUIDocument.Document;
    // Selection
    var selection = ActiveUIDocument.Selection;

    // Pick Object
    var reference = selection.PickObject(ObjectType.Element);

    // Element
    var elementId = reference.ElementId;
    var element = document.GetElement(elementId);
            
    // Procura parâmetro pelo nome
    var parameter = element.LookupParameter(parameterName);
    
    // Se parâmetro for valido
    if (parameter != null)
    {
        // Message
        string title = "Revit";
        string message = "";
        message += element.Name;
        message += "\n";
        message += parameter.AsString();
        message += "\n";
        
        // Task Dialog
        TaskDialog task = new TaskDialog(title);
        task.MainInstruction = message;
        task.Show();	
    }
}

/// <summary>
/// Seleciona elemento e edita o parametro de Comentário
/// </summary>
public void SelectElementEditParameter()
{
    // Nome do Parâmetro
    var parameterName = "Comments";
    // Texto para colocar no Parâmetro
    var parameterText = "Este é um texto!";
    
    // Document
    var document = ActiveUIDocument.Document;
    // Selection
    var selection = ActiveUIDocument.Selection;

    // Pick Object
    var reference = selection.PickObject(ObjectType.Element);

    // Element
    var elementId = reference.ElementId;
    var element = document.GetElement(elementId);
            
    // Procura parâmetro pelo nome
    var parameter = element.LookupParameter(parameterName);
    
    if (parameter != null)
    {
        // Cria Transaction
        Transaction transaction = new Transaction(document);
        transaction.Start("SelectElementEditParameter");
        
        // Muda valor do parâmetro
        parameter.Set(parameterText);
        
        // Envia todas as modificações
        transaction.Commit();
        
        // Message
        string title = "Revit";
        string message = "";
        message += element.Name;
        message += "\n";
        message += parameter.AsString();
        message += "\n";
        
        // Task Dialog
        TaskDialog task = new TaskDialog(title);
        task.MainInstruction = message;
        task.Show();	
    }
}

#endregion
```

## Licença

<p>Este projeto está licenciado sob <a rel="license" href="https://creativecommons.org/licenses/by-nc-sa/4.0/deed.pt">Atribuição-NãoComercial-CompartilhaIgual 4.0 Internacional</a>.</p>

---

Você gostou deste projeto? Por favor [marque este projeto com estrela no GitHub](https://github.com/ricaun/RevitAPI/stargazers)!

[Video]: https://youtu.be/XSzhnT5PPnU
[VideoIma]: https://img.youtube.com/vi/XSzhnT5PPnU/hqdefault.jpg

[Element]: https://www.revitapidocs.com/2020/eb16114f-69ea-f4de-0d0d-f7388b105a16.htm
[Parameter]: https://www.revitapidocs.com/2020/333ff41b-e6a7-d959-60bf-c3bfae495581.htm
[Transaction]: https://www.revitapidocs.com/2020/308ebf8d-d96d-4643-cd1d-34fffcea53fd.htm
