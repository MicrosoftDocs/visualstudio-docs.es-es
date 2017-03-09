---
title: "&#39;Global&#39; no se permite en este contexto; se esperaba un identificador | Microsoft Docs"
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
  - "vbc36001"
  - "bc36001"
helpviewer_keywords: 
  - "BC36001"
ms.assetid: d515daa2-f53d-424c-81fd-e9c4b12f331b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Global&#39; no se permite en este contexto; se esperaba un identificador
La palabra clave `Global` se usa en una instrucción donde no está permitida.  
  
 La palabra clave `Global` permite obtener acceso a un espacio de nombres definido fuera de la jerarquía del espacio de nombres en la que se va a compilar el código.`Global` inicia la ruta de acceso de calificación en el nivel más externo del espacio de nombres de la biblioteca de clases de .NET Framework. Para obtener un ejemplo, vea [Global \- delete](http://msdn.microsoft.com/es-es/18c8ba14-40f6-4978-8096-6a5852324635).  
  
 Ciertas instrucciones, como `Imports` y `Namespace`, son independientes del espacio de nombres en el que se va a compilar el código. Requieren una ruta de acceso completa a partir del espacio de nombres de nivel de raíz como, por ejemplo, <xref:System> o <xref:Microsoft.VisualBasic>. En tales instrucciones, la palabra clave `Global` es superflua y no está permitida.  
  
 **Identificador de error:** BC36001  
  
### Para corregir este error  
  
-   Quite la palabra clave `Global` de la instrucción. No es necesaria.  
  
## Vea también  
 [Global \- delete](http://msdn.microsoft.com/es-es/18c8ba14-40f6-4978-8096-6a5852324635)   
 [Instrucción Imports \(Tipo y espacio de nombres de .NET\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type)   
 [Namespace \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/namespace-statement)   
 [Referencias y la instrucción Imports](/dotnet/visual-basic/programming-guide/program-structure/references-and-the-imports-statement)