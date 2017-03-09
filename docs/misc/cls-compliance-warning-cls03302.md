---
title: "Advertencia de conformidad con CLS CLS03302 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS03302"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03302"
ms.assetid: 3b99e64b-d5cb-4eb8-81b5-fd96992f2c10
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS03302
Los eventos deben adherirse a un patrón de asignación de nombres concreto  
  
 Los eventos deben adherirse a un modelo de nomenclatura específico; el nombre de las funciones de descriptor de acceso del evento será el mismo que el nombre del evento, con **raise\_**, **remove\_** o **add\_**.  
  
 En las comparaciones de nombres correspondientes, se omitirá el atributo **specialname** y se seguirán las reglas del identificador.  
  
 Para más información sobre la comprobación de conformidad con CLS, vea [Ensamblados compatibles con CLS](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 La siguiente declaración de función \(mediante el lenguaje ensamblador MSIL\) muestra lo que podría provocar CLS03302:  
  
```  
.method public specialname instance void add_MyEventaaa(class MyAssemblyDelegate __unnamed000) cil managed { } // end of method One::add_MyEvent .method public specialname instance void remove_MyEventaaa(class MyAssemblyDelegate __unnamed000) cil managed { } // end of method One::remove_MyEvent .method public specialname instance void raise_MyEventaaa(object __unnamed000, class [mscorlib]System.EventArgs __unnamed001) cil managed { } // end of method One::raise_MyEvent .event specialname MyAssemblyDelegate MyEvent { .addon instance void One::add_MyEventaaa(class MyAssemblyDelegate) .removeon instance void remove_MyEventaaa(class MyAssemblyDelegate) .fire instance void raise_MyEventaaa(object, class [mscorlib]System.EventArgs) } // end of event One::MyEvent } // end of class One  
```  
  
 Observe que los nombres de los métodos de descriptor de acceso son diferentes al nombre del evento.  Al asegurarse de que todos los nombres de descriptor de acceso de eventos seguirán el patrón de nomenclatura, puede resolver CLS03302.