---
title: "Ya no se admite el evento &#39;Class_Terminate&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42002"
  - "bc42002"
helpviewer_keywords: 
  - "BC42002"
ms.assetid: 11eeac74-666d-4b23-81bc-b1691290ddd0
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ya no se admite el evento &#39;Class_Terminate&#39;
Ya no se admite el evento 'Class\_Terminate'. Use 'Sub Finalize' para liberar recursos.  
  
 El evento `Class_Terminate` de versiones anteriores de Visual Basic se ha reemplazado por destructores de clase.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC42002  
  
### Para corregir este error  
  
-   Declare un procedimiento `Sub` denominado `Finalize` para terminar una clase.`Sub Finalize` se llama cuando el recolector de elementos no utilizados detecta que no hay más referencias activas a la instancia.  
  
## Vea también  
 [Classes for Visual Basic 6.0 Users](http://msdn.microsoft.com/es-es/d625222c-cd32-4c8d-b25c-ea71729b88b7)   
 [NO ESTÁ EN LA COMPILACIÓN: Usar constructores y destructores](http://msdn.microsoft.com/es-es/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [NO ESTÁ EN LA COMPILACIÓN: Cómo: Implementar el patrón Dispose Finalize \(Visual Basic\)](http://msdn.microsoft.com/es-es/adf7a232-4ebb-485d-8626-8d64421eb0c4)