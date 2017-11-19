---
title: "Tutorial: Actualizar un gráfico en un documento utilizando botones de Radio | Documentos de Microsoft"
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
- documents [Office development in Visual Studio], updating using controls
- controls [Office development in Visual Studio], updating documents
ms.assetid: 56e6d1f2-65a4-41f0-aff5-f0cfd96d7185
caps.latest.revision: "60"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2d6fa02174a8b334b404a0a4ea84ee0e8089c584
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-updating-a-chart-in-a-document-using-radio-buttons"></a>Tutorial: Actualizar un gráfico en un documento utilizando botones de radio
  En este tutorial se demuestra cómo usar los botones de radio en una personalización de nivel de documento para Microsoft Office Word a fin de ofrecer a los usuarios la opción de seleccionar estilos de gráfico en el documento.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Agregar un gráfico al documento en un proyecto de nivel de documento en tiempo de diseño.  
  
-   Agrupar botones de radio agregándolos a un control de usuario.  
  
-   Cambiar el estilo del gráfico cuando se selecciona una opción.  
  
 Para ver el resultado como un ejemplo completo, vea el ejemplo de controles de Word en [ejemplos de desarrollo de Office y tutoriales](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Crear el proyecto  
 El primer paso es crear un proyecto de tipo Documento de Word.  
  
#### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto  
  
1.  Cree un proyecto de documento de Word con el nombre **Mis opciones de gráfico**. En el asistente, seleccione **crear un nuevo documento**. Para obtener más información, consulta [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo documento de Word en el diseñador y agrega el **Mis opciones de gráfico** proyecto al **el Explorador de soluciones**.  
  
## <a name="adding-a-chart-to-the-document"></a>Agregar un gráfico al documento  
  
#### <a name="to-add-a-chart"></a>Para agregar un gráfico  
  
1.  En el documento de Word que se hospeda en el Diseñador de Visual Studio, en la cinta de opciones, haga clic en el **insertar** ficha.  
  
2.  En el **texto** grupo, haga clic en el **Insertar objeto** botón de lista desplegable y haga clic en **objeto**.  
  
     El **objeto** abre el cuadro de diálogo.  
  
3.  En el **tipo de objeto** lista el **crear nuevo** ficha, seleccione **gráfico de Microsoft Graph** y, a continuación, haga clic en **Aceptar**.  
  
     Se agrega un gráfico al documento en el punto de inserción y el **hoja de datos** ventana aparece con algunos datos predeterminados.  
  
4.  Cerrar la **hoja de datos** ventana para aceptar los valores predeterminados en el gráfico y hacer clic en el documento que se va a mover el foco fuera del gráfico.  
  
5.  Haga clic en el gráfico y, a continuación, haga clic en **formato de objeto**.  
  
6.  En el **diseño** pestaña de la **formato de objeto** cuadro de diálogo, seleccione **cuadrado** y haga clic en **Aceptar**.  
  
## <a name="adding-a-user-control-to-the-project"></a>Agregar un control de usuario al proyecto  
 De manera predeterminada, los botones de radio de un documento no se excluyen mutuamente. Puede hacer que funcionen correctamente si los agrega a un control de usuario y luego escribe código para controlar la selección.  
  
#### <a name="to-add-a-user-control"></a>Para agregar un control de usuario  
  
1.  Seleccione el **Mis opciones de gráfico** proyecto **el Explorador de soluciones**.  
  
2.  En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.  
  
3.  En el **Agregar nuevo elemento** cuadro de diálogo, haga clic en **Control de usuario**, nombre del control **ChartOptions** y haga clic en **agregar**.  
  
#### <a name="to-add-windows-form-controls-to-the-user-control"></a>Para agregar controles de Windows Forms al control de usuario  
  
1.  Si el control de usuario no está visible en el diseñador, haga doble clic en **ChartOptions** en **el Explorador de soluciones**.  
  
2.  Desde el **controles comunes** pestaña de la **cuadro de herramientas**, arrastre el primer **botón de Radio** controlar al control de usuario y cambie las siguientes propiedades.  
  
    |Propiedad|Valor|  
    |--------------|-----------|  
    |**Nombre**|**columnChart**|  
    |**Texto**|**Gráfico de columnas**|  
  
3.  Agregue un segundo **botón de Radio** al usuario controlar y cambiar las propiedades siguientes.  
  
    |Propiedad|Valor|  
    |--------------|-----------|  
    |**Nombre**|**barChart**|  
    |**Texto**|**Gráfico de barras**|  
  
4.  Agregue un tercer **botón de Radio** al usuario controlar y cambiar las propiedades siguientes.  
  
    |Propiedad|Valor|  
    |--------------|-----------|  
    |**Nombre**|**lineChart**|  
    |**Texto**|**Gráfico de líneas**|  
  
5.  Agregue un cuarto **botón de Radio** al usuario controlar y cambiar las propiedades siguientes.  
  
    |Propiedad|Valor|  
    |--------------|-----------|  
    |**Nombre**|**areaBlockChart**|  
    |**Texto**|**Gráfico de bloques de áreas**|  
  
## <a name="adding-references"></a>Agregar referencias  
 Para obtener acceso al gráfico desde el control de usuario en un documento, debe tener una referencia al ensamblado Microsoft.Office.Interop.Graph en el proyecto.  
  
#### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>Para agregar una referencia al ensamblado Microsoft.Office.Interop.Graph  
  
1.  En el menú **Proyecto**, haga clic en **Agregar referencia**.  
  
     Aparecerá el cuadro de diálogo **Agregar referencia**.  
  
2.  En el **.NET** ficha, seleccione **Microsoft.Office.Interop.Graph** y haga clic en **Aceptar**. Seleccione la versión 14.0.0.0 del ensamblado.  
  
## <a name="changing-the-chart-style-when-a-radio-button-is-selected"></a>Cambiar el estilo del gráfico cuando se selecciona un botón de radio  
 Para que los botones funcionen correctamente, cree un evento público en el control de usuario, agregue una propiedad para establecer el tipo de selección y cree un procedimiento para el evento `CheckedChanged` de cada uno de los botones de radio.  
  
#### <a name="to-create-an-event-and-property-on-a-user-control"></a>Para crear un evento y una propiedad en un control de usuario  
  
1.  En **el Explorador de soluciones**, haga clic en el control de usuario y, a continuación, haga clic en **ver código**.  
  
2.  Agregue código para crear un evento `SelectionChanged` y la propiedad `Selection` de la clase `ChartOptions`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#9)]  
  
#### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>Para controlar el evento CheckedChange de los botones de radio  
  
1.  Establezca el tipo de gráfico en el controlador de eventos `CheckedChanged` del botón de radio `areaBlockChart` y, a continuación, genere el evento.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#10)]  
  
2.  Establezca el tipo de gráfico en el controlador de eventos `CheckedChanged` del botón de radio `barChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#11)]  
  
3.  Establezca el tipo de gráfico en el controlador de eventos `CheckedChanged` del botón de radio `columnChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#12)]  
  
4.  Establezca el tipo de gráfico en el controlador de eventos `CheckedChanged` del botón de radio `lineChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#13)]  
  
5.  En C#, debe agregar controladores de eventos para los botones de radio. Puede agregar el código al constructor `ChartOptions`, debajo de la llamada a `InitializeComponent`. Para obtener información acerca de cómo crear controladores de eventos, vea [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#14)]  
  
## <a name="adding-the-user-control-to-the-document"></a>Agregar el control de usuario al documento  
 Cuando se compila la solución, el nuevo control de usuario se agrega automáticamente a la **cuadro de herramientas**. A continuación, puede arrastrar el control desde el **cuadro de herramientas** al documento.  
  
#### <a name="to-add-the-user-control-your-document"></a>Para agregar el control de usuario al documento  
  
1.  En el menú **Compilar** , haga clic en **Compilar solución**.  
  
     El **ChartOptions** control de usuario se agrega a la **cuadro de herramientas**.  
  
2.  En **el Explorador de soluciones**, haga clic en **ThisDocument.vb** o **ThisDocument.cs**y, a continuación, haga clic en **Diseñador de vistas**.  
  
3.  Arrastre el `ChartOptions` controlar desde la **cuadro de herramientas** al documento.  
  
     En el **propiedades** ventana, el nombre del control que se ha agregado al documento `ChartOptions1`.  
  
## <a name="changing-the-chart-type"></a>Cambiar el tipo de gráfico  
 Cree un controlador de eventos para cambiar el tipo de gráfico según la opción que se seleccione en el control de usuario.  
  
#### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>Para cambiar el tipo de gráfico que se muestra en el documento  
  
1.  Agregue el siguiente controlador de eventos a la clase `ThisDocument`.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#15)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#15)]  
  
2.  En C#, debe agregar un controlador de eventos para el control de usuario al evento <xref:Microsoft.Office.Tools.Word.Document.Startup>.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#16)]  
  
## <a name="testing-the-application"></a>Probar la aplicación  
 Ahora puede probar el documento para asegurarse de que el estilo del gráfico se actualiza correctamente al seleccionar un botón de radio.  
  
#### <a name="to-test-your-document"></a>Para probar el documento  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Seleccione varios botones de radio.  
  
3.  Confirme que el estilo del gráfico cambia para coincidir con la selección.  
  
## <a name="next-steps"></a>Pasos siguientes  
 A continuación, podría realizar las siguientes tareas:  
  
-   Usar un botón para rellenar un cuadro de texto. Para obtener más información, consulte [Tutorial: mostrar texto en un cuadro de texto en un documento utilizando un botón](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Cambiar el formato por medio de la selección de un estilo de un cuadro combinado. Para obtener más información, consulte [Tutorial: Cambiar documento formato utilizando controles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Vea también  
 [Tutoriales para Word](../vsto/walkthroughs-using-word.md)   
 [Tutoriales y ejemplos de desarrollo de office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Limitaciones de los controles de Windows Forms en los documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  