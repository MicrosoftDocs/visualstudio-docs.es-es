---
title: "Advertencia de conformidad con CLS CLS02809 | Microsoft Docs"
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
  - "CLS02809"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02809"
ms.assetid: a6e7b8e5-1587-437e-9d07-8a32fc5c4842
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS02809
Las propiedades deben ajustarse a un patrón de asignación de nombres concreto  
  
 Las propiedades deben adherirse a un modelo de nomenclatura específico; el nombre de las funciones de descriptor de acceso de la propiedad será el mismo que el nombre de la propiedad, con **get\_** o **set\_**.  
  
 En las comparaciones de nombres correspondientes, se omitirá el atributo **specialname** y se seguirán las reglas del identificador.  
  
 Para más información sobre la comprobación de conformidad con CLS, vea [Ensamblados compatibles con CLS](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 En la siguiente declaración de función \(mediante el lenguaje ensamblador MSIL\) se muestra lo que podría provocar la advertencia CLS02809:  
  
```  
.method public specialname instance void set_MyPropertya(int32 __unnamed000) cil managed { } // end of method One::set_MyProperty .method public specialname instance int32 get_MyPropertya() cil managed { } // end of method One::get_MyProperty .property instance int32 MyProperty() { .get instance int32 One::get_MyPropertya() .set instance void One::set_MyPropertya(int32) } // end of property One::MyProperty  
```  
  
 Observe que los nombres de los métodos de descriptor de acceso son diferentes al nombre de la propiedad.  Al asegurarse de que todos los nombres de propiedad seguirán el patrón de nomenclatura, podrá resolver el error CLS02809.