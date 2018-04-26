---
title: 'Diseñador de flujo de trabajo: Cómo: crear una aplicación de consola de flujos de trabajo'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6461a644bdedd3d391059cd8a3a17f887e77c6b3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-workflow-console-application"></a>Crear una aplicación de consola de flujos de trabajo

Windows Workflow Foundation (WF) le permite crear flujos de trabajo para ejecutar sistemas o procesos humanos. El Diseñador de flujo de trabajo de Windows proporciona la superficie de diseño para crear estos flujos de trabajo. El Diseñador de flujo de trabajo puede utilizarse para crear flujos de trabajo de Visual Studio o se puede integrar en otras aplicaciones que hospedan el diseñador.

En este tema se describe cómo utilizar el Diseñador de flujo de trabajo en Visual Studio 2010 para crear un flujo de trabajo en una aplicación de consola.

## <a name="to-create-a-workflow-console-application"></a>Para crear una aplicación de consola de flujos de trabajo

1.  Inicie Visual Studio 2010.

2.  En el menú **Archivo**, elija **Nuevo** y después seleccione **Proyecto**.

     Aparece el cuadro de diálogo **Nuevo proyecto** .

3.  En el **plantillas instaladas** panel, seleccione **flujo de trabajo** desde el **Visual C#** o **Visual Basic** agrupaciones, dependiendo de su idioma de preferencia.

4.  En el panel central, seleccione **aplicación de consola de flujos de trabajo**.

5.  En el **nombre** cuadro, escriba un nombre descriptivo para el proyecto para que sea fácil de identificar.

6.  En el **ubicación** cuadro, escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para navegar hasta él.

7.  En el **solución** cuadro, escriba el nombre de la nueva solución. Haga clic en **Aceptar** para crear la aplicación.

    > [!NOTE]
    > Si desea agregar una aplicación de consola de flujos de trabajo a una solución existente, ábrala en Visual Studio 2010, derecho, haga clic en la solución en **el Explorador de soluciones**y seleccione **agregar**, a continuación,  **Nuevo proyecto** para abrir el **nuevo proyecto** cuadro de diálogo. Continúe de la forma descrita anteriormente en este procedimiento.

8.  La plantilla del proyecto crea una definición de flujo de trabajo en XAML y la definición de la aplicación de consola está en código fuente. El Diseñador de flujo de trabajo se abre y muestra el lienzo del flujo de trabajo que creó.

9. Para crear un flujo de trabajo, arrastre actividades u otros elementos de flujo de trabajo desde el **cuadro de herramientas** a la superficie de diseño del flujo de trabajo.

## <a name="see-also"></a>Vea también

- [Crear un proyecto de flujo de trabajo](../workflow-designer/creating-a-workflow-project.md)