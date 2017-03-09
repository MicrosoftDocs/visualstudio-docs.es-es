---
title: "Se esperaba un identificador precedido por un punto | Microsoft Docs"
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
  - "bc36576"
  - "vbc36576"
helpviewer_keywords: 
  - "BC36576"
ms.assetid: 02217cc4-8972-4a6d-97a6-4ecbb7399af2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se esperaba un identificador precedido por un punto
Se ha incluido un valor del que no se puede inferir un nombre de propiedad en la lista de inicializadores de una declaración de tipo anónimo sin que se asigne a un nombre de propiedad.  
  
```  
' Not valid. ' Dim anon1 = New With {.grade = 100, 95}  
```  
  
 **Identificador de error:** BC36576  
  
### Para corregir este error  
  
-   Proporcione un nombre de propiedad para cada valor de la lista de inicializadores, como se muestra en el código siguiente:  
  
    ```  
    Dim anon2 = New With {.grade1 = 100, .grade2 = 95}  
    ```  
  
## Vea también  
 [Inicializadores de objeto: Tipos con nombre y anónimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Cómo: declarar una instancia de un tipo anónimo \(Visual Basic\)](http://msdn.microsoft.com/es-es/119f616c-9bcd-4731-ac00-4285be5959f7)   
 [Cómo: Deducir tipos y nombres de propiedades en declaraciones de tipos anónimos](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)