---
title: 'Tutorial: Creación del primer complemento de VSTO para Excel'
description: Cree un complemento de nivel de aplicación para Microsoft Excel. Las características que cree están disponibles para la propia aplicación, independientemente de qué libros estén abiertos.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Excel [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fcb2bcc91eb1d19309904caae16701b814113089
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824411"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-excel"></a>Tutorial: Creación del primer complemento de VSTO para Excel
  Este tutorial introductorio muestra cómo crear un complemento de nivel de aplicación para Microsoft Office Excel. Las características que cree en este tipo de solución estarán disponibles para la propia aplicación, con independencia de los libros que se abran.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 En este tutorial se muestran las tareas siguientes:

- Crear un proyecto de complemento de VSTO para Excel.

- Escribir código que usa el modelo de objetos de Excel para agregar texto un libro cuando se guarda.

- Compilar y ejecutar el proyecto para probarlo.

- Limpiar el proyecto completado para que el complemento de VSTO deje de ejecutarse automáticamente en el equipo de desarrollo.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Creación del proyecto

#### <a name="to-create-a-new-excel-vsto-add-in-project-in-visual-studio"></a>Para crear un nuevo proyecto de complemento de VSTO en Visual Studio

1. Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. En el menú **Archivo** , elija **Nuevo** y haga clic en **Proyecto**.

3. En el panel de plantillas, expanda **Visual C#** o **Visual Basic** y luego expanda **Office/SharePoint**.

4. En el nodo **Office/SharePoint** expandido, seleccione el nodo **Complementos de Office** .

5. En la lista de plantillas de proyecto, seleccione **Complemento de Excel 2010** o **Complemento de Excel 2013**.

6. En el cuadro **Nombre** , escriba **FirstExcelAddIn**.

7. Haga clic en **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea el **proyecto FirstExcelAddIn** y abre el archivo de código ThisAddIn en el editor.

## <a name="write-code-to-add-text-to-the-saved-workbook"></a>Escribir código para agregar texto al libro guardado
 A continuación, agregue código al archivo de código ThisAddIn. El nuevo código utiliza el modelo de objetos de Excel para insertar texto reutilizable en la primera fila de la hoja de cálculo activa. La hoja de cálculo activa es la hoja de cálculo que está abierta cuando el usuario guarda el libro. De forma predeterminada, el archivo de código ThisAddIn contiene el siguiente código generado:

- Una definición parcial de la clase `ThisAddIn` . Esta clase proporciona un punto de entrada para el código y proporciona acceso al modelo de objetos de Excel. Para obtener más información, [vea Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md). El resto de la `ThisAddIn` clase se define en un archivo de código oculto que no debe modificar.

- Los controladores de eventos `ThisAddIn_Startup` y `ThisAddIn_Shutdown` . Se llama a estos controladores de eventos cuando Excel carga y descarga el complemento de VSTO. Use estos controladores de eventos para inicializar el complemento de VSTO cuando se cargue y para limpiar los recursos que usa el complemento cuando se descargue. Para obtener más información, vea [Eventos en proyectos de Office.](../vsto/events-in-office-projects.md)

### <a name="to-add-a-line-of-text-to-the-saved-workbook"></a>Para agregar una línea de texto al libro guardado

1. En el archivo de código ThisAddIn, agregue el código siguiente a la clase `ThisAddIn` . El nuevo código define un controlador de eventos para el evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> , que se desencadena cuando se guarda un libro.

    Cuando el usuario guarda un libro, el controlador de eventos agrega el nuevo texto al principio de la hoja de cálculo activa.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelAddInTutorial/ThisAddIn.vb" id="Snippet1":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs" id="Snippet1":::

2. Si está utilizando C#, agregue el siguiente código necesario para el controlador de eventos `ThisAddIn_Startup` . Este código se utiliza para conectar el controlador de eventos `Application_WorkbookBeforeSave` con el evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs" id="Snippet2":::

   Para modificar el libro cuando se guarda, los ejemplos de código anteriores utilizan los siguientes objetos:

- El campo `Application` de la clase `ThisAddIn` . El campo `Application` devuelve un objeto <xref:Microsoft.Office.Interop.Excel.Application> que representa la instancia actual de Excel.

- El parámetro `Wb` del controlador de eventos para el evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> . El parámetro `Wb` es un objeto <xref:Microsoft.Office.Interop.Excel.Workbook> que representa el libro guardado. Para obtener más información, vea Información [general del modelo de objetos de Excel.](../vsto/excel-object-model-overview.md)

## <a name="test-the-project"></a>Prueba del proyecto

### <a name="to-test-the-project"></a>Para probar el proyecto

1. Presione **F5** para compilar y ejecutar el proyecto.

     Al compilar el proyecto, el código se compila en un ensamblado que se incluye en la carpeta de salida de compilación del proyecto. Visual Studio crea también un conjunto de entradas del registro que permiten que Excel detecte y cargue el complemento de VSTO, y establece la configuración de seguridad en el equipo de desarrollo para permitir la ejecución del complemento de VSTO. Para obtener más información, vea [Compilar soluciones de Office.](../vsto/building-office-solutions.md)

2. En Excel, guarde el libro.

3. Compruebe que el texto siguiente se agrega al libro.

     **Este texto se agregó mediante código.**

4. Cierre Excel.

## <a name="clean-up-the-project"></a>Limpieza del proyecto
 Cuando termine de desarrollar un proyecto, quite el ensamblado del complemento de VSTO, las entradas del registro y la configuración de seguridad del equipo de desarrollo. De lo contrario, el complemento de VSTO se ejecutará cada vez que abra Excel en el equipo de desarrollo.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Para limpiar el proyecto completado en el equipo de desarrollo

1. En el menú **Crear** de Visual Studio, haga clic en **Limpiar solución**.

## <a name="next-steps"></a>Pasos siguientes
 Ahora que ha creado un complemento básico de VSTO para Excel, puede obtener más información sobre cómo desarrollar complementos de VSTO en estos temas:

- Tareas generales de programación que puede realizar en complementos de VSTO: [Complementos vsTO del programa](../vsto/programming-vsto-add-ins.md).

- Tareas de programación específicas de complementos vsTO de Excel: [soluciones de Excel](../vsto/excel-solutions.md).

- Uso del modelo de objetos de Excel: Información [general del modelo de objetos de Excel.](../vsto/excel-object-model-overview.md)

- Personalizar la interfaz de usuario (UI) de Excel, por ejemplo, agregando una pestaña personalizada a la cinta de opciones o creando su propio panel de tareas personalizado: personalización de la interfaz de usuario [de Office.](../vsto/office-ui-customization.md)

- Compilación y depuración de complementos VSTO para Excel: [compilar soluciones de Office](../vsto/building-office-solutions.md).

- Implementación de complementos de VSTO para Excel: [implemente una solución de Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Consulte también
- [Introducción al desarrollo de soluciones de Office &#40;vsto&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Soluciones de Excel](../vsto/excel-solutions.md)
- [Programas de complementos VSTO](../vsto/programming-vsto-add-ins.md)
- [Introducción al modelo de objetos de Excel](../vsto/excel-object-model-overview.md)
- [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)
- [Compilación de soluciones de Office](../vsto/building-office-solutions.md)
- [Implementación de una solución de Office](../vsto/deploying-an-office-solution.md)
- [Introducción a las plantillas de proyecto de Office](../vsto/office-project-templates-overview.md)
