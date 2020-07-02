---
title: 'Diseñador de flujo de trabajo: agregar un nuevo elemento al proyecto de flujo de trabajo'
ms.date: 06/25/2018
ms.topic: how-to
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53737eb421f4194b00354899e373441ff0a97227
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814621"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Cómo: agregar un nuevo elemento a un proyecto de flujo de trabajo

Después de crear un proyecto de flujo de trabajo, puede Agregar actividades de flujo de trabajo, diseñadores y otros elementos conocidos de Visual Studio al proyecto.

En la tabla siguiente se enumeran los elementos de Windows Workflow Foundation (WF) que se pueden agregar a un proyecto de flujo de trabajo:

| Nombre | Descripción |
|-| - |
| Actividad | Actividad que va a estar formada por otras actividades. Al seleccionar este elemento, se agrega el mismo archivo XAML al proyecto que obtendría cuando se selecciona la plantilla **biblioteca de actividades** para un nuevo proyecto. Para obtener más información sobre este procedimiento, vea [crear un proyecto de flujo de trabajo](creating-a-workflow-project.md). |
| Diseñador de actividad | Diseñador que se usa para personalizar la experiencia en tiempo de diseño de una actividad. Al seleccionar este elemento, se agregan los mismos archivos al proyecto que obtendría cuando se selecciona la plantilla **biblioteca del diseñador de actividad** para un nuevo proyecto. |
| Actividad de código | Actividad con lógica de ejecución escrita en código. Ya se ha generado automáticamente un archivo de código fuente con invalidación del método <xref:System.Activities.CodeActivity.Execute%2A>. |
| Servicio de flujo de trabajo WCF | Servicio de [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] compilado mediante actividades de flujo de trabajo. Al seleccionar este elemento, se agregan los mismos archivos al proyecto que obtendría cuando se selecciona la plantilla **aplicación de servicio de flujo de trabajo WCF** para un nuevo proyecto. Para obtener más información acerca de este procedimiento, consulte [Cómo: crear una aplicación de servicio de flujo de trabajo WCF](creating-a-workflow-project.md). |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Para agregar un nuevo elemento a un proyecto de flujo de trabajo

1. En el menú **Proyecto**, seleccione **Agregar nuevo elemento**.

   Se abrirá el cuadro de diálogo **Agregar nuevo elemento**.

1. En el panel izquierdo, seleccione la categoría **flujo de trabajo** y, a continuación, seleccione una plantilla de elemento de flujo de trabajo.

   > [!NOTE]
   > Si no ve la categoría de **flujo de trabajo** , instale primero el **Windows Workflow Foundation** componente de Visual Studio. Para obtener instrucciones detalladas, consulte [instalación de Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Escriba un nombre para el elemento en el cuadro **nombre** situado en la parte inferior del cuadro de diálogo.

1. Seleccione **Agregar** para agregar el elemento al proyecto.

## <a name="see-also"></a>Vea también

- [Crear un proyecto de flujo de trabajo](../workflow-designer/creating-a-workflow-project.md)
