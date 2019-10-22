---
title: Formas boundsrules restringir la ubicación y el tamaño de la forma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d660189ede0848216eb44d6ef49fe9c93a06ec8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672727"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>Ubicación y tamaño de las reglas de restricción de formas BoundsRules
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una *regla de límites* es una clase que define los límites en el tamaño y la ubicación de una forma. Proporciona un método al que se llama repetidamente mientras un usuario arrastra una forma o las esquinas o lados de una forma.

 En el ejemplo siguiente se restringe una forma rectangular para que sea una barra de tamaño fijo, ya sea horizontal o vertical. Cuando el usuario arrastra las esquinas o los lados, el contorno se voltea entre las dos configuraciones permitidas de alto y ancho.

 La regla de límites es una clase derivada de <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. Se crea una instancia de la regla en la forma:

```
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

 Tenga en cuenta que la ubicación y el tamaño se pueden restringir si lo desea.

## <a name="see-also"></a>Vea también
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules> [responder a los cambios y propagarlos](../modeling/responding-to-and-propagating-changes.md)
