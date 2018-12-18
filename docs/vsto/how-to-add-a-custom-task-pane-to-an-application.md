---
title: 'Cómo: agregar un panel de tareas personalizado a una aplicación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], adding to application
- custom task panes [Office development in Visual Studio], adding to application
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b8608fcc263be4750c38b6fe3f84967f40dd34ab
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548819"
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>Cómo: agregar un panel de tareas personalizado a una aplicación
  Puede agregar un panel de tareas personalizado a las aplicaciones enumeradas anteriormente mediante el complemento de VSTO. Para obtener más información, consulte [paneles de tareas personalizados](../vsto/custom-task-panes.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="add-a-custom-task-pane-to-an-application"></a>Agregar un panel de tareas personalizado a una aplicación  
  
### <a name="to-add-a-custom-task-pane-to-an-application"></a>Para agregar un panel de tareas personalizado a una aplicación  
  
1.  Abra o cree un proyecto de complemento de VSTO para una de las aplicaciones enumeradas anteriormente. Para obtener más información, consulte [Cómo: proyectos de Office crear en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  En el menú **Proyecto** , haga clic en **Agregar control de usuario**.  
  
3.  En el **Agregar nuevo elemento** diálogo cuadro, cambie el nombre del nuevo control de usuario a **MyUserControl**y, a continuación, haga clic en **agregar**.  
  
     Se abre el control de usuario en el diseñador.  
  
4.  Agregar uno o más controles de formularios Windows Forms desde la **cuadro de herramientas** al control de usuario.  
  
5.  Abra la **ThisAddIn.cs** o **ThisAddIn.vb** archivo de código.  
  
6.  Agregue el código siguiente a la clase `ThisAddIn` . Este código declara instancias de `MyUserControl` y <xref:Microsoft.Office.Tools.CustomTaskPane> como miembros de la clase `ThisAddIn` .  
  
     [!code-vb[Trin_TaskPaneBasic#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#1)]
     [!code-csharp[Trin_TaskPaneBasic#1](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#1)]  
  
7.  Agregue el código siguiente al controlador de eventos `ThisAddIn_Startup`. Este código crea un nuevo <xref:Microsoft.Office.Tools.CustomTaskPane> agregando el objeto `MyUserControl` a la colección `CustomTaskPanes`. El código también muestra el panel de tareas.  
  
     [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
     [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]  
  
    > [!NOTE]  
    >  Este código asocia el panel de tareas personalizado a la ventana activa de la aplicación. En algunas aplicaciones, tal vez desee modificar este código para asegurarse de que el panel de tareas aparece con otros documentos o elementos de la aplicación. Para obtener más información, consulte [paneles de tareas personalizados](../vsto/custom-task-panes.md).  
  
## <a name="see-also"></a>Vea también  
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [Paneles de tareas personalizados](../vsto/custom-task-panes.md)   
 [Tutorial: Automatizar una aplicación desde un panel de tareas personalizado](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)  
  
  