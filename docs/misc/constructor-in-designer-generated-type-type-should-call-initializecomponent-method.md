---
title: "El &#39;&lt;constructor&gt;&#39; del tipo &#39;&lt;tipo&gt;&#39; generado por el dise&#241;ador debe llamar al m&#233;todo InitializeComponent | Microsoft Docs"
ms.custom: ""
ms.date: "10/25/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40054"
  - "bc40054"
helpviewer_keywords: 
  - "BC40054"
ms.assetid: beac93b0-d427-4df6-9582-fd69c7a53673
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El &#39;&lt;constructor&gt;&#39; del tipo &#39;&lt;tipo&gt;&#39; generado por el dise&#241;ador debe llamar al m&#233;todo InitializeComponent
Un constructor en un tipo generado por el diseñador no llama al método `InitializeComponent` del tipo.  
  
 Cada constructor en un tipo generado por el diseñador debe llamar al método `InitializeComponent` del tipo.  
  
 **Identificador de error:** BC40054  
  
### Para corregir este error  
  
-   Agregue una llamada al método `InitializeComponent` en el constructor.  
  
## Vea también  
 <xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute>   
 [NO ESTÁ EN LA COMPILACIÓN: Usar constructores y destructores](http://msdn.microsoft.com/es-es/548eebe1-86c4-4377-b2f5-447cb8be3d90)