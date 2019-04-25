---
title: Ubicación de la forma y tamaño Boundsrules | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d09be82be084767bfb2d300a1877e95456a957b4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996283"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>Ubicación y tamaño de las reglas de restricción de formas BoundsRules
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un *regla de límites* es una clase que define los límites en el tamaño y la ubicación de una forma. Proporciona un método que se llama repetidamente mientras un usuario está arrastrando una forma o los extremos o lados de una forma.  
  
 En el ejemplo siguiente se restringe a una forma rectangular sea una barra de tamaño fijo, ya sea horizontal o vertical. Cuando el usuario arrastra los extremos o lados, el esquema se voltea entre las dos configuraciones permitidas de alto y ancho.  
  
 Los límites de regla es una clase derivada de <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. En la forma se crea una instancia de la regla:  
  
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
  
 Tenga en cuenta que se pueden restringir la ubicación y el tamaño si desea.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [Responder a los cambios y propagarlos](../modeling/responding-to-and-propagating-changes.md)
