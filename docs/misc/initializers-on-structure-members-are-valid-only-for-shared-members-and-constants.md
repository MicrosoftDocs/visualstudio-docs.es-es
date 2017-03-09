---
title: "Los inicializadores en miembros de estructura solo son v&#225;lidos para las constantes y los miembros &#39;Shared&#39; | Microsoft Docs"
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
  - "bc31049"
  - "vbc31049"
helpviewer_keywords: 
  - "BC31049"
ms.assetid: 8356978e-7f84-4932-be0f-dda005c9f8ca
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los inicializadores en miembros de estructura solo son v&#225;lidos para las constantes y los miembros &#39;Shared&#39;
Se inicializó una variable de miembro de estructura como parte de su declaración.  
  
 **Identificador de error:** BC31049  
  
### Para corregir este error  
  
-   Use una constante en lugar de una variable.  
  
-   Agregue un constructor con parámetros a la estructura. Por ejemplo:  
  
    ```  
    Structure TestStruct Public t As Integer Sub New(ByVal Tval As Integer) t = Tval End Sub End Structure  
    ```  
  
## Vea también  
 [Cómo: Declarar una estructura](../Topic/How%20to:%20Declare%20a%20Structure%20\(Visual%20Basic\).md)   
 [Constantes y enumeraciones](/dotnet/visual-basic/programming-guide/language-features/constants-enums/index)