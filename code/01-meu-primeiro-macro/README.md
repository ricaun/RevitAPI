# Meu primeiro Macro

Projeto que cria um [TaskDialog] que mostra uma mensagem simples utilizando o Macro do Revit.

## Vídeo

[<img src="https://img.youtube.com/vi/qY4bDOyZozQ/hqdefault.jpg" width="50%">](https://youtu.be/qY4bDOyZozQ)

## Código

```C#
public void ShowMessage()
{
    TaskDialog.Show("Hello Revit!", "Meu primeiro macro!");
}
```

```C#
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
```

```C#
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
}
```

## Licença

<p>Este projeto está licenciado sob <a rel="license" href="https://creativecommons.org/licenses/by-nc-sa/4.0/deed.pt">Atribuição-NãoComercial-CompartilhaIgual 4.0 Internacional</a>.</p>

---

Você gostou deste projeto? Por favor [marque este projeto com estrela no GitHub](https://github.com/ricaun/RevitAPI/stargazers)!

[TaskDialog]: https://www.revitapidocs.com/2020/853afb57-7455-a636-9881-61a391118c16.htm
