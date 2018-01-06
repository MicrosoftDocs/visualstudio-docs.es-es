---
title: 'Tutorial: Insertar texto en un documento de un panel de acciones | Documentos de Microsoft'
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
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
ms.assetid: fd14c896-5737-4a20-94f7-6064b67112c5
caps.latest.revision: "70"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 789ad22524a5c0128320bfb833b8ad97e294a86f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-inserting-text-into-a-document-from-an-actions-pane"></a>Tutorial: Insertar texto en un documento de un panel de acciones
  Este tutorial muestra cómo crear un panel de acciones en un documento de Microsoft Office Word. El panel de acciones contiene dos controles que recopilan datos y, a continuación, envían el texto al documento.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Diseñar una interfaz mediante controles de formularios Windows Forms en un control de panel de acciones.  
  
-   Mostrar el panel de acciones cuando se abre la aplicación.  
  
> [!NOTE]  
>  Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Crear el proyecto  
 El primer paso es crear un proyecto de tipo Documento de Word.  
  
#### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto  
  
1.  Cree un proyecto de documento de Word con el nombre **Mi panel de acciones básico**. En el asistente, seleccione **crear un nuevo documento**. Para obtener más información, consulta [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo documento de Word en el diseñador y agrega el **Mi panel de acciones básico** proyecto al **el Explorador de soluciones**.  
  
## <a name="adding-text-and-bookmarks-to-the-document"></a>Agregar texto y marcadores al documento  
 El panel Acciones enviará el texto a marcadores del documento. Para diseñar el documento, escriba algún texto para crear un formulario básico.  
  
#### <a name="to-add-text-to-your-document"></a>Para agregar texto al documento  
  
1.  Escriba el siguiente texto en un documento de Word:  
  
     **21 de marzo de 2008**  
  
     **Name**  
  
     **Dirección**  
  
     **Este es un ejemplo de un panel de acciones básicas en Word.**  
  
 Puede agregar un <xref:Microsoft.Office.Tools.Word.Bookmark> control al documento arrastrándolo desde el **cuadro de herramientas** en Visual Studio o mediante la **marcador** cuadro de diálogo de Word.  
  
#### <a name="to-add-a-bookmark-control-to-your-document"></a>Para agregar un control Bookmark a documentos  
  
1.  Desde el **controles de Word** pestaña de la **cuadro de herramientas**, arrastre un <xref:Microsoft.Office.Tools.Word.Bookmark> control al documento.  
  
     El **agregar Control de marcador** aparece el cuadro de diálogo.  
  
2.  Seleccionar la palabra **nombre**, sin seleccionar la marca de párrafo y haga clic en **Aceptar**.  
  
    > [!NOTE]  
    >  La marca de párrafo debe estar fuera del marcador. Si las marcas de párrafo no son visibles en el documento, haga clic en el **herramientas** menú, elija **herramientas de Microsoft Office Word** y, a continuación, haga clic en **opciones**. Haga clic en el **vista** pestaña y seleccione la **marcas de párrafo** casilla de verificación en la **marcas de formato** sección de la **opciones** cuadro de diálogo.  
  
3.  En el **propiedades** ventana, cambiar la **nombre** propiedad de **Bookmark1** a **showName**.  
  
4.  Seleccionar la palabra **dirección**, sin seleccionar la marca de párrafo.  
  
5.  En el **insertar** ficha de la cinta de opciones, en el **vínculos** grupo, haga clic en **marcador**.  
  
6.  En el **marcador** cuadro de diálogo, escriba **showAddress** en el **nombre del marcador** y haga clic en **agregar**.  
  
## <a name="adding-controls-to-the-actions-pane"></a>Agregar controles al panel de acciones  
 Para diseñar la interfaz de panel de acciones, agregue un control de panel de acciones al proyecto y, a continuación, agregar controles de formularios Windows Forms al control del panel de acciones.  
  
#### <a name="to-add-an-actions-pane-control"></a>Para agregar un control de panel de acciones  
  
1.  Seleccione el **Mi panel de acciones básico** proyecto **el Explorador de soluciones**.  
  
2.  En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.  
  
3.  En el **Agregar nuevo elemento** cuadro de diálogo, haga clic en **Control del panel de acciones**, nombre del control **InsertTextControl,** y haga clic en **agregar**.  
  
#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Para agregar controles de formulario Windows Forms al control del panel de acciones  
  
1.  Si el control de panel de acciones no está visible en el diseñador, haga doble clic en **InsertTextControl**.  
  
2.  Desde el **controles comunes** pestaña de la **cuadro de herramientas**, arrastre un **etiqueta** hasta el control de panel de acciones.  
  
3.  Cambiar el **texto** propiedad del control Label a **nombre**.  
  
4.  Agregar un **Textbox** controlar al control del panel de acciones y cambie las siguientes propiedades.  
  
    |Property|Valor|  
    |--------------|-----------|  
    |**Name**|**getName**|  
    |**Size**|**130, 20**|  
  
5.  Agregue un segundo **etiqueta** controlar al control del panel de acciones y cambie la **texto** propiedad **dirección**.  
  
6.  Agregue un segundo **Textbox** controlar al control del panel de acciones y cambie las siguientes propiedades.  
  
    |Property|Valor|  
    |--------------|-----------|  
    |**Name**|**getAddress**|  
    |**Acepta el valor devuelto**|**True**|  
    |**Multiline**|**True**|  
    |**Size**|**130, 40**|  
  
7.  Agregar un **botón** controlar al control del panel de acciones y cambie las siguientes propiedades.  
  
    |Property|Valor|  
    |--------------|-----------|  
    |**Name**|**addText**|  
    |**Texto**|**Insertar**|  
  
## <a name="adding-code-to-insert-text-into-the-document"></a>Agregar código para insertar texto en el documento  
 En el panel Acciones, escriba código que inserta el texto de los cuadros de texto en la correspondiente <xref:Microsoft.Office.Tools.Word.Bookmark> controles en el documento. Puede usar el `Globals` clase para tener acceso a controles en el documento de los controles del panel de acciones. Para obtener más información, consulte [acceso Global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
#### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Para insertar texto en el panel de acciones en un marcador en el documento  
  
1.  Agregue el código siguiente a la <xref:System.Windows.Forms.Control.Click> controlador de eventos de la **addText** botón.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]  
  
2.  En C#, debe agregar un controlador de eventos para el clic de botón. Puede colocar este código en el `InsertTextControl` constructor después de llamar a `IntializeComponent`. Para obtener información acerca de cómo crear controladores de eventos, vea [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]  
  
## <a name="adding-code-to-show-the-actions-pane"></a>Agregar código para mostrar el panel de acciones  
 Para mostrar el panel Acciones, agregue el control que creó para la colección de controles.  
  
#### <a name="to-show-the-actions-pane"></a>Para mostrar el panel de acciones  
  
1.  Crear una nueva instancia del control del panel de acciones en el `ThisDocument` clase.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]  
  
2.  Agregue el código siguiente a la <xref:Microsoft.Office.Tools.Word.Document.Startup> controlador de eventos de `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]  
  
## <a name="testing-the-application"></a>Probar la aplicación  
 Probar el documento para comprobar que se abre el panel de acciones cuando se abre el documento y que el texto escrito en los cuadros de texto se inserta en los marcadores cuando se hace clic en el botón.  
  
#### <a name="to-test-your-document"></a>Para probar el documento  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Confirme que el panel de acciones esté visible.  
  
3.  Escriba su nombre y dirección en los cuadros de texto en el panel de acciones y haga clic en **insertar**.  
  
## <a name="next-steps"></a>Pasos siguientes  
 A continuación, podría realizar las siguientes tareas:  
  
-   Crear un panel de acciones en Excel. Para obtener más información, consulte [Cómo: agregar un panel de acciones a libros de Excel](http://msdn.microsoft.com/en-us/62abfce6-e44f-419d-85d8-26bf59f33872).  
  
-   Enlazar datos a controles en un panel de acciones. Para obtener más información, consulte [Tutorial: enlazar datos a controles en un panel de acciones de Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md)   
 [Cómo: agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Cómo: agregar un panel de acciones a libros de Excel](http://msdn.microsoft.com/en-us/62abfce6-e44f-419d-85d8-26bf59f33872)   
 [Cómo: administrar el diseño de controles en paneles de acciones](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Bookmark (Control)](../vsto/bookmark-control.md)  
  
  