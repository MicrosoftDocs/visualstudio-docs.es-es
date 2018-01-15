---
title: "BoundsRules restringir la ubicación de la forma y el tamaño | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7600f71cc7203b48a6a20da98f59846a0b62bc13
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>Ubicación y tamaño de las reglas de restricción de formas BoundsRules
A *regla límites* es una clase que define los límites en el tamaño y la ubicación de una forma. Proporciona un método que se llama repetidamente mientras un usuario está arrastrando una forma o los extremos o lados de una forma.  
  
 En el ejemplo siguiente, se restringe una forma rectangular como una barra de tamaño fijo, horizontal o vertical. Cuando el usuario arrastra los extremos o lados, voltea el esquema entre las dos configuraciones permitidas de alto y ancho.  
  
 Los límites de reglas es una clase derivada de <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. Se crea una instancia de la regla en la forma:  
  
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
  
 Tenga en cuenta que la ubicación y el tamaño pueden restringirse si desea.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [Responder a los cambios y propagarlos](../modeling/responding-to-and-propagating-changes.md)