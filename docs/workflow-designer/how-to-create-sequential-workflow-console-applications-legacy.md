---
title: 'Diseñador de flujo de trabajo: Cómo: crear aplicaciones de consola de flujos de trabajo secuenciales (heredado)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb4e048fdf8eb8fee541f84656a29427b5a07a1d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Cómo: Crear aplicaciones de consola de flujos de trabajo secuenciales (Heredado)

Siga estos pasos para crear un proyecto de aplicación de consola de flujos de trabajo secuenciales mediante heredado proporcionados por el Diseñador de flujo de trabajo de Windows mediante Visual Studio 2010. Use el Diseñador de flujo de trabajo heredado cuando deba tener como destino la versión 3.5 de .NET Framework o el conocido como WinFX.

## <a name="to-create-a-sequential-workflow-console-application"></a>Para crear una aplicación de consola de flujos de trabajo secuenciales

1.  Inicie Visual Studio.

2.  En el menú **Archivo**, elija **Nuevo** y después seleccione **Proyecto**.

     Aparece el cuadro de diálogo **Nuevo proyecto** .

3.  Seleccione el **.NET Framework 3.0** opción o **.NET Framework 3.5** opción en la lista desplegable lista en la parte superior de la **nuevo proyecto** ventana para tener acceso al diseñador heredado.

    > [!NOTE]
    > La opción predeterminada en Visual Studio 2010 es **.NET Framework 4**. Esta opción se utiliza para crear aplicaciones de Windows Workflow Foundation (WF) que tienen como destino .NET Framework 4 y no usa el diseñador heredado.

4.  En el **tipos de proyecto** panel, seleccione proyectos de Visual C# o proyectos de Visual Basic (en **otros lenguajes**) y, a continuación, seleccione **flujo de trabajo**.

5.  En el **plantillas** panel, seleccione **aplicación de consola de flujos de trabajo secuenciales**.

6.  En el **nombre** cuadro, escriba un nombre descriptivo para el proyecto para que sea fácil de identificar.

7.  En el **ubicación** cuadro, escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para navegar hasta él.

     Se abrirá el Diseñador de Windows Forms, que mostrará el formulario Form1 del proyecto creado.

8.  Haga clic en **Aceptar**.

     Se abre el Diseñador de flujo de trabajo y muestra la superficie de diseño de flujo de trabajo del flujo de trabajo secuencial que ha creado.

9. Arrastre una actividad desde la **cuadro de herramientas** a la superficie de diseño en el **coloque la actividad** área designada.

## <a name="see-also"></a>Vea también

- [Crear proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md)
- [Desarrollo de flujos de trabajo](http://msdn.microsoft.com/en-us/557bcb1f-a7ab-49f6-8df7-2706b7001301)