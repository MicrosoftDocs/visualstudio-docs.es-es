---
title: 'Cómo: Agregar diagramas de clases a proyectos (Diseñador de clases)'
ms.date: 05/08/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 94e13d4c1dbda200c2e2660e4b3b44e62ed99496
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="how-to-add-class-diagrams-to-projects"></a>Cómo: Agregar diagramas de clases a proyectos

Para diseñar, editar y refactorizar clases y otros tipos, agregue un diagrama de clases al proyecto de C#, Visual Basic o C++. Para visualizar distintas partes del código de un proyecto, agregue varios diagramas de clases al proyecto.

No se pueden crear diagramas de clases de proyectos que compartan código en varias aplicaciones. Para crear diagramas de clases UML, vea [Cómo: Crear proyectos y diagramas de modelado UML](../../modeling/create-uml-modeling-projects-and-diagrams.md).

## <a name="install-the-class-designer-component"></a>Instalar el componente del Diseñador de clases

Si va a ejecutar Visual Studio 2017 y no ha instalado el componente del **Diseñador de clases**, siga estos pasos para instalarlo.

1. Abra el **Instalador de Visual Studio** desde el menú Inicio de Windows o seleccionando **Herramientas** > **Obtener herramientas y características** en la barra de menús de Visual Studio.

   Se abrirá el **Instalador de Visual Studio**.

1. Seleccione la pestaña **Componentes individuales** y, después, desplácese hacia abajo hasta la categoría **Herramientas de código**.

1. Seleccione **Diseñador de clases** y **Modificar**.

   ![Componente del Diseñador de clases en el Instalador de Visual Studio](media/class-designer-component.png)

   El componente del **Diseñador de clases** empezará a instalarse.

## <a name="add-a-blank-class-diagram-to-a-project"></a>Agregar un diagrama de clases en blanco a un proyecto

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo del proyecto y, después, elija **Agregar** > **Nuevo elemento**. También puede presionar **Ctrl**+**Mayús**+**A**.

   Se abrirá el cuadro de diálogo **Agregar nuevo elemento**.

2. Expanda **Elementos comunes** > **General** y, después, seleccione **Diagrama de clases** en la lista de plantillas. Para los proyectos de Visual C++, busque en la categoría **Utilidad** la plantilla **Diagrama de clases**.

   > [!NOTE]
   > Si no ve la plantilla **Diagrama de clases**, [siga los pasos](#install-the-class-designer-component) para instalar el componente del **Diseñador de clases** de Visual Studio.

   El diagrama de clases se abre en el Diseñador de clases y aparece como un archivo que tiene la extensión *.cd* en el **Explorador de soluciones**. Puede arrastrar formas y líneas al diagrama desde el **cuadro de herramientas**.

Para agregar varios diagramas de clases, repita los pasos de este procedimiento.

## <a name="add-a-class-diagram-based-on-existing-types"></a>Agregar un diagrama de clases basado en tipos existentes

En el **Explorador de soluciones**, abra el menú contextual del archivo de clases y, después, elija **Ver diagrama de clases**.

O bien

En **Vista de clases**, abra el menú contextual del espacio de nombres o del tipo y, después, elija **Ver diagrama de clases**.

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>Para mostrar los contenidos de un proyecto completo en un diagrama de clases

En el **Explorador de soluciones** o en la Vista de clases, haga clic con el botón derecho en el proyecto y elija **Ver**; después, elija **Ver diagrama de clases**.

Se crea un diagrama de clases que se rellena automáticamente.

## <a name="see-also"></a>Vea también

- [Cómo: Crear tipos con el Diseñador de clases](how-to-create-types.md)
- [Cómo: Ver los tipos existentes](how-to-view-existing-types.md)
- [Diseñar y ver clases y tipos](designing-and-viewing-classes-and-types.md)
- [Visualización de tipos y relaciones](viewing-types-and-relationships.md)
- [Trabajar con diagramas de clases](working-with-class-diagrams.md)
