---
title: Proyectos de Office en el entorno de Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.WordDocument
- VST.ProjectItem.ExcelWorkbook
- VST.ProjectItem.ExcelTemplate
- VST.ProjectItem.ExcelSheet
- VST.ProjectItem.BlueprintCode
- VST.ProjectItem.Word
- VST.ProjectItem.Excel
- VST.ProjectItem.AddinProject
- Designer_Microsoft.VisualStudio.OfficeTools.Excel.Design.WorksheetDesigner
- VST.ProjectItem.ExtendedBluePrint
- VST.ProjectItem.WordTemplate
- Designer_Microsoft.VisualStudio.OfficeTools.Word.Design.DocumentDesigner
- VST.Designer.ExcelVST.Designer.Word
- VST.ProjectItem.ExtendedBlueprintCode
- VST.ProjectItem.BluePrint
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- hidden files [Office development in Visual Studio]
- project files [Office development in Visual Studio], hidden
- Office development in Visual Studio, documents in Visual Studio
- design view, Excel
- designers, Office development in Visual Studio
- Office documents [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], about documents in Visual Studio
- designers [Office development in Visual Studio]
- Word designer
- Word [Office development in Visual Studio], Word designer
- Visual Studio, Office documents in
- worksheets [Office development in Visual Studio]
- VST.Designer.ExcelVST.Designer.Word
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 80a8f866cb43eb6279cca45bebc94c54af898eab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="office-projects-in-the-visual-studio-environment"></a>Proyectos de Office en el entorno de Visual Studio
  Los proyectos de Microsoft Office tienen una experiencia de desarrollo que es similar a otros tipos de proyectos en Visual Studio, como los proyectos de Windows Forms. Al crear o abrir un proyecto de Office, los elementos del proyecto aparecen en el **Explorador de soluciones**. Para los proyectos en el nivel de documento, el documento (es decir, el documento de Word o el libro de Excel) se abre en Visual Studio y se comporta como un diseñador visual.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="project-items-in-solution-explorer"></a>Elementos de proyecto en el Explorador de soluciones  
 En un proyecto de nivel de documento, el **Explorador de soluciones** muestra los siguientes elementos predeterminados:  
  
-   Nodos del documento, el libro y las hojas que son personalizados por el proyecto. Estos nodos actúan como contenedores para los archivos de código que están asociados al documento, el libro y las hojas.  
  
-   Los archivos de código que están asociados al documento, el libro y las hojas que son personalizados por el proyecto. En proyectos de Word, los archivos de código están asociados al documento o plantilla de Word. En los proyectos de Excel, los archivos de código están asociados al libro o plantilla de Excel, y a cada hoja de cálculo y hoja de gráfico del libro o plantilla.  
  
-   Los archivos de proyecto ocultos que no piensa editar directamente. Para obtener más información, vea [Archivos de proyecto ocultos](#hiddenfiles).  
  
 En un proyecto de complemento VSTO, el **Explorador de soluciones** muestra los siguientes elementos predeterminados:  
  
-   El nodo de la aplicación. Este nodo tiene el mismo nombre que la aplicación host, como **Word**, **Excel**u **Outlook**. El nodo de la aplicación contiene el archivo de código ThisAddIn. También proporciona la propiedad **Espacio de nombres para el elemento host** . Para obtener más información sobre esta propiedad, consulte [Properties in Office Projects](../vsto/properties-in-office-projects.md).  
  
-   El archivo de código ThisAddIn. Este archivo contiene la clase `ThisAddIn` generada para el complemento VSTO. Para obtener más información acerca de esta clase, vea [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   Los archivos de proyecto ocultos que no piensa editar directamente. Para obtener más información, vea [Archivos de proyecto ocultos](#hiddenfiles).  
  
### <a name="temporary-certificates"></a>Certificados temporales  
 Los proyectos de Office también incluyen un certificado temporal denominado *NombreDeProyecto*_TemporaryKey.pfx. Este certificado se usa para firmar los manifiestos de implementación y aplicación para el proyecto durante el desarrollo. Para obtener más información, consulte [otorgar confianza a las soluciones de Office](../vsto/granting-trust-to-office-solutions.md) y [proteger soluciones de Office](../vsto/securing-office-solutions.md).  
  
###  <a name="hiddenfiles"></a> Archivos de proyecto ocultos  
 Hay varios archivos de proyecto que están ocultos de manera predeterminada. Visual Studio genera estos archivos, que son diferentes según el tipo de proyecto. Para mostrar los archivos ocultos, haga clic en **Mostrar todos los archivos** en el **Explorador de soluciones**.  
  
 No modifique los archivos de proyecto ocultos. No se permite la modificación directa de estos archivos, ya que se puede dañar el proyecto. Los archivos de proyecto ocultos vuelven a generarse por completo cuando se producen determinados cambios en el documento. Si realiza cambios manuales en un archivo de proyecto oculto, se pierden cuando se regenera el archivo.  
  
## <a name="document-designer-in-document-level-projects"></a>Diseñador de documentos en los proyectos de nivel de documento  
 Los proyectos de nivel de documento para Excel y Word proporcionan un diseñador que hospeda el documento que está asociado al proyecto en Visual Studio. El diseñador permite modificar el documento sin tener que salir del entorno de Visual Studio.  
  
 Para abrir un documento en el diseñador, haga doble clic en el archivo de código que está asociado al documento en el **Explorador de soluciones** . Por ejemplo, para abrir la hoja de cálculo **Sheet1** en el diseñador en un proyecto de Excel, haga doble clic en el archivo de código **Sheet1** .  
  
 Al modificar el documento en el diseñador, puede aprovechar las ventajas de la funcionalidad nativa de la aplicación de Office. Por ejemplo, puede escribir texto en el documento o la hoja de cálculo, o puede usar la Cinta de opciones para realizar tareas como agregar una tabla o un gráfico. La asignación de métodos abreviados de teclado es la de Visual Studio de forma predeterminada. Para usar en su lugar las asignaciones de métodos abreviados de teclado de Office, cambie los valores que se encuentran bajo el nodo **Configuración de teclado de Microsoft Office** , en el cuadro de diálogo **Opciones** del menú **Herramientas** .  
  
### <a name="controls-on-documents"></a>Controles en documentos  
 Puede arrastrar *controles host* y controles de Windows Forms del **Cuadro de herramientas** de Visual Studio a la superficie de diseño del documento. Los controles host son versiones especializadas de los objetos de Office, como controles de contenido de Word y rangos de Excel, que se pueden usar en los proyectos de Office creados con Visual Studio. Los controles host tienen características adicionales que no están disponibles en los objetos de Office correspondientes, como el enlace de datos y eventos adicionales.  
  
 Para obtener más información, vea [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md) y [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
### <a name="excel-worksheets-and-workbooks-in-the-designer"></a>Hojas de cálculo y libros de Excel en el diseñador  
 Al abrir una hoja de cálculo en el diseñador, puede modificarla del mismo modo que cuando está abierta directamente en Excel. Si se hace doble clic en una celda de una hoja de cálculo, la celda cambia al modo de edición. Si se hace doble clic en una celda que contiene un control host, el editor de código se abre y Visual Studio genera el controlador de eventos predeterminado para el control. Para navegar a otras hojas de cálculo, puede hacer clic en las pestañas de la hoja de cálculo en la parte inferior del diseñador.  
  
 Al abrir el libro en el diseñador, no hay ninguna superficie de diseño. La vista de diseño del libro es una gran bandeja de componentes que ocupa todo el diseñador.  
  
 El libro y cada hoja del libro tienen un archivo de código asociado. Cada archivo de código contiene una clase de *elemento host* generada que representa el libro o la hoja. Para obtener más información, consulta [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md).  
  
### <a name="word-documents-in-the-designer"></a>Documentos de Word en el diseñador  
 Al abrir el documento en el diseñador, puede modificarlo del mismo modo que cuando está abierto directamente en Word. Si hace doble clic en una palabra del documento, esa palabra se selecciona. Sin embargo, si la palabra está dentro de un control host, el editor de código se abre y Visual Studio genera el controlador de eventos predeterminado para el control.  
  
 El documento tiene un archivo de código asociado. El archivo de código contiene una clase de *elemento host* generada que representa el documento. Para obtener más información, consulta [Document Host Item](../vsto/document-host-item.md).  
  
### <a name="design-mode-vs-run-time-mode"></a>Modo de diseño frente a Modo en tiempo de ejecución  
 Cuando se abre un documento en el entorno de Visual Studio, siempre es en *modo de diseño*. Algunas tareas, como arrastrar un control host hacia la superficie del documento, solo se pueden realizar en modo de diseño.  
  
 Para ver el documento en *modo en tiempo de ejecución*, debe abrir la aplicación y el documento fuera de Visual Studio. También tiene la posibilidad de compilar y ejecutar el proyecto, con lo que se abrirán automáticamente el documento y la aplicación fuera de Visual Studio.  
  
## <a name="code-editor"></a>Editor de código  
 El Editor de código permite ver y modificar los archivos de código visibles en la solución. Estos archivos contienen el código que define el comportamiento de la solución.  
  
 Para obtener más información sobre el Editor de código, vea [escribir código en el Editor de texto y código](/visualstudio/ide/writing-code-in-the-code-and-text-editor). Para obtener más información sobre cómo escribir código en proyectos de Office, consulte [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="properties-window"></a>Ventana Propiedades  
 La ventana **Propiedades** muestra las propiedades de los elementos de proyecto que están seleccionados en el **Explorador de soluciones**y los elementos de la interfaz de usuario que están seleccionados en el diseñador, como los controles o el documento en un proyecto de nivel de documento. Algunas propiedades son específicas de la aplicación y el documento, mientras que otras son iguales en todos los proyectos.  
  
## <a name="data-sources-window"></a>Ventana Orígenes de datos  
 Puede usar la ventana **Orígenes de datos** en los proyectos de Office de nivel de documento para arrastrar un origen de datos a su documento y crear un control enlazado al origen de datos. Para obtener más información, consulte [enlazar controles a datos en Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).  
  
## <a name="see-also"></a>Vea también  
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Información general de plantillas de proyecto de Office](../vsto/office-project-templates-overview.md)   
 [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Propiedades de los proyectos de Office](../vsto/properties-in-office-projects.md)  
  
  