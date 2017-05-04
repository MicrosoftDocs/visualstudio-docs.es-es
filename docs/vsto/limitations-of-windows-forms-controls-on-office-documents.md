---
title: "Limitaciones de los controles de formularios Windows Forms en los documentos de Office | Microsoft Docs"
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
  - "controles ActiveX [desarrollo de Office en Visual Studio]"
  - "controles [desarrollo de Office en Visual Studio], controles de Windows Forms"
  - "documentos de Office [desarrollo de Office en Visual Studio], controles de Windows Forms"
  - "Cuadro de herramientas [desarrollo de Office en Visual Studio], controles no admitidos"
  - "controles de usuario [desarrollo de Office en Visual Studio], agrupar controles"
  - "controles de formularios Windows Forms [desarrollo de Office en Visual Studio], ActiveX heredados"
  - "controles de formularios Windows Forms [desarrollo de Office en Visual Studio], limitaciones"
  - "controles de formularios Windows Forms [desarrollo de Office en Visual Studio], cuadro de herramientas"
  - "controles de formularios Windows Forms [desarrollo de Office en Visual Studio], propiedades y métodos no admitidos"
ms.assetid: 95ff473e-4952-4977-bc88-c77289c9fb0b
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Limitaciones de los controles de formularios Windows Forms en los documentos de Office
  Existen algunas diferencias entre los controles de formularios Windows Forms que se agregan a documentos de Microsoft Office Word u hojas de cálculo de Microsoft Office Excel, y los controles de formularios Windows Forms que se agregan a formularios Windows Forms.  Por ejemplo, cuando se agrega un control <xref:Microsoft.Office.Tools.Word.Controls.Button> a un documento, las propiedades como <xref:Microsoft.Office.Tools.Word.Controls.Button.Dock%2A>, <xref:Microsoft.Office.Tools.Word.Controls.Button.Anchor%2A> y <xref:Microsoft.Office.Tools.Word.Controls.Button.TabIndex%2A> no se comportan como cabría esperar.  
  
 Muchas de estas diferencias proceden del modo en que los controles de los formularios Windows Forms se hospedan en los documentos.  Cuando se agrega un control de Windows Forms a un documento, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] incrusta un control ActiveX en el que se va a hospedar dicho control en el documento.  El control de formularios Windows Forms no se incrusta directamente en el documento.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Limitaciones de los métodos y las propiedades de los controles de Windows Forms  
 Existe una serie de métodos y propiedades de controles de Windows Forms que no funcionan en un documento como lo harían en un Windows Form y, por consiguiente, se recomienda no utilizarlos.  Por ejemplo, establecer propiedades como `Dock` y `Anchor` solo afecta a la posición del control de los formularios Windows Forms con respecto al control ActiveX contenedor, no con respecto al documento.  A continuación, se muestra una lista de métodos y propiedades de controles de Windows Forms no compatibles con Word y Excel:  
  
-   Métodos y propiedades no compatibles con controles de Excel:  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
-   Métodos y propiedades no compatibles con controles de Word:  
  
    -   `Hide`  
  
    -   `Show`  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
    -   `Visible`  
  
 Tampoco puede establecer la propiedad `Top` o `Left` de los controles de formularios Windows Forms que están en línea con el texto de un documento de Word.  Los controles de formularios Windows Forms se agregan en línea con el texto en los casos siguientes:  
  
-   cuando agrega mediante programación un control a un documento de Word y utiliza un método que especifica un intervalo para la ubicación.  
  
-   cuando agrega un control de formularios Windows Forms a un documento de Word en tiempo de diseño.  Puede cambiar esto modificando el control en el diseñador.  
  
## Diferencias de los controles de Windows Forms en documentos de Office  
 En líneas generales, los controles de Windows Forms presentan el mismo comportamiento en un documento de Office que en Windows Forms, pero existen algunas diferencias.  En la tabla siguiente se describen las diferencias que existen para los controles de formularios Windows Forms en documentos de Office:  
  
|Funcionalidad|Difference|  
|-------------------|----------------|  
|Orden de tabulación de los controles|No se puede utilizar el tabulador en los controles colocados en una hoja de cálculo de Excel o en un documento de Word.|  
|Agrupación de los controles|No se puede utilizar un control <xref:System.Windows.Forms.GroupBox> para contener otros controles en un documento de Office.  Cuando se agregan varios botones de radio directamente al documento, éstos se excluyen mutuamente.  Puede escribir código para que los botones de radio se excluyan mutuamente; sin embargo, es preferible agregar los botones de radio a un control de usuario y, a continuación, agregar dicho control de usuario al documento.  Para obtener más información, vea el ejemplo Word Controls y el ejemplo Excel Controls en [Ejemplos y tutoriales del desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).|  
|Tipo de control|Los controles de Windows Forms que se usan en documentos están encapsulados en una clase proporcionada por el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que les ofrece una funcionalidad adicional específica de la hoja de cálculo de Excel o del documento de Word.  Por ejemplo, si tiene un control `Button` en una hoja de cálculo de Excel, asegúrese de especificar el tipo como <xref:Microsoft.Office.Tools.Excel.Controls.Button> en lugar de como <xref:System.Windows.Forms.Button> cuando se haga referencia al objeto o se proceda a su conversión.|  
|Posición y tamaño de los controles|El tamaño y posición del control vienen determinados por las propiedades que forman parte del control ActiveX contenedor.  Las propiedades del control ActiveX no adquieren los mismos valores que las propiedades equivalentes de un control de formularios Windows Forms.  Cuando se establecen las propiedades `Top`, `Left`, `Height` o `Width` de un control, éstas se miden en puntos en lugar de en píxeles.|  
|Posición de los controles en documentos de Word|Si agrega controles a un diseño de flujo, tenga presente que los controles fluirán con el contenido conforme vaya cambiando.  Cuando se arrastra un control desde el **Cuadro de herramientas**, no se puede delimitar a un párrafo porque el control se agrega al documento de Word en línea con el texto.  Si se utiliza otro método para agregar el control, como hacer doble clic en el control, el control se insertará según la opción de Word que se haya establecido para la inserción de imágenes.<br /><br /> No se puede establecer la propiedad `Left` o `Top` de un control que esté insertado en el texto.<br /><br /> No puede colocar los controles en un encabezado o pie de página, ni dentro de un subdocumento.|  
|Eventos de control|Cuando se selecciona el control, inicia eventos en el orden siguiente:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Cuando se cancela la selección del control, inicia eventos en el orden siguiente:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|  
|Ajuste de escala de los controles|Cuando se cambia la configuración de zoom de un documento por un valor distinto de 100%, se deshabilitan los controles, aunque parezca que se ajustan a la escala del documento.  Por ejemplo, si hace clic en un botón cuando el documento tiene un zoom de 130%, mostrará un mensaje que indica que se ha deshabilitado el control hasta que el zoom se establezca en 100%.  Los controles funcionarán correctamente cuando se cambie el zoom a 100%.|  
|Valores de propiedad de los controles|Aunque las propiedades de controles de un Windows Form se establecen en un valor entero, se establecen en Single en el caso de los controles de documentos de Word.  En Excel, los valores de propiedad de los controles se establecen en Double.  Si la propiedad `Height` y `Width` de un control en una hoja de cálculo supera el tamaño de la hoja de cálculo o de la pantalla, se trunca el valor.|  
|Cambio de tamaño de los controles|Si cambia el tamaño de un control en el documento mediante uno de los ocho controladores de tamaño, las nuevas dimensiones del control no se reflejarán en la ventana **Propiedades** hasta que no se vuelva a seleccionar el control.|  
|Comportamiento de los controles|Es posible que los controles de una hoja de cálculo de Excel se comporten de forma imprevisible al dividir la ventana de la hoja de cálculo.  Por ejemplo, puede que el acceso al control <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> en la hoja de cálculo sólo esté disponible en una de las ventanas.|  
|Denominación de los controles|No se puede utilizar palabras reservadas para denominar controles.  Por ejemplo, si se agrega un control <xref:Microsoft.Office.Tools.Excel.Controls.Button> a una hoja de cálculo y se cambia el nombre a **System**, se producirán errores al compilar el proyecto.|  
|Adición de controles mediante programación|No utilice el constructor del control para agregar un control al documento en tiempo de ejecución.  En su lugar, utilice los métodos auxiliares que proporciona el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  Por ejemplo, utilice el método <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> para agregar un botón a una hoja de cálculo.  Si desea agregar un control no admitido por estos métodos auxiliares, puede utilizar el método AddControl.  Para obtener más información, vea [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).|  
|Copia de los controles|Si se copia un control de formularios Windows Forms y se pega en un documento en tiempo de ejecución, se pegará un control ActiveX contenedor en el documento.  El control de formularios Windows Forms no aparece en la nueva ubicación y el código subyacente al control original no se copia en el control ActiveX contenedor.|  
  
## Limitaciones de los proyectos en el nivel del documento  
 Algunas limitaciones del uso de controles de formularios Windows Forms en documentos son únicas de proyectos en el nivel del documento.  
  
### Controles compatibles en tiempo de diseño  
 Cuando se abre una hoja de cálculo de Excel o un documento de Word en el diseñador de Visual Studio, se quitan del **Cuadro de herramientas** ciertos controles de Windows Forms.  Esto se debe a limitaciones técnicas o al hecho de que la funcionalidad ya esté disponible en Word o Excel.  Los proyectos de Excel y Word admiten todos los controles de Windows Forms y otros componentes que aparecen en el **Cuadro de herramientas** cuando el documento tiene el foco. También se pueden agregar controles de otros fabricantes a una hoja de cálculo o un documento.  
  
> [!NOTE]  
>  Si el documento está protegido, se quitan todos los controles del **Cuadro de herramientas**.  Para obtener información sobre la protección de documentos, vea [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md).  
  
> [!NOTE]  
>  Los controles de otros fabricantes deben tener el atributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> establecido en **true** para que se puedan usar en una solución de Office.  
  
 Los controles y componentes siguientes no están disponibles en el **Cuadro de herramientas**:  
  
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
  
### Compatibilidad con controles ActiveX heredados  
 Si crea un proyecto de Office de nivel de documento que use un documento de Word o un libro de Excel existentes que contengan controles ActiveX, no se pierde la funcionalidad de los controles ActiveX; sin embargo, no existe compatibilidad alguna con la adición de controles ActiveX nuevos a los documentos desde Visual Studio.  Por ejemplo, si el documento de Word tiene un botón del **Cuadro de controles** que ejecuta una macro de Visual Basic para Aplicaciones \(VBA\), continuará ejecutando dicha macro después de haber utilizado el documento en un proyecto de Office.  No obstante, se recomienda quitar los controles ActiveX y las macros de VBA, y reemplazarlos con controles de Windows Forms y código administrado.  
  
## Vea también  
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Información general sobre controles de formularios Windows Forms en documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Cómo: Agregar controles de Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)  
  
  