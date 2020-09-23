# Meu primeiro Macro

Projeto que cria um [TaskDialog] que mostra uma mensagem simples utilizando o Macro do Revit.

## Vídeo

[<img src="https://img.youtube.com/vi/qY4bDOyZozQ/hqdefault.jpg" width="50%">](https://youtu.be/qY4bDOyZozQ)

## Código

```C#
public void ShowMessageSimple()
{
    TaskDialog("Hello, Revit!");
}
```

```C#
public void ShowMessageNewLine()
{
    string message = "";
    message += "Revit!";
    message += Environment.NewLine;
    message += "Revit!";
    message += Environment.NewLine;
    message += "Revit!";
    message += Environment.NewLine;
    TaskDialog("Hello", message);
}
```

## Licença

<p>Este projeto está licenciado sob <a rel="license" href="https://creativecommons.org/licenses/by-nc-sa/4.0/deed.pt">Atribuição-NãoComercial-CompartilhaIgual 4.0 Internacionale</a>.</p>

[TaskDialog]: https://www.revitapidocs.com/2020/853afb57-7455-a636-9881-61a391118c16.htm
