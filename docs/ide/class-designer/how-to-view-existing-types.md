---
title: 'Cómo: Ver los tipos existentes (Diseñador de clases)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f477f64188c9592db65d0a82c8a1b8b3ec5b776
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956658"
---
# <a name="how-to-view-existing-types-in-class-designer"></a>Cómo: Ver los tipos existentes en el Diseñador de clases

Para ver un tipo existente y sus miembros, agregue su forma a un diagrama de clases.

Puede ver los tipos locales y aquellos a los que se hace referencia. Los tipos locales existen en el proyecto que está abierto y son de lectura y escritura. Los tipos a los que se hace referencia existen en otros proyectos o en un ensamblado al que se hace referencia y son de sólo lectura.

Para diseñar nuevos tipos en los diagramas de clases, vea [Cómo: Crear tipos con el Diseñador de clases](how-to-create-types.md).

## <a name="to-see-types-in-a-project-on-a-class-diagram"></a>Para ver los tipos de un proyecto en un diagrama de clase

1.  Desde un proyecto en el **Explorador de soluciones**, abra un archivo de diagrama de clases (.cd) existente. O bien, si no existe ningún diagrama de clase, agregue uno nuevo al proyecto. Vea [Cómo: Agregar diagramas de clases a proyectos](how-to-add-class-diagrams-to-projects.md).

2.  Desde el proyecto, en el **Explorador de soluciones**, arrastre un archivo de código fuente hasta el diagrama de clases.

    > [!NOTE]
    > Si la solución tiene un proyecto que comparte código en varias aplicaciones, puede arrastrar archivos o código a un diagrama de clases únicamente de estos orígenes:
    >
    > - El proyecto de la aplicación que contiene el diagrama
    > - Un proyecto compartido importado por el proyecto de la aplicación
    > - Un proyecto al que se hace referencia
    > - Un ensamblado

    En el diagrama, en la posición a la que arrastró el archivo, aparecen formas que representan los tipos definidos en el archivo de código fuente.

También puede ver los tipos del proyecto si arrastra uno o varios tipos desde el nodo del proyecto en la **Vista de clases** hasta el diagrama de clases.

> [!TIP]
> Si la **Vista de clases** no está abierta, abra la **Vista de clases** desde el menú **Ver**.

Para mostrar tipos en las ubicaciones predeterminadas del diagrama, seleccione uno o varios tipos en la **Vista de clases**, haga clic con el botón derecho en los tipos seleccionados y elija **Ver diagrama de clases**.

> [!NOTE]
> Si ya existe en el proyecto un diagrama de clases cerrado que contenga el tipo, el diagrama se abre para mostrar la forma de tipo. Pero si no existe en el proyecto ningún diagrama de clases que contenga el tipo, el **Diseñador de clases** crea uno nuevo y lo abre para mostrar el tipo.

Cuando se muestra por primera vez un tipo en el diagrama, su forma aparece contraída de forma predeterminada. Puede expandir la forma para ver su contenido.

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>Para mostrar el contenido de un proyecto en un diagrama de clases

En el **Explorador de soluciones** o en la **Vista de clases**, haga clic con el botón derecho en el proyecto y elija **Ver**; después, elija **Ver diagrama de clases**. Se crea un diagrama de clases que se rellena automáticamente.

## <a name="see-also"></a>Vea también

- [Cómo: Ver la herencia entre tipos](how-to-view-inheritance-between-types.md)
- [Cómo: Personalizar los diagramas de clases](how-to-customize-class-diagrams.md)
- [Visualización de tipos y relaciones](viewing-types-and-relationships.md)