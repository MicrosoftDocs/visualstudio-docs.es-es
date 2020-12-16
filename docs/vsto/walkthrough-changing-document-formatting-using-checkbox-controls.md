---
title: Cambiar el formato de un documento mediante controles CheckBox
description: Aprenda a usar Windows Forms controles en una personalización de nivel de documento para que Microsoft Word cambie el formato del texto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 931e9554a10e0e1525d9ee4a10505633b211610b
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527244"
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>Tutorial: cambiar el formato de un documento mediante controles CheckBox
  En este tutorial se muestra cómo usar los controles Windows Forms en una personalización de nivel de documento para Microsoft Office Word para cambiar el formato del texto.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Agregar texto y un control al documento en un proyecto de nivel de documento en tiempo de diseño.

- Dar formato al texto cuando se selecciona una opción.

  Para ver el resultado como un ejemplo completado, vea el ejemplo de controles de Word en [ejemplos y tutoriales de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Creación del proyecto
 El primer paso es crear un proyecto de tipo Documento de Word.

### <a name="create-a-new-project"></a>Creación de un proyecto

1. Cree un proyecto de documento de Word con el nombre **mi formato de Word**. En el asistente, seleccione **crear un nuevo documento**.

     Para obtener más información, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio abre el nuevo documento de Word en el diseñador y agrega el proyecto **mi formato de Word** a **Explorador de soluciones**.

## <a name="add-text-and-controls-to-the-word-document"></a>Agregar texto y controles al documento de Word
 En este tutorial, agregue tres casillas y texto en un <xref:Microsoft.Office.Tools.Word.Bookmark> control al documento de Word. Las casillas presentarán opciones al usuario para dar formato al texto.

### <a name="add-three-check-boxes"></a>Agregar tres casillas

1. Compruebe que el documento esté abierto en el diseñador de Visual Studio.

2. En la pestaña **controles comunes** del **cuadro de herramientas**, arrastre el primer <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> control hasta el documento.

3. En la ventana **Propiedades** , cambie las siguientes propiedades:

    |Propiedad|Value|
    |--------------|-----------|
    |**Nombre**|**applyBoldFont**|
    |**Texto**|**Negrita**|

4. Presione **entrar** para desplace el punto de inserción debajo de la primera casilla.

5. Agregue una segunda casilla al documento debajo de la `ApplyBoldFont` casilla y cambie las propiedades siguientes.

    |Propiedad|Value|
    |--------------|-----------|
    |**Nombre**|**applyItalicFont**|
    |**Texto**|**Cursiva**|

6. Presione **entrar** para desplace el punto de inserción debajo de la segunda casilla.

7. Agregue una tercera casilla al documento debajo de la `ApplyItalicFont` casilla y cambie las propiedades siguientes.

    |Propiedad|Value|
    |--------------|-----------|
    |**Nombre**|**applyUnderlineFont**|
    |**Texto**|**Subrayado**|

### <a name="add-text-and-a-bookmark-control"></a>Agregar texto y un control Bookmark

1. Mueva el punto de inserción debajo de los controles de casilla y escriba el texto siguiente:

    **Haga clic en una casilla para cambiar el formato de este texto.**

2. En la pestaña **controles de Word** del **cuadro de herramientas**, arrastre un <xref:Microsoft.Office.Tools.Word.Bookmark> control hasta el documento.

    Aparece el cuadro de diálogo **Agregar control de marcador** .

3. Seleccione el texto que agregó al documento y haga clic en **Aceptar**.

    <xref:Microsoft.Office.Tools.Word.Bookmark>Se agrega un control denominado **Bookmark1** al texto seleccionado en el documento.

4. En la ventana **propiedades** , cambie el valor de la propiedad **(Name)** a **fontText.**

   A continuación, escriba el código para dar formato al texto cuando se active o desactive una casilla.

## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>Dar formato al texto cuando una casilla está activada o desactivada
 Cuando el usuario seleccione una opción de formato, cambie el formato del texto del documento.

### <a name="change-formatting-when-a-check-box-is-selected"></a>Cambiar el formato cuando se activa una casilla

1. Haga clic con el botón secundario `ThisDocument` en **Explorador de soluciones** y, a continuación, haga clic en **Ver código** en el menú contextual.

2. Solo para C#, agregue las siguientes constantes a la clase **ThisDocument** .

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]

3. Agregue el código siguiente al <xref:System.Windows.Forms.Control.Click> controlador de eventos de la `applyBoldFont` casilla.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]

4. Agregue el código siguiente al <xref:System.Windows.Forms.Control.Click> controlador de eventos de la `applyItalicFont` casilla.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]

5. Agregue el código siguiente al <xref:System.Windows.Forms.Control.Click> controlador de eventos de la `applyUnderlineFont` casilla.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]

6. En C#, debe agregar controladores de eventos para los cuadros de texto al <xref:Microsoft.Office.Tools.Word.Document.Startup> evento. Para obtener información sobre cómo crear controladores de eventos, consulte [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]

## <a name="test-the-application"></a>Prueba de la aplicación
 Ahora puede probar el documento para comprobar que el texto tiene el formato correcto al activar o desactivar una casilla.

### <a name="test-your-document"></a>Prueba del documento

1. Presione **F5** para ejecutar el proyecto.

2. Activar o desactivar una casilla.

3. Confirme que el texto tiene el formato correcto.

## <a name="next-steps"></a>Pasos siguientes
 En este tutorial se muestran los aspectos básicos del uso de las casillas y el cambio mediante programación del formato de texto en documentos de Word. A continuación, podría realizar las siguientes tareas:

- Use un botón para rellenar un cuadro de texto. Para obtener más información, vea [Tutorial: mostrar texto en un cuadro de texto de un documento mediante un botón](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

- Usar botones de radio para seleccionar estilos de gráfico. Para obtener más información, vea [Tutorial: actualizar un gráfico en un documento mediante botones de radio](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>Consulte también
- [Tutoriales de uso de Word](../vsto/walkthroughs-using-word.md)
- [Ejemplos y tutoriales de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md)
- [NamedRange (control)](../vsto/namedrange-control.md)
- [Limitaciones de los controles de Windows Forms en documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
