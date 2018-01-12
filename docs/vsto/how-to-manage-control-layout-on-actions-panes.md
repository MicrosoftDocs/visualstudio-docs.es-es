---
title: "Cómo: administrar el diseño de controles en paneles de acciones | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7b70bf12ee608b28e462f022fae15b3be6336545
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Cómo: Administrar el diseño de controles en paneles de acciones
  Un panel de acciones se acopla a la derecha de un documento u hoja de cálculo de forma predeterminada; Sin embargo, se puede acoplar a la izquierda, superior o inferior. Si está utilizando varios controles de usuario, puede escribir código para apilar correctamente los controles de usuario en el panel Acciones. Para obtener más información, consulta [Actions Pane Overview](../vsto/actions-pane-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 El orden de apilamiento de los controles depende de si el panel de acciones está acoplado vertical u horizontalmente.  
  
> [!NOTE]  
>  Si el usuario cambia el tamaño del panel de acciones en tiempo de ejecución, puede establecer los controles que se va a cambiar el tamaño con el panel de acciones. Puede utilizar la propiedad <xref:System.Windows.Forms.Control.Anchor%2A> de un control de Windows Forms para anclar los controles al panel de acciones. Para obtener más información, consulte [Cómo: delimitar controles en formularios Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).  
  
> [!NOTE]  
>  Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Para establecer el orden de apilamiento de los controles de panel de acciones  
  
1.  Abra un proyecto de nivel de documento para Microsoft Office Word que incluye un panel de acciones con varios controles de usuario o controles del panel de acciones anidados. Para obtener más información, consulte [Cómo: agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
2.  Haga clic en **ThisDocument.cs** o **ThisDocument.vb** en **el Explorador de soluciones** y, a continuación, haga clic en **ver código**.  
  
3.  En el <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> controlador de eventos del panel de acciones, compruebe si la orientación del panel de acciones es horizontal.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]  
  
4.  Si la orientación es horizontal, apile los controles de panel de acciones desde la izquierda; en caso contrario, colóquelos en una pila de la parte superior.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]  
  
5.  En C#, debe agregar un controlador de eventos para el `ActionsPane` a la <xref:Microsoft.Office.Tools.Word.Document.Startup> controlador de eventos. Para obtener información acerca de cómo crear controladores de eventos, vea [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]  
  
6.  Ejecute el proyecto y compruebe que los controles del panel de acciones se apilan de izquierda a derecha cuando el panel de acciones está acoplado en la parte superior del documento y los controles están apilados de arriba a abajo cuando se acopla el panel de acciones en el lado derecho del documento.  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para este ejemplo se necesita:  
  
-   Controles de un proyecto de nivel de documento de Word con un panel de acciones que contiene varios controles de usuario o el panel de acciones anidados.  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md)   
 [Cómo: agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Cómo: agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Tutorial: Insertar texto en un documento de un panel de acciones](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Tutorial: Inserción de texto en un documento desde un panel de acciones](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  