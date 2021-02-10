---
title: Usar el Diseñador de clases
description: Aprenda a diseñar, visualizar y refactorizar las clases y otros tipos del código con el Diseñador de clases en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 05/08/2018
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.diagram
- vs.classdesigner.enum
helpviewer_keywords:
- Class Designer [Visual Studio]
- Class Designer, about Class Designer
- types [Visual Studio], viewing
- classes [Visual Studio], viewing
- class designer
ms.assetid: 40ed2c9d-0ce0-4b95-ad78-5dec2065ccea
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 236efe20ee652e2690cedf36843d539bf8a9cc46
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850300"
---
# <a name="design-and-view-classes-and-types-with-class-designer"></a>Diseñar y ver clases y tipos con el Diseñador de clases

Diseñe, visualice y refactorice clases y otros tipos del código con el **Diseñador de clases** de Visual Studio. Use diagramas de clases para crear y editar clases del proyecto de C#, Visual Basic o C++. También puede usar diagramas de clases para comprender mejor la estructura del proyecto o reorganizar el código.

## <a name="what-you-can-do-with-class-diagrams"></a>Qué puede hacer con los diagramas de clases

- **Diseñar**: edite el código del proyecto modificando el diagrama de clases. Agregar nuevos elementos y eliminar los que no quiera. Los cambios se reflejan en el código.

- **Visualizar**: comprenda la estructura del proyecto viendo las clases del proyecto en un diagrama. Personalice el diagrama para poder centrarse en los detalles del proyecto que más le importan. Guarde el diagrama para utilizarlo más adelante en demostraciones o documentación.

- **Refactorizar**: reemplace métodos, cambie el nombre de los identificadores, refactorice parámetros e implemente interfaces y clases abstractas.

## <a name="view-types-and-relationships"></a>Ver tipos y relaciones

Los diagramas de clases muestran los detalles de los tipos (por ejemplo, sus miembros constituyentes) y las relaciones que tienen entre ellos. La visualización de estas entidades es una vista dinámica del código. Esto significa que puede editar tipos en el diseñador y, después, ver los cambios reflejados en el código fuente de la entidad. Del mismo modo, el diagrama de clases se mantiene sincronizado con los cambios que haga en los archivos del código.

> [!NOTE]
> Si el proyecto contiene un diagrama de clases y además hace referencia a un tipo que se encuentra en otro proyecto, el diagrama de clases no mostrará el tipo al que se hace referencia hasta que se compile el proyecto para ese tipo. Del mismo modo, el diagrama no mostrará los cambios en el código de la entidad externa hasta que se recompile el proyecto para esa entidad.

## <a name="class-diagram-workflow"></a>Flujo de trabajo de los diagramas de clases

Los diagramas de clases pueden ayudarle a entender la estructura de clases de los proyectos. Es posible que estos proyectos los hayan creado otros desarrolladores o que solo necesite un actualizador en un proyecto que haya creado. Puede usar los diagramas de clases para personalizar, compartir y presentar información de proyectos con otros usuarios.

El primer paso para presentar la información del proyecto es crear un diagrama de clases que muestre lo que quiera mostrar. Para más información, vea [Agregar un diagrama de clases](how-to-add-class-diagrams-to-projects.md). Puede crear varios diagramas de clases para un proyecto y utilizarlos para mostrar una vista única del proyecto, un subconjunto determinado de tipos del proyecto o un subconjunto determinado de miembros de tipos.

Además de definir lo que muestra cada diagrama de clases, puede cambiar la forma en la que se presenta la información. Para más información, vea [Cómo: Personalizar los diagramas de clases](how-to-customize-class-diagrams.md).

Después de ajustar uno o varios diagramas de clases, puede copiarlos a documentos de Microsoft Office e imprimirlos o exportarlos como archivos de imagen. Para más información, vea [Cómo: Copiar elementos del diagrama de clases en un documento de Microsoft Office](how-to-copy-class-diagram-elements-to-a-microsoft-office-document.md), [Cómo: Imprimir diagramas de clases](how-to-print-class-diagrams.md) y [Cómo: Exportar los diagramas de clases como imágenes](how-to-export-class-diagrams-as-images.md).

> [!NOTE]
> El Diseñador de clases no realiza un seguimiento de la ubicación de los archivos de origen, por lo que cambiar la estructura del proyecto o mover los archivos de origen del proyecto puede hacer que el Diseñador de clases pierda de vista el tipo, especialmente el tipo de origen de una typedef, de clases base o de tipos de asociación. Puede que reciba un error, como **El Diseñador de clases no puede mostrar este tipo**. Si lo recibe, arrastre otra vez el código fuente modificado o reubicado al diagrama de clases para volver a mostrarlo.

## <a name="see-also"></a>Vea también

- [Características del editor de código](../writing-code-in-the-code-and-text-editor.md)
- [Asignar dependencias en las soluciones](../../modeling/map-dependencies-across-your-solutions.md)
