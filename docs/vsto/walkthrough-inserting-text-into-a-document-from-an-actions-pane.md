---
title: 'Tutorial: Insertar texto en un documento desde un panel de acciones'
description: Cree un panel de acciones en un documento de Microsoft Word. Obtenga información sobre que el panel de acciones contiene dos controles que recopilan entradas y, a continuación, envían el texto al documento.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1ac42954e32b30a293abbe031218213948fb103a
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824983"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>Tutorial: Insertar texto en un documento desde un panel de acciones
  En este tutorial se muestra cómo crear un panel de acciones en un Microsoft Office word. El panel de acciones contiene dos controles que recopilan la entrada y, a continuación, envían el texto al documento.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Diseñe una interfaz mediante Windows Forms controles en un control del panel de acciones.

- Muestra el panel de acciones cuando se abre la aplicación.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Creación del proyecto
 El primer paso es crear un proyecto de tipo Documento de Word.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de documento de Word con el nombre **Panel Mis acciones básicas**. En el asistente, seleccione **Crear un nuevo documento.** Para obtener más información, [vea Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio el nuevo documento de Word en el diseñador y agrega el **proyecto Panel** Mis acciones básicas **a Explorador de soluciones**.

## <a name="add-text-and-bookmarks-to-the-document"></a>Agregar texto y marcadores al documento
 El panel de acciones enviará texto a los marcadores del documento. Para diseñar el documento, escriba texto para crear un formulario básico.

### <a name="to-add-text-to-your-document"></a>Para agregar texto al documento

1. Escriba el texto siguiente en el documento de Word:

    **21 de marzo de 2008**

    **Nombre**

    **Dirección**

    **Este es un ejemplo de un panel de acciones básicas en Word.**

   Puede agregar un control al documento arrastrándolo desde el cuadro de herramientas de Visual Studio o mediante el cuadro de diálogo <xref:Microsoft.Office.Tools.Word.Bookmark> Marcador de Word.  

### <a name="to-add-a-bookmark-control-to-your-document"></a>Para agregar un control Bookmark al documento

1. En la **pestaña Controles de** Word del Cuadro de **herramientas,** arrastre <xref:Microsoft.Office.Tools.Word.Bookmark> un control al documento.

     Aparece **el cuadro de diálogo Agregar control** marcador .

2. Seleccione la palabra **Nombre** sin seleccionar la marca de párrafo y haga clic en **Aceptar.**

    > [!NOTE]
    > La marca de párrafo debe estar fuera del marcador. Si las marcas de párrafo no  están visibles en el documento, haga clic en el menú Herramientas, seleccione Microsoft Office **Word Tools** y, a continuación, haga clic en **Opciones.** Haga clic **en la pestaña** Ver y active la casilla Marcas **de** párrafo en la sección Marcas **de formato** del cuadro **de diálogo** Opciones .

3. En la **ventana Propiedades,** cambie la **propiedad Name** de **Bookmark1** a **showName.**

4. Seleccione la palabra **Dirección** sin seleccionar la marca de párrafo.

5. En la **pestaña Insertar** de la cinta de opciones, en el grupo **Vínculos,** haga clic en **Marcador**.

6. En el **cuadro de** diálogo Marcador , escriba **showAddress** en el **cuadro Nombre del** marcador y haga clic en **Agregar**.

## <a name="add-controls-to-the-actions-pane"></a>Agregar controles al panel de acciones
 Para diseñar la interfaz del panel de acciones, agregue un control de panel de acciones al proyecto y, a continuación, agregue Windows Forms controles al control del panel de acciones.

### <a name="to-add-an-actions-pane-control"></a>Para agregar un control de panel de acciones

1. Seleccione el **proyecto My Basic Actions Pane (Mis** acciones básicas) **Explorador de soluciones**.

2. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

3. En el cuadro **de diálogo Agregar** nuevo elemento , haga clic en Control **panel** Acciones , asigne al control el nombre **InsertTextControl y haga** clic en **Agregar**.

#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Para agregar controles de Windows Forms al control del panel de acciones

1. Si el control del panel de acciones no está visible en el diseñador, haga doble clic **en InsertTextControl**.

2. En la **pestaña Controles comunes** del Cuadro de **herramientas**, arrastre un control **Etiqueta** al control del panel de acciones.

3. Cambie la **propiedad Text** del control Etiqueta a **Nombre.**

4. Agregue un **control Cuadro de** texto al control del panel de acciones y cambie las siguientes propiedades.

    |Propiedad|Value|
    |--------------|-----------|
    |**Nombre**|**getName**|
    |**Tamaño**|**130, 20**|

5. Agregue un segundo control **Etiqueta** al control del panel de acciones y cambie la **propiedad Texto** a **Dirección**.

6. Agregue un segundo control **Cuadro de** texto al control del panel de acciones y cambie las siguientes propiedades.

    |Propiedad|Value|
    |--------------|-----------|
    |**Nombre**|**getAddress**|
    |**Acepta devolución**|**True**|
    |**Multiline**|**True**|
    |**Tamaño**|**130, 40**|

7. Agregue un **control Botón** al control del panel de acciones y cambie las siguientes propiedades.

    |Propiedad|Value|
    |--------------|-----------|
    |**Nombre**|**addText**|
    |**Texto**|**Insertar**|

## <a name="add-code-to-insert-text-into-the-document"></a>Agregar código para insertar texto en el documento
 En el panel de acciones, escriba código que inserte el texto de los cuadros de texto en los <xref:Microsoft.Office.Tools.Word.Bookmark> controles adecuados del documento. Puede usar la clase `Globals` para tener acceso a los controles del documento desde los controles del panel de acciones. Para obtener más información, vea [Acceso global a objetos en proyectos de Office.](../vsto/global-access-to-objects-in-office-projects.md)

### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Para insertar texto desde el panel de acciones en un marcador del documento

1. Agregue el código siguiente al controlador <xref:System.Windows.Forms.Control.Click> de eventos del botón **addText.**

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb" id="Snippet8":::

2. En C#, debe agregar un controlador de eventos para el clic de botón. Puede colocar este código en el `InsertTextControl` constructor después de llamar a `InitializeComponent` . Para obtener información sobre cómo crear controladores de eventos, [vea Cómo: Crear controladores de eventos en proyectos de Office.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs" id="Snippet9":::

## <a name="add-code-to-show-the-actions-pane"></a>Agregar código para mostrar el panel de acciones
 Para mostrar el panel de acciones, agregue el control que creó a la colección de controles.

### <a name="to-show-the-actions-pane"></a>Para mostrar el panel de acciones

1. Cree una nueva instancia del control del panel de acciones en la `ThisDocument` clase .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet10":::

2. Agregue el código siguiente al controlador <xref:Microsoft.Office.Tools.Word.Document.Startup> de eventos de `ThisDocument` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet11":::

## <a name="test-the-application"></a>Prueba de la aplicación
 Pruebe el documento para comprobar que el panel de acciones se abre cuando se abre el documento y que el texto escrito en los cuadros de texto se inserta en los marcadores cuando se hace clic en el botón.

### <a name="to-test-your-document"></a>Para probar el documento

1. Presione **F5** para ejecutar el proyecto.

2. Confirme que el panel de acciones está visible.

3. Escriba su nombre y dirección en los cuadros de texto del panel de acciones y haga clic **en Insertar.**

## <a name="next-steps"></a>Pasos siguientes
 A continuación, podría realizar las siguientes tareas:

- Cree un panel de acciones en Excel. Para obtener más información, [vea Cómo: Agregar un panel de acciones a libros de Excel.](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))

- Enlazar datos a controles en un panel de acciones. Para obtener más información, vea [Tutorial: Enlazar datos a controles en un panel de acciones de Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).

## <a name="see-also"></a>Consulte también
- [Información general del panel Acciones](../vsto/actions-pane-overview.md)
- [Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Cómo: Agregar un panel de acciones a libros de Excel](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))
- [Cómo: Administrar el diseño de control en los paneles de acciones](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Bookmark (control)](../vsto/bookmark-control.md)
