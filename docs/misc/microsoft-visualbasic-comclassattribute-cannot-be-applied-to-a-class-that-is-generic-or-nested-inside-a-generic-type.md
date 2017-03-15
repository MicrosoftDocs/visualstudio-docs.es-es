---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; no se puede aplicar a una clase gen&#233;rica o contenida dentro de un tipo gen&#233;rico. | Microsoft Docs"
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
  - "vbc31527"
  - "bc31527"
helpviewer_keywords: 
  - "BC31527"
ms.assetid: ea125bff-d020-4933-b277-6e24943eea88
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; no se puede aplicar a una clase gen&#233;rica o contenida dentro de un tipo gen&#233;rico.
Una clase se declara con <xref:Microsoft.VisualBasic.ComClassAttribute>, pero es genérica o está contenida en una clase o estructura genérica.  
  
 Para ser elegible para la interoperabilidad COM, una clase de .NET Framework debe cumplir los requisitos siguientes:  
  
-   Debe ser `Public`, todos sus contenedores deben ser `Public`, y debe exponer al menos un miembro `Public`.  
  
-   No debe ser *abstract*, es decir, no debe declararse con `MustInherit`.  
  
-   No debe ser genérica ni declararse dentro de un tipo de contenedor genérico.  
  
 **Identificador de error:** BC31527  
  
### Para corregir este error  
  
-   Cambie la declaración de la clase para que no sea genérica y asegúrese de que su elemento contenedor no sea genérico.  
  
     O bien  
  
-   Si la clase o su elemento contenedor deben ser genéricos, elimine <xref:Microsoft.VisualBasic.ComClassAttribute> de la declaración de clase. No se puede exponer a COM.  
  
## Vea también  
 <xref:Microsoft.VisualBasic.ComClassAttribute>   
 [Interoperabilidad COM](/dotnet/visual-basic/programming-guide/com-interop/index)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)