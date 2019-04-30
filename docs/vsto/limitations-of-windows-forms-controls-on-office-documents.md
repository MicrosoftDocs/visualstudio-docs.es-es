---
title: Limitaciones de los controles de Windows Forms en documentos de Office
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 610ee5e18054b6da35a3098b851d1585c70b6bc3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583781"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Limitaciones de los controles de Windows Forms en documentos de Office

Hay algunas diferencias entre los controles de Windows Forms que se agregan a documentos de Microsoft Office Word u hojas de cálculo de Microsoft Office Excel y controles de Windows Forms que se agregan a Windows Forms. Por ejemplo, cuando agrega un <xref:Microsoft.Office.Tools.Word.Controls.Button> de control a un documento, las propiedades como <xref:System.Windows.Forms.Control.Dock>, <xref:System.Windows.Forms.Control.Anchor>, y <xref:System.Windows.Forms.Control.TabIndex> no se comportan como cabría esperar.

Muchas de estas diferencias se deben a la forma ese formularios de Windows se hospedan los controles en documentos. Cuando se agrega un control de Windows Forms a un documento, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] incrusta un control ActiveX que, a continuación, hospeda el control de Windows Forms en el documento. El control Windows Forms no se incrusta directamente en el documento.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Limitaciones de los métodos y propiedades de controles de Windows Forms

Hay una serie de métodos y propiedades de controles de Windows Forms que no funcionan del mismo modo en un documento tal como lo harían en un formulario de Windows y, por lo tanto, se recomienda que no se usaron. Por ejemplo, establecer propiedades como <xref:System.Windows.Forms.Control.Dock> y <xref:System.Windows.Forms.Control.Anchor> solo afecta a la posición del control con respecto al control ActiveX de contenedor, en lugar del documento. La siguiente es una lista de métodos no admitidos y las propiedades de controles de Windows Forms para Word y Excel:

- Propiedades no compatibles de controles de Excel:

    - <xref:System.Windows.Forms.Control.Anchor>
    - <xref:System.Windows.Forms.Control.Dock>
    - <xref:System.Windows.Forms.Control.Location>
    - <xref:System.Windows.Forms.Control.TabIndex>
    - <xref:System.Windows.Forms.Control.TabStop>
    - <xref:System.Windows.Forms.Control.TopLevelControl>

- Propiedades de controles de Word y métodos no admitidos:

    - <xref:System.Windows.Forms.Control.Hide%2A>
    - <xref:System.Windows.Forms.Control.Show%2A>
    - <xref:System.Windows.Forms.Control.Anchor>
    - <xref:System.Windows.Forms.Control.Dock>
    - <xref:System.Windows.Forms.Control.Location>
    - <xref:System.Windows.Forms.Control.TabIndex>
    - <xref:System.Windows.Forms.Control.TabStop>
    - <xref:System.Windows.Forms.Control.TopLevelControl>
    - <xref:System.Windows.Forms.Control.Visible>

No se puede establecer también la <xref:System.Windows.Forms.Control.Left> o <xref:System.Windows.Forms.Control.Top> propiedad de los controles de Windows Forms que están en consonancia con texto en un documento de Word. Controles de formularios Windows Forms se agregan en línea con el texto en los casos siguientes:

- Agregar un control a un documento de Word y utilizar un método que especifica un intervalo para la ubicación mediante programación.

- Agregue un control de Windows Forms a un documento de Word en tiempo de diseño. Puede cambiar esto modificando el control en el diseñador.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Diferencias en los controles de Windows Forms en documentos de Office

Controles de formularios Windows Forms tienen generalmente el mismo comportamiento en un documento de Office tal como lo hacen en un formulario de Windows, pero existen algunas diferencias. En la tabla siguiente se describe las diferencias que existen para los controles de Windows Forms en documentos de Office.

|Funcionalidad|Diferencia|
|-------------------|----------------|
|Orden de tabulación de control|No puede desplazarse los controles ubicados en una hoja de cálculo de Excel o un documento de Word.|
|Agrupación de control|No puede usar un <xref:System.Windows.Forms.GroupBox> control para contener otros controles en un documento de Office. Al agregar varios botones de radio directamente al documento, los botones de radio no son mutuamente excluyentes. Puede escribir código para que los botones de radio mutuamente excluyentes; Sin embargo, el método preferido es agregar los botones de radio a un control de usuario y, a continuación, agregue el control de usuario al documento. Para obtener más información, vea el ejemplo de controles de Word o Excel de ejemplo de controles en [tutoriales y ejemplos de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).|
|Tipo de control|Controles de Windows Forms usados en los documentos se encapsulan en una clase proporcionada por el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] una funcionalidad adicional específica de los controles que proporciona a la hoja de cálculo de Excel o un documento de Word. Por ejemplo, si tiene un **botón** de control en una hoja de cálculo de Excel, asegúrese de especificar el tipo como <xref:Microsoft.Office.Tools.Excel.Controls.Button> lugar <xref:System.Windows.Forms.Button> cuando haga referencia o convertir el objeto.|
|Posición del control y el tamaño|El tamaño y posición del control viene determinada por las propiedades que forman parte del contenedor del control ActiveX. Las propiedades del control ActiveX toman valores diferentes que las propiedades equivalentes de un control Windows Forms. Al establecer el `Top`, `Left`, `Height`, o `Width` propiedades de un control, se mide en puntos, en lugar de píxeles.|
|Posición del control en documentos de Word|Si agrega controles a un diseño de flujo, tenga en cuenta que los controles fluirán con el contenido, como los cambios de contenido. No se puede delimitar el control a un párrafo cuando se arrastra desde el **cuadro de herramientas** porque el control se agrega al documento de Word en línea con el texto. Si emplea otro método para agregar el control, por ejemplo, haga doble clic en el control, se inserta el control de acuerdo con la opción de Word que haya definido para la inserción de imágenes.<br /><br /> No puede establecer el `Left` o `Top` propiedad de un control que está en línea con el texto.<br /><br /> No se puede colocar controles en un encabezado o pie de página, o dentro de un subdocumento.|
|Eventos de control|Cuando se selecciona el control, genera los eventos en el orden siguiente:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Cuando se anula la selección del control, genera los eventos en el orden siguiente:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|
|Escalado de control|Al cambiar la configuración del zoom de un documento a cualquier cosa que no sea 100%, los controles están deshabilitados, aunque parecen a escala con el documento. Por ejemplo, si hace clic en un botón cuando el documento se encuentra en % 130 de zoom, se mostrará un mensaje que se ha deshabilitado el control hasta que se establezca el zoom al 100%. Los controles funcionará correctamente al cambiar el zoom al 100%.|
|Valores de propiedad de control|Aunque se establecen las propiedades de controles de Windows Forms a un valor entero, se establecen en un único para los controles de un documento de Word. En Excel, los valores de propiedad de los controles se establecen en un valor doble. Si el `Height` y `Width` propiedad de un control en una hoja de cálculo supera el tamaño de la hoja de cálculo o de la pantalla, el valor se trunca.|
|Cambiar el tamaño de control|Si cambia el tamaño de un control en el documento mediante uno de los controladores de tamaño de ocho, las nuevas dimensiones del control no se reflejan en el **propiedades** ventana hasta que se vuelva a seleccionar el control.|
|Comportamiento de control|Los controles en una hoja de cálculo de Excel pueden comportarse de forma impredecible cuando se divide la ventana de la hoja de cálculo. Por ejemplo, el acceso a un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> en la hoja de cálculo solo esté disponible en una de las ventanas.|
|Control de nomenclatura|No se puede utilizar palabras reservadas para denominar controles. Por ejemplo, si agrega un <xref:Microsoft.Office.Tools.Excel.Controls.Button> a una hoja de cálculo y cambie el nombre a **sistema**, se producen errores al compilar el proyecto.|
|Agregar controles mediante programación|No utilice el constructor del control para agregar un control al documento en tiempo de ejecución. En su lugar, use los métodos auxiliares proporcionados por el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Por ejemplo, use el <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> para agregar un botón a una hoja de cálculo. Si desea agregar un control que no es compatible con estos métodos auxiliares, puede usar el `AddControl` método. Para obtener más información, consulte [agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).|
|Copiando los controles|Si copia un control de Windows Forms y péguelo en un documento en tiempo de ejecución, se pega un control ActiveX de contenedor vacío en el documento. El control Windows Forms no aparece en la nueva ubicación y código subyacente del control original no se copia en el contenedor del control ActiveX.|

## <a name="limitations-in-document-level-projects"></a>Limitaciones en los proyectos de nivel de documento

Algunas limitaciones del uso de controles de Windows Forms en documentos son únicos de los proyectos de nivel de documento.

### <a name="control-support-at-design-time"></a>Compatibilidad con el control en tiempo de diseño

Algunos controles de Windows Forms se quitan de la **cuadro de herramientas** cuando una hoja de cálculo de Excel o un documento de Word está abierto en el Diseñador de Visual Studio. Esto es debido a limitaciones técnicas o porque la funcionalidad ya está disponible dentro de Word o Excel. Los proyectos de Excel y Word admiten todos los controles de Windows Forms y otros componentes que aparecen en la **cuadro de herramientas** cuando el documento tiene el foco, y también puede agregar controles de terceros a una hoja de cálculo o documento.

> [!NOTE]
> Se quitan todos los controles de la **cuadro de herramientas** cuando un documento está protegido. Para obtener información acerca de la protección de documentos, consulte [protección en soluciones de nivel de documento de documentos](../vsto/document-protection-in-document-level-solutions.md).

> [!NOTE]
> Controles de terceros deben tener la <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo establecido en **true** para poder usarse en una solución de Office.

Los siguientes controles y componentes no están disponibles en el **cuadro de herramientas**:

- <xref:System.Windows.Forms.BindingNavigator>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.DataGrid>

- <xref:System.DirectoryServices.DirectoryEntry>

- <xref:System.DirectoryServices.DirectorySearcher>

- <xref:System.Windows.Forms.ErrorProvider>

- <xref:System.Diagnostics.EventLog>

- <xref:System.IO.FileSystemWatcher>

- <xref:System.Windows.Forms.FlowLayoutPanel>

- <xref:System.Windows.Forms.GroupBox>

- <xref:System.Windows.Forms.MainMenu>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Messaging.MessageQueue>

- <xref:System.Windows.Forms.NotifyIcon>

- <xref:System.Windows.Forms.PageSetupDialog>

- <xref:System.Windows.Forms.Panel>

- <xref:System.Diagnostics.PerformanceCounter>

- <xref:System.Windows.Forms.PrintDialog>

- <xref:System.Drawing.Printing.PrintDocument>

- <xref:System.Windows.Forms.PrintPreviewControl>

- <xref:System.Diagnostics.Process>

- <xref:System.Windows.Forms.RichTextBox>

- <xref:System.IO.Ports.SerialPort>

- <xref:System.ServiceProcess.ServiceController>

- <xref:System.Windows.Forms.SplitContainer>

- <xref:System.Windows.Forms.Splitter>

- <xref:System.Windows.Forms.StatusBar>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.TabControl>

- <xref:System.Windows.Forms.TableLayoutPanel>

- <xref:System.Timers.Timer>

- <xref:System.Windows.Forms.Timer>

- <xref:System.Windows.Forms.ToolBar>

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.ToolStripContainer>

- <xref:System.Windows.Forms.ToolStripDropDown>

- <xref:System.Windows.Forms.ToolStripDropDownMenu>

- <xref:System.Windows.Forms.ToolStripPanel>

### <a name="support-for-legacy-activex-controls"></a>Compatibilidad con controles ActiveX heredados

Si crea un proyecto de Office de nivel de documento que usa un documento de Word existente o un libro de Excel que contiene controles ActiveX, la funcionalidad de los controles ActiveX no se pierde; Sin embargo, no hay ninguna compatibilidad para agregar nuevos controles ActiveX a los documentos desde Visual Studio. Por ejemplo, si el documento de Word tiene un botón desde la **Control** cuadro de herramientas que se ejecuta una macro Visual Basic para aplicaciones (VBA), se seguirá ejecutando la macro después de que el documento se ha utilizado en un proyecto de Office. Sin embargo, se recomienda quitar los controles ActiveX y macros de VBA y sustituirlos por otros controles de formularios Windows Forms y código administrado.

## <a name="see-also"></a>Vea también

- [Controles en documentos de Office](../vsto/controls-on-office-documents.md)
- [Controles de Windows Forms en información general sobre documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Cómo: Agregar controles de formularios Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)