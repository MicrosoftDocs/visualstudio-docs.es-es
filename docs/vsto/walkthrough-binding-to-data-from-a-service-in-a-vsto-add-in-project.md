---
title: "Tutorial: Establecer enlaces a datos de un servicio en un proyecto de complemento VSTO"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "bases de datos [desarrollo de Office en Visual Studio], desplazarse por registros"
  - "registros [desarrollo de Office en Visual Studio], desplazarse"
  - "datos [desarrollo de Office en Visual Studio], desplazarse por registros de bases de datos"
ms.assetid: 9b008be4-06a3-4ffc-9f02-79dd6cfe00ab
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Tutorial: Establecer enlaces a datos de un servicio en un proyecto de complemento VSTO
  Puede enlazar datos a controles host en proyectos de complemento de VSTO. Este tutorial muestra cómo agregar controles a un documento de Microsoft Office Word, enlazar los controles a los datos recuperados de MSDN Content Service y responder a eventos en tiempo de ejecución.  
  
 **Aplicación:** la información de este tema se aplica a los proyectos de nivel de aplicación de Word 2010. Para obtener más información, consulta [Características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Agregar un control <xref:Microsoft.Office.Tools.Word.RichTextContentControl> a un documento en tiempo de ejecución.  
  
-   Enlazar el control <xref:Microsoft.Office.Tools.Word.RichTextContentControl> a los datos de un servicio web.  
  
-   Responder al evento <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> eventos de un control <xref:Microsoft.Office.Tools.Word.RichTextContentControl>.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Crear un proyecto nuevo  
 El primer paso es crear un proyecto de complemento de VSTO de Word.  
  
#### Para crear un nuevo proyecto  
  
1.  Cree un proyecto de complemento VSTO de Word con el nombre **MTPS Content Service** mediante Visual Basic o C\#.  
  
     Para obtener más información, consulta [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el archivo `ThisAddIn.vb` o `ThisAddIn.cs` y agrega el proyecto al **Explorador de soluciones**.  
  
## Agregar un servicio web  
 Para este tutorial, use un servicio web denominado MTPS Content Service. Este servicio web devuelve información de un artículo MSDN especificado en forma de una cadena XML o texto sin formato. Un paso posterior muestra cómo mostrar la información devuelta en un control de contenido.  
  
#### Para agregar el servicio de contenido de MTPS al proyecto  
  
1.  En el menú **Datos**, haga clic en **Agregar nuevo elemento**.  
  
2.  En el **Asistente para la configuración de orígenes de datos**, haga clic en **Servicio** y haga clic en **Siguiente**.  
  
3.  En el campo **Dirección**, escriba la dirección URL siguiente:  
  
     **http:\/\/services.msdn.microsoft.com\/ContentServices\/ContentService.asmx**  
  
4.  Haga clic en **Ir**.  
  
5.  En el campo **Espacio de nombres**, escriba **ContentService** y haga clic en **Aceptar**.  
  
6.  En el cuadro de diálogo **Asistente para agregar referencias**, haga clic en **Finalizar**.  
  
## Agregar un control de contenido y enlazarlo a datos en tiempo de ejecución  
 En proyectos de complemento VSTO, se agregan y se enlazan controles en tiempo de ejecución. En este tutorial, configure el control content para recuperar datos desde el servicio web cuando un usuario hace clic dentro del control.  
  
#### Para agregar un control de contenido y enlazar a datos  
  
1.  En la clase `ThisAddIn`, declare las variables para el servicio de contenido de MTPS, el control de contenido y el enlace de datos.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#2)]  
  
2.  Agregue el método siguiente a la clase `ThisAddIn`. Este método crea un control content al principio del documento activo.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#4)]  
  
3.  Agregue el método siguiente a la clase `ThisAddIn`. Este método inicializa los objetos necesarios para crear y enviar una solicitud al servicio web.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#6)]  
  
4.  Cree un controlador de eventos para recuperar el documento de MSDN Library sobre controles content cuando un usuario hace clic dentro del control content y enlazar los datos al control de contenido.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#5)]  
  
5.  Llame a los métodos `AddRichTextControlAtRange` y `InitializeServiceObjects` desde el método `ThisAddIn_Startup`. Para programadores de C\#, agregue un controlador de eventos.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#3)]  
  
## Probar el complemento  
 Al abrir Word, aparecerá el control <xref:Microsoft.Office.Tools.Word.RichTextContentControl>. El texto del control cambia al hacer clic en él.  
  
#### Para probar el complemento VSTO  
  
1.  Presione **F5**.  
  
2.  Haga clic dentro del control content.  
  
     La información se descarga desde MTPS Content Service y se muestra dentro del control content.  
  
## Vea también  
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  