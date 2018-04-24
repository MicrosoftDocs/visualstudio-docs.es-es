---
title: Información adicional sobre los errores del Diseñador de clases | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8cd6223786db06506c1fa4ac9b6bd3118eb5e3d7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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