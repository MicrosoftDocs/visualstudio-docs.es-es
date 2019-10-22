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
ms.openlocfilehash: 81a7da585f49b2a2d1f7df4df11d0c78b7a35d69
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251912"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Limitaciones de los controles de Windows Forms en documentos de Office

Hay algunas diferencias entre Windows Forms controles que se agregan a Microsoft Office documentos de Word o Microsoft Office hojas de cálculo de Excel, y Windows Forms controles que se agregan a Windows Forms. Por ejemplo, cuando se agrega un <xref:Microsoft.Office.Tools.Word.Controls.Button> control a un documento, las propiedades <xref:System.Windows.Forms.Control.Dock>como, <xref:System.Windows.Forms.Control.Anchor>y <xref:System.Windows.Forms.Control.TabIndex> no se comportan como cabría esperar.

Muchas de estas diferencias se deben a la manera en que los controles de Windows Forms se hospedan en los documentos. Cuando se agrega un control Windows Forms a un documento, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] incrusta un control ActiveX que, a continuación, hospeda el control Windows Forms en el documento. El control Windows Forms no se inserta directamente en el documento.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Limitaciones de los métodos y las propiedades de los controles de Windows Forms

Hay una serie de métodos y propiedades de Windows Forms controles que no funcionan de la misma forma en un documento que en un Windows Form y, por lo tanto, se recomienda que no se usen. Por ejemplo, establecer propiedades como <xref:System.Windows.Forms.Control.Dock> y <xref:System.Windows.Forms.Control.Anchor> solo afecta a la posición del control con respecto al control ActiveX del contenedor, en lugar de al documento. A continuación se muestra una lista de métodos y propiedades no admitidos de controles de Windows Forms para Word y Excel:

- Propiedades no admitidas de los controles de Excel:

  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>

- Métodos y propiedades no admitidos de los controles de Word:

  - <xref:System.Windows.Forms.Control.Hide%2A>
  - <xref:System.Windows.Forms.Control.Show%2A>
  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>
  - <xref:System.Windows.Forms.Control.Visible>

Tampoco se puede establecer la <xref:System.Windows.Forms.Control.Left> propiedad <xref:System.Windows.Forms.Control.Top> o de Windows Forms controles que están en línea con texto en un documento de Word. Los controles de Windows Forms se agregan en línea con el texto en los casos siguientes:

- Puede agregar mediante programación un control a un documento de Word y utilizar un método que especifique un intervalo para la ubicación.

- En tiempo de diseño, se agrega un control Windows Forms a un documento de Word. Puede cambiar esto modificando el control en el diseñador.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Diferencias en los controles de Windows Forms en documentos de Office

Los controles Windows Forms suelen tener el mismo comportamiento en un documento de Office que en Windows Forms, pero existen algunas diferencias. En la tabla siguiente se describen las diferencias que existen para los controles de Windows Forms en documentos de Office.

|Funcionalidad|Diferencia|
|-------------------|----------------|
|Orden de las pestañas de control|No se puede realizar una tabulación a través de los controles colocados en una hoja de cálculo o un documento de Word|
|Agrupación de controles|No se puede usar <xref:System.Windows.Forms.GroupBox> un control para que contenga otros controles en un documento de Office. Cuando se agregan varios botones de radio directamente al documento, los botones de radio no se excluyen mutuamente. Puede escribir código para que los botones de radio sean mutuamente excluyentes. sin embargo, el método preferido es agregar los botones de radio a un control de usuario y, a continuación, agregar el control de usuario al documento. Para obtener más información, vea el ejemplo de controles de Word o de controles de Excel en [ejemplos y tutoriales de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).|
|Tipo de control|Windows Forms controles utilizados en los [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] documentos se incluyen en una clase proporcionada por que proporciona a los controles funcionalidad adicional específica de la hoja de cálculo de Excel o el documento de Word. Por ejemplo, si tiene un control de **botón** en una hoja de cálculo de Excel, asegúrese de especificar el <xref:Microsoft.Office.Tools.Excel.Controls.Button> tipo como <xref:System.Windows.Forms.Button> en lugar de al hacer referencia o convertir el objeto.|
|Posición y tamaño del control|El tamaño y la posición del control vienen determinados por las propiedades que forman parte del control ActiveX del contenedor. Las propiedades del control ActiveX toman valores distintos de las propiedades equivalentes de un control Windows Forms. Al establecer las `Top`propiedades, `Left`, `Height`o `Width` de un control, se mide en puntos, en lugar de píxeles.|
|Colocar el control en documentos de Word|Si agrega controles a un diseño basado en Flow, tenga en cuenta que los controles fluyen con el contenido a medida que cambia el contenido. No se puede delimitar el control a un párrafo cuando se arrastra desde el **cuadro de herramientas** porque el control se agrega al documento de Word en línea con el texto. Si usa otro método para agregar el control, por ejemplo, al hacer doble clic en el control, el control se inserta según la opción Word que haya establecido para insertar imágenes.<br /><br /> No se puede establecer `Left` la `Top` propiedad o de un control que está alineado con el texto.<br /><br /> No se pueden colocar controles en un encabezado o pie de página, ni dentro de un subdocumento.|
|Eventos de control|Cuando se selecciona el control, genera eventos en el orden siguiente:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Cuando se anula la selección del control, genera eventos en el orden siguiente:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|
|Escalado de controles|Al cambiar la configuración de zoom de un documento a un valor distinto del 100%, se deshabilitan los controles, aunque parece que se escalan con el documento. Por ejemplo, si hace clic en un botón cuando el documento tiene un zoom del 130%, se mostrará un mensaje que indica que el control se ha deshabilitado hasta que el zoom se establezca en 100%. Los controles funcionarán correctamente cuando cambie el zoom a 100%.|
|Valores de propiedad del control|Aunque las propiedades de los controles en un formulario de Windows Forms se establecen en un valor entero, se establecen en un único para los controles de un documento de Word. En Excel, los valores de propiedad de los controles se establecen en un valor Double. Si las `Height` propiedades `Width` y de un control en una hoja de cálculo superan el tamaño de la hoja de cálculo o de la pantalla, el valor se trunca.|
|Cambiar el tamaño del control|Si cambia el tamaño de un control en el documento con uno de los ocho controladores de tamaño, las nuevas dimensiones de control no se reflejan en la ventana **propiedades** hasta que se reseleccione el control.|
|Comportamiento del control|Los controles de una hoja de cálculo de Excel pueden comportarse de forma impredecible cuando la ventana de la hoja de cálculo está dividida. Por ejemplo, el acceso a <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> un de la hoja de cálculo solo puede estar disponible en una de las ventanas.|
|Nomenclatura de controles|No se pueden usar palabras reservadas para asignar nombres a los controles. Por ejemplo, si agrega un <xref:Microsoft.Office.Tools.Excel.Controls.Button> a una hoja de cálculo y cambia el nombre a **System**, se producen errores al compilar el proyecto.|
|Agregar controles mediante programación|No utilice el constructor del control para agregar un control al documento en tiempo de ejecución. En su lugar, use los métodos auxiliares proporcionados por [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Por ejemplo, use el <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> método para agregar un botón a una hoja de cálculo. Si desea agregar un control que no es compatible con estos métodos auxiliares, puede utilizar el `AddControl` método. Para obtener más información, vea [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).|
|Copiar controles|Si copia un control Windows Forms y lo pega en un documento en tiempo de ejecución, se pega un control ActiveX de contenedor vacío en el documento. El control Windows Forms no aparece en la nueva ubicación y el código subyacente del control original no se copia en el control ActiveX del contenedor.|

## <a name="limitations-in-document-level-projects"></a>Limitaciones en los proyectos de nivel de documento

Algunas limitaciones del uso de controles de Windows Forms en documentos son exclusivas de los proyectos de nivel de documento.

### <a name="control-support-at-design-time"></a>Controlar la compatibilidad en tiempo de diseño

Algunos controles Windows Forms se quitan del **cuadro de herramientas** cuando se abre una hoja de cálculo de Excel o un documento de Word en el diseñador de Visual Studio. Esto se debe a limitaciones técnicas o a que la funcionalidad ya está disponible en Word o Excel. Los proyectos de Excel y Word admiten todos los controles Windows Forms y otros componentes que aparecen en el **cuadro de herramientas** cuando el documento tiene el foco, y también puede Agregar controles de terceros a una hoja de cálculo o un documento.

> [!NOTE]
> Todos los controles se quitan del **cuadro de herramientas** cuando se protege un documento. Para obtener información sobre la protección de documentos, consulte [protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md).

> [!NOTE]
> Los controles de terceros deben tener el <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo establecido en **true** para poder usarse en una solución de Office.

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

Si crea un proyecto de Office de nivel de documento que use un documento de Word o un libro de Excel existente que contenga controles ActiveX, no se perderá la funcionalidad de los controles ActiveX. sin embargo, no se admite la adición de nuevos controles ActiveX a los documentos desde Visual Studio. Por ejemplo, si el documento de Word tiene un botón del cuadro de herramientas de **control** que ejecuta una macro Visual Basic para aplicaciones (VBA), seguirá ejecutando la macro después de que el documento se haya usado en un proyecto de Office. Sin embargo, se recomienda que quite los controles ActiveX y las macros VBA y los reemplace por Windows Forms controles y código administrado.

## <a name="see-also"></a>Vea también

- [Controles en documentos de Office](../vsto/controls-on-office-documents.md)
- [Información general sobre los controles de Windows Forms en documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Cómo: Agregar controles Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
