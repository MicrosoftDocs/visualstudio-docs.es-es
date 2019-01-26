---
title: Crear un proyecto de Workflow Foundation
ms.date: 06/25/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 577bb58101556dc17c62453bfe18e9618c879405
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999956"
---
# <a name="workflow-project-templates"></a>Plantillas de proyecto de flujo de trabajo

Puede crear flujos de trabajo, servicios de flujo de trabajo de Windows Communication Foundation (WCF), las actividades personalizadas y diseñadores de actividad personalizados mediante el uso de plantillas de proyecto de Visual Studio. En este artículo se describe cómo crear aplicaciones y bibliotecas con las plantillas de proyecto disponibles en Visual Studio.

## <a name="create-a-workflow-project"></a>Crear un proyecto de flujo de trabajo

Visual Studio proporciona cuatro plantillas de proyecto de flujo de trabajo diferentes:

- Aplicación de consola de flujo de trabajo

- Aplicación de servicio de flujo de trabajo WCF

- Biblioteca de actividades

- Biblioteca del Diseñador de actividad

Para obtener acceso a estas plantillas, instale primero el **Windows Workflow Foundation** componente de Visual Studio 2017. Para obtener instrucciones detalladas, consulte [instalar Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Una vez instalado el **Windows Workflow Foundation** componente, abra el **nuevo proyecto** cuadro de diálogo seleccionando **archivo** > **New**  >  **Proyecto**.

1. En el panel izquierdo, seleccione el **Visual C#** > **flujo de trabajo** categoría (o **Visual Basic** > **deflujodetrabajo**si prefiere Visual Basic).

1. En el panel central, seleccione una plantilla de proyecto, como **aplicación de consola de flujos de trabajo**.

1. En el **nombre** , escriba un nombre descriptivo para el proyecto para que sea fácil de identificar.

1. En el **ubicación** cuadro, escriba el directorio en el que desea guardar el proyecto o seleccione **examinar** para desplazarse hasta él.

1. En el **solución** cuadro, escriba el nombre para la nueva solución. Seleccione **Aceptar** para crear la aplicación.

   > [!NOTE]
   > Si desea agregar un nuevo proyecto a una solución existente, ábrala en Visual Studio, haga clic en la solución en **el Explorador de soluciones**y seleccione **agregar** > **nuevo Proyecto** para abrir el **nuevo proyecto** cuadro de diálogo.

## <a name="workflow-console-app"></a>Aplicación de consola de flujo de trabajo

Si elige la **aplicación de consola de flujos de trabajo** plantilla, Visual Studio crea una definición de flujo de trabajo en XAML. El Diseñador de flujo de trabajo se abre y muestra el lienzo del flujo de trabajo que creó. Para crear un flujo de trabajo, arrastre actividades u otros elementos de flujo de trabajo de **cuadro de herramientas** a la superficie de diseño.

## <a name="wcf-workflow-service-app"></a>Aplicación de servicio de flujo de trabajo WCF

Si elige la **aplicación de servicio de flujo de trabajo de WCF** plantilla, Visual Studio crea una definición de servicio como XAML. Se abre el Diseñador de flujo de trabajo a la vista de diseño con un <xref:System.Activities.Statements.Sequence> actividad que contiene un conjunto de <xref:System.ServiceModel.Activities.Receive> y <xref:System.ServiceModel.Activities.SendReply> actividades.

## <a name="activity-library"></a>Biblioteca de actividades

Si elige la **biblioteca de actividades** plantilla, Visual Studio crea una definición de actividad en XAML. Diseñador de flujo de trabajo se abre y muestra el lienzo para su actividad personalizada. Arrastre una actividad **cuadro de herramientas** hasta la superficie de diseño para incluirla en su actividad personalizada.

> [!NOTE]
> En el cuerpo de la actividad personalizada le permite sólo una actividad secundaria. Sin embargo, esa actividad secundaria podría ser una actividad compuesta, como un <xref:System.Activities.Statements.Sequence> actividad o <xref:System.Activities.Statements.Flowchart> actividad.

## <a name="activity-designer-library"></a>Biblioteca del Diseñador de actividad

Si elige la **biblioteca del Diseñador de actividad** plantilla, Visual Studio crea una definición del Diseñador de actividad en XAML y un archivo de implementación de código subyacente. El Diseñador de flujo de trabajo se abre y muestra el lienzo del Diseñador de actividad. Windows Presentation Foundation (WPF) de arrastrar los controles de **cuadro de herramientas** hasta la superficie de diseño para usarlos en el Diseñador de actividad personalizado.

Para obtener un ejemplo de cómo implementar un diseñador de actividad personalizado, vea [Cómo: Crear un diseñador de actividad personalizado](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Diseñadores de actividad personalizados pueden usarse para las actividades personalizadas y para las actividades de .NET Framework de forma predeterminada.

## <a name="see-also"></a>Vea también

- [Use el Diseñador de flujo de trabajo](developing-applications-with-the-workflow-designer.md)
- [Diseñar flujos de trabajo (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)