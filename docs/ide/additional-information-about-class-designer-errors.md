---
title: "Additional Information About Class Designer Errors | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.CPlusPlusViewInDiagramNoTypeFound"
  - "vs.classdesigner.CPlusPlusNoTypeFound"
  - "vs.classdesigner.CannotShowBaseType"
  - "vs.classdesigner.MatchOrphanTypesAtLoad"
  - "vs.classdesigner.CannotShowType"
  - "vs.classdesigner.AssociationTypeNotFoundError"
  - "vs.classdesigner.ViewInDiagramNoTypesFound"
  - "vs.classdesigner.CannotImplementInterface"
  - "vs.classdesigner.CannotShowImplementedInterface"
  - "vs.classdesigner.ViewInDiagramUnparsableTypeFound"
  - "vs.classdesigner.AssociationTypeNotFound"
  - "vs.classdesigner.CPlusPlusTypeCannotBeAdded"
helpviewer_keywords: 
  - "errors, class diagrams"
  - "errors, Class Designer"
  - "error messages, Class Designer"
  - "Class Designer [Visual Studio], errors"
  - "error messages, class diagrams"
  - "class diagrams, errors"
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Additional Information About Class Designer Errors
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El Diseñador de clases no hace un seguimiento de la ubicación de los archivos de origen, por lo que modificar la estructura del proyecto o mover los archivos de origen del proyecto puede hacer que el Diseñador de clases pierda de vista el tipo \(sobre todo el tipo de origen de una typedef, de clases base o de tipos de asociación\).  Es posible que reciba un error como **Class Designer is unable to display this type**.  Si lo recibe, arrastre otra vez el código fuente modificado o reubicado al diagrama de clases para volver a mostrarlo.  
  
 Encontrará ayuda relacionada con otros errores y advertencias en los siguientes recursos:  
  
 [Working with Visual C\+\+ Code \(Class Designer\)](../ide/working-with-visual-cpp-code-class-designer.md)  
 Incluye información de solución de problemas sobre la visualización de C\+\+ en un diagrama de clases.  
  
 [Foro del Diseñador de clases de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160754)  
 Proporciona un foro para formular preguntas sobre el Diseñador de clases.  
  
## Vea también  
 [Designing and Viewing Classes and Types](../ide/designing-and-viewing-classes-and-types.md)