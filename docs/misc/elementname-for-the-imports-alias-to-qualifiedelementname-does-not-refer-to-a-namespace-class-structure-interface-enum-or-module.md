---
title: "&#39;&lt;nombreDeElemento&gt;&#39; del alias de Imports para &#39;&lt;nombreDeElementoCompleto&gt;&#39; no hace referencia a Namespace, Class, Structure, Interface, Enum o Module | Microsoft Docs"
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
  - "bc30798"
  - "vbc30798"
helpviewer_keywords: 
  - "BC30798"
ms.assetid: bfa66627-516a-4955-977d-92372bcea090
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nombreDeElemento&gt;&#39; del alias de Imports para &#39;&lt;nombreDeElementoCompleto&gt;&#39; no hace referencia a Namespace, Class, Structure, Interface, Enum o Module
Una [Instrucción Imports \(Tipo y espacio de nombres de .NET\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) especifica un elemento de programación que no se puede importar.  
  
 La instrucción `Imports` se usa para reducir o eliminar la necesidad de una cadena de calificación delante de un nombre de elemento. El elemento se califica en la propia instrucción `Imports` para proporcionar una ruta de acceso inequívoca a una declaración única del elemento. Por tanto, no es necesario calificar las referencias al elemento.  
  
 `Imports` se usa habitualmente para espacios de nombres, pero también puede importar una clase, un módulo, una estructura, una interfaz o una enumeración para permitir la referencia a sus elementos sin una cadena de calificación larga.  
  
 Para más información, vea "Importar elementos contenedores" en [NO ESTÁ EN LA COMPILACIÓN: Resolver una referencia cuando varias variables tienen el mismo nombre](http://msdn.microsoft.com/es-es/9601e39f-1911-44e1-ace5-3f6e090408b9).  
  
 **Identificador de error:** BC30798  
  
### Para corregir este error  
  
1.  Compruebe la ortografía de los elementos de la cadena de calificación en la instrucción `Imports`, especialmente del último elemento de la cadena, que es el elemento está calificando.  
  
2.  Compruebe que el elemento que está calificando es de un tipo válido \(espacio de nombres, clase, módulo, estructura, interfaz o enumeración\). De lo contrario, quite la instrucción `Imports`.  
  
## Vea también  
 [Referencias y la instrucción Imports](/dotnet/visual-basic/programming-guide/program-structure/references-and-the-imports-statement)