---
title: 'Diseñador de flujo de trabajo: Cómo: crear un proyecto de flujo de trabajo vacío (heredado)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- projects, empty workflow
- empty workflow projects
- workflows, empty workflow projects
ms.assetid: f81b9cf2-9adb-47a2-936b-cb1851614e19
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2aa51df35a1187c8d327a401d77c12e4532f4eb8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-an-empty-workflow-project-legacy"></a>Cómo: Crear un proyecto de flujo de trabajo vacío (Heredado)

Siga estos pasos para crear un proyecto de flujo de trabajo vacío mediante el Diseñador de flujo de trabajo de Windows heredado proporcionada por Visual Studio 2010. Use el Diseñador de flujo de trabajo heredado cuando deba tener como destino la versión 3.5 de .NET Framework o el conocido como WinFX.

## <a name="to-create-an-empty-workflow-project"></a>Para crear un proyecto de flujo de trabajo vacío

1.  Inicie Visual Studio.

2.  En el menú **Archivo**, elija **Nuevo** y después seleccione **Proyecto**.

     Aparece el cuadro de diálogo **Nuevo proyecto** .

3.  Seleccione el **.NET Framework 3.0** opción o **.NET Framework 3.5** opción en la lista desplegable lista en la parte superior de la **nuevo proyecto** ventana para tener acceso al diseñador heredado.

    > [!NOTE]
    > La opción predeterminada en Visual Studio 2010 es **.NET Framework 4**. Esta opción se utiliza para crear aplicaciones de Windows Workflow Foundation (WF) que tienen como destino .NET Framework 4 y no usa el diseñador heredado.

4.  En el **tipos de proyecto** panel, seleccione Visual C# o Visual Basic (en **otros lenguajes**) y, a continuación, seleccione **flujo de trabajo**.

5.  En el **plantillas** panel, seleccione **proyecto vacío de flujo de trabajo**.

6.  En el **nombre** cuadro, escriba un nombre descriptivo para el proyecto para que sea fácil de identificar.

7.  En el **ubicación** cuadro, escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para navegar hasta él.

     Si desea que un directorio de solución creado para el proyecto, seleccione la **crear directorio para la solución** casilla de verificación y escriba un nombre en el **nombre de la solución** cuadro.

8.  Haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también

- [Crear proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md)