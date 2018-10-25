---
title: 'Diseñador de flujo de trabajo - Cómo: agregar un nuevo elemento a un proyecto de flujo de trabajo'
ms.date: 06/25/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dbed404f2cdd69446d8945fc9ff96703eccd161f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49814239"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Cómo: agregar un nuevo elemento a un proyecto de flujo de trabajo

Después de crear un proyecto de flujo de trabajo, puede agregar las actividades de flujo de trabajo, diseñadores y otros elementos conocidos de Visual Studio al proyecto.

En la tabla siguiente se enumera los elementos de Windows Workflow Foundation (WF) que se pueden agregar a un proyecto de flujo de trabajo:


| nombre | Descripción |
|-| - |
| Actividad | Actividad que va a estar formada por otras actividades. Al seleccionar esta opción agrega el mismo archivo XAML al proyecto que obtendría cuando se selecciona el **biblioteca de actividades** plantilla para un nuevo proyecto. Para obtener más información acerca de este procedimiento, consulte [Cómo: crear una biblioteca de actividades](../workflow-designer/how-to-create-an-activity-library.md). |
| Diseñador de actividad | Diseñador que se usa para personalizar la experiencia en tiempo de diseño de una actividad. Si selecciona este elemento agrega los mismos archivos al proyecto que obtendría cuando se selecciona el **biblioteca del Diseñador de actividad** plantilla para un nuevo proyecto. Para obtener más información acerca de este procedimiento, consulte [Cómo: crear una biblioteca del Diseñador de actividades](../workflow-designer/how-to-create-an-activity-designer-library.md). |
| Actividad de código | Actividad con lógica de ejecución escrita en código. Ya se ha generado automáticamente un archivo de código fuente con invalidación del método <xref:System.Activities.CodeActivity.Execute%2A>. |
| Servicio de flujo de trabajo WCF | Servicio de [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] compilado mediante actividades de flujo de trabajo. Si selecciona este elemento agrega los mismos archivos al proyecto que obtendría cuando se selecciona el **aplicación de servicio de flujo de trabajo de WCF** plantilla para un nuevo proyecto. Para obtener más información acerca de este procedimiento, consulte [Cómo: crear una aplicación de servicio de flujo de trabajo de WCF](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md). |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Para agregar un nuevo elemento a un proyecto de flujo de trabajo

1. En el **proyecto** menú, seleccione **Agregar nuevo elemento**.

   Se abrirá el cuadro de diálogo **Agregar nuevo elemento**.

1. En el panel izquierdo, seleccione el **flujo de trabajo** categoría y, a continuación, seleccione una plantilla de elemento de flujo de trabajo.

   > [!NOTE]
   > Si no ve el **flujo de trabajo** categoría, instalar primero el **Windows Workflow Foundation** componente de Visual Studio 2017. Para obtener instrucciones detalladas, consulte [instalar Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Escriba un nombre para el elemento en el **nombre** cuadro en la parte inferior del cuadro de diálogo.

1. Seleccione **agregar** para agregar el elemento al proyecto.

## <a name="see-also"></a>Vea también

- [Crear un proyecto de flujo de trabajo](../workflow-designer/creating-a-workflow-project.md)