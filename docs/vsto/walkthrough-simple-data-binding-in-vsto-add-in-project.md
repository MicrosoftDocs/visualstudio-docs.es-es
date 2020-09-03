---
title: 'Tutorial: enlace de datos simple en un proyecto de complemento de VSTO'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- data binding [Office development in Visual Studio], Word
- data [Office development in Visual Studio], simple binding data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bcfb150cc0b97b72fd0f6eac02f59ae1db3e9ca6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985404"
---
# <a name="walkthrough-simple-data-binding-in-vsto-add-in-project"></a>Tutorial: enlace de datos simple en un proyecto de complemento de VSTO

Puede enlazar datos a controles host y controles de Windows Forms en proyectos de complemento de VSTO. En este tutorial se muestra cómo se agregan controles a un documento de Microsoft Office Word y cómo se enlazan los controles a datos en tiempo de ejecución.

[!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

En este tutorial se muestran las tareas siguientes:

- Agregar un elemento <xref:Microsoft.Office.Tools.Word.ContentControl> a un documento en tiempo de ejecución.

- Crear un <xref:System.Windows.Forms.BindingSource> que conecta el control a una instancia de un conjunto de datos.

- Permitir al usuario que se desplace por los registros y visualizarlos en el control.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos

Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- Acceso a una instancia en ejecución de SQL Server 2005 o SQL Server 2005 Express que tenga asociada la base de datos de ejemplo `AdventureWorksLT` . Puede descargar la `AdventureWorksLT` base de datos desde el [repositorio de github de ejemplos de SQL Server](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Para obtener más información sobre cómo asociar una base de datos, vea los siguientes temas:

  - Para adjuntar una base de datos mediante SQL Server Management Studio o SQL Server Management Studio Express, consulte [Cómo: adjuntar una base de datos (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Para adjuntar una base de datos mediante la línea de comandos, vea [Cómo: adjuntar un archivo de base de datos a SQL Server Express](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Creación de un nuevo proyecto

El primer paso es crear un proyecto de complemento de VSTO de Word.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de complemento de VSTO para Word con el nombre **Rellenar documentos desde una base de datos**, mediante Visual Basic o C#.

     Para obtener más información, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio abre el archivo *ThisAddIn. VB* o *ThisAddIn.CS* y agrega el proyecto **rellenar documentos desde una base de datos** a **Explorador de soluciones**.

2. Si el proyecto tiene como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , agregue una referencia al ensamblado *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* . Esta referencia es obligatoria para agregar mediante programación controles de Windows Forms al documento más adelante en este tutorial.

## <a name="create-a-data-source"></a>Creación de un origen de datos

Use la ventana **Orígenes de datos** para agregar un conjunto de datos con tipo al proyecto.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Para agregar un conjunto de datos con tipo al proyecto

1. Si la ventana **orígenes de datos** no está visible, puede mostrarla en la barra de menús y elegir **Ver**  >  **otros**  >  **orígenes de datos**de Windows.

2. Elija **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

3. Haga clic en **Base de datos**y luego en **Siguiente**.

4. Si ya tiene una conexión a la base de datos `AdventureWorksLT` , elija esa conexión y haga clic en **Siguiente**.

    De lo contrario, haga clic en **Nueva conexión**y use el cuadro de diálogo **Agregar conexión** para crear la nueva conexión. Para obtener más información, consulte [Agregar nuevas conexiones](../data-tools/add-new-connections.md).

5. En la página **Guardar cadena de conexión en el archivo de configuración de la aplicación** , haga clic en **Siguiente**.

6. En la página **Elegir los objetos de base de datos** expanda **Tablas** y seleccione **Customer (SalesLT)**.

7. Haga clic en **Finalizar**

    El archivo *AdventureWorksLTDataSet. xsd* se agrega a **Explorador de soluciones**. Este archivo define los siguientes elementos:

   - Un conjunto de datos con tipo denominado `AdventureWorksLTDataSet`. Este conjunto de datos representa el contenido de la tabla **Customer (SalesLT)** de la base de datos AdventureWorksLT.

   - Un TableAdapter denominado `CustomerTableAdapter` . Este TableAdapter se puede usar para leer y escribir datos en `AdventureWorksLTDataSet` . Para obtener más información, vea [información general de TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Estos dos objetos se usarán más adelante en este tutorial.

## <a name="create-controls-and-binding-controls-to-data"></a>Crear controles y enlazar controles a los datos

La interfaz para ver los registros de base de datos en este tutorial es básica y se crea dentro del documento. Un elemento <xref:Microsoft.Office.Tools.Word.ContentControl> muestra un registro único de la base de datos a la vez y dos controles <xref:Microsoft.Office.Tools.Word.Controls.Button> le permiten desplazarse hacia delante y atrás por los registros. El control de contenido usa un elemento <xref:System.Windows.Forms.BindingSource> para conectarse a la base de datos.

Para obtener más información sobre cómo enlazar controles a datos, vea [enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-create-the-interface-in-the-document"></a>Para crear la interfaz en el documento

1. En la clase `ThisAddIn` , declare los siguientes controles para mostrar y desplazarse por la tabla `Customer` de la base de datos `AdventureWorksLTDataSet` .

     [!code-vb[Trin_WordAddInDatabase#1](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDatabase#1](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#1)]

2. En el método `ThisAddIn_Startup` , agregue el siguiente código para inicializar el conjunto de datos y rellenarlo con la información de la base de datos `AdventureWorksLTDataSet` .

     [!code-vb[Trin_WordAddInDatabase#2](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDatabase#2](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#2)]

3. Agregue el código siguiente al método `ThisAddIn_Startup` . Esto genera un elemento host que extiende el documento. Para obtener más información, vea [ampliar documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

     [!code-vb[Trin_WordAddInDatabase#3](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDatabase#3](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#3)]

4. Defina varios intervalos al principio del documento. Estos intervalos identifican dónde se insertará texto y se colocarán los controles.

     [!code-vb[Trin_WordAddInDatabase#4](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDatabase#4](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#4)]

5. Agregue los controles de interfaz a los intervalos definidos previamente.

     [!code-vb[Trin_WordAddInDatabase#5](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDatabase#5](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#5)]

6. Enlace el control de contenido a `AdventureWorksLTDataSet` mediante el elemento <xref:System.Windows.Forms.BindingSource>. Para los desarrolladores de C#, agregue dos controladores de eventos para los controles <xref:Microsoft.Office.Tools.Word.Controls.Button> .

     [!code-vb[Trin_WordAddInDatabase#6](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#6)]
     [!code-csharp[Trin_WordAddInDatabase#6](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#6)]

7. Agregue el código siguiente para navegar por los registros de la base de datos.

     [!code-vb[Trin_WordAddInDatabase#7](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDatabase#7](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#7)]

## <a name="test-the-add-in"></a>Probar el complemento

Cuando abre Word, el control de contenido muestra los datos del conjunto de datos `AdventureWorksLTDataSet` . Desplácese por los registros de la base de datos haciendo clic en los botones **Siguiente** y **Anterior** .

### <a name="to-test-the-vsto-add-in"></a>Para probar el complemento de VSTO

1. Presione **F5**.

     Se crea un control de contenido denominado `customerContentControl` y se rellena con datos. Al mismo tiempo, se agregan al proyecto un objeto de conjunto de datos denominado `adventureWorksLTDataSet` y una <xref:System.Windows.Forms.BindingSource> denominada `customerBindingSource` . El <xref:Microsoft.Office.Tools.Word.ContentControl> se enlaza a <xref:System.Windows.Forms.BindingSource>, que a su vez se enlaza al objeto de conjunto de datos.

2. Haga clic en los botones **Siguiente** y **Anterior** para desplazarse por los registros de la base de datos.

## <a name="see-also"></a>Consulte también

- [Datos en soluciones de Office](../vsto/data-in-office-solutions.md)
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Cómo: rellenar hojas de cálculo con datos de una base de datos](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Cómo: rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Cómo: rellenar documentos con datos de servicios](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Cómo: rellenar documentos con datos de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Cómo: desplazarse por los registros de base de datos de una hoja de cálculo](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Cómo: actualizar un origen de datos con datos de un control host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Tutorial: enlace de datos simple en un proyecto de nivel de documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [Tutorial: enlace de datos complejo en un proyecto de nivel de documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Usar archivos de base de datos local en información general sobre soluciones de Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md)
- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Cómo: rellenar documentos con datos de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Cómo: actualizar un origen de datos con datos de un control host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Usar archivos de base de datos local en información general sobre soluciones de Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Información general sobre el componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)
