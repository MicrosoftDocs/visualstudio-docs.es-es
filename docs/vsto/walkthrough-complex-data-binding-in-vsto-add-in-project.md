---
title: 'Tutorial: Enlace de datos complejos en el proyecto de complemento VSTO'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], Excel
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fd034f4802679daa442f04b469a37f04d580ea94
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758945"
---
# <a name="walkthrough-complex-data-binding-in-vsto-add-in-project"></a>Tutorial: Enlace de datos complejos en el proyecto de complemento VSTO
  Puede enlazar datos a controles host y controles de Windows Forms en proyectos de complemento de VSTO. En este tutorial se muestra cómo agregar controles a una hoja de cálculo de Microsoft Office Excel y enlazar los controles a datos en tiempo de ejecución.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

 En este tutorial se muestran las tareas siguientes:

-   Agregar un <xref:Microsoft.Office.Tools.Excel.ListObject> control a una hoja de cálculo en tiempo de ejecución.

-   Crear un <xref:System.Windows.Forms.BindingSource> que conecta el control a una instancia de un conjunto de datos.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesita los componentes siguientes para completar este tutorial:

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

-   Acceso a una instancia en ejecución de SQL Server 2005 o SQL Server 2005 Express que tenga asociada la base de datos de ejemplo `AdventureWorksLT` . Puede descargar el `AdventureWorksLT` desde la base de datos la [sitio Web de CodePlex](http://go.microsoft.com/fwlink/?LinkId=115611). Para obtener más información sobre cómo asociar una base de datos, vea los siguientes temas:

    -   Para adjuntar una base de datos mediante SQL Server Management Studio o SQL Server Management Studio Express, vea [Cómo: adjuntar una base de datos (SQL Server Management Studio)](http://msdn.microsoft.com/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).

    -   Para adjuntar una base de datos mediante la línea de comandos, consulte [Cómo: adjuntar un archivo de base de datos a SQL Server Express](http://msdn.microsoft.com/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).

## <a name="create-a-new-project"></a>Crear un proyecto nuevo
 En primer lugar, es necesario crear un proyecto de complemento de VSTO para Excel.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1.  Cree un proyecto de complemento de VSTO para Excel con el nombre **Rellenar hojas de cálculo de una base de datos**, mediante Visual Basic o C#.

     Para obtener más información, consulta [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio abre el archivo `ThisAddIn.vb` o `ThisAddIn.cs` y agrega el proyecto **Rellenar hojas de cálculo de una base de datos** al **Explorador de soluciones**.

## <a name="create-a-data-source"></a>Crear un origen de datos
 Use la ventana **Orígenes de datos** para agregar un conjunto de datos con tipo al proyecto.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Para agregar un conjunto de datos con tipo al proyecto

1.  Si el **orígenes de datos** ventana no está visible, muéstrela; en la barra de menús, elija **vista** > **Other Windows**  >   **Orígenes de datos**.

2.  Elija **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

3.  Haga clic en **Base de datos**y luego en **Siguiente**.

4.  Si ya tiene una conexión a la base de datos `AdventureWorksLT` , elija esa conexión y haga clic en **Siguiente**.

     De lo contrario, haga clic en **Nueva conexión**y use el cuadro de diálogo **Agregar conexión** para crear la nueva conexión. Para obtener más información, consulte [agregar nuevas conexiones](../data-tools/add-new-connections.md).

5.  En la página **Guardar cadena de conexión en el archivo de configuración de la aplicación** , haga clic en **Siguiente**.

6.  En la página **Elegir los objetos de base de datos** expanda **Tablas** y seleccione **Dirección (SalesLT)**.

7.  Haga clic en **Finalizar**.

     El *AdventureWorksLTDataSet.xsd* archivo se agrega a **el Explorador de soluciones**. Este archivo define los siguientes elementos:

    -   Un conjunto de datos con tipo denominado `AdventureWorksLTDataSet`. Este conjunto de datos representa el contenido de la tabla **Dirección (SalesLT)** de la base de datos AdventureWorksLT.

    -   Un TableAdapter llamado `AddressTableAdapter`. Este TableAdapter puede usarse para leer y escribir datos el `AdventureWorksLTDataSet`. Para obtener más información, consulte [información general sobre TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Estos dos objetos se usarán más adelante en este tutorial.

## <a name="create-controls-and-bind-controls-to-data"></a>Crear controles y enlazar controles a datos
 En este tutorial, el control <xref:Microsoft.Office.Tools.Excel.ListObject> muestra todos los datos en la tabla seleccionada en cuanto el usuario abre el libro. El objeto de lista usa <xref:System.Windows.Forms.BindingSource> para conectar el control a la base de datos.

 Para obtener más información acerca de los controles de enlace a datos, vea [enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-add-the-list-object-dataset-and-table-adapter"></a>Para agregar el objeto de lista, el conjunto de datos y el adaptador de tabla

1.  En la clase `ThisAddIn` , declare los siguientes controles para mostrar la tabla `Address` del conjunto de datos `AdventureWorksLTDataSet` .

     [!code-csharp[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#1)]

2.  En el método `ThisAddIn_Startup` , agregue el siguiente código para inicializar el conjunto de datos y rellenarlo con la información del conjunto de datos `AdventureWorksLTDataSet` .

     [!code-csharp[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#2)]

3.  Agregue el código siguiente al método `ThisAddIn_Startup` . Esto genera un elemento host que extiende la hoja de cálculo. Para obtener más información, consulte [documentos ampliar Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

     [!code-csharp[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#3)]

4.  Cree un rango y agregue el control <xref:Microsoft.Office.Tools.Excel.ListObject> .

     [!code-csharp[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#4)]

5.  Enlace el objeto de lista a `AdventureWorksLTDataSet` mediante <xref:System.Windows.Forms.BindingSource>. Pase los nombres de las columnas que desea enlazar al objeto de lista.

     [!code-csharp[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#5)]

## <a name="test-the-add-in"></a>Probar el complemento
 Al abrir Excel, el control <xref:Microsoft.Office.Tools.Excel.ListObject> muestra los datos de la tabla `Address` del conjunto de datos `AdventureWorksLTDataSet` .

### <a name="to-test-the-vsto-add-in"></a>Para probar el complemento de VSTO

-   Presione **F5**.

     Se creará un control <xref:Microsoft.Office.Tools.Excel.ListObject> denominado `addressListObject` en la hoja de cálculo. Al mismo tiempo, se agregan al proyecto un objeto de conjunto de datos denominado `adventureWorksLTDataSet` y una <xref:System.Windows.Forms.BindingSource> denominada `addressBindingSource` . El <xref:Microsoft.Office.Tools.Excel.ListObject> se enlaza a <xref:System.Windows.Forms.BindingSource>, que a su vez se enlaza al objeto de conjunto de datos.

## <a name="see-also"></a>Vea también

- [Datos en soluciones de Office](../vsto/data-in-office-solutions.md)
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Cómo: Rellenar hojas de cálculo con datos de una base de datos](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Cómo: rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Cómo: rellenar documentos con datos de servicios](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Cómo: rellenar documentos con datos de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Cómo: desplazarse por los registros de base de datos en una hoja de cálculo](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Cómo: actualizar un origen de datos con datos de un control host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Tutorial: Enlace de datos Simple en un proyecto de nivel de documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [Tutorial: Enlace de datos complejo en un proyecto de nivel de documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Usar archivos de base de datos local en información general sobre soluciones de Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md)
- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Usar archivos de base de datos local en información general sobre soluciones de Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Información general del componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)