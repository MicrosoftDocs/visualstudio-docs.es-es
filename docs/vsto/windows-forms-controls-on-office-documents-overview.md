---
title: Controles de Windows Forms en información general sobre documentos de Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- old data showing in error [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], Word
- Windows Forms controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], arranging
- data [Office development in Visual Studio], old data showing in error
- user controls [Office development in Visual Studio], Windows Forms
- Windows Forms controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], removing
- application development [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Windows Forms controls
- Office [Office development in Visual Studio], Windows Forms controls
- Office documents [Office development in Visual Studio, controls
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], about Windows Forms controls
- Office applications [Office development in Visual Studio], Windows Forms
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 51c671a583e4e96b51ae6627de1fce738696fe22
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892786"
---
# <a name="windows-forms-controls-on-office-documents-overview"></a>Controles de Windows Forms en información general sobre documentos de Office
  Los controles de Windows Forms son objetos con los que pueden interactuar los usuarios para escribir o manipular datos. En los proyectos de nivel de documento para Microsoft Office Excel y Microsoft Office Word, puede agregar controles de formularios Windows Forms al documento o libro del proyecto en tiempo de diseño, o puede agregar estos controles mediante programación en tiempo de ejecución. Puede agregar estos controles mediante programación a cualquier documento o libro abierto en tiempo de ejecución en un complemento VSTO para Excel o Word.  
  
 Para obtener más información, consulte [Cómo: agregar Windows Forms controles a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="use-windows-forms-controls"></a>Usar controles de Windows Forms  
 Puede agregar controles de Windows Forms a documentos y a elementos de interfaz de usuario (IU) personalizables, incluidos paneles de acciones, paneles de tareas personalizados y formularios de Windows Forms. Los controles de formularios de Windows Forms tienen generalmente el mismo comportamiento en documentos que en estos otros elementos de interfaz de usuario, pero existen algunas diferencias. Para obtener información, consulte [controla las limitaciones de los formularios Windows Forms en documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  
  
 La decisión de si desea agregar controles de formularios Windows Forms a un documento o algún otro elemento de interfaz de usuario depende de varios factores. Al diseñar la interfaz de usuario de la solución, considere los usos de los controles de formularios Windows Forms, como se describe en la tabla siguiente.  
  
 En un documento.  
 -   Si desea mostrar los controles todo el tiempo.  
  
- Si desea que los usuarios escriban datos directamente en el documento, por ejemplo, en documentos basados en formularios donde se bloquea la superficie de edición.  
  
- Si desea que los controles se muestren en consonancia con los datos del documento. Por ejemplo, si va a agregar botones a cada fila de un objeto de lista, desearía tenerlos en consonancia con cada elemento de la lista.  
  
  En el panel de acciones o en el panel de tareas personalizado.  
  -   Si desea proporcionar información contextual al usuario.  
  
- Si desea que solo aparezcan los resultados en el documento y no los controles ni los datos de consulta .  
  
- Si desea asegurarse de que los controles no se imprimen con el documento.  
  
- Si desea asegurarse de que los controles no interfieren con la vista del documento.  
  
  En un formulario de Windows Form.  
  -   Si desea controlar el tamaño de la interfaz de usuario.  
  
- Si desea impedir que los usuarios oculten o eliminen los controles.  
  
- Si desea obtener datos proporcionados por el usuario y evitar que el usuario realice cualquier acción en el documento hasta que se reciban estos datos.  
  
## <a name="add-windows-forms-controls-programmatically"></a>Agregar controles de formularios Windows Forms mediante programación  
 Puede agregar controles de formularios Windows Forms a documentos de Word y hojas de cálculo de Excel en tiempo de ejecución. El [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] proporciona métodos del asistente para agregar los controles de formularios de Windows Forms más comunes. Estos métodos del asistente permiten agregar rápidamente controles al documento de Office y obtener acceso a la funcionalidad combinada de control de formularios de Windows Forms y la funcionalidad relacionada con Office de estos controles.  
  
 Para obtener más información, consulte [agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="use-windows-forms-controls-in-document-level-projects"></a>Usar controles de formularios Windows Forms en proyectos de nivel de documento  
 Algunos aspectos del uso de controles de formularios de Windows Forms en documentos son únicos de los proyectos de nivel de documento, que le permiten diseñar la interfaz de usuario del documento mediante el Diseñador de Visual Studio.  
  
### <a name="create-custom-user-controls"></a>Crear controles de usuario personalizados  
 Puede agregar un control de usuario al proyecto y luego agregarlo al **Cuadro de herramientas**. Luego puede arrastrar el control de usuario directamente al documento de la misma manera que agregaría un control de formularios de Windows Forms al documento. Hay algunos aspectos que tener en cuenta al crear controles de usuario:  
  
-   No cree un control de usuario **sealed** . Al arrastrar el control a su documento, Visual Studio genera una clase contenedora derivada del control de usuario para extenderlo y permitir su uso en el documento. Si el control de usuario es **sealed**, Visual Studio no puede generar la clase contenedora.  
  
-   Los controles de usuario deben tener el atributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> establecido en **true**. Los controles de usuario creados dentro de un proyecto de Office tienen este atributo establecido en **true** de manera predeterminada, pero los controles de usuario que forman parte de proyectos externos pueden no tener este atributo establecido en **true**.  
  
-   Después de agregar un control de usuario al documento, no cambie el nombre ni elimine <xref:System.Windows.Forms.UserControl> la clase del proyecto. Si necesita cambiar el nombre de un control de usuario, debe eliminarlo primero del documento y luego agregarlo de nuevo después de cambiarle el nombre.  
  
### <a name="arrange-controls-at-design-time"></a>Organizar controles en tiempo de diseño  
 Si agrega varios controles a sus documentos de Word y Excel en tiempo de diseño, puede establecer rápidamente la alineación de todos los controles seleccionados mediante las barras de herramientas de **Microsoft Office Word** y **Microsoft Office Excel** en Visual Studio. Estas barras de herramientas solo están disponibles cuando un documento o una hoja de cálculo están abiertas en el diseñador.  
  
 Al seleccionar varios controles en el diseñador, puede utilizar los siguientes botones de estas barras de herramientas para organizar los controles:  
  
-   **Alinear lados izquierdos**  
  
-   **Alinear centros**  
  
-   **Alinear lados derechos**  
  
-   **Alinear lados superiores**  
  
-   **Alinear puntos medios**  
  
-   **Alinear lados inferiores**  
  
-   **Igualar espaciado horizontal**  
  
-   **Igualar espaciado vertical**  
  
> [!NOTE]  
>  En proyectos de Word, estos botones están habilitados solo si los controles seleccionados no están en línea con el texto. De forma predeterminada, los controles que se agregan al documento en tiempo de diseño están en línea con el texto.  
  
### <a name="prevent-old-data-from-appearing-in-excel-workbooks-during-loading"></a>Impedir que los datos antiguos aparezcan en los libros de Excel durante la carga  
 Al agregar controles de formularios de Windows Forms a documentos u hojas de cálculo en tiempo de diseño, los controles permanecen en el documento cuando el usuario cierra el documento. Los controles agregados en tiempo de diseño también se denominan *controles estáticos*.  
  
 Cuando se abre un libro de Excel que contiene controles estáticos, el libro presenta un mapa de bits del control en un control ActiveX hasta que el código de personalización se ejecute y cargue el control real. Excel crea este mapa de bits y lo almacena en el libro cada vez que se guarde el libro. El mapa de bits muestra el control tal como aparecía la última vez que se guardó el libro, incluidos los datos que estaba mostrando el control. Para obtener más información sobre el control ActiveX que contiene controles de formularios Windows Forms y mapas de bits, consulte [controla las limitaciones de los formularios Windows Forms en documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  
  
 En ciertas condiciones, el código no se carga y solo se muestra el mapa de bits, por ejemplo, cuando el usuario abre el libro en modo de diseño. Además, si el usuario abre el libro en un equipo que no tenga [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] instalado, no se puede ejecutar la personalización para cargar los controles y, por tanto, solo está visible el mapa de bits del control. Siempre debe quitar la información personal de los controles en los libros antes de guardar el libro y enviarlo a otro usuario para asegurarse de que su información personal no se revele accidentalmente.  
  
### <a name="match-control-size-to-cell-size-on-an-excel-worksheet"></a>Ajustar el tamaño del control al tamaño de la celda en una hoja de cálculo de Excel  
 Puede establecer el control para cambiar de tamaño automáticamente cuando se cambia el tamaño de la celda principal. Para obtener más información, consulte [Cómo: cambiar el tamaño de los controles dentro de las celdas de la hoja de cálculo](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### <a name="add-components-that-are-shared-by-all-worksheets"></a>Agregar componentes compartidos por todas las hojas de cálculo  
 Puede agregar componentes que desee compartir entre todas las hojas de cálculo, como un <xref:System.Data.DataSet>, al diseñador del libro en lugar de a las hojas de cálculo. El componente aparecerá en la bandeja de componentes.  
  
### <a name="formula-for-embedding-controls-on-an-excel-worksheet"></a>Fórmula para incrustar controles en una hoja de cálculo de Excel  
 Cuando seleccione un control en Excel, verá **=EMBED("WinForms.Control.Host","")** en la **Barra de fórmulas**. Este texto es necesario y no se debe eliminar.  
  
### <a name="layout-style-of-controls-on-a-word-document"></a>Estilo de diseño de controles en un documento de Word  
 Cuando se agrega un control al documento de Word en un proyecto de nivel de documento mediante el diseñador de Visual Studio, el control se agrega en línea con el texto. Para cambiar el estilo de diseño del control, haga doble clic en el control, y luego haga clic en **Formato de control**. Seleccione un estilo de ajuste en la página **Diseño** del cuadro de diálogo **Formato de objeto** .  
  
 Cuando se agrega un control a un documento de Word en tiempo de ejecución, puede especificar el estilo de diseño del nuevo control mediante el uso de diferentes `Add` \< *clase control*> sobrecargas del método de la <xref:Microsoft.Office.Tools.Word.ControlCollection> clase:  
  
- Para agregar el control en línea con el texto, use una sobrecarga que acepte un <xref:Microsoft.Office.Interop.Word.Range> que especifique la ubicación del control.  
  
- Para agregar el control como una forma flotante, use una sobrecarga que acepte las coordenadas superiores e izquierdas del control.  
  
  Para obtener más información, consulte [agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
  Si abre una plantilla de Word en el diseñador de Visual Studio, los controles no alineados en la plantilla podrían no verse, porque Visual Studio abre la plantilla en vista **Normal** . Para ver los controles, cambie la vista a **Diseño de impresión**.  
  
### <a name="controls-outside-the-main-document-body"></a>Controles fuera del cuerpo del documento principal  
 Los controles de formularios de Windows Forms no se admiten dentro de un encabezado o pie de página, ni dentro de un subdocumento.  
  
### <a name="add-components-at-design-time"></a>Agregar componentes en tiempo de diseño  
 Algunos controles o componentes no están visibles en el documento y, en su lugar, se muestran en una bandeja de componentes. Visual Studio proporciona una bandeja de componentes para cada ventana de documento. La bandeja de componentes aparece en la pantalla solo si existen componentes en el documento.  
  
## <a name="see-also"></a>Vea también  
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Información general sobre el panel de acciones](../vsto/actions-pane-overview.md)   
 [Controles de formularios Windows Forms](/dotnet/framework/winforms/controls/index)   
 [Limitaciones de los controles de Windows Forms en documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)   
 [Cómo: agregar controles de formularios Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Cómo: cambiar el tamaño de los controles dentro de las celdas de la hoja de cálculo](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Cómo: ocultar controles en hojas de cálculo al imprimir](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Tutorial: Cambiar el formato de hoja de cálculo utilizando controles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Tutorial: Cambiar el formato de un documento utilizando controles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)   
 [Tutorial: Mostrar texto en un cuadro de texto en una hoja de cálculo utilizando un botón](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Tutorial: Mostrar texto en un cuadro de texto en un documento utilizando un botón](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)   
 [Limitaciones de los controles de Windows Forms en documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)   
 [Tutorial: Actualizar un gráfico en un documento utilizando botones de radio](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)   
 [Tutorial: Actualizar un gráfico en una hoja de cálculo utilizando botones de radio](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  