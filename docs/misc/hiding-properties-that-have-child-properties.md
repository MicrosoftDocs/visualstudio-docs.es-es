---
title: "Ocultar propiedades que tienen propiedades secundarias | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "propiedades [SDK de Visual Studio], ocultar"
  - "ventana Propiedades, ocultar propiedades que tienen propiedades secundarias"
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# Ocultar propiedades que tienen propiedades secundarias
Desearía ocultar las propiedades que tienen propiedades secundarias:  
  
-   Si ha anidado los proyectos en el proyecto principal mediante programación controles algunos aspectos del proyecto secundario.  
  
-   Si utiliza un control con un diseñador especializado y no desea ofrecer a los desarrolladores acceso completo a todas las propiedades del control.  
  
-   Si tiene la propiedad del ámbito de un objeto y desea restringir la vista de propiedades.  
  
### para ocultar las propiedades que tienen propiedades secundarias  
  
1.  establezca el parámetro de `pfDisplay` en <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> a `FALSE`.  
  
2.  establezca el parámetro de `pfHide` en <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> a `TRUE`.  
  
## Vea también  
 [Mostrar cuadrícula de propiedades](../extensibility/internals/properties-display-grid.md)