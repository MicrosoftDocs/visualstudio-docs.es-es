---
title: Mostrar texto en el cuadro de texto del documento con el botón
description: Obtenga información sobre cómo puede usar los botones y cuadros de texto en una personalización de nivel de documento para Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text boxes, displaying text in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1cda1fe3e7430ff30dcc3b3921eb2bcd4d31b699
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97522755"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-document-using-a-button"></a>Tutorial: mostrar texto en un cuadro de texto de un documento mediante un botón
  Este tutorial muestra cómo usar los botones y cuadros de texto en una personalización de nivel de documento para Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Agregar controles al documento Word en un proyecto de nivel de documento en tiempo de diseño.

- Rellenar un cuadro de texto cuando se hace clic en un botón.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Creación del proyecto
 El primer paso es crear un proyecto de tipo Documento de Word.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de documento de Word con el nombre **mi palabra Button**. En el asistente, seleccione **crear un nuevo documento**.

     Para obtener más información, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio abre el nuevo documento de Word en el diseñador y agrega el proyecto **My Word Button** a **Explorador de soluciones**.

## <a name="add-controls-to-the-word-document"></a>Agregar controles al documento de Word
 Los controles de interfaz de usuario están compuestos por un botón y un cuadro de texto en el documento de Word.

### <a name="to-add-a-button-and-a-text-box"></a>Para agregar un botón y un cuadro de texto

1. Compruebe que el documento esté abierto en el diseñador de Visual Studio.

2. En la pestaña **controles comunes** del **cuadro de herramientas**, arrastre un <xref:Microsoft.Office.Tools.Word.Controls.TextBox> control hasta el documento.

   > [!NOTE]
   > En Word, los controles se colocan de forma predeterminada en línea con el texto. Puede modificar la forma en que se insertan los controles y los objetos de forma cambiando el valor predeterminado en la pestaña **Editar** del cuadro de diálogo **Opciones** de Word.

3. En el menú **Ver** , haga clic en **Ventana de propiedades**.

4. Busque **textBox1** en el cuadro desplegable de la ventana **propiedades** y cambie la propiedad **nombre** del cuadro de texto a **textoparamostrar**.

5. Arrastre un control de **botón** al documento y cambie las propiedades siguientes.

   |Propiedad|Value|
   |--------------|-----------|
   |**Nombre**|**insertText**|
   |**Texto**|**Insertar texto**|

   Ahora puede escribir el código que se ejecutará cuando se haga clic en el botón.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Rellenar el cuadro de texto cuando se haga clic en el botón
 Cada vez que el usuario haga clic en el botón, **Hola mundo!** se agrega al cuadro de texto.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Para escribir en el cuadro de texto cuando se haga clic en el botón

1. En **Explorador de soluciones**, haga clic con el botón secundario en **ThisDocument** y, a continuación, haga clic en **Ver código** en el menú contextual.

2. Agregue el siguiente código al controlador de eventos <xref:System.Windows.Forms.Control.Click> del botón.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]

3. En C#, debe agregar un controlador de eventos para el botón al evento <xref:Microsoft.Office.Tools.Word.Document.Startup>. Para obtener información sobre cómo crear controladores de eventos, consulte [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]

## <a name="test-the-application"></a>Prueba de la aplicación
 Ahora puede probar el documento para asegurarse de que el mensaje **Hola mundo.** aparece en el cuadro de texto al hacer clic en el botón.

### <a name="to-test-your-document"></a>Para probar el documento

1. Presione **F5** para ejecutar el proyecto.

2. Haga clic en el botón.

3. Confirme que **Hola mundo!** aparece en el cuadro de texto.

## <a name="next-steps"></a>Pasos siguientes
 Este tutorial muestra los conceptos básicos del uso de botones y cuadros de texto en documentos de Word. A continuación, podría realizar las siguientes tareas:

- Usar un cuadro combinado para cambiar el formato. Para obtener más información, vea [Tutorial: cambiar el formato de un documento mediante controles de casilla](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

- Usar botones de radio para seleccionar estilos de gráfico. Para obtener más información, vea [Tutorial: actualizar un gráfico en un documento mediante botones de radio](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>Consulte también
- [Información general sobre los controles de Windows Forms en documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Tutoriales de uso de Word](../vsto/walkthroughs-using-word.md)
- [Ejemplos y tutoriales de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Cómo: agregar controles Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
