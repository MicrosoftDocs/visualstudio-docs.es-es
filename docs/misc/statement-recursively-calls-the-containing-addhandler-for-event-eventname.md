---
title: "La instrucci&#243;n llama recursivamente al elemento contenedor &#39;AddHandler&#39; para el evento &#39;&lt;nombreEvento&gt;&#39;. | Microsoft Docs"
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
  - "bc41998"
  - "vbc41998"
helpviewer_keywords: 
  - "BC41998"
ms.assetid: 4375b191-fbd9-4e93-b9bb-9159d533ddf6
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La instrucci&#243;n llama recursivamente al elemento contenedor &#39;AddHandler&#39; para el evento &#39;&lt;nombreEvento&gt;&#39;.
Las instrucciones del descriptor de acceso `AddHandler` de una definición de evento no debe hacer referencia al evento directamente.  
  
 El enfoque recomendado es almacenar la lista de los controladores del evento como un campo privado en la clase, estructura o módulo que definió el evento. Para obtener más información, vea [Cómo: Declarar eventos personalizados para evitar bloqueos](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Avoid%20Blocking%20\(Visual%20Basic\).md) y [Cómo: Declarar eventos personalizados para conservar memoria](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md).  
  
 **Identificador de error:** BC41998  
  
### Para corregir este error  
  
-   Vuelva a escribir la definición de evento para evitar la recursividad.  
  
## Vea también  
 [AddHandler: eliminar](http://msdn.microsoft.com/es-es/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [Cómo: Declarar eventos personalizados para evitar bloqueos](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Avoid%20Blocking%20\(Visual%20Basic\).md)   
 [Cómo: Declarar eventos personalizados para conservar memoria](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md)