# Rotaciona Elementos

Projeto que rotaciona a posição de [Element] utiliando o [ElementTransformUtils].

Utiliza as [Rotinas Utils]
* PickElement
* PickPoint

## Vídeo

[![VideoIma]][Video]

## Código

```C#
#region 05 - Rotaciona Elementos

/// <summary>
/// Seleciona elemento e rotaciona em relação ao ponto
/// </summary>
public void ElementRotate()
{
    // Document
    var document = ActiveUIDocument.Document;
    
    // Pick Element
    var element = PickElement();
    
    // Se Element for valido
    while (element != null)
    {
        // angle
        var angle = 90.0;
        
        // deg to rad
        angle *= Math.PI / 180.0;
        
        // Pega ponto
        var center = PickXYZ();
        
        // Se ponto existir
        if (center != null)
        {
            // axis
            var axis = Line.CreateBound(center, center + XYZ.BasisZ);
            
            // Cria Transaction
            using (Transaction transaction = new Transaction(document)) {
                transaction.Start("ElementRotate");
            
                // Rotate Element
                ElementTransformUtils.RotateElement(document, element.Id, axis, angle);
                
                // Envia todas as modificações
                transaction.Commit();
            }
                                
            // Pick Element
            element = PickElement();
        }
    }
}

/// <summary>
/// Seleciona elementos e rotaciona em relação ao ponto
/// </summary>
public void ElementRotateAll()
{
    // Document
    var document = ActiveUIDocument.Document;
    
    // Pick Element
    var elements = PickElements();
    
    // Se Element for valido
    if (elements != null)
    {
        // angle
        var angle = 90.0;
        
        // deg to rad
        angle *= Math.PI / 180.0;
        
        // Pega ponto
        var center = PickXYZ();
        
        // Se ponto existir
        if (center != null)
        {
            // axis
            var axis = Line.CreateBound(center, center + XYZ.BasisZ);
            
            // Cria Transaction
            using (Transaction transaction = new Transaction(document)) {
                transaction.Start("ElementRotate");
            
                // Rotate Element
                ElementTransformUtils.RotateElements(document, elements.Select(e => e.Id).ToList(), axis, angle);
                
                // Envia todas as modificações
                transaction.Commit();
            }
        }
    }
}

/// <summary>
/// Seleciona elemento e rotaciona com o centro
/// </summary>
public void ElementRotateCenter()
{
    // Document
    var document = ActiveUIDocument.Document;
    
    // Pick Element
    var element = PickElement();
    
    // Se Element for valido
    while (element != null)
    {
        // angle
        var angle = 90.0;
        
        // deg to rad
        angle *= Math.PI / 180.0;
        
        // Pega ponto
        var center = XYZ.Zero;
        
        // Location
        var location = element.Location;
        
        // Location é do tipo ponto
        if (location is LocationPoint)
        {
            var locationPoint = location as LocationPoint;
            center = locationPoint.Point;
        }
        
        // Location é do tipo curva
        else if (location is LocationCurve)
        {
            var locationCurve = location as LocationCurve;
            center = (locationCurve.Curve.GetEndPoint(0) + locationCurve.Curve.GetEndPoint(1)) / 2.0;
        }
        
        // axis
        var axis = Line.CreateBound(center, center + XYZ.BasisZ);
        
        // Cria Transaction
        using (Transaction transaction = new Transaction(document)) {
            transaction.Start("ElementRotate");
        
            // Rotate Element
            ElementTransformUtils.RotateElement(document, element.Id, axis, angle);
            
            // Envia todas as modificações
            transaction.Commit();
        }
        // Pick Element
        element = PickElement();
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

[Rotinas Utils]: code/00-rotinas-utils/

[Element]: https://www.revitapidocs.com/2020/eb16114f-69ea-f4de-0d0d-f7388b105a16.htm
[ElementTransformUtils]: https://www.revitapidocs.com/2020/781ad017-5ee5-f44b-5db2-e8e1f883ae5d.htm
[Transaction]: https://www.revitapidocs.com/2020/308ebf8d-d96d-4643-cd1d-34fffcea53fd.htm
