# Meu primeiro Macro

Projeto que cria um [TaskDialog] que mostra uma mensagem simples utilizando o Macro do Revit.

## Vídeo

[![VideoIma]][Video]

## Código

```C#
#region 01 - Meu primeiro Macro

/// <summary>
/// Mostra caixa de dialogo com texto simples
/// </summary>
public void ShowMessage()
{
    TaskDialog.Show("Hello Revit!", "Meu primeiro macro!");
}

/// <summary>
/// Mostra caixa de dialogo com texto de multipla linhas
/// </summary>
public void ShowMessage2()
{
    string title = "Hello Revit!";
    string message = "Meu primeiro macro!";
    message += "\n";
    message += "Segunda linha!";
    message += "\n";
    message += "Terceira linha!";
    TaskDialog task = new TaskDialog(title);
    task.MainInstruction = message;
    task.Show();
}

/// <summary>
/// Mostra caixa de dialogo complexa com multipla opções
/// </summary>
public void ShowMessage3()
{
    string title = "Hello Revit!";
    string message = "Meu primeiro macro!";
    string content = "As opções abaixo abre outra mensagem.";
    string footer = "<a href=\"https://github.com/ricaun/RevitAPI\">Github</a>";
    
    // Define TaskDialog
    TaskDialog taskDialog = new TaskDialog(title);
    taskDialog.MainInstruction = message;
    taskDialog.MainContent = content;
    taskDialog.FooterText = footer;

    // Configuração dos botões
    taskDialog.AddCommandLink(TaskDialogCommandLinkId.CommandLink1, "Opção 1");
    taskDialog.AddCommandLink(TaskDialogCommandLinkId.CommandLink2, "Opção 2");
    taskDialog.CommonButtons = TaskDialogCommonButtons.Close;
    taskDialog.DefaultButton = TaskDialogResult.Close;
    
    // Espera TaskDialogResult
    TaskDialogResult result = taskDialog.Show();
    
    // Se opção 1
    if (result == TaskDialogResult.CommandLink1)
    {
        TaskDialog.Show("Hello Revit!", "Opção 1!");
    }
    
    // Se opção 2
    if (result == TaskDialogResult.CommandLink2)
    {
        TaskDialog.Show("Hello Revit!", "Opção 2!");
    }

    // Se Close
    if (result == TaskDialogResult.Close)
    {
        TaskDialog.Show("Hello Revit!","Close!");
    }
			
    // Se Cancel
    if (result == TaskDialogResult.Cancel)
    {
        TaskDialog.Show("Hello Revit!","Cancel!");
    }
}

#endregion
```

## Licença

<p>Este projeto está licenciado sob <a rel="license" href="https://creativecommons.org/licenses/by-nc-sa/4.0/deed.pt">Atribuição-NãoComercial-CompartilhaIgual 4.0 Internacional</a>.</p>

---

Você gostou deste projeto? Por favor [marque este projeto com estrela no GitHub](https://github.com/ricaun/RevitAPI/stargazers)!

[Video]: https://youtu.be/o4T34RXnZAU
[VideoIma]: https://img.youtube.com/vi/o4T34RXnZAU/hqdefault.jpg

[Video2]: https://youtu.be/XSzhnT5PPnU
[VideoIma2]: https://img.youtube.com/vi/XSzhnT5PPnU/hqdefault.jpg

[TaskDialog]: https://www.revitapidocs.com/2020/853afb57-7455-a636-9881-61a391118c16.htm