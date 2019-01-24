---
title: 'Tutorial: Mostrar texto en un cuadro de texto en un documento utilizando un botón'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text boxes, displaying text in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 188fc5d954bb41ced952e48874816bdfd503765b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910144"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-document-using-a-button"></a>Tutorial: Mostrar texto en un cuadro de texto en un documento utilizando un botón
  Este tutorial muestra cómo usar los botones y cuadros de texto en una personalización de nivel de documento para Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
- Agregar controles al documento Word en un proyecto de nivel de documento en tiempo de diseño.  
  
- Rellenar un cuadro de texto cuando se hace clic en un botón.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="create-the-project"></a>Crear el proyecto  
 El primer paso es crear un proyecto de tipo Documento de Word.  
  
### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto  
  
1.  Cree un proyecto de documento de Word con el nombre **Mi botón de Word**. En el asistente, seleccione **crear un nuevo documento**.  
  
     Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo documento de Word en el diseñador y agrega el **Mi botón de Word** proyecto a **el Explorador de soluciones**.  
  
## <a name="add-controls-to-the-word-document"></a>Agregar controles al documento de Word  
 Los controles de interfaz de usuario están compuestos por un botón y un cuadro de texto en el documento de Word.  
  
### <a name="to-add-a-button-and-a-text-box"></a>Para agregar un botón y un cuadro de texto  
  
1. Compruebe que el documento esté abierto en el diseñador de Visual Studio.  
  
2. Desde el **controles comunes** pestaña de la **cuadro de herramientas**, arrastre un <xref:Microsoft.Office.Tools.Word.Controls.TextBox> control al documento.  
  
   > [!NOTE]  
   >  En Word, los controles se colocan de forma predeterminada en línea con el texto. Puede modificar los controles de la forma y se insertan los objetos de forma cambiando el valor predeterminado en el **editar** pestaña de la **opciones** cuadro de diálogo de Word.  
  
3. En el menú **Ver** , haga clic en la **Ventana Propiedades**.  
  
4. Buscar **TextBox1** en el **propiedades** cuadro de lista desplegable de la ventana y cambie el **nombre** propiedad del cuadro de texto a **displayText**.  
  
5. Arrastre un **botón** control al documento y cambie las siguientes propiedades.  
  
   |Property|Valor|  
   |--------------|-----------|  
   |**Name**|**insertText**|  
   |**Texto**|**Insertar texto**|  
  
   Ahora puede escribir el código que se ejecutará cuando se haga clic en el botón.  
  
## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Rellenar el cuadro de texto cuando se hace clic en el botón  
 Cada vez que el usuario hace clic en el botón, **Hello World!** se agrega al cuadro de texto.  
  
### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Para escribir en el cuadro de texto cuando se haga clic en el botón  
  
1.  En **el Explorador de soluciones**, haga clic en **ThisDocument**y, a continuación, haga clic en **ver código** en el menú contextual.  
  
2.  Agregue el siguiente código al controlador de eventos <xref:System.Windows.Forms.Control.Click> del botón.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]  
  
3.  En C#, debe agregar un controlador de eventos para el botón al evento <xref:Microsoft.Office.Tools.Word.Document.Startup>. Para obtener información acerca de cómo crear controladores de eventos, vea [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]  
  
## <a name="test-the-application"></a>Probar la aplicación  
 Ahora puede probar el documento para asegurarse de que el mensaje **Hello World!** aparece en el cuadro de texto al hacer clic en el botón.  
  
### <a name="to-test-your-document"></a>Para probar el documento  
  
1.  Presione **F5** para ejecutar el proyecto.  
  
2.  Haga clic en el botón.  
  
3.  Confirme que **Hola a todos!** aparece en el cuadro de texto.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Este tutorial muestra los conceptos básicos del uso de botones y cuadros de texto en documentos de Word. A continuación, podría realizar las siguientes tareas:  
  
-   Usar un cuadro combinado para cambiar el formato. Para obtener más información, vea [Tutorial: Cambiar formato de documento utilizando controles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
-   Usar botones de radio para seleccionar estilos de gráfico. Para obtener más información, vea [Tutorial: Actualizar un gráfico en un documento utilizando botones de radio](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  
## <a name="see-also"></a>Vea también  
 [Controles de Windows Forms en información general sobre documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Tutoriales para Word](../vsto/walkthroughs-using-word.md)   
 [Tutoriales y ejemplos de desarrollo de office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Cómo: Agregar controles de formularios Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)  
