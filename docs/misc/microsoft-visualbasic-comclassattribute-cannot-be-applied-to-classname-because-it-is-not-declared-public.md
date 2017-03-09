---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; no se puede aplicar a &#39;&lt;classname&gt;&#39; porque no est&#225; declarado como &#39;Public&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32509"
  - "vbc32509"
helpviewer_keywords: 
  - "BC32509"
ms.assetid: ac46851f-53ab-4ce6-87b1-4c4d29508527
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; no se puede aplicar a &#39;&lt;classname&gt;&#39; porque no est&#225; declarado como &#39;Public&#39;.
Una clase se declara con <xref:Microsoft.VisualBasic.ComClassAttribute>, pero su declaración no especifica `Public`.  
  
 Para ser elegible para la interoperabilidad COM, una clase de .NET Framework debe cumplir los requisitos siguientes:  
  
-   Debe ser `Public`, todos sus contenedores deben ser `Public`, y debe exponer al menos un miembro `Public`.  
  
-   No debe ser *abstracta*, es decir, debe no declararse con `MustInherit`.  
  
-   No debe ser genérica ni declararse dentro de un tipo de contenedor genérico.  
  
 **Identificador de error:** BC32509  
  
### Para corregir este error  
  
-   Agregue la palabra clave `Public` a la declaración de clase.  
  
     O bien  
  
-   Si la clase o su elemento contenedor no pueden ser `Public`, quite <xref:Microsoft.VisualBasic.ComClassAttribute> de la declaración de clase. No se puede exponer a COM.  
  
## Vea también  
 <xref:Microsoft.VisualBasic.ComClassAttribute>   
 [Interoperabilidad COM](/dotnet/visual-basic/programming-guide/com-interop/index)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)