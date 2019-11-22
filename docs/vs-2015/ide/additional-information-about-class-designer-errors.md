---
title: Información adicional sobre los errores del Diseñador de clases | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 10eb94783abbd63ca152fbf73a544665199ba137
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300291"
---
# <a name="additional-information-about-class-designer-errors"></a>Información adicional sobre los errores del Diseñador de clases
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El Diseñador de clases no hace un seguimiento de la ubicación de los archivos de origen, por lo que modificar la estructura del proyecto o mover los archivos de origen del proyecto puede hacer que el Diseñador de clases pierda de vista el tipo (sobre todo el tipo de origen de una typedef, de clases base o de tipos de asociación). Puede que obtenga un error, como **El Diseñador de clases no puede mostrar este tipo**. Si lo recibe, arrastre otra vez el código fuente modificado o reubicado al diagrama de clases para volver a mostrarlo.

 Encontrará ayuda relacionada con otros errores y advertencias en los siguientes recursos:

 [Trabajar con código C++ Visual (diseñador de clases)](../ide/working-with-visual-cpp-code-class-designer.md) incluye información de solución de problemas C++ sobre cómo mostrar en un diagrama de clases.

 [Foro del Diseñador de clases de Visual Studio](https://go.microsoft.com/fwlink/?LinkId=160754) proporciona un foro para formular preguntas sobre el Diseñador de clases.

## <a name="see-also"></a>Otras referencias
 [Diseñar y ver clases y tipos](../ide/designing-and-viewing-classes-and-types.md)
