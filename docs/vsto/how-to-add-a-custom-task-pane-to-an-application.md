---
title: 'Cómo: Agregar un panel de tareas personalizado a una aplicación'
description: Obtenga información sobre cómo agregar un panel de tareas personalizado a las aplicaciones mediante el complemento Visual Studio Tools para Office (VSTO).
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d85edb9773783abe6282918c432fc1a4eff83944
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826725"
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>Cómo: Agregar un panel de tareas personalizado a una aplicación
  Puede agregar un panel de tareas personalizado a las aplicaciones enumeradas anteriormente mediante el complemento de VSTO. Para obtener más información, vea [Paneles de tareas personalizados.](../vsto/custom-task-panes.md)

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="add-a-custom-task-pane-to-an-application"></a>Agregar un panel de tareas personalizado a una aplicación

### <a name="to-add-a-custom-task-pane-to-an-application"></a>Para agregar un panel de tareas personalizado a una aplicación

1. Abra o cree un proyecto de complemento de VSTO para una de las aplicaciones enumeradas anteriormente. Para obtener más información, [vea Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. En el menú **Proyecto** , haga clic en **Agregar control de usuario**.

3. En el **cuadro de diálogo Agregar** nuevo elemento , cambie el nombre del nuevo control de usuario a **MyUserControl** y, a continuación, haga clic **en Agregar**.

     Se abre el control de usuario en el diseñador.

4. Agregue uno o varios controles Windows Forms del cuadro **de herramientas** al control de usuario.

5. Abra el **archivo de código ThisAddIn.cs** **o ThisAddIn.vb.**

6. Agregue el siguiente código a la clase `ThisAddIn` . Este código declara instancias de `MyUserControl` y <xref:Microsoft.Office.Tools.CustomTaskPane> como miembros de la clase `ThisAddIn` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs" id="Snippet1":::

7. Agregue el código siguiente al controlador de eventos `ThisAddIn_Startup`. Este código crea un nuevo <xref:Microsoft.Office.Tools.CustomTaskPane> agregando el objeto `MyUserControl` a la colección `CustomTaskPanes` . El código también muestra el panel de tareas.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs" id="Snippet2":::

    > [!NOTE]
    > Este código asocia el panel de tareas personalizado a la ventana activa de la aplicación. En algunas aplicaciones, tal vez desee modificar este código para asegurarse de que el panel de tareas aparece con otros documentos o elementos de la aplicación. Para obtener más información, vea [Paneles de tareas personalizados.](../vsto/custom-task-panes.md)

## <a name="see-also"></a>Consulte también
- [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)
- [Paneles de tareas personalizados](../vsto/custom-task-panes.md)
- [Tutorial: Automatización de una aplicación desde un panel de tareas personalizado](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
