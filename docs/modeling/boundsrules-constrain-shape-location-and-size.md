---
title: Ubicación y tamaño de las reglas de restricción de formas BoundsRules
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 104a74a38099286675a742ce9eea367d9eeabe84
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31944393"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>Ubicación y tamaño de las reglas de restricción de formas BoundsRules

A *regla límites* es una clase que define los límites en el tamaño y la ubicación de una forma. Proporciona un método que se llama repetidamente mientras un usuario está arrastrando una forma o los extremos o lados de una forma.

En el ejemplo siguiente, se restringe una forma rectangular como una barra de tamaño fijo, horizontal o vertical. Cuando el usuario arrastra los extremos o lados, voltea el esquema entre las dos configuraciones permitidas de alto y ancho.

Los límites de reglas es una clase derivada de <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. Se crea una instancia de la regla en la forma:

```csharp
using Microsoft.VisualStudio.Modeling.Diagrams; ...

public partial class BarShape
{
  /// <summary>
  /// Rule invoked when the user is resizing a shape.
  /// </summary>
  public override BoundsRules BoundsRules
  { get { return new BarBoundsRule(); } }
}

/// <summary>
/// Rule invoked when the user is changing a shape's outline.
/// Provides real-time mouse rubber-band feedback, so must work fast.
/// </summary>
public class BarBoundsRule: BoundsRules
{
  public override RectangleD GetCompliantBounds
     (ShapeElement shape, RectangleD proposedBounds)
  {
    double thickness = 0.1;
    if (proposedBounds.Height > proposedBounds.Width)
    {
      // There is a minimum width for a shape; the width
      // will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
            new SizeD(thickness, proposedBounds.Height));
    }
    else
    {
      // There is a minimum height for a shape; the
      // height will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
         new SizeD(proposedBounds.Width, thickness));
} } }
```

Tenga en cuenta que la ubicación y el tamaño pueden restringirse si desea.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>
- [Respuesta a cambios y propagación](../modeling/responding-to-and-propagating-changes.md)