---
title: "Información adicional sobre los errores del Diseñador de clases | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.CPlusPlusViewInDiagramNoTypeFound
- vs.classdesigner.CPlusPlusNoTypeFound
- vs.classdesigner.CannotShowBaseType
- vs.classdesigner.MatchOrphanTypesAtLoad
- vs.classdesigner.CannotShowType
- vs.classdesigner.AssociationTypeNotFoundError
- vs.classdesigner.ViewInDiagramNoTypesFound
- vs.classdesigner.CannotImplementInterface
- vs.classdesigner.CannotShowImplementedInterface
- vs.classdesigner.ViewInDiagramUnparsableTypeFound
- vs.classdesigner.AssociationTypeNotFound
- vs.classdesigner.CPlusPlusTypeCannotBeAdded
helpviewer_keywords:
- errors, class diagrams
- errors, Class Designer
- error messages, Class Designer
- Class Designer [Visual Studio], errors
- error messages, class diagrams
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 53b61b1fa49ffcbc047d47dd26586b45ae883c5f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="additional-information-about-class-designer-errors"></a>Información adicional sobre los errores del Diseñador de clases
El Diseñador de clases no hace un seguimiento de la ubicación de los archivos de origen, por lo que modificar la estructura del proyecto o mover los archivos de origen del proyecto puede hacer que el Diseñador de clases pierda de vista el tipo (sobre todo el tipo de origen de una typedef, de clases base o de tipos de asociación). Puede que obtenga un error, como **El Diseñador de clases no puede mostrar este tipo**. Si lo recibe, arrastre otra vez el código fuente modificado o reubicado al diagrama de clases para volver a mostrarlo.  
  
Encontrará ayuda relacionada con otros errores y advertencias en los siguientes recursos:  
  
[Trabajar con código de Visual C++](working-with-visual-cpp-code.md)  
Incluye información de solución de problemas sobre la visualización de C++ en un diagrama de clases.  
  
[Foro del Diseñador de clases de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160754)  
Proporciona un foro para formular preguntas sobre el Diseñador de clases.  
  
## <a name="see-also"></a>Vea también
[Diseñar y ver clases y tipos](designing-and-viewing-classes-and-types.md)