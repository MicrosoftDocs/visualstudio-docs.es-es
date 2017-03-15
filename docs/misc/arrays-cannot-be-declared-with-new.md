---
title: "Las matrices no se pueden declarar con &#39;New&#39;. | Microsoft Docs"
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
  - "vbc30053"
  - "bc30053"
helpviewer_keywords: 
  - "BC30053"
ms.assetid: aa55f3b7-2045-497b-9543-5ec6e2b74fe2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las matrices no se pueden declarar con &#39;New&#39;.
La palabra clave `New` solo puede aparecer en la parte de la inicialización de una declaración de matriz. Esto significa que `New` debe estar en el lado derecho del signo igual \(`=`\) para que pueda crear un nuevo tipo de matriz, que se asignará a la variable de matriz.  
  
 El acceso directo para la inicialización de clase no está disponible para las matrices. Las siguientes dos líneas de código son ambas válidas y equivalentes, porque inicializan un objeto desde una clase.  
  
```  
Dim formA as Form = New Form Dim formA as New Form  
```  
  
 Sin embargo, la inicialización de matriz no puede usar el mismo método abreviado como la inicialización de la clase.  
  
 Tenga en cuenta que la cláusula `New` para una matriz debe contener ambos paréntesis, `()`, y las llaves, `{}`. Los paréntesis especifican que el nuevo tipo es una matriz, y las llaves proporcionan los valores de inicialización. El compilador requiere las llaves aunque estén vacías, es decir, aunque no esté inicializando ninguno de los valores de matriz.  
  
 **Identificador de error:** BC30053  
  
### Para corregir este error  
  
-   Reemplace una instrucción como `Dim myDates() As New Date` por una instrucción como `Dim myDates() As Date = New Date() {}`.  
  
## Vea también  
 [Matrices](/dotnet/visual-basic/programming-guide/language-features/arrays/index)   
 [Cómo: Inicializar una variable de matriz en Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)