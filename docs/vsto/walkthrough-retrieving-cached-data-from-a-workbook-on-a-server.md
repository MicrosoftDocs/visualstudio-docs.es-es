---
title: 'Tutorial: recuperar datos almacenados en caché de un libro en un servidor'
description: Obtenga información sobre cómo recuperar datos de un conjunto de datos almacenado en la memoria caché de un libro de Microsoft Excel sin iniciar Excel con la clase ServerDocument.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], retrieving data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f32ad4ffe44eb725953bc664acf4c4c38da4b11e
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524845"
---
# <a name="walkthrough-retrieve-cached-data-from-a-workbook-on-a-server"></a>Tutorial: recuperar datos almacenados en caché de un libro en un servidor
  En este tutorial se muestra cómo recuperar datos de un conjunto de datos almacenado en la memoria caché de un libro de Microsoft Office Excel sin iniciar Excel mediante la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Definir un conjunto de datos que contiene datos de la base de datos *AdventureWorksLT* .

- Crear instancias del conjunto de información en un proyecto de libro de Excel y un proyecto de aplicación de consola.

- Crear un <xref:Microsoft.Office.Tools.Excel.ListObject> que esté enlazado al conjunto de datos en el libro y rellenar <xref:Microsoft.Office.Tools.Excel.ListObject> con datos cuando se abra el libro.

- Agregar el conjunto de datos del libro a la memoria caché de datos.

- Lectura de datos del conjunto de datos almacenado en memoria caché en el conjunto de datos de la aplicación de consola, sin iniciar Excel.

  Aunque en este tutorial se da por supuesto que está ejecutando el código en el equipo de desarrollo, el código que se muestra en este tutorial puede usarse en un servidor que no tenga instalado Excel.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Acceso a una instancia en ejecución de Microsoft SQL Server o Microsoft SQL Server Express que tenga adjunta la base de datos de ejemplo AdventureWorksLT. Puede descargar la base de datos AdventureWorksLT desde el [sitio web de CodePlex](https://archive.codeplex.com/?p=SqlServerSamples). Para obtener más información sobre cómo asociar una base de datos, vea los siguientes temas:

  - Para adjuntar una base de datos mediante SQL Server Management Studio o SQL Server Management Studio Express, consulte [Cómo: adjuntar una base de datos (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Para adjuntar una base de datos mediante la línea de comandos, vea [Cómo: adjuntar un archivo de base de datos a SQL Server Express](/previous-versions/sql/).

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Crear un proyecto de biblioteca de clases que define un conjunto de
 Para usar el mismo conjunto de información en un proyecto de libro de Excel y en una aplicación de consola, debe definir el conjunto de DataSet en un ensamblado independiente al que hagan referencia ambos proyectos. Para este tutorial, defina el conjunto de DataSet en un proyecto de biblioteca de clases.

### <a name="create-the-class-library-project"></a>Crear el proyecto de biblioteca de clases

1. Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. En el menú **Archivo** , seleccione **Nuevo** y haga clic en **Proyecto**.

3. En el panel plantillas, expanda **Visual C#** o **Visual Basic** y, a continuación, haga clic en **Windows**.

4. En la lista de plantillas de proyecto, seleccione **biblioteca de clases**.

5. En el cuadro **nombre** , escriba **AdventureWorksDataSet**.

6. Haga clic en **examinar**, navegue hasta la carpeta *%userprofile%\My Documents* (para Windows XP y versiones anteriores) o *%userprofile%\Documents* (para Windows Vista) y, a continuación, haga clic en **Seleccionar carpeta**.

7. En el cuadro de diálogo **nuevo proyecto** , asegúrese de que la casilla **Crear directorio para la solución** no esté activada.

8. Haga clic en **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **AdventureWorksDataSet** a **Explorador de soluciones** y abre el archivo de código *Class1.CS* o *Class1. VB* .

9. En **Explorador de soluciones**, haga clic con el botón secundario en *Class1.CS* o *Class1. VB* y, a continuación, haga clic en **eliminar**. No necesita este archivo para este tutorial.

## <a name="define-a-dataset-in-the-class-library-project"></a>Definición de un conjunto de DataSet en el proyecto de biblioteca de clases
 Defina un conjunto de datos con tipo que contenga los datos de la base de datos AdventureWorksLT para SQL Server 2005. Más adelante en este tutorial, hará referencia a este conjunto de información desde un proyecto de libro de Excel y un proyecto de aplicación de consola.

 El DataSet es un *conjunto de datos con tipo* que representa los datos de la tabla Product de la base de datos AdventureWorksLT. Para obtener más información acerca de los conjuntos de datos con tipo, vea [herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

### <a name="define-a-typed-dataset-in-the-class-library-project"></a>Definir un conjunto de tipos en el proyecto de biblioteca de clases

1. En **Explorador de soluciones**, haga clic en el proyecto **AdventureWorksDataSet** .

2. Si la ventana **orígenes de datos** no está visible, puede mostrarla en la barra de menús y elegir **Ver**  >  **otros**  >  **orígenes de datos** de Windows.

3. Elija **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

4. Haga clic en **Base de datos** y luego en **Siguiente**.

5. Si tiene una conexión existente a la base de datos AdventureWorksLT, elija esta conexión y haga clic en **siguiente**.

    De lo contrario, haga clic en **Nueva conexión** y use el cuadro de diálogo **Agregar conexión** para crear la nueva conexión. Para obtener más información, consulte [Agregar nuevas conexiones](../data-tools/add-new-connections.md).

6. En la página **Guardar cadena de conexión en el archivo de configuración de la aplicación** , haga clic en **Siguiente**.

7. En la página **Elija los objetos de base de datos** , expanda **tablas** y seleccione **Product (SalesLT)**.

8. Haga clic en **Finalizar**

    El archivo *AdventureWorksLTDataSet. xsd* se agrega al proyecto **AdventureWorksDataSet** . Este archivo define los siguientes elementos:

   - Un conjunto de datos con tipo denominado `AdventureWorksLTDataSet`. Este conjunto de datos representa el contenido de la tabla Product en la base de datos AdventureWorksLT.

   - Un TableAdapter denominado `ProductTableAdapter` . Este TableAdapter se puede usar para leer y escribir datos en `AdventureWorksLTDataSet` . Para obtener más información, vea [información general de TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Estos dos objetos se usarán más adelante en este tutorial.

9. En **Explorador de soluciones**, haga clic con el botón secundario en **AdventureWorksDataSet** y haga clic en **compilar**.

     Compruebe que el proyecto se compila sin errores.

## <a name="create-an-excel-workbook-project"></a>Crear un proyecto de libro de Excel
 Cree un proyecto de libro de Excel para la interfaz con los datos. Más adelante en este tutorial, creará un <xref:Microsoft.Office.Tools.Excel.ListObject> que muestre los datos y agregará una instancia del conjunto de datos a la memoria caché de datos del libro.

### <a name="create-the-excel-workbook-project"></a>Crear el proyecto de libro de Excel

1. En **Explorador de soluciones**, haga clic con el botón secundario en la solución **AdventureWorksDataSet** , seleccione **Agregar** y, a continuación, haga clic en **nuevo proyecto**.

2. En el panel de plantillas, expanda **Visual C#** o **Visual Basic** y luego expanda **Office/SharePoint**.

3. En el nodo **Office/SharePoint** expandido, seleccione el nodo **Complementos de Office** .

4. En la lista de plantillas de proyecto, seleccione el proyecto **Libro de Excel 2010** o **Libro de Excel 2013** .

5. En el cuadro **nombre** , escriba **AdventureWorksReport**. No modifique la ubicación.

6. Haga clic en **OK**.

     Se abre el **Asistente para proyectos de Visual Studio Tools para Office** .

7. Asegúrese de que **la opción crear un nuevo documento** está seleccionada y haga clic en **Aceptar**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] abre el libro **adventureworksreport** en el diseñador y agrega el proyecto **adventureworksreport** a **Explorador de soluciones**.

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Agregar el conjunto de datos a los orígenes de datos en el proyecto de libro de Excel
 Antes de poder mostrar el conjunto de datos en el libro de Excel, primero debe agregar el conjunto de datos a los orígenes de datos del proyecto de libro de Excel.

1. En **Explorador de soluciones**, haga doble clic en *Sheet1.CS* o *Sheet1. VB* en el proyecto **AdventureWorksReport** .

     El libro se abre en el diseñador.

2. En el menú **Datos** , haga clic en **Agregar nuevo elemento**.

     Se abre el **Asistente para la configuración de orígenes de datos** .

3. Haga clic en **objeto** y, a continuación, en **siguiente**.

4. En la página **Seleccione el objeto al que desea enlazar** , haga clic en **Agregar referencia**.

5. En la pestaña **proyectos** , haga clic en **AdventureWorksDataSet** y, a continuación, haga clic en **Aceptar**.

6. En el espacio de nombres **adventureworksdataset** del ensamblado **adventureworksdataset** , haga clic en **AdventureWorksLTDataSet** y, a continuación, haga clic en **Finalizar**.

     Se abre la ventana **orígenes de datos** y se agrega **AdventureWorksLTDataSet** a la lista de orígenes de datos.

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Crear un objeto ListObject que esté enlazado a una instancia del conjunto de información
 Para mostrar el conjunto de información en el libro, cree un <xref:Microsoft.Office.Tools.Excel.ListObject> que esté enlazado a una instancia del conjunto de DataSet. Para obtener más información sobre cómo enlazar controles a datos, vea [enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).

1. En la ventana **orígenes de datos** , expanda el nodo **AdventureWorksLTDataSet** en **AdventureWorksDataSet**.

2. Seleccione el nodo **producto** , haga clic en la flecha desplegable que aparece y seleccione **ListObject** en la lista desplegable.

     Si la flecha desplegable no aparece, confirme que el libro está abierto en el diseñador.

3. Arrastre la tabla **Product** hasta la celda a1.

     <xref:Microsoft.Office.Tools.Excel.ListObject>Se crea un control denominado `productListObject` en la hoja de cálculo, a partir de la celda a1. Al mismo tiempo, se agregan al proyecto un objeto de conjunto de datos denominado `adventureWorksLTDataSet` y una <xref:System.Windows.Forms.BindingSource> denominada `productBindingSource` . El <xref:Microsoft.Office.Tools.Excel.ListObject> se enlaza a <xref:System.Windows.Forms.BindingSource>, que a su vez se enlaza al objeto de conjunto de datos.

## <a name="add-the-dataset-to-the-data-cache"></a>Agregar el conjunto de datos a la memoria caché de datos
 Para habilitar el código fuera del proyecto de libro de Excel para tener acceso al conjunto de datos del libro, debe agregar el conjunto de datos a la memoria caché de datos. Para obtener más información sobre la memoria caché de datos, vea [datos almacenados en caché en personalizaciones de nivel de documento](../vsto/cached-data-in-document-level-customizations.md) y [datos de caché](../vsto/caching-data.md).

1. En el diseñador, haga clic en **AdventureWorksLTDataSet**.

2. En la ventana **propiedades** , establezca la propiedad **Modifiers** en **Public**.

3. Establezca la propiedad **CacheInDocument** en **true**.

## <a name="initialize-the-dataset-in-the-workbook"></a>Inicializar el conjunto de DataSet en el libro
 Antes de poder recuperar los datos del conjunto de datos almacenado en memoria caché mediante la aplicación de consola, primero debe rellenar el conjunto de datos almacenado en caché con los datos.

1. En **Explorador de soluciones**, haga clic con el botón secundario en el archivo *Sheet1.CS* o *Hoja1. VB* y haga clic en **Ver código**.

2. Reemplace el controlador de eventos `Sheet1_Startup` por el siguiente código: Este código usa una instancia de la `ProductTableAdapter` clase que se define en el proyecto **AdventureWorksDataSet** para rellenar el conjunto de datos almacenado en memoria caché con datos, si está actualmente vacío.

     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]

## <a name="checkpoint"></a>Punto de control
 Compile y ejecute el proyecto de libro de Excel para asegurarse de que se compila y se ejecuta sin errores. Esta operación también rellena el conjunto de datos almacenado en memoria caché y guarda los datos en el libro.

### <a name="build-and-run-the-project"></a>Compilación y ejecución del proyecto

1. En **Explorador de soluciones**, haga clic con el botón derecho en el proyecto **AdventureWorksReport** , elija **depurar** y, a continuación, haga clic en **Iniciar nueva instancia**.

     El proyecto se compila y el libro se abre en Excel. Verifique lo siguiente:

    - <xref:Microsoft.Office.Tools.Excel.ListObject>Rellena los datos.

    - El valor de la columna **ListPrice** de la primera fila de <xref:Microsoft.Office.Tools.Excel.ListObject> es 1431,5. Más adelante en este tutorial, usará una aplicación de consola para modificar los valores de la columna **ListPrice** .

2. Guarde el libro. No modifique el nombre de archivo o la ubicación del libro.

3. Cierre Excel.

## <a name="create-a-console-application-project"></a>Crear un proyecto de aplicación de consola
 Cree un proyecto de aplicación de consola que se utilizará para modificar los datos del conjunto de datos almacenado en la memoria caché del libro.

1. En **Explorador de soluciones**, haga clic con el botón secundario en la solución **AdventureWorksDataSet** , seleccione **Agregar** y, a continuación, haga clic en **nuevo proyecto**.

2. En el panel **tipos de proyecto** , expanda **Visual C#** o **Visual Basic** y, a continuación, haga clic en **Windows**.

3. En el panel **Plantillas**, seleccione **Aplicación de consola**.

4. En el cuadro **nombre** , escriba **DataReader**. No modifique la ubicación.

5. Haga clic en **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **DataReader** a **Explorador de soluciones** y abre el archivo de código *Program.CS* o *Module1. VB* .

## <a name="retrieve-data-from-the-cached-dataset-by-using-the-console-application"></a>Recuperar datos del conjunto de datos almacenado en memoria caché mediante la aplicación de consola
 Utilice la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase en la aplicación de consola para leer los datos en un `AdventureWorksLTDataSet` objeto local. Para confirmar que el conjunto de datos local se inicializó con datos del conjunto de datos almacenado en memoria caché, la aplicación muestra el número de filas del conjunto de datos local.

### <a name="retrieve-data-from-the-cached-dataset"></a>Recuperar datos del conjunto de datos almacenado en caché

1. En **Explorador de soluciones**, haga clic con el botón derecho en el proyecto **DataReader** y haga clic en **Agregar referencia**.

2. En la pestaña **.net** , seleccione **Microsoft. VisualStudio. Tools. Applications. ServerDocument**.

3. Haga clic en **OK**.

4. En **Explorador de soluciones**, haga clic con el botón derecho en el proyecto **DataReader** y haga clic en **Agregar referencia**.

5. En la pestaña **proyectos** , seleccione **AdventureWorksDataSet** y haga clic en **Aceptar**.

6. Abra el archivo *Program.CS* o *Module1. VB* en el editor de código.

7. Agregue lo siguiente **mediante** (para C#) o la instrucción **Imports** (for Visual Basic) en la parte superior del archivo de código.

    [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
    [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]

8. Agregue el siguiente código al método `Main`. Este código declara los objetos siguientes:

   - Instancia del `AdventureWorksLTDataSet` tipo que se define en el proyecto **AdventureWorksDataSet** .

   - La ruta de acceso al libro AdventureWorksReport en la carpeta Build del proyecto **adventureworksreport** .

   - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>Objeto que se va a usar para tener acceso a la memoria caché de datos del libro.

     > [!NOTE]
     > En el código siguiente se supone que el libro se guarda con la extensión *. xlsx* . Si el libro del proyecto tiene una extensión diferente, modifique la ruta de acceso según sea necesario.

     [!code-csharp[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#10)]
     [!code-vb[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#10)]

9. Agregue el código siguiente al `Main` método, después del código que agregó en el paso anterior. Este código realiza las tareas siguientes:

   - Usa la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> propiedad de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase para tener acceso al conjunto de los conjuntos de copia de la memoria caché del libro.

   - Lee los datos del conjunto de datos almacenado en memoria caché en el conjunto de datos local.

   - Muestra el número de filas del conjunto de datos local para confirmar que tiene datos.

     [!code-csharp[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#11)]
     [!code-vb[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#11)]

10. En el menú **compilar** , haga clic en **generar DataReader**.

## <a name="test-the-project"></a>Prueba del proyecto
 Al ejecutar la aplicación de consola, se muestra el número de filas del conjunto de filas local.

### <a name="test-the-workbook"></a>Probar el libro

1. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto **DataReader** , seleccione **depurar** y, a continuación, haga clic en **Iniciar nueva instancia**.

     Compruebe que la aplicación indica que el conjunto de filas local tiene 295 filas.

2. Presione **ENTRAR** para cerrar la aplicación.

## <a name="next-steps"></a>Pasos siguientes
 Puede obtener más información sobre cómo trabajar con datos almacenados en caché en estos temas:

- Cambiar los datos de un conjunto de datos almacenado en memoria caché sin iniciar Excel. Para obtener más información, vea [Tutorial: cambiar los datos almacenados en caché de un libro en un servidor](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).

## <a name="see-also"></a>Consulte también

- [Tutorial: insertar datos en un libro en un servidor](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)
- [Tutorial: cambiar los datos almacenados en caché de un libro en un servidor](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)
