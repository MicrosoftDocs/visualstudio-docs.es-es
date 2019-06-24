---
title: Enlazar a datos del servicio en un proyecto de complemento de VSTO
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c6278e4e849d698097fe3760411a3121d977df07
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328854"
---
# <a name="walkthrough-bind-to-data-from-a-service-in-a-vsto-add-in-project"></a>Tutorial: Enlazar a datos desde un servicio en un proyecto de complemento VSTO
  Puede enlazar datos a controles host en proyectos de complemento de VSTO. Este tutorial muestra cómo agregar controles a un documento de Microsoft Office Word, enlazar los controles a los datos recuperados de MSDN Content Service y responder a eventos en tiempo de ejecución.

 **Se aplica a:** La información de este tema se aplica a los proyectos de nivel de aplicación para Word 2010. Para obtener más información, consulte [Características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).

 En este tutorial se muestran las tareas siguientes:

- Agregar un <xref:Microsoft.Office.Tools.Word.RichTextContentControl> control a un documento en tiempo de ejecución.

- Enlace el <xref:Microsoft.Office.Tools.Word.RichTextContentControl> control a los datos de un servicio web.

- Responder al evento <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> eventos de un control <xref:Microsoft.Office.Tools.Word.RichTextContentControl> .

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesita los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-a-new-project"></a>Crear un proyecto nuevo
 El primer paso es crear un proyecto de complemento de VSTO de Word.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de complemento VSTO de Word con el nombre **MTPS Content Service**mediante Visual Basic o C#.

     Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio abre el archivo `ThisAddIn.vb` o `ThisAddIn.cs` y agrega el proyecto al **Explorador de soluciones**.

## <a name="add-a-web-service"></a>Agregar un servicio web
 En este tutorial, utilice un servicio web denominado MTPS Content Service. Este servicio web devuelve información de un artículo MSDN especificado en forma de una cadena XML o texto sin formato. Un paso posterior muestra cómo mostrar la información devuelta en un control de contenido.

### <a name="to-add-the-mtps-content-service-to-the-project"></a>Para agregar el servicio de contenido de MTPS al proyecto

1. En el menú **Datos** , haga clic en **Agregar nuevo elemento**.

2. En el **Asistente para la configuración de orígenes de datos**, haga clic en **Servicio**y haga clic en **Siguiente**.

3. En el campo **Dirección** , escriba la dirección URL siguiente:

     **http://services.msdn.microsoft.com/ContentServices/ContentService.asmx**

4. Haga clic en **Ir**.

5. En el campo **Espacio de nombres** , escriba **ContentService**y haga clic en **Aceptar**.

6. En el cuadro de diálogo **Asistente para agregar referencias** , haga clic en **Finalizar**.

## <a name="add-a-content-control-and-bind-to-data-at-runtime"></a>Agregar un control de contenido y enlazar a datos en tiempo de ejecución
 En los proyectos de complemento VSTO, agregue y enlazar los controles en tiempo de ejecución. En este tutorial, configure el control content para recuperar datos desde el servicio web cuando un usuario hace clic dentro del control.

### <a name="to-add-a-content-control-and-bind-to-data"></a>Para agregar un control de contenido y enlazar a datos

1. En la clase `ThisAddIn` , declare las variables para el servicio de contenido de MTPS, el control de contenido y el enlace de datos.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#2)]

2. Agregue el método siguiente a la clase `ThisAddIn`. Este método crea un control content al principio del documento activo.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#4)]

3. Agregue el método siguiente a la clase `ThisAddIn`. Este método inicializa los objetos necesarios para crear y enviar una solicitud al servicio web.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#6)]

4. Cree un controlador de eventos para recuperar el documento de MSDN Library sobre controles content cuando un usuario hace clic dentro del control content y enlazar los datos al control de contenido.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#5)]

5. Llame a los métodos `AddRichTextControlAtRange` y `InitializeServiceObjects` desde el método `ThisAddIn_Startup` . Para programadores de C#, agregue un controlador de eventos.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#3)]

## <a name="test-the-add-in"></a>Probar el complemento
 Al abrir Word, aparecerá el control <xref:Microsoft.Office.Tools.Word.RichTextContentControl> . El texto del control cambia al hacer clic en él.

### <a name="to-test-the-vsto-add-in"></a>Para probar el complemento VSTO

1. Presione **F5**.

2. Haga clic dentro del control content.

     La información se descarga desde MTPS Content Service y se muestra dentro del control content.

## <a name="see-also"></a>Vea también
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
