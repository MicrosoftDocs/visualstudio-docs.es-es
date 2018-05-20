---
title: 'Tutorial: Cambiar el formato de un documento utilizando controles CheckBox'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word documents, changing formatting using controls
- documents [Office development in Visual Studio], formatting
- check boxes, Word documents
- documents [Office development in Visual Studio], check box controls
- controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 459253c6a84add4fcca68565d5bf082dc0931f22
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>Tutorial: Cambiar el formato de un documento utilizando controles CheckBox
  Este tutorial muestra cómo usar controles de formularios Windows Forms en una personalización de nivel de documento para Microsoft Office Word para cambiar el formato de texto.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Agregar texto y un control al documento en un proyecto de nivel de documento en tiempo de diseño.  
  
-   Dar formato al texto cuando se selecciona una opción.  
  
 Para ver el resultado como un ejemplo completo, vea el ejemplo de controles de Word en [tutoriales y ejemplos de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="create-the-project"></a>Crear el proyecto  
 El primer paso es crear un proyecto de tipo Documento de Word.  
  
### <a name="create-a-new-project"></a>Crear un proyecto nuevo  
  
1.  Cree un proyecto de documento de Word con el nombre **Mi formato de Word**. En el asistente, seleccione **crear un nuevo documento**.  
  
     Para obtener más información, consulte [Cómo: proyectos de Office crear en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo documento de Word en el diseñador y agrega el **Mi formato de Word** proyecto al **el Explorador de soluciones**.  
  
## <a name="add-text-and-controls-to-the-word-document"></a>Agregar texto y controles al documento de Word  
 En este tutorial, agregue tres casillas y algo de texto en un <xref:Microsoft.Office.Tools.Word.Bookmark> control al documento de Word. Las casillas de verificación presentará opciones al usuario para dar formato al texto.  
  
### <a name="add-three-check-boxes"></a>Agregar tres casillas de verificación  
  
1.  Compruebe que el documento esté abierto en el diseñador de Visual Studio.  
  
2.  Desde el **controles comunes** pestaña de la **cuadro de herramientas**, arrastre el primer <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> control al documento.  
  
3.  En la ventana **Propiedades** , cambie las siguientes propiedades:  
  
    |Property|Valor|  
    |--------------|-----------|  
    |**Name**|**applyBoldFont**|  
    |**Texto**|**Negrita**|  
  
4.  Presione **ENTRAR** para mover el punto de inserción por debajo de la primera casilla de verificación.  
  
5.  Agregar una segunda casilla al documento debajo la `ApplyBoldFont` casilla de verificación y cambie las siguientes propiedades.  
  
    |Property|Valor|  
    |--------------|-----------|  
    |**Name**|**applyItalicFont**|  
    |**Texto**|**cursiva**|  
  
6.  Presione **ENTRAR** para mover el punto de inserción por debajo de la casilla correspondiente al segundo.  
  
7.  Agregue una tercera casilla al documento debajo la `ApplyItalicFont` casilla de verificación y cambie las siguientes propiedades.  
  
    |Property|Valor|  
    |--------------|-----------|  
    |**Name**|**applyUnderlineFont**|  
    |**Texto**|**subrayado**|  
  
### <a name="add-text-and-a-bookmark-control"></a>Agregar texto y un control Bookmark  
  
1.  Mover el punto de inserción debajo de los controles de casilla de verificación y escriba el texto siguiente:  
  
     **Haga clic en una casilla de verificación para cambiar el formato de este texto.**  
  
2.  Desde el **controles de Word** pestaña de la **cuadro de herramientas**, arrastre un <xref:Microsoft.Office.Tools.Word.Bookmark> control al documento.  
  
     El **agregar Control de marcador** aparece el cuadro de diálogo.  
  
3.  Seleccione el texto que agregó al documento y haga clic en **Aceptar**.  
  
     A <xref:Microsoft.Office.Tools.Word.Bookmark> control denominado **Bookmark1** se agrega al texto seleccionado en el documento.  
  
4.  En el **propiedades** ventana, cambie el valor de la **(nombre)** propiedad **fontText.**  
  
 A continuación, escribir el código para dar formato al texto cuando se activa o se desactiva una casilla de verificación.  
  
## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>Dar formato al texto cuando se activa o se desactiva una casilla de verificación  
 Cuando el usuario selecciona una opción de formato, cambiar el formato del texto en el documento.  
  
### <a name="change-formatting-when-a-check-box-is-selected"></a>Cambiar el formato cuando se selecciona una casilla de verificación  
  
1.  Haga clic en `ThisDocument` en **el Explorador de soluciones**y, a continuación, haga clic en **ver código** en el menú contextual.  
  
2.  Sólo para C#, agregue las siguientes constantes para el **ThisDocument** clase.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]  
  
3.  Agregue el código siguiente a la <xref:System.Windows.Forms.Control.Click> controlador de eventos de la `applyBoldFont` casilla de verificación.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]  
  
4.  Agregue el código siguiente a la <xref:System.Windows.Forms.Control.Click> controlador de eventos de la `applyItalicFont` casilla de verificación.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]  
  
5.  Agregue el código siguiente a la <xref:System.Windows.Forms.Control.Click> controlador de eventos de la `applyUnderlineFont` casilla de verificación.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]  
  
6.  En C#, debe agregar controladores de eventos para los cuadros de texto para el <xref:Microsoft.Office.Tools.Word.Document.Startup> eventos. Para obtener información sobre cómo crear controladores de eventos, vea [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]  
  
## <a name="test-the-application"></a>Probar la aplicación  
 Ahora puede probar el documento para comprobar que el texto se formateó correctamente cuando se activa o desactiva una casilla de verificación.  
  
### <a name="test-your-document"></a>Probar el documento  
  
1.  Presione **F5** para ejecutar el proyecto.  
  
2.  Active o desactive una casilla de verificación.  
  
3.  Confirme que el texto tiene el formato correcto.  
  
## <a name="next-steps"></a>Pasos siguientes  
 En este tutorial se muestra los aspectos básicos del uso de casillas de verificación y cambio del formato del texto en documentos de Word mediante programación. A continuación, podría realizar las siguientes tareas:  
  
-   Usar un botón para rellenar un cuadro de texto. Para obtener más información, consulte [Tutorial: mostrar texto en un cuadro de texto en un documento utilizando un botón](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Usar botones de radio para seleccionar estilos de gráfico. Para obtener más información, consulte [Tutorial: actualizar un gráfico en un documento utilizando botones de opción](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  

## <a name="see-also"></a>Vea también  
 [Tutoriales para Word](../vsto/walkthroughs-using-word.md)   
 [Tutoriales y ejemplos de desarrollo de office](../vsto/office-development-samples-and-walkthroughs.md)   
 [NamedRange (control)](../vsto/namedrange-control.md)   
 [Limitaciones de los controles de formularios Windows Forms en documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  