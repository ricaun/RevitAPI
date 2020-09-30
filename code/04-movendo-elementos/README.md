# Movendo Elementos

Projeto que move a posição de [Element] utiliando o [ElementTransformUtils].

Utiliza as [Rotinas Utils]
* PickElement
* PickElements
* PickXYZ

## Vídeo

[![VideoIma]][Video]

## Código

```C#
#region 04 - Move Elementos 

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
        // Valor para mover
        var move = new XYZ(1.0,0.0,0.0);
        
        // Pés para metros
        move = move.Divide(0.3048);

        // Cria Transaction
        using (Transaction transaction = new Transaction(document)) 
        {
            transaction.Start("ElementMove");
            
            // Move Element
            ElementTransformUtils.MoveElement(document, element.Id, move);
            
            // Envia todas as modificações
            transaction.Commit();
        }
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
    while (element != null) 
    {
        // Valor para mover
        var move = new XYZ(1.0,0.0,0.0);
        
        // Pés para metros
        move = move.Divide(0.3048);
        
        // Cria Transaction
        using (Transaction transaction = new Transaction(document)) 
        {
            transaction.Start("ElementMove");
            
            // Move Element
            ElementTransformUtils.MoveElement(document, element.Id, move);
            
            // Envia todas as modificações
            transaction.Commit();
        }
        
        // Pick outro Element
        element = PickElement();
    }
}

/// <summary>
/// Seleciona elemento e move utilizando ponto
/// </summary>
public void ElementMovePoint()
{
    // Document
    var document = ActiveUIDocument.Document;
    
    // Pick Element
    var element = PickElement();
    
    // Se Element for valido
    if (element != null)
    {
        // Pega primeiro ponto
        var point1 = PickXYZ();
        if (point1 == null) return;
        
        // Pega segundo ponto
        var point2 = PickXYZ();
        if (point2 == null) return;
        
        // Valor para mover
        var move = point2 - point1;
        
        // Cria Transaction
        using (Transaction transaction = new Transaction(document)) 
        {
            transaction.Start("ElementMove");
        
            // Move Element
            ElementTransformUtils.MoveElement(document, element.Id, move);
            
            // Envia todas as modificações
            transaction.Commit();
        }
    }
}

/// <summary>
/// Seleciona elementos e move todos com o mouse
/// </summary>
public void ElementMoveAll()
{
    // Document
    var document = ActiveUIDocument.Document;
    
    // Pick Elements
    var elements = PickElements();

    // Se Element for valido
    if (elements != null) 
    {
        // Pega primeiro ponto
        var point1 = PickXYZ();
        if (point1 == null) return;
        
        // Pega segundo ponto
        var point2 = PickXYZ();
        if (point2 == null) return;
        
        // Valor para mover
        var move = point2 - point1;
        
        // Cria Transaction
        using (Transaction transaction = new Transaction(document)) {
            transaction.Start("ElementMove");

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

[Video]: https://youtu.be/Apl5c4Rl8WY
[VideoIma]: https://img.youtube.com/vi/Apl5c4Rl8WY/hqdefault.jpg

[Rotinas Utils]: code/00-rotinas-utils/

[Element]: https://www.revitapidocs.com/2020/eb16114f-69ea-f4de-0d0d-f7388b105a16.htm
[ElementTransformUtils]: https://www.revitapidocs.com/2020/781ad017-5ee5-f44b-5db2-e8e1f883ae5d.htm
[Transaction]: https://www.revitapidocs.com/2020/308ebf8d-d96d-4643-cd1d-34fffcea53fd.htm
