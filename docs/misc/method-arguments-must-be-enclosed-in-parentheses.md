---
title: "Los argumentos de m&#233;todo se deben incluir entre par&#233;ntesis | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30800"
  - "bc30800"
helpviewer_keywords: 
  - "BC30800"
ms.assetid: ecdec760-8b51-474f-acad-17cf8059d83b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los argumentos de m&#233;todo se deben incluir entre par&#233;ntesis
Las reglas que rigen las llamadas a procedimiento son más sencillas en las versiones más recientes de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Todos los argumentos se deben incluir entre paréntesis.  
  
 **Identificador de error:** BC30800  
  
### Para corregir este error  
  
-   Incluya la lista de argumentos entre paréntesis; por ejemplo:  
  
    ```  
    MySub(ArrayIndex, NewValue)  
    ```  
  
## Vea también  
 [Procedure Calling Sequence Changes in Visual Basic](http://msdn.microsoft.com/es-es/4ef1eea6-36cb-4b97-a31b-9ba65e46a9fd)   
 [Argumentos y parámetros de procedimiento](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments)