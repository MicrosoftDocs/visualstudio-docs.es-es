---
title: "No se puede usar la sintaxis de inicializador de objetos para inicializar una instancia de tipo &#39;Object&#39; | Microsoft Docs"
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
  - "bc30994"
  - "vbc30994"
helpviewer_keywords: 
  - "BC30994"
ms.assetid: 2ef65965-f014-4fc1-8c7d-c603f0a764df
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede usar la sintaxis de inicializador de objetos para inicializar una instancia de tipo &#39;Object&#39;
No se puede inicializar una instancia de `Object` mediante la sintaxis de inicializador de objeto. Una instancia de `Object` no tiene propiedades ni campos a los que asignar un valor y la sintaxis de inicializador requiere al menos una propiedad o un campo de este tipo.  
  
```  
' Not valid. ' Dim obj1 = New Object With {} ' Dim obj2 = New Object With {.ToString = <some value>}  
```  
  
 **Identificador de error:** BC30994  
  
### Para corregir este error  
  
1.  Declare instancias de tipo `Object` sin usar una lista de inicializadores:  
  
    ```  
    Dim obj3 as Object Dim obj4 as New Object()  
    ```  
  
## Vea también  
 [Inicializadores de objeto: Tipos con nombre y anónimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Object \(Tipo de datos\)](/dotnet/visual-basic/language-reference/data-types/object-data-type)