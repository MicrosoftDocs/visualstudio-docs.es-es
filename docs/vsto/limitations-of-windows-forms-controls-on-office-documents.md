---
title: Limitaciones de Windows Forms controles en documentos de Office | Documentos de Microsoft
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
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], ActiveX legacy
- ActiveX controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], limitations
- controls [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], unsupported properties and methods
- Toolbox [Office development in Visual Studio], unsupported controls
- user controls [Office development in Visual Studio], grouping controls
- Windows Forms controls [Office development in Visual Studio], Toolbox
ms.assetid: 95ff473e-4952-4977-bc88-c77289c9fb0b
caps.latest.revision: "56"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d7fbbad8433df7dd36d8f09a13305da3e15430c5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Limitaciones de los controles de formularios Windows Forms en los documentos de Office
  Hay algunas diferencias entre los controles de formularios Windows Forms que se agregan a documentos de Microsoft Office Word u hojas de cálculo de Microsoft Office Excel y controles de formularios Windows Forms que se agregan a Windows Forms. Por ejemplo, cuando se agrega un <xref:Microsoft.Office.Tools.Word.Controls.Button> como el control a un documento, propiedades <xref:Microsoft.Office.Tools.Word.Controls.Button.Dock%2A>, <xref:Microsoft.Office.Tools.Word.Controls.Button.Anchor%2A>, y <xref:Microsoft.Office.Tools.Word.Controls.Button.TabIndex%2A> no se comportan como cabría esperar.  
  
 Muchas de estas diferencias se deben a la forma que se hospedan los controles de Windows Forms en documentos. Cuando se agrega un control de formularios Windows Forms a un documento, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] incrusta un control ActiveX que, a continuación, hospeda el control de formularios Windows Forms en el documento. El control de formularios Windows Forms no se incrusta directamente en el documento.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Limitaciones de los métodos y propiedades de controles de Windows Forms  
 Hay una serie de métodos y propiedades de controles de formularios Windows Forms que no funcionan del mismo modo en un documento tal y como lo harían en un formulario Windows Forms y, por lo tanto, se recomienda que no usarse. Por ejemplo, establecer propiedades como `Dock` y `Anchor` sólo afecta a la posición del control en relación con el control de ActiveX de contenedor, en lugar de con el documento. La siguiente es una lista de métodos no compatibles y las propiedades de controles de formularios Windows Forms para Word y Excel:  
  
-   Métodos no admitidos y las propiedades de controles de Excel:  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
-   Propiedades de controles de Word y métodos no admitidos:  
  
    -   `Hide`  
  
    -   `Show`  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
    -   `Visible`  
  
 No se puede establecer también la `Left` o `Top` propiedades de controles de formularios Windows Forms que están en línea con el texto en un documento de Word. Controles de formularios Windows Forms se agregan en línea con el texto en los siguientes casos:  
  
-   Agregar un control a un documento de Word y utilizar un método que especifica un intervalo para la ubicación mediante programación.  
  
-   Agregar un control de formularios Windows Forms a un documento de Word en tiempo de diseño. Puede cambiar esto modificando el control en el diseñador.  
  
## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Diferencias en los controles de Windows Forms en documentos de Office  
 Controles de formularios Windows Forms tienen generalmente el mismo comportamiento en un documento de Office tal y como lo hacen en un formulario Windows Forms, pero existen algunas diferencias. La tabla siguiente describen las diferencias que existen para los controles de formularios Windows Forms en documentos de Office.  
  
|Funcionalidad|Diferencia|  
|-------------------|----------------|  
|Orden de tabulación del control|No puede desplazarse controles situados en una hoja de cálculo de Excel o un documento de Word.|  
|Agrupación de control|No se puede utilizar un <xref:System.Windows.Forms.GroupBox> control para contener otros controles en un documento de Office. Cuando se agregan varios botones de radio directamente al documento, los botones de opción no son mutuamente excluyentes. Puede escribir código para hacer que los botones de opción mutuamente excluyentes; Sin embargo, el método preferido es agregar los botones de radio a un control de usuario y, a continuación, agregue el control de usuario al documento. Para obtener más información, vea el ejemplo de controles de Word o Excel de muestra de controles en [ejemplos de desarrollo de Office y tutoriales](../vsto/office-development-samples-and-walkthroughs.md).|  
|Tipo de control|Controles de formularios Windows Forms que se usan en los documentos se encapsulan en una clase proporcionada por el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que proporciona a los controles una funcionalidad adicional específica a la hoja de cálculo de Excel o un documento de Word. Por ejemplo, si tiene un `Button` de control en una hoja de cálculo de Excel, asegúrese de especificar el tipo como <xref:Microsoft.Office.Tools.Excel.Controls.Button> en lugar de <xref:System.Windows.Forms.Button> cuando haga referencia o convertir el objeto.|  
|Posición del control y el tamaño|El tamaño y la posición del control se determina mediante las propiedades que forman parte del contenedor del control ActiveX. Las propiedades del control ActiveX adquieren los mismos valores que las propiedades equivalentes de un control de formularios Windows Forms. Al establecer el `Top`, `Left`, `Height`, o `Width` propiedades de un control, se mide en puntos, en lugar de píxeles.|  
|Posición del control en documentos de Word|Si agrega controles a un diseño de flujo, tenga en cuenta que los controles fluirán con el contenido que los cambios de contenido. No se puede delimitar el control a un párrafo cuando se arrastra desde el **cuadro de herramientas** porque el control se agrega al documento de Word en línea con el texto. Si emplea otro método para agregar el control, por ejemplo, haga doble clic en el control, se inserta el control de acuerdo con la opción de Word que ha configurado para insertar imágenes.<br /><br /> No se puede establecer la `Left` o `Top` propiedad de un control que está en línea con el texto.<br /><br /> No se puede colocar controles en un encabezado o pie de página, ni dentro de un subdocumento.|  
|Eventos de control|Cuando se selecciona el control, genera eventos en el orden siguiente:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Cuando se anula la selección de control, genera eventos en el orden siguiente:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|  
|Ajuste de escala de control|Al cambiar la configuración del zoom de un documento a algo distinto de 100%, controles están deshabilitados, aunque parezcan escalar con el documento. Por ejemplo, si hace clic en un botón cuando el documento está en zoom de 130%, mostrará un mensaje que se ha deshabilitado el control hasta que se establezca el zoom al 100%. Los controles funcionarán correctamente cuando se cambie el zoom al 100%.|  
|Valores de propiedad de control|Aunque las propiedades de controles en un formulario Windows Forms se establecen en un valor entero, se establecen en una única para los controles en un documento de Word. En Excel, los valores de propiedad de los controles se establecen en un valor double. Si el `Height` y `Width` propiedad de un control en una hoja de cálculo supera el tamaño de la pantalla o la hoja de cálculo, el valor se trunca.|  
|Cambiar el tamaño de control|Si cambia el tamaño de un control en el documento mediante uno de los controladores de ocho tamaño, las nuevas dimensiones del control no se reflejan en el **propiedades** ventana hasta que se vuelva a seleccionar el control.|  
|Controlar el comportamiento|Controles en una hoja de cálculo de Excel pueden tener un comportamiento impredecible cuando se divide la ventana de la hoja de cálculo. Por ejemplo, el acceso a un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> en la hoja de cálculo sólo esté disponible en una de las ventanas.|  
|Control de nomenclatura|No se puede utilizar palabras reservadas para denominar controles. Por ejemplo, si agrega un <xref:Microsoft.Office.Tools.Excel.Controls.Button> a una hoja de cálculo y cambie el nombre a **System**, se producen errores al compilar el proyecto.|  
|Agregar controles mediante programación|No utilice el constructor del control para agregar un control al documento en tiempo de ejecución. En su lugar, use los métodos auxiliares proporcionados por el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Por ejemplo, use la <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> método para agregar un botón a una hoja de cálculo. Si desea agregar un control que no es compatible con estos métodos auxiliares, puede utilizar el método AddControl. Para obtener más información, consulta [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).|  
|Copiando los controles|Si copia un control de formularios Windows Forms y péguelo en un documento en tiempo de ejecución, un contenedor vacío control ActiveX se pega en el documento. El control de formularios Windows Forms no aparece en la nueva ubicación y código subyacente del control original no se copia en el contenedor de controles ActiveX.|  
  
## <a name="limitations-in-document-level-projects"></a>Limitaciones en los proyectos de nivel de documento  
 Algunas limitaciones del uso de controles de formularios Windows Forms en documentos son únicos a los proyectos de nivel de documento.  
  
### <a name="control-support-at-design-time"></a>Compatibilidad con el control en tiempo de diseño  
 Ciertos controles de formularios Windows Forms se quitan de la **cuadro de herramientas** cuando una hoja de cálculo de Excel o un documento de Word está abierto en el Diseñador de Visual Studio. Esto es debido a las limitaciones técnicas o porque la funcionalidad ya está disponible en Word o Excel. Los proyectos de Excel y Word admiten todos los controles de formularios Windows Forms y otros componentes que aparecen en la **cuadro de herramientas** cuando el documento tiene el foco, y también puede agregar controles de terceros a una hoja de cálculo o documento.  
  
> [!NOTE]  
>  Todos los controles se quitan de la **cuadro de herramientas** cuando un documento está protegido. Para obtener información acerca de la protección de documentos, consulte [protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md).  
  
> [!NOTE]  
>  Controles de terceros deben tener la <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo establecido en **true** para poder usarse en una solución de Office.  
  
 Los siguientes controles y componentes no están disponibles en la **cuadro de herramientas**:  
  
-   <xref:System.Windows.Forms.BindingNavigator>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.DataGrid>  
  
-   <xref:System.DirectoryServices.DirectoryEntry>  
  
-   <xref:System.DirectoryServices.DirectorySearcher>  
  
-   <xref:System.Windows.Forms.ErrorProvider>  
  
-   <xref:System.Diagnostics.EventLog>  
  
-   <xref:System.IO.FileSystemWatcher>  
  
-   <xref:System.Windows.Forms.FlowLayoutPanel>  
  
-   <xref:System.Windows.Forms.GroupBox>  
  
-   <xref:System.Windows.Forms.MainMenu>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Messaging.MessageQueue>  
  
-   <xref:System.Windows.Forms.NotifyIcon>  
  
-   <xref:System.Windows.Forms.PageSetupDialog>  
  
-   <xref:System.Windows.Forms.Panel>  
  
-   <xref:System.Diagnostics.PerformanceCounter>  
  
-   <xref:System.Windows.Forms.PrintDialog>  
  
-   <xref:System.Drawing.Printing.PrintDocument>  
  
-   <xref:System.Windows.Forms.PrintPreviewControl>  
  
-   <xref:System.Diagnostics.Process>  
  
-   <xref:System.Windows.Forms.RichTextBox>  
  
-   <xref:System.IO.Ports.SerialPort>  
  
-   <xref:System.ServiceProcess.ServiceController>  
  
-   <xref:System.Windows.Forms.SplitContainer>  
  
-   <xref:System.Windows.Forms.Splitter>  
  
-   <xref:System.Windows.Forms.StatusBar>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
-   <xref:System.Windows.Forms.TableLayoutPanel>  
  
-   <xref:System.Timers.Timer>  
  
-   <xref:System.Windows.Forms.Timer>  
  
-   <xref:System.Windows.Forms.ToolBar>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.ToolStripContainer>  
  
-   <xref:System.Windows.Forms.ToolStripDropDown>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownMenu>  
  
-   <xref:System.Windows.Forms.ToolStripPanel>  
  
### <a name="support-for-legacy-activex-controls"></a>Compatibilidad con controles ActiveX heredados  
 Si crea un proyecto de Office de nivel de documento que usa un documento de Word existente o un libro de Excel que contiene los controles ActiveX, la funcionalidad de los controles ActiveX no se pierden; Sin embargo, no hay ninguna compatibilidad para agregar nuevos controles ActiveX a los documentos desde Visual Studio. Por ejemplo, si el documento de Word tiene un botón de la **Control** cuadro de herramientas que se ejecuta una macro Visual Basic para aplicaciones (VBA), seguirá ejecutándose la macro después de que el documento se ha utilizado en un proyecto de Office. Sin embargo, se recomienda quitar los controles ActiveX y las macros de VBA y sustituirlos por otros controles de formularios Windows Forms y código administrado.  
  
## <a name="see-also"></a>Vea también  
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Controles en documentos de Office información general sobre formularios Windows Forms](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Cómo: Agregar controles de Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)  
  
  