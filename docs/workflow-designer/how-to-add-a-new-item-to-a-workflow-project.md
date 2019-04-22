---
title: 'Diseñador de flujo de trabajo - Cómo: Agregar un nuevo elemento a un proyecto de flujo de trabajo'
ms.date: 06/25/2018
ms.topic: conceptual
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6f0fb6c013e3df041e750344c09fb19f8c43b254
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649594"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Procedimiento Agregar un nuevo elemento a un proyecto de flujo de trabajo

Después de crear un proyecto de flujo de trabajo, puede agregar las actividades de flujo de trabajo, diseñadores y otros elementos conocidos de Visual Studio al proyecto.

En la tabla siguiente se enumera los elementos de Windows Workflow Foundation (WF) que se pueden agregar a un proyecto de flujo de trabajo:

| Name | Descripción |
|-| - |
| Actividad | Actividad que va a estar formada por otras actividades. Al seleccionar esta opción agrega el mismo archivo XAML al proyecto que obtendría cuando se selecciona el **biblioteca de actividades** plantilla para un nuevo proyecto. Para obtener más información acerca de este procedimiento, consulte [crear un proyecto de flujo de trabajo](creating-a-workflow-project.md). |
| Diseñador de actividad | Diseñador que se usa para personalizar la experiencia en tiempo de diseño de una actividad. Si selecciona este elemento agrega los mismos archivos al proyecto que obtendría cuando se selecciona el **biblioteca del Diseñador de actividad** plantilla para un nuevo proyecto. |
| Actividad de código | Actividad con lógica de ejecución escrita en código. Ya se ha generado automáticamente un archivo de código fuente con invalidación del método <xref:System.Activities.CodeActivity.Execute%2A>. |
| Servicio de flujo de trabajo WCF | Servicio de [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] compilado mediante actividades de flujo de trabajo. Si selecciona este elemento agrega los mismos archivos al proyecto que obtendría cuando se selecciona el **aplicación de servicio de flujo de trabajo de WCF** plantilla para un nuevo proyecto. Para obtener más información acerca de este procedimiento, consulte [Cómo: Crear una aplicación de servicio de flujo de trabajo WCF](/visualstudio/workflow-designer/creating-a-workflow-project). |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Para agregar un nuevo elemento a un proyecto de flujo de trabajo

1. En el menú **Proyecto**, seleccione **Agregar nuevo elemento**.

   Se abre el cuadro de diálogo **Agregar nuevo elemento**.

1. En el panel izquierdo, seleccione el **flujo de trabajo** categoría y, a continuación, seleccione una plantilla de elemento de flujo de trabajo.

   > [!NOTE]
   > Si no ve el **flujo de trabajo** categoría, instalar primero el **Windows Workflow Foundation** componente de Visual Studio. Para obtener instrucciones detalladas, consulte [instalar Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Escriba un nombre para el elemento en el **nombre** cuadro en la parte inferior del cuadro de diálogo.

1. Seleccione **agregar** para agregar el elemento al proyecto.

## <a name="see-also"></a>Vea también

- [Crear un proyecto de flujo de trabajo](../workflow-designer/creating-a-workflow-project.md)