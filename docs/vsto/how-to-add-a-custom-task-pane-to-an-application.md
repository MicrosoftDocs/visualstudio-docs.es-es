---
title: 'Cómo: agregar un panel de tareas personalizado a una aplicación'
description: Obtenga información sobre cómo puede Agregar un panel de tareas personalizado a las aplicaciones mediante el complemento Visual Studio Tools para Office (VSTO).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], adding to application
- custom task panes [Office development in Visual Studio], adding to application
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1e8056eddef6329aeb10ed5545c4146f0af0f167
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845055"
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>Cómo: agregar un panel de tareas personalizado a una aplicación
  Puede agregar un panel de tareas personalizado a las aplicaciones enumeradas anteriormente mediante el complemento de VSTO. Para obtener más información, consulte [paneles de tareas personalizados](../vsto/custom-task-panes.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="add-a-custom-task-pane-to-an-application"></a>Agregar un panel de tareas personalizado a una aplicación

### <a name="to-add-a-custom-task-pane-to-an-application"></a>Para agregar un panel de tareas personalizado a una aplicación

1. Abra o cree un proyecto de complemento de VSTO para una de las aplicaciones enumeradas anteriormente. Para obtener más información, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. En el menú **Proyecto** , haga clic en **Agregar control de usuario**.

3. En el cuadro de diálogo **Agregar nuevo elemento** , cambie el nombre del nuevo control de usuario a **MyUserControl** y, a continuación, haga clic en **Agregar**.

     Se abre el control de usuario en el diseñador.

4. Agregue uno o varios controles de Windows Forms desde el **cuadro de herramientas** al control de usuario.

5. Abra el archivo de código **ThisAddIn.CS** o **ThisAddIn. VB** .

6. Agregue el siguiente código a la clase `ThisAddIn` . Este código declara instancias de `MyUserControl` y <xref:Microsoft.Office.Tools.CustomTaskPane> como miembros de la clase `ThisAddIn` .

     [!code-vb[Trin_TaskPaneBasic#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#1)]
     [!code-csharp[Trin_TaskPaneBasic#1](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#1)]

7. Agregue el código siguiente al controlador de eventos `ThisAddIn_Startup`. Este código crea un nuevo <xref:Microsoft.Office.Tools.CustomTaskPane> agregando el objeto `MyUserControl` a la colección `CustomTaskPanes` . El código también muestra el panel de tareas.

     [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
     [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]

    > [!NOTE]
    > Este código asocia el panel de tareas personalizado a la ventana activa de la aplicación. En algunas aplicaciones, tal vez desee modificar este código para asegurarse de que el panel de tareas aparece con otros documentos o elementos de la aplicación. Para obtener más información, consulte [paneles de tareas personalizados](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Vea también
- [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)
- [Paneles de tareas personalizados](../vsto/custom-task-panes.md)
- [Tutorial: automatizar una aplicación desde un panel de tareas personalizado](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
