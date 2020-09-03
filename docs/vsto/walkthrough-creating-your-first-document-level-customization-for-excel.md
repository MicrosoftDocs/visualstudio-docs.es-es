---
title: Crear la primera personalización de nivel de documento para Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Excel [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d45461c7dab250cd43d7a25d8693658c7b8e164
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "74566980"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-excel"></a>Tutorial: crear la primera personalización de nivel de documento para Excel

  Este tutorial introductorio muestra cómo crear una personalización de nivel de documento para Microsoft Office Excel. Las características que se crean en este tipo de solución solo están disponibles cuando se abre un libro concreto. No se puede usar una personalización de nivel de documento para realizar cambios en toda la aplicación, por ejemplo para mostrar una nueva pestaña de la cinta de opciones cuando se abre un libro.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Crear un proyecto de libro de Excel.

- Agregar texto a una hoja de cálculo que se hospeda en el diseñador de Visual Studio.

- Escribir código que usa el modelo de objetos de Excel para agregar texto a la hoja de cálculo personalizada cuando se abre.

- Compilar y ejecutar el proyecto para probarlo.

- Limpiar el proyecto completado para quitar los archivos de compilación innecesarios y la configuración de seguridad del equipo de desarrollo.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos

 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Crear el proyecto

### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>Para crear un nuevo proyecto de libro de Excel en Visual Studio

1. Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. En el menú **Archivo** , seleccione **Nuevo**y haga clic en **Proyecto**.
::: moniker range="vs-2017"
3. En el panel de plantillas, expanda **Visual C#** o **Visual Basic**y luego expanda **Office/SharePoint**.

4. En el nodo **Office/SharePoint** expandido, seleccione el nodo **Complementos de VSTO** .

5. En la lista de plantillas de proyecto, elija un proyecto de libro de Excel VSTO.

6. En el cuadro **nombre** , escriba **FirstWorkbookCustomization**.

7. Haga clic en **Aceptar**.

8. Seleccione **crear un nuevo documento** en el **Asistente para proyectos de Visual Studio Tools de Office**y haga clic en **Aceptar**.
::: moniker-end
::: moniker range=">=vs-2019"
3. En el cuadro de diálogo **crear un nuevo proyecto** , seleccione el proyecto de **libro de Excel VSTO** .

     [!INCLUDE[new-project-dialog-search](../vsto/includes/new-project-dialog-search-md.md)]

4. Haga clic en **Next**.

5. Escriba **FirstWorkbookCustomization** en el cuadro **nombre** del cuadro de diálogo **configurar el nuevo proyecto** y haga clic en **crear**.

6. Seleccione **crear un nuevo documento** en el **Asistente para proyectos de Visual Studio Tools de Office**y haga clic en **Aceptar**.
::: moniker-end
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea el proyecto **FirstWorkbookCustomization** y agrega los siguientes archivos al proyecto.

   - *FirstWorkbookCustomization*. xlsx: representa el libro de Excel en el proyecto. Contiene todas las hojas de cálculo y los gráficos.

   - Hoja1 (archivo *. VB* para Visual Basic o archivo *. CS* para Visual C#): hoja de cálculo que proporciona la superficie de diseño y el código de la primera hoja de cálculo del libro. Para obtener más información, vea [elemento host de hoja de cálculo](../vsto/worksheet-host-item.md).

   - Hoja2 (archivo *. VB* para Visual Basic o archivo *. CS* para Visual C#): hoja de cálculo que proporciona la superficie de diseño y el código para la segunda hoja de cálculo del libro.

   - Sheet3 (archivo *. VB* para Visual Basic o archivo *. CS* para Visual C#): hoja de cálculo que proporciona la superficie de diseño y el código para la tercera hoja de cálculo del libro.

   - ThisWorkbook (archivo *. VB* para Visual Basic o archivo *. CS* para Visual C#): contiene la superficie de diseño y el código para las personalizaciones de nivel de libro. Para obtener más información, vea [Workbook host Item](../vsto/workbook-host-item.md).

     El archivo de código Sheet1 se abre automáticamente en el diseñador.

## <a name="close-and-reopen-worksheets-in-the-designer"></a>Cerrar y volver a abrir las hojas de cálculo en el diseñador

 Puede volver a abrir el libro o la hoja de cálculo si los cierra deliberada o accidentalmente en el diseñador mientras está desarrollando el proyecto.

### <a name="to-close-and-reopen-a-worksheet-in-the-designer"></a>Para cerrar y volver a abrir una hoja de cálculo en el diseñador

1. Cierre el libro haciendo clic en el botón **cerrar** (X) de la ventana del diseñador.

2. En **Explorador de soluciones**, haga clic con el botón secundario en el archivo de código **Hoja1** y haga clic en **Diseñador de vistas**.

     \- o -

     En **Explorador de soluciones**, haga doble clic en el archivo de código **Hoja1** .

## <a name="add-text-to-a-worksheet-in-the-designer"></a>Agregar texto a una hoja de cálculo en el diseñador

 Puede diseñar la interfaz de usuario de la personalización modificando la hoja de cálculo que está abierta en el diseñador. Por ejemplo, puede agregar texto a las celdas, aplicar fórmulas o agregar controles de Excel. Para obtener más información sobre cómo usar el diseñador, vea [proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>Para agregar texto a la hoja de cálculo mediante el diseñador

1. En la hoja de cálculo que está abierta en el diseñador, seleccione la celda **a1**y escriba el texto siguiente.

     **Este texto se agregó mediante el diseñador.**

> [!WARNING]
> Si agrega esta línea de texto a la celda **a2**, otro código de este ejemplo lo sobrescribirá.

## <a name="add-text-to-a-worksheet-programmatically"></a>Agregar texto a una hoja de cálculo mediante programación

 A continuación, agregue código al archivo de código Sheet1. El nuevo código usa el modelo de objetos de Excel para agregar una segunda línea de texto al libro. De forma predeterminada, el archivo de código Sheet1 contiene el siguiente código generado:

- Una definición parcial de la clase `Sheet1`, que representa el modelo de programación de la hoja de cálculo y proporciona acceso al modelo de objetos de Excel. Para obtener más información, [elemento host de hoja de cálculo](../vsto/worksheet-host-item.md) y [información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md). El resto de la clase `Sheet1` se define en un archivo de código oculto que no se debe modificar.

- Los controladores de eventos `Sheet1_Startup` y `Sheet1_Shutdown` . Se llama a estos controladores de eventos cuando Excel carga y descarga la personalización. Use estos controladores de eventos para inicializar la personalización cuando se cargue y para limpiar los recursos que usa la personalización cuando se descargue. Para obtener más información, vea [eventos en proyectos de Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>Para agregar una segunda línea de texto a la hoja de cálculo mediante código

1. En **Explorador de soluciones**, haga clic con el botón secundario en **Hoja1**y, a continuación, haga clic en **Ver código**.

     El archivo de código se abre en Visual Studio.

2. Reemplace el controlador de eventos `Sheet1_Startup` por el siguiente código: Cuando se abre Sheet1, este código agrega una segunda línea de texto a la hoja de cálculo.

     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb#1)]

## <a name="test-the-project"></a>Prueba del proyecto

### <a name="to-test-your-workbook"></a>Para probar el libro

1. Presione **F5** para compilar y ejecutar el proyecto.

     Al compilar el proyecto, el código se compila en un ensamblado que está asociado al libro. Visual Studio coloca una copia del libro y el ensamblado en la carpeta de resultados de compilación del proyecto y establece la configuración de seguridad en el equipo de desarrollo para permitir que se ejecute la personalización. Para obtener más información, vea [compilar soluciones de Office](../vsto/building-office-solutions.md).

2. En el libro, compruebe que ve el texto siguiente.

     **Este texto se agregó mediante el diseñador.**

     **Este texto se agregó mediante código.**

3. Cierre el libro.

## <a name="clean-up-the-project"></a>Limpiar el proyecto

 Cuando termine de desarrollar un proyecto, debe quitar los archivos de la carpeta de resultados de compilación y la configuración de seguridad creada por el proceso de compilación.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Para limpiar el proyecto completado en el equipo de desarrollo

1. En el menú **Crear** de Visual Studio, haga clic en **Limpiar solución**.

## <a name="next-steps"></a>Pasos siguientes

 Ahora que ha creado una personalización de nivel de documento básico para Excel, en los siguientes temas obtendrá más información sobre cómo desarrollar personalizaciones:

- Tareas de programación generales que puede realizar en las personalizaciones de nivel de documento: [personalizaciones de nivel de documento de programa](../vsto/programming-document-level-customizations.md).

- Tareas de programación específicas de las personalizaciones de nivel de documento para Excel: [soluciones de Excel](../vsto/excel-solutions.md).

- Usar el modelo de objetos de Excel: [información general sobre el modelo de objetos de Excel](../vsto/excel-object-model-overview.md).

- Personalización de la interfaz de usuario de Excel, por ejemplo, agregando una pestaña personalizada a la cinta de opciones o creando su propio panel de acciones: [Personalización](../vsto/office-ui-customization.md)de la interfaz de usuario de Office.

- Usar objetos de Excel extendidos proporcionados por las herramientas de desarrollo de Office en Visual Studio para realizar tareas que no son posibles mediante el uso del modelo de objetos de Excel (por ejemplo, hospedar controles administrados en documentos y enlazar controles de Excel a los datos mediante el modelo de enlace de datos de Windows Forms): [automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md).

- Compilar y depurar personalizaciones de nivel de documento para Excel: [compilar soluciones de Office](../vsto/building-office-solutions.md).

- Implementar personalizaciones de nivel de documento para Excel: [implementar una solución de Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Consulte también

- [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Soluciones de Excel](../vsto/excel-solutions.md)
- [Personalizaciones de nivel de documento de programa](../vsto/programming-document-level-customizations.md)
- [Información general del modelo de objetos de Excel](../vsto/excel-object-model-overview.md)
- [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)
- [Compilar soluciones de Office](../vsto/building-office-solutions.md)
- [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)
- [Información general de plantillas de proyecto de Office](../vsto/office-project-templates-overview.md)
