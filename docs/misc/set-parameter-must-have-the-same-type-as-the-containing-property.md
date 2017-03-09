---
title: "El par&#225;metro &#39;Set&#39; debe tener el mismo tipo que la propiedad que lo contiene | Microsoft Docs"
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
  - "vbc31064"
  - "bc31064"
helpviewer_keywords: 
  - "BC31064"
ms.assetid: f0b8310d-68a1-4989-ac64-03b1861528ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El par&#225;metro &#39;Set&#39; debe tener el mismo tipo que la propiedad que lo contiene
El parámetro del procedimiento de propiedad `Set` tiene un tipo diferente al de la propiedad a la que pertenece.  
  
 **Identificador de error:** BC31064  
  
### Para corregir este error  
  
-   Cambie el tipo de datos del parámetro a `Set` para que coincida con el tipo de datos de la propiedad. Por ejemplo:  
  
    ```  
    Class Class1 ' Declare a local variable to hold the property value. Private Fval As Integer Property F() As Integer Get Return Fval End Get Set(ByVal Value As Integer) Fval = Value End Set End Property End Class  
    ```  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Cómo: Agregar campos y propiedades a una clase](http://msdn.microsoft.com/es-es/ae53f61b-3abc-413e-8931-703c5f5e8fc2)   
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [NO ESTÁ EN LA COMPILACIÓN: Propiedades y procedimientos de propiedad](http://msdn.microsoft.com/es-es/23e2a1ec-7e9d-4109-8940-c703d981077b)