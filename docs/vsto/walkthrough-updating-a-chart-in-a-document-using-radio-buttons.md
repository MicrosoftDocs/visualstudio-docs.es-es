---
title: "Tutorial: Actualizar un gr&#225;fico en un documento utilizando botones de radio | Microsoft Docs"
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
  - "controles [desarrollo de Office en Visual Studio], actualizar documentos"
  - "documentos [desarrollo de Office en Visual Studio], actualizar utilizando controles"
ms.assetid: 56e6d1f2-65a4-41f0-aff5-f0cfd96d7185
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# Tutorial: Actualizar un gr&#225;fico en un documento utilizando botones de radio
  En este tutorial se demuestra cómo usar los botones de radio en una personalización de nivel de documento para Microsoft Office Word a fin de ofrecer a los usuarios la opción de seleccionar estilos de gráfico en el documento.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Agregar un gráfico al documento en un proyecto de nivel de documento en tiempo de diseño.  
  
-   Agrupar botones de radio agregándolos a un control de usuario.  
  
-   Cambiar el estilo del gráfico cuando se selecciona una opción.  
  
 Para ver el resultado como ejemplo completado, vea el ejemplo de controles de Word en [Ejemplos y tutoriales del desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Crear el proyecto  
 El primer paso es crear un proyecto de tipo Documento de Word.  
  
#### Para crear un nuevo proyecto  
  
1.  Cree un proyecto de Documento de Word con el nombre **Mis opciones de gráfico**.  En el asistente, seleccione **Crear un nuevo documento**.  Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo documento de Word en el diseñador y agrega el proyecto **Mis opciones de gráfico** al **Explorador de soluciones**.  
  
## Agregar un gráfico al documento  
  
#### Para agregar un gráfico  
  
1.  En el documento de Word hospedado en el diseñador de Visual Studio, en la cinta, haga clic en la pestaña **Insertar**.  
  
2.  En el grupo **Texto**, haga clic en el botón desplegable **Insertar objeto** y haga clic en **Objeto**.  
  
     Se abrirá el cuadro de diálogo **Objeto**.  
  
3.  En la lista **Tipo de objeto** de la pestaña **Crear nuevo**, seleccione **Gráfico de Microsoft Graph** y, a continuación, haga clic en **Aceptar**.  
  
     Se agrega un gráfico al documento en el punto de inserción y aparece la ventana **Hoja de datos** con datos predeterminados.  
  
4.  Cierre la ventana **Hoja de datos** para aceptar los valores predeterminados del gráfico y haga clic dentro del documento para alejar el foco del gráfico.  
  
5.  Haga clic con el botón secundario en el gráfico y, a continuación, haga clic en **Formato de objeto**.  
  
6.  En la pestaña **Diseño** del cuadro de diálogo **Formato de objeto**, seleccione **Cuadrado** y haga clic en **Aceptar**.  
  
## Agregar un control de usuario al proyecto  
 De manera predeterminada, los botones de radio de un documento no se excluyen mutuamente.  Puede hacer que funcionen correctamente si los agrega a un control de usuario y luego escribe código para controlar la selección.  
  
#### Para agregar un control de usuario  
  
1.  Seleccione el proyecto **Mis opciones de gráfico** en el **Explorador de soluciones**.  
  
2.  En el menú **Proyecto**, haga clic en **Agregar nuevo elemento**.  
  
3.  En el cuadro de diálogo **Agregar nuevo elemento**, haga clic en **Control de usuario**, asigne el nombre **ChartOptions** al control y haga clic en **Agregar**.  
  
#### Para agregar controles de Windows Forms al control de usuario  
  
1.  Si el control de usuario no está visible en el diseñador, haga doble clic en **ChartOptions** en el **Explorador de soluciones**.  
  
2.  Desde la pestaña **Controles comunes** del **Cuadro de herramientas**, arrastre el primer control **Botón de radio** al control de usuario y cambie las propiedades siguientes.  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**Nombre**|**columnChart**|  
    |**Text**|Gráfico de columnas|  
  
3.  Agregue un segundo **Botón de radio** al control de usuario y cambie las siguientes propiedades.  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**Nombre**|**barChart**|  
    |**Text**|Gráfico de barras|  
  
4.  Agregue un tercer **Botón de radio** al control de usuario y cambie las siguientes propiedades.  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**Nombre**|**lineChart**|  
    |**Text**|Gráfico de líneas|  
  
5.  Agregue un cuarto **Botón de radio** al control de usuario y cambie las siguientes propiedades.  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**Nombre**|**areaBlockChart**|  
    |**Text**|Gráfico de bloques de áreas|  
  
## Agregar referencias  
 Para obtener acceso al gráfico desde el control de usuario en un documento, debe tener una referencia al ensamblado Microsoft.Office.Interop.Graph en el proyecto.  
  
#### Para agregar una referencia al ensamblado Microsoft.Office.Interop.Graph  
  
1.  En el menú **Proyecto**, haga clic en **Agregar referencia**.  
  
     Aparecerá el cuadro de diálogo **Agregar referencia**.  
  
2.  En la pestaña **.NET**, seleccione **Microsoft.Office.Interop.Graph** y haga clic en **Aceptar**.  Seleccione la versión 14.0.0.0 del ensamblado.  
  
## Cambiar el estilo del gráfico cuando se selecciona un botón de radio  
 Para que los botones funcionen correctamente, cree un evento público en el control de usuario, agregue una propiedad para establecer el tipo de selección y cree un procedimiento para el evento `CheckedChanged` de cada uno de los botones de radio.  
  
#### Para crear un evento y una propiedad en un control de usuario  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en el control de usuario y, a continuación, haga clic en **Ver código**.  
  
2.  Agregue código para crear un evento `SelectionChanged` y la propiedad `Selection` de la clase `ChartOptions`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#9)]  
  
#### Para controlar el evento CheckedChange de los botones de radio  
  
1.  Establezca el tipo de gráfico en el controlador de eventos `CheckedChanged` del botón de radio `areaBlockChart` y, a continuación, genere el evento.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#10)]  
  
2.  Establezca el tipo de gráfico en el controlador de eventos `CheckedChanged` del botón de radio `barChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#11)]  
  
3.  Establezca el tipo de gráfico en el controlador de eventos `CheckedChanged` del botón de radio `columnChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#12)]  
  
4.  Establezca el tipo de gráfico en el controlador de eventos `CheckedChanged` del botón de radio `lineChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#13)]  
  
5.  En C\#, debe agregar controladores de eventos para los botones de radio.  Puede agregar el código al constructor `ChartOptions`, debajo de la llamada a `InitializeComponent`.  Para obtener información acerca de la creación de controladores de eventos, vea [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#14)]  
  
## Agregar el control de usuario al documento  
 Cuando compila la solución, el nuevo control de usuario se agrega automáticamente al **Cuadro de herramientas**.  A continuación, puede arrastrar el control desde el **Cuadro de herramientas** al documento.  
  
#### Para agregar el control de usuario al documento  
  
1.  En el menú **Compilar**, haga clic en **Compilar solución**.  
  
     El control **ChartOptions** se ha agregado al **Cuadro de herramientas**.  
  
2.  En el **Explorador de soluciones**, haga clic con el botón derecho en **ThisDocument.vb** o **ThisDocument.cs** y luego haga clic en **Diseñador de vistas**.  
  
3.  Arrastre el control `ChartOptions` del **Cuadro de herramientas** al documento.  
  
     En la ventana **Propiedades**, dé el nombre `ChartOptions1` al control que acaba de agregar al documento.  
  
## Cambiar el tipo de gráfico  
 Cree un controlador de eventos para cambiar el tipo de gráfico según la opción que se seleccione en el control de usuario.  
  
#### Para cambiar el tipo de gráfico que se muestra en el documento  
  
1.  Agregue el siguiente controlador de eventos a la clase `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#15)]  
  
2.  En C\#, debe agregar un controlador de eventos para el control de usuario al evento <xref:Microsoft.Office.Tools.Word.Document.Startup>.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#16)]  
  
## Probar la aplicación  
 Ahora puede probar el documento para asegurarse de que el estilo del gráfico se actualiza correctamente al seleccionar un botón de radio.  
  
#### Para probar el documento  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Seleccione varios botones de radio.  
  
3.  Confirme que el estilo del gráfico cambia para coincidir con la selección.  
  
## Pasos siguientes  
 A continuación, podría realizar las siguientes tareas:  
  
-   Usar un botón para rellenar un cuadro de texto.  Para obtener más información, vea [Tutorial: Mostrar texto en un cuadro de texto en un documento utilizando un botón](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Cambiar el formato por medio de la selección de un estilo de un cuadro combinado.  Para obtener más información, vea [Tutorial: Cambiar el formato de un documento utilizando controles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## Vea también  
 [Tutoriales para Word](../vsto/walkthroughs-using-word.md)   
 [Ejemplos y tutoriales del desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Limitaciones de los controles de formularios Windows Forms en los documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  