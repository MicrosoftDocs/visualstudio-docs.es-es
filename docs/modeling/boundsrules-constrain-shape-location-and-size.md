---
title: "Ubicaci&#243;n y tama&#241;o de las reglas de restricci&#243;n de formas BoundsRules | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lenguaje específico de dominio, eventos"
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 18
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 18
---
# Ubicaci&#243;n y tama&#241;o de las reglas de restricci&#243;n de formas BoundsRules
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Una regla de Límites* es una clase que define los límites en el tamaño y la ubicación de una forma.  Proporciona un método que se llama repetidamente mientras un usuario está arrastrando una forma o las esquinas o los lados de una forma.  
  
 El ejemplo siguiente restringe una forma rectangular para ser una barra de tamaño fijo, u horizontal o vertical.  Cuando el usuario arrastra las esquinas o lateral, el esquema mueve volteado entre las dos configuraciones permitidas de alto y ancho.  
  
 la regla de los límites es una clase derivada de <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>.  una instancia de la regla se crea en la forma:  
  
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
  
 Observe que la ubicación y el tamaño pueden ser restringidos si desea.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [Responder a los cambios y propagarlos](../modeling/responding-to-and-propagating-changes.md)