---
title: Cambiar el formato de documento mediante controles CheckBox
description: Obtenga información sobre cómo usar Windows Forms en una personalización de nivel de documento de Microsoft Word para cambiar el formato de texto.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3f6fbb91c37fd8956860eed8e4d39f8b0a8c1a0e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824424"
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>Tutorial: Cambiar el formato de documento mediante controles CheckBox
  En este tutorial se muestra cómo usar Windows Forms en una personalización de nivel de documento para Microsoft Office Word para cambiar el formato de texto.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Agregar texto y un control al documento en un proyecto de nivel de documento en tiempo de diseño.

- Aplicar formato al texto cuando se selecciona una opción.

  Para ver el resultado como un ejemplo completado, vea el ejemplo de controles de Word en los tutoriales y ejemplos [de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Creación del proyecto
 El primer paso es crear un proyecto de tipo Documento de Word.

### <a name="create-a-new-project"></a>Crear un proyecto nuevo

1. Cree un proyecto de documento de Word con el nombre **My Word Formatting**. En el asistente, seleccione **Crear un nuevo documento.**

     Para obtener más información, [vea Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio el nuevo documento de Word en el diseñador y agrega el **proyecto My Word Formatting** **a Explorador de soluciones**.

## <a name="add-text-and-controls-to-the-word-document"></a>Agregar texto y controles al documento de Word
 Para este tutorial, agregue tres casillas y texto en <xref:Microsoft.Office.Tools.Word.Bookmark> un control al documento de Word. Las casillas presentarán opciones al usuario para dar formato al texto.

### <a name="add-three-check-boxes"></a>Agregar tres casillas

1. Compruebe que el documento esté abierto en el diseñador de Visual Studio.

2. En la **pestaña Controles comunes** del Cuadro **de** herramientas , arrastre el primer control <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> al documento.

3. En la ventana **Propiedades** , cambie las siguientes propiedades:

    |Propiedad|Value|
    |--------------|-----------|
    |**Nombre**|**applyBoldFont**|
    |**Texto**|**Negrita**|

4. Presione **Entrar para** mover el punto de inserción debajo de la primera casilla.

5. Agregue una segunda casilla al documento debajo de la `ApplyBoldFont` casilla y cambie las siguientes propiedades.

    |Propiedad|Value|
    |--------------|-----------|
    |**Nombre**|**applyItalicFont**|
    |**Texto**|**Cursiva**|

6. Presione **Entrar para** mover el punto de inserción debajo de la segunda casilla.

7. Agregue una tercera casilla al documento debajo de la `ApplyItalicFont` casilla y cambie las propiedades siguientes.

    |Propiedad|Value|
    |--------------|-----------|
    |**Nombre**|**applyUnderlineFont**|
    |**Texto**|**Subrayar**|

### <a name="add-text-and-a-bookmark-control"></a>Agregar texto y un control Bookmark

1. Mueva el punto de inserción debajo de los controles de casilla y escriba el texto siguiente:

    **Haga clic en una casilla para cambiar el formato de este texto.**

2. En la **pestaña Controles de** Word del Cuadro **de** herramientas , arrastre un control <xref:Microsoft.Office.Tools.Word.Bookmark> al documento.

    Aparece **el cuadro de diálogo Agregar control** marcador .

3. Seleccione el texto que agregó al documento y haga clic en **Aceptar.**

    Se agrega un control denominado <xref:Microsoft.Office.Tools.Word.Bookmark> **Bookmark1** al texto seleccionado en el documento.

4. En la **ventana** Propiedades, cambie el valor de la propiedad **(Name)** **a fontText.**

   A continuación, escriba el código para dar formato al texto cuando una casilla esté activada o desactivada.

## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>Dar formato al texto cuando una casilla está activada o desactivada
 Cuando el usuario seleccione una opción de formato, cambie el formato del texto del documento.

### <a name="change-formatting-when-a-check-box-is-selected"></a>Cambiar el formato cuando se selecciona una casilla

1. Haga clic con el `ThisDocument` botón derecho en **Explorador de soluciones** y, a continuación, haga clic en **Ver código** en el menú contextual.

2. Solo para C#, agregue las siguientes constantes a la **clase ThisDocument.**

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet2":::

3. Agregue el código siguiente al controlador <xref:System.Windows.Forms.Control.Click> de eventos de la `applyBoldFont` casilla.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet3":::

4. Agregue el código siguiente al controlador <xref:System.Windows.Forms.Control.Click> de eventos de la `applyItalicFont` casilla.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet4":::

5. Agregue el código siguiente al controlador <xref:System.Windows.Forms.Control.Click> de eventos de la `applyUnderlineFont` casilla.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet5":::

6. En C#, debe agregar controladores de eventos para los cuadros de texto al <xref:Microsoft.Office.Tools.Word.Document.Startup> evento. Para obtener información sobre cómo crear controladores de eventos, [vea Cómo: Crear controladores de eventos en proyectos de Office.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet6":::

## <a name="test-the-application"></a>Prueba de la aplicación
 Ahora puede probar el documento para comprobar que el texto tiene el formato correcto al activar o borrar una casilla.

### <a name="test-your-document"></a>Prueba del documento

1. Presione **F5** para ejecutar el proyecto.

2. Activar o desactivar una casilla.

3. Confirme que el formato del texto es correcto.

## <a name="next-steps"></a>Pasos siguientes
 En este tutorial se muestran los conceptos básicos del uso de casillas y el cambio de formato de texto mediante programación en documentos de Word. A continuación, podría realizar las siguientes tareas:

- Use un botón para rellenar un cuadro de texto. Para obtener más información, [vea Tutorial: Mostrar texto en un cuadro de texto de un documento mediante un botón](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

- Usar botones de radio para seleccionar estilos de gráfico. Para obtener más información, vea [Tutorial: Actualizar un gráfico en un documento mediante botones de radio](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>Consulte también
- [Tutoriales con Word](../vsto/walkthroughs-using-word.md)
- [Ejemplos y tutoriales de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Control NamedRange](../vsto/namedrange-control.md)
- [Limitaciones de los Windows Forms controles en documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
