---
title: 'Cómo: Ver los tipos existentes (Diseñador de clases) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 925220d583695e0116fb5901d92626bfcfa7450f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670540"
---
# <a name="how-to-view-existing-types-class-designer"></a>Cómo: Ver los tipos existentes (Diseñador de clases)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para ver un tipo existente y sus miembros, agregue su forma a un diagrama de clases.

 Puede ver los tipos locales y aquellos a los que se hace referencia. Los tipos locales existen en el proyecto que está abierto y son de lectura y escritura. Los tipos a los que se hace referencia existen en otros proyectos o en un ensamblado al que se hace referencia y son de sólo lectura.

 Para diseñar nuevos tipos en los diagramas de clases, consulte [Cómo: Crear tipos con el Diseñador de clases](../ide/how-to-create-types-by-using-class-designer.md).

### <a name="to-see-types-in-a-project-on-a-class-diagram"></a>Para ver los tipos de un proyecto en un diagrama de clase

1. Desde un proyecto en el Explorador de soluciones, abra un archivo de diagrama de clase (.cd) existente. O bien, si no existe ningún diagrama de clase, agregue uno nuevo al proyecto. Vea [Cómo: Agregar diagramas de clase a proyectos (Diseñador de clases) ](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).

2. Desde el proyecto, en el Explorador de soluciones, arrastre un archivo de código fuente hasta el diagrama de clase.

   > [!WARNING]
   > Si la solución tiene un proyecto que comparte código en varias aplicaciones, puede arrastrar archivos o código a un diagrama de clases únicamente de estos orígenes:
   >
   > - El proyecto de la aplicación que contiene el diagrama
   >   - Un proyecto compartido importado por el proyecto de la aplicación
   >   - Un proyecto al que se hace referencia
   >   - Un ensamblado

    En el diagrama, en la posición a la que arrastró el archivo, aparecen formas que representan los tipos definidos en el archivo de código fuente.

   También puede ver los tipos del proyecto arrastrando uno o varios tipos desde el nodo del proyecto en la Vista de clases hasta el diagrama de clases.

> [!TIP]
> Si la vista de clases no está abierta, ábrala desde el menú **Ver**. Para obtener más información sobre la vista de clases, consulte [Ver clases y sus miembros](https://msdn.microsoft.com/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).

 Para mostrar tipos en las ubicaciones predeterminadas del diagrama, seleccione uno o varios tipos en la vista de clases, haga clic con el botón derecho del mouse en los tipos seleccionados y elija **Ver diagrama de clases**.

> [!NOTE]
> Si ya existe en el proyecto un diagrama de clases cerrado que contenga el tipo, el diagrama se abre para mostrar la forma de tipo. Sin embargo, si no existe en el proyecto ningún diagrama de clases que contenga el tipo, el Diseñador de clases crea uno nuevo y lo abre para mostrar el tipo.

 Cuando se muestra por primera vez un tipo en el diagrama, su forma aparece contraída de forma predeterminada. Puede expandir la forma para ver su contenido.

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>Para mostrar el contenido de un proyecto en un diagrama de clases

1. En el Explorador de soluciones o en la Vista de clases, haga clic con el botón derecho en el proyecto y elija **Vista**; después, elija **Ver diagrama de clases**.

     Se crea un diagrama de clases que se rellena automáticamente.

## <a name="see-also"></a>Vea también
 [Cómo: ver la herencia entre tipos (diseñador de clases)](../ide/how-to-view-inheritance-between-types-class-designer.md) [Cómo: personalizar los diagramas de clases (diseñador de clases)](../ide/how-to-customize-class-diagrams-class-designer.md) [ver tipos y relaciones (diseñador de clases)](../ide/viewing-types-and-relationships-class-designer.md)
