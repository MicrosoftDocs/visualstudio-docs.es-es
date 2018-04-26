---
title: 'Diseñador de flujo de trabajo: Cómo: crear aplicaciones de consola de flujo de trabajo de equipo de estado (heredado)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- console applications, state machine workflows
- state machine workflow console applications
- state machine workflows, console applicationa
ms.assetid: d6170b5d-5d4f-48e1-8257-c78604f27eac
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 805b048a9e30f7a637e178d223b962259dadd926
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-state-machine-workflow-console-applications-legacy"></a>Cómo: Crear aplicaciones de consola de flujos de trabajo de equipo de estado (Heredado)

Siga estos pasos para crear un proyecto de aplicación de consola de flujo de trabajo de equipo de estado con heredado proporcionados por el Diseñador de flujo de trabajo de Windows mediante Visual Studio 2010. Use el Diseñador de flujo de trabajo heredado cuando deba tener como destino la versión 3.5 de .NET Framework o el conocido como WinFX.

## <a name="to-create-a-state-machine-application-project"></a>Para crear un proyecto de aplicación de equipo de estado

1.  Inicie Visual Studio.

2.  En el menú **Archivo**, elija **Nuevo** y después seleccione **Proyecto**.

     Aparece el cuadro de diálogo **Nuevo proyecto** .

3.  Seleccione el **.NET Framework 3.0** opción o **.NET Framework 3.5** opción en la lista desplegable lista en la parte superior de la **nuevo proyecto** ventana para tener acceso al diseñador heredado.

    > [!NOTE]
    > La opción predeterminada en Visual Studio 2010 es **.NET Framework 4**. Esta opción se utiliza para crear aplicaciones de Windows Workflow Foundation (WF) que tienen como destino .NET Framework 4 y no usa el diseñador heredado.

4.  En el **tipos de proyecto** panel, seleccione Visual C# o Visual Basic (en **otros lenguajes**) y, a continuación, seleccione **flujo de trabajo**.

5.  En el **plantillas** panel, seleccione **aplicación de consola de flujo de trabajo de equipo de estado**.

6.  En el **nombre** cuadro, escriba un nombre descriptivo para el proyecto para que sea fácil de identificar.

7.  En el **ubicación** cuadro, escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para navegar hasta él.

     Si desea que un directorio de solución creado para el proyecto, seleccione la **crear directorio para la solución** casilla de verificación y escriba un nombre en el **nombre de la solución** cuadro.

8.  Haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también

- [Crear proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md)
- [Cómo: Crear una biblioteca de flujos de trabajo de máquina de estados (heredado)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)