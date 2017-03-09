---
title: "El argumento de tipo &#39;&lt;nombreDeArgumentoDeTipo&gt;&#39; se declar&#243; como &#39;MustInherit&#39; y no respeta la restricci&#243;n &#39;New&#39; para el par&#225;metro de tipo &#39;&lt;nombreDeTipoDePar&#225;metro&gt;&#39; | Microsoft Docs"
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
  - "vbc32082"
  - "BC32082"
helpviewer_keywords: 
  - "BC32082"
ms.assetid: 597e5944-a61b-4858-ada5-efb80b27f26b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El argumento de tipo &#39;&lt;nombreDeArgumentoDeTipo&gt;&#39; se declar&#243; como &#39;MustInherit&#39; y no respeta la restricci&#243;n &#39;New&#39; para el par&#225;metro de tipo &#39;&lt;nombreDeTipoDePar&#225;metro&gt;&#39;
Se invoca un tipo genérico con una clase `MustInherit` como argumento de tipo, pero el parámetro de tipo correspondiente está declarado con la restricción `New`.  
  
 La restricción `New` establece que el tipo que se pasa en el argumento de tipo correspondiente debe admitir la creación de objetos. Sin embargo, una clase *abstract*, es decir, una clase declarada como `MustInherit`, no expone ningún constructor porque no es posible crear objetos a partir de ella.  
  
 **Identificador de error:** BC32082  
  
### Para corregir este error  
  
1.  Si la clase usada en el argumento de tipo debe ser abstracta, quite la palabra clave `MustInherit` de su declaración.  
  
2.  Si la clase usada en el argumento de tipo debe ser abstracta, pero no se necesita para construir el tipo genérico, pase una clase diferente en el argumento de tipo.  
  
3.  Si el parámetro de tipo correspondiente no necesita crear objetos a partir del tipo que se le pasa, quite la restricción `New` de su declaración.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [New \(Operador\)](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)