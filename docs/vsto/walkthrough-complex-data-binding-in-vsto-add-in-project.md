---
title: 'Tutorial: Enlace de datos complejo en el proyecto de complemento de VSTO'
description: Obtenga información sobre cómo agregar controles a una hoja de cálculo de Microsoft Excel y enlazar los controles a datos en tiempo de ejecución.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], Excel
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 49f87968c545e9fcca7548cd2fbda866d18b660b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826361"
---
# <a name="walkthrough-complex-data-binding-in-vsto-add-in-project"></a>Tutorial: Enlace de datos complejo en el proyecto de complemento de VSTO
  Puede enlazar datos a controles host y controles de Windows Forms en proyectos de complemento de VSTO. En este tutorial se muestra cómo agregar controles a una hoja de cálculo de Microsoft Office Excel y enlazar los controles a datos en tiempo de ejecución.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Agregar un control <xref:Microsoft.Office.Tools.Excel.ListObject> a una hoja de cálculo en tiempo de ejecución.

- Crear un <xref:System.Windows.Forms.BindingSource> que conecta el control a una instancia de un conjunto de datos.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Acceso a una instancia en ejecución de SQL Server 2005 o SQL Server 2005 Express que tenga asociada la base de datos de ejemplo `AdventureWorksLT` . Puede descargar la base `AdventureWorksLT` de datos desde el repositorio SQL Server ejemplos de [GitHub](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Para obtener más información sobre cómo asociar una base de datos, vea los siguientes temas:

  - Para adjuntar una base de datos mediante SQL Server Management Studio o SQL Server Management Studio Express, vea Cómo: Adjuntar una base de datos [(SQL Server Management Studio).](/sql/relational-databases/databases/attach-a-database)

  - Para adjuntar una base de datos mediante la línea de comandos, vea [Cómo: Adjuntar un archivo de base](/previous-versions/sql/)de datos a SQL Server Express .

## <a name="create-a-new-project"></a>Crear un proyecto nuevo
 En primer lugar, es necesario crear un proyecto de complemento de VSTO para Excel.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de complemento de VSTO para Excel con el nombre **Rellenar hojas de cálculo de una base de datos**, mediante Visual Basic o C#.

     Para obtener más información, consulta [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio abre el archivo `ThisAddIn.vb` o `ThisAddIn.cs` y agrega el proyecto **Rellenar hojas de cálculo de una base de datos** al **Explorador de soluciones**.

## <a name="create-a-data-source"></a>Creación de un origen de datos
 Use la ventana **Orígenes de datos** para agregar un conjunto de datos con tipo al proyecto.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Para agregar un conjunto de datos con tipo al proyecto

1. Si la **ventana Orígenes de** datos no está visible, para mostrarla, en la barra de menús, elija **Ver** otros orígenes de  >  **datos** de Windows  >  .

2. Elija **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

3. Haga clic en **Base de datos** y luego en **Siguiente**.

4. Si ya tiene una conexión a la base de datos `AdventureWorksLT` , elija esa conexión y haga clic en **Siguiente**.

    De lo contrario, haga clic en **Nueva conexión** y use el cuadro de diálogo **Agregar conexión** para crear la nueva conexión. Para obtener más información, vea [Agregar nuevas conexiones.](../data-tools/add-new-connections.md)

5. En la página **Guardar cadena de conexión en el archivo de configuración de la aplicación** , haga clic en **Siguiente**.

6. En la página **Elegir los objetos de base de datos** expanda **Tablas** y seleccione **Dirección (SalesLT)**.

7. Haga clic en **Finalizar**

    El *archivo AdventureWorksLTDataSet.xsd* se agrega a **Explorador de soluciones**. Este archivo define los siguientes elementos:

   - Un conjunto de datos con tipo denominado `AdventureWorksLTDataSet`. Este conjunto de datos representa el contenido de la tabla **Dirección (SalesLT)** de la base de datos AdventureWorksLT.

   - Un TableAdapter denominado `AddressTableAdapter` . Este TableAdapter se puede usar para leer y escribir datos en `AdventureWorksLTDataSet` . Para obtener más información, vea [Introducción a TableAdapter.](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)

     Estos dos objetos se usarán más adelante en este tutorial.

## <a name="create-controls-and-bind-controls-to-data"></a>Creación de controles y enlace de controles a datos
 En este tutorial, el control <xref:Microsoft.Office.Tools.Excel.ListObject> muestra todos los datos en la tabla seleccionada en cuanto el usuario abre el libro. El objeto de lista usa <xref:System.Windows.Forms.BindingSource> para conectar el control a la base de datos.

 Para obtener más información sobre cómo enlazar controles a datos, vea [Enlazar datos a controles en soluciones de Office.](../vsto/binding-data-to-controls-in-office-solutions.md)

### <a name="to-add-the-list-object-dataset-and-table-adapter"></a>Para agregar el objeto de lista, el conjunto de datos y el adaptador de tabla

1. En la clase `ThisAddIn` , declare los siguientes controles para mostrar la tabla `Address` del conjunto de datos `AdventureWorksLTDataSet` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb" id="Snippet1":::

2. En el método `ThisAddIn_Startup` , agregue el siguiente código para inicializar el conjunto de datos y rellenarlo con la información del conjunto de datos `AdventureWorksLTDataSet` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb" id="Snippet2":::

3. Agregue el siguiente código al método `ThisAddIn_Startup`. Esto genera un elemento host que extiende la hoja de cálculo. Para obtener más información, vea Extender documentos de Word y libros de Excel en [complementos de VSTO en tiempo de ejecución.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb" id="Snippet3":::

4. Cree un rango y agregue el control <xref:Microsoft.Office.Tools.Excel.ListObject> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb" id="Snippet4":::

5. Enlace el objeto de lista a `AdventureWorksLTDataSet` mediante <xref:System.Windows.Forms.BindingSource>. Pase los nombres de las columnas que desea enlazar al objeto de lista.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb" id="Snippet5":::

## <a name="test-the-add-in"></a>Prueba del complemento
 Al abrir Excel, el control <xref:Microsoft.Office.Tools.Excel.ListObject> muestra los datos de la tabla `Address` del conjunto de datos `AdventureWorksLTDataSet` .

### <a name="to-test-the-vsto-add-in"></a>Para probar el complemento de VSTO

- Presione **F5**.

     Se creará un control <xref:Microsoft.Office.Tools.Excel.ListObject> denominado `addressListObject` en la hoja de cálculo. Al mismo tiempo, se agregan al proyecto un objeto de conjunto de datos denominado `adventureWorksLTDataSet` y una <xref:System.Windows.Forms.BindingSource> denominada `addressBindingSource` . El <xref:Microsoft.Office.Tools.Excel.ListObject> se enlaza a <xref:System.Windows.Forms.BindingSource>, que a su vez se enlaza al objeto de conjunto de datos.

## <a name="see-also"></a>Consulte también

- [Datos en soluciones de Office](../vsto/data-in-office-solutions.md)
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Cómo: Rellenar hojas de cálculo con datos de una base de datos](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Cómo: Rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Cómo: Rellenar documentos con datos de servicios](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Cómo: Rellenar documentos con datos de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Cómo: Desplazarse por los registros de base de datos de una hoja de cálculo](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Actualización de un origen de datos con datos de un control host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Tutorial: Enlace de datos simple en un proyecto de nivel de documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [Tutorial: Enlace de datos complejo en un proyecto de nivel de documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Información general sobre el uso de archivos de base de datos local en soluciones de Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md)
- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Información general sobre el uso de archivos de base de datos local en soluciones de Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Información general sobre el componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)
