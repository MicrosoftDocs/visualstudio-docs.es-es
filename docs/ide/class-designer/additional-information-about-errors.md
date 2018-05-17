---
title: Errores del Diseñador de clases
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: troubleshooting
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
- error messages, class diagrams
- Class Designer [Visual Studio], errors
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 014497d0b32df61412820468a8f3f7e0b177c14f
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="class-designer-errors"></a>Errores del Diseñador de clases

El **Diseñador de clases** no hace un seguimiento de la ubicación de los archivos de origen, por lo que modificar la estructura del proyecto o mover los archivos de origen del proyecto puede hacer que el **Diseñador de clases** pierda de vista el tipo. Por ejemplo, es habitual modificar el tipo de origen de una definición de tipo, de clases base y de tipos de asociación. Puede que obtenga un error, como **El Diseñador de clases no puede mostrar este tipo**. Para resolver el error, arrastre otra vez el código fuente modificado o reubicado al diagrama de clases para mostrarlo.

## <a name="resources"></a>Recursos

Encontrará ayuda relacionada con otros errores y advertencias en los siguientes recursos:

- [Trabajar con código de Visual C++](working-with-visual-cpp-code.md) incluye información de solución de problemas sobre la visualización de C++ en un diagrama de clases.
- [Foro del Diseñador de clases de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160754) proporciona un foro para formular preguntas sobre el **Diseñador de clases**.

## <a name="see-also"></a>Vea también

- [Diseñar y ver clases y tipos](designing-and-viewing-classes-and-types.md)
