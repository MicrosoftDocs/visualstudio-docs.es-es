---
title: Crear un proyecto de Workflow Foundation
ms.date: 06/25/2018
ms.topic: conceptual
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f793e6ff468bdec6df499c5e5eb6b8524e9e4d5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650576"
---
# <a name="workflow-project-templates"></a>Plantillas de proyecto de flujo de trabajo

Puede crear flujos de trabajo, servicios de flujo de trabajo de Windows Communication Foundation (WCF), actividades personalizadas y diseñadores de actividad personalizados mediante plantillas de proyecto de Visual Studio. En este artículo se describe cómo crear bibliotecas y aplicaciones con las plantillas de proyecto disponibles en Visual Studio.

## <a name="create-a-workflow-project"></a>Crear un proyecto de flujo de trabajo

Visual Studio proporciona cuatro plantillas de proyecto de flujo de trabajo diferentes:

- Aplicación de consola de flujos de trabajo

- Aplicación de servicio de flujo de trabajo WCF

- Biblioteca de actividades

- Biblioteca del diseñador de actividad

Para tener acceso a estas plantillas, primero Instale el componente **Windows Workflow Foundation** de Visual Studio. Para obtener instrucciones detalladas, consulte [instalación de Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Después de instalar el componente de **Windows Workflow Foundation** , seleccione **archivo**  > **nuevo**  > **proyecto**.

1. Busque y seleccione una plantilla de proyecto de flujo de trabajo, por ejemplo, la plantilla **aplicación de consola de flujos** de trabajo.

1. Continúe con la creación del proyecto.

   > [!NOTE]
   > Si desea agregar un nuevo proyecto a una solución existente, abra la solución en Visual Studio, haga clic con el botón derecho en la solución en **Explorador de soluciones**y seleccione **Agregar**  > **nuevo proyecto**.

## <a name="workflow-console-app"></a>Aplicación de consola de flujos de trabajo

Si elige la plantilla **aplicación de consola de flujos de trabajo** , Visual Studio crea una definición de flujo de trabajo en XAML. El Diseñador de flujo de trabajo se abre y muestra el lienzo del flujo de trabajo que creó. Para crear un flujo de trabajo, arrastre actividades u otros elementos de flujo de trabajo desde el **cuadro de herramientas** a la superficie de diseño.

## <a name="wcf-workflow-service-app"></a>Aplicación de servicio de flujo de trabajo WCF

Si elige la plantilla de **aplicación de servicio de flujo de trabajo WCF** , Visual Studio crea una definición de servicio como XAML. El Diseñador de flujo de trabajo se abre en la vista de diseño con una actividad <xref:System.Activities.Statements.Sequence> que contiene un conjunto de actividades de <xref:System.ServiceModel.Activities.Receive> y <xref:System.ServiceModel.Activities.SendReply>.

## <a name="activity-library"></a>Biblioteca de actividades

Si elige la plantilla **biblioteca de actividades** , Visual Studio crea una definición de actividad en XAML. Diseñador de flujo de trabajo se abre y muestra el lienzo para su actividad personalizada. Arrastre una actividad desde el **cuadro de herramientas** hasta la superficie de diseño para incluirla en la actividad personalizada.

> [!NOTE]
> Solo se permite una actividad secundaria en el cuerpo de la actividad personalizada. Sin embargo, esa actividad secundaria podría ser una actividad compuesta, como una actividad <xref:System.Activities.Statements.Sequence> o una actividad <xref:System.Activities.Statements.Flowchart>.

## <a name="activity-designer-library"></a>Biblioteca del diseñador de actividad

Si elige la plantilla **biblioteca del diseñador de actividad** , Visual Studio crea una definición del diseñador de actividad en XAML y un archivo de implementación de código subyacente. El Diseñador de flujo de trabajo se abre y muestra el lienzo del diseñador de actividad. Arrastre controles de Windows Presentation Foundation (WPF) desde el **cuadro de herramientas** a la superficie de diseño para usarlos en el diseñador de actividad personalizado.

Para obtener un ejemplo de cómo implementar un diseñador de actividad personalizado, vea [Cómo: crear un diseñador de actividad personalizado](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Los diseñadores de actividad personalizados se pueden usar para las actividades personalizadas y para las actividades .NET predeterminadas.

## <a name="see-also"></a>Vea también

- [Usar el Diseñador de flujo de trabajo](developing-applications-with-the-workflow-designer.md)
- [Diseñar flujos de trabajo (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)