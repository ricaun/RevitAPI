# Seleciona Parede com Filtro

Projeto que seleciona todos os [Element] da mesma categoria [Wall] utilizando o [FilteredElementCollector].

## Vídeo

[![VideoIma]][Video]

## Código

```C#
#region 07 - Seleciona Parede com Filtro

/// <summary>
/// Seleciona todas os elementos Wall
/// </summary>
public void SelectWall()
{
    // Document
    Document document = ActiveUIDocument.Document;
    
    // FilteredElementCollector Wall
    var filteredElementCollector = new FilteredElementCollector(document)
        .OfClass(typeof(Wall))
        .Cast<Wall>();
    
    // To List
    var walls = filteredElementCollector
        .ToList();
    
    // Message
    string title = "Revit";
    string message = "";
    
    // ForEach
    foreach (var wall in walls) {
        message += wall.Name;
        message += "\n";
    }
    
    // Task Dialog
    TaskDialog task = new TaskDialog(title);
    task.MainInstruction = message;
    task.Show();
}

/// <summary>
/// Seleciona todas os elementos Wall na vista ativa
/// </summary>
public void SelectWallView()
{
    // Document
    Document document = ActiveUIDocument.Document;
    
    // View
    View view = document.ActiveView;

    // FilteredElementCollector Wall
    var filteredElementCollector = new FilteredElementCollector(document, view.Id)
        .OfClass(typeof(Wall))
        .Cast<Wall>();
    
    // To List
    var walls = filteredElementCollector
        .ToList();
    
    // Message
    string title = "Revit";
    string message = "";
    
    // ForEach
    foreach (var wall in walls) {
        message += wall.Name;
        message += "\n";
    }
    
    // Task Dialog
    TaskDialog task = new TaskDialog(title);
    task.MainInstruction = message;
    task.Show();
}

/// <summary>
/// Seleciona todas os elementos Wall que contain no nome 300
/// </summary>
public void SelectWall300()
{
    // Document
    Document document = ActiveUIDocument.Document;
    
    // FilteredElementCollector Wall
    var filteredElementCollector = new FilteredElementCollector(document)
        .OfClass(typeof(Wall))
        .Cast<Wall>();
    
    // To List
    var walls = filteredElementCollector
        .Where(w => w.Name.Contains("300"))
        .ToList();
    
    // Message
    string title = "Revit";
    string message = "";
    
    // ForEach
    foreach (var wall in walls) {
        message += wall.Name;
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

[Video]: https://youtu.be/CuVFPAAlqpw
[VideoIma]: https://img.youtube.com/vi/CuVFPAAlqpw/hqdefault.jpg

[Rotinas Utils]: code/00-rotinas-utils/

[Element]: https://www.revitapidocs.com/2020/eb16114f-69ea-f4de-0d0d-f7388b105a16.htm
[Wall]: https://www.revitapidocs.com/2020/b5891733-c602-12df-beab-da414b58d608.htm
[FilteredElementCollector]: https://www.revitapidocs.com/2020/263cf06b-98be-6f91-c4da-fb47d01688f3.htm
