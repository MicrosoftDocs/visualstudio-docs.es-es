---
title: 'Tutorial: Cambio de los datos almacenados en caché en un libro en un servidor'
description: Obtenga información sobre cómo modificar un conjunto de datos almacenado en caché en un libro de Microsoft Excel sin iniciar Excel mediante la clase ServerDocument.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], changing server data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f03175abb843abefe5266724890457c795369d63
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824437"
---
# <a name="walkthrough-change-cached-data-in-a-workbook-on-a-server"></a>Tutorial: Cambio de los datos almacenados en caché en un libro en un servidor
  En este tutorial se muestra cómo modificar un conjunto de datos almacenado en caché Microsoft Office libro de Excel sin iniciar Excel mediante la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase .

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 En este tutorial se muestran las tareas siguientes:

- Definición de un conjunto de datos que contiene datos de la base de datos AdventureWorksLT.

- Crear instancias del conjunto de datos en un proyecto de libro de Excel y un proyecto de aplicación de consola.

- Crear un objeto enlazado al conjunto de datos del libro y rellenar con <xref:Microsoft.Office.Tools.Excel.ListObject> datos cuando se abre el <xref:Microsoft.Office.Tools.Excel.ListObject> libro.

- Agregar el conjunto de datos en el libro a la caché de datos.

- Modificar una columna de datos en el conjunto de datos almacenado en caché mediante la ejecución de código en la aplicación de consola, sin iniciar Excel.

  Aunque en este tutorial se da por supuesto que está ejecutando el código en el equipo de desarrollo, el código que se muestra en este tutorial se puede usar en un servidor que no tenga Instalado Excel.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Acceso a una instancia en ejecución de Microsoft SQL Server o Microsoft SQL Server Express que tenga asociada la base de datos de ejemplo AdventureWorksLT. Puede descargar la base de datos AdventureWorksLT desde el [repositorio SQL Server ejemplos de GitHub](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Para obtener más información sobre cómo asociar una base de datos, vea los siguientes temas:

  - Para adjuntar una base de datos mediante SQL Server Management Studio o SQL Server Management Studio Express, vea Cómo: Adjuntar una base de datos [(SQL Server Management Studio).](/sql/relational-databases/databases/attach-a-database)

  - Para adjuntar una base de datos mediante la línea de comandos, vea [Cómo: Adjuntar un archivo de base](/previous-versions/sql/)de datos a SQL Server Express .

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Creación de un proyecto de biblioteca de clases que define un conjunto de datos
 Para usar el mismo conjunto de datos en un proyecto de libro de Excel y una aplicación de consola, debe definir el conjunto de datos en un ensamblado independiente al que hacen referencia ambos proyectos. Para este tutorial, defina el conjunto de datos en un proyecto de biblioteca de clases.

### <a name="to-create-the-class-library-project"></a>Para crear el proyecto de biblioteca de clases

1. Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. En el menú **Archivo** , elija **Nuevo** y haga clic en **Proyecto**.

3. En el panel plantillas, expanda **Visual C#** **o Visual Basic** y, a continuación, haga clic en **Windows**.

4. En la lista de plantillas de proyecto, seleccione **Biblioteca de clases**.

5. En el **cuadro** Nombre, escriba **AdventureWorksDataSet.**

6. Haga clic **en** Examinar, vaya a la *carpeta %UserProfile%\Mis documentos* (para Windows XP y versiones anteriores) o *%UserProfile%\Documents* (para Windows Vista) y, a continuación, haga clic en **Seleccionar carpeta.**

7. En el **cuadro de diálogo** Nuevo proyecto, asegúrese de que la casilla Crear **directorio** para la solución no está activada.

8. Haga clic en **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]agrega el **proyecto AdventureWorksDataSet** **a Explorador de soluciones** y abre el archivo de código **Class1.cs** **o Class1.vb.**

9. En **Explorador de soluciones**, haga clic con el botón **derecho en Class1.cs** o **Class1.vb** y, a continuación, haga clic **en Eliminar**. No necesita este archivo para este tutorial.

## <a name="define-a-dataset-in-the-class-library-project"></a>Definición de un conjunto de datos en el proyecto de biblioteca de clases
 Defina un conjunto de datos con tipo que contenga datos de la base de datos AdventureWorksLT para SQL Server 2005. Más adelante en este tutorial, hará referencia a este conjunto de datos desde un proyecto de libro de Excel y un proyecto de aplicación de consola.

 El conjunto de datos es *un conjunto de datos con tipo* que representa los datos de la tabla Product de la base de datos AdventureWorksLT. Para obtener más información sobre los conjuntos de datos con tipo, vea [Herramientas de conjunto de datos Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>Para definir un conjunto de datos con tipo en el proyecto de biblioteca de clases

1. En **Explorador de soluciones**, haga clic en **el proyecto AdventureWorksDataSet.**

2. Si la **ventana Orígenes de** datos no está visible, para mostrarla, en la barra de menús, elija **Ver** otros orígenes de  >  **datos** de Windows  >  .

3. Elija **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

4. Haga clic en **Base de datos** y luego en **Siguiente**.

5. Si ya tiene una conexión a la base de datos AdventureWorksLT, elija esta conexión y haga clic **en Siguiente.**

    De lo contrario, haga clic en **Nueva conexión** y use el cuadro de diálogo **Agregar conexión** para crear la nueva conexión. Para obtener más información, vea [Agregar nuevas conexiones.](../data-tools/add-new-connections.md)

6. En la página **Guardar cadena de conexión en el archivo de configuración de la aplicación** , haga clic en **Siguiente**.

7. En la página **Elegir los objetos de base de** datos, expanda **Tablas** y seleccione **Producto (SalesLT).**

8. Haga clic en **Finalizar**

    El *archivo AdventureWorksLTDataSet.xsd* se agrega al **proyecto AdventureWorksDataSet.** Este archivo define los siguientes elementos:

   - Un conjunto de datos con tipo denominado `AdventureWorksLTDataSet`. Este conjunto de datos representa el contenido de la tabla Product en la base de datos AdventureWorksLT.

   - Un TableAdapter denominado `ProductTableAdapter` . Este TableAdapter se puede usar para leer y escribir datos en `AdventureWorksLTDataSet` . Para obtener más información, vea [Información general de TableAdapter.](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)

     Estos dos objetos se usarán más adelante en este tutorial.

9. En Explorador de soluciones , **haga** clic con el botón derecho **en AdventureWorksDataSet** y haga clic en **Compilar**.

     Compruebe que el proyecto se compila sin errores.

## <a name="create-an-excel-workbook-project"></a>Creación de un proyecto de libro de Excel
 Cree un proyecto de libro de Excel para la interfaz de los datos. Más adelante en este tutorial, creará un objeto que muestra los datos y agregará una instancia del conjunto de datos a la caché de <xref:Microsoft.Office.Tools.Excel.ListObject> datos del libro.

### <a name="to-create-the-excel-workbook-project"></a>Para crear el proyecto de libro de Excel

1. En **Explorador de soluciones**, haga clic con el botón derecho en la **solución AdventureWorksDataSet,** seleccione Agregar **y,** a continuación, haga clic en **Nuevo proyecto.**

2. En el panel plantillas, expanda **Visual C#** **o Visual Basic** y, a continuación, **expanda Office**.

3. En el nodo **de Office** expandido, seleccione el **nodo 2010.**

4. En la lista de plantillas de proyecto, seleccione el proyecto Libro de Excel.

5. En el **cuadro** Nombre, escriba **AdventureWorksReport**. No modifique la ubicación.

6. Haga clic en **OK**.

     Se abre el **Asistente para proyectos de Visual Studio Tools para Office** .

7. Asegúrese de **que está seleccionada la opción Crear** un nuevo documento y haga clic en **Aceptar.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] abre el **libro AdventureWorksReport** en el diseñador y agrega el **proyecto AdventureWorksReport** **a Explorador de soluciones**.

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Agregar el conjunto de datos a orígenes de datos en el proyecto de libro de Excel
 Para poder mostrar el conjunto de datos en el libro de Excel, primero debe agregar el conjunto de datos a los orígenes de datos en el proyecto de libro de Excel.

### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>Para agregar el conjunto de datos a los orígenes de datos del proyecto de libro de Excel

1. En **Explorador de soluciones**, haga doble clic **en Sheet1.cs** o **Sheet1.vb** en el **proyecto AdventureWorksReport.**

     El libro se abre en el diseñador.

2. En el menú **Datos** , haga clic en **Agregar nuevo elemento**.

     Se **abre el Asistente para configuración del origen de** datos.

3. Haga clic **en Objeto** y, a continuación, en **Siguiente.**

4. En la **página Seleccionar el objeto al que desea enlazar,** haga clic en Agregar **referencia.**

5. En la **pestaña Proyectos,** haga clic **en AdventureWorksDataSet y,** a continuación, haga clic **en Aceptar.**

6. En el **espacio de nombres AdventureWorksDataSet** del ensamblado **AdventureWorksDataSet,** haga clic **en AdventureWorksLTDataSet** y, a continuación, haga clic **en Finalizar.**

     Se **abre la ventana** Orígenes de datos y **AdventureWorksLTDataSet** se agrega a la lista de orígenes de datos.

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Creación de un elemento ListObject enlazado a una instancia del conjunto de datos
 Para mostrar el conjunto de datos en el libro, cree un objeto enlazado a <xref:Microsoft.Office.Tools.Excel.ListObject> una instancia del conjunto de datos. Para obtener más información sobre cómo enlazar controles a datos, vea [Enlazar datos a controles en soluciones de Office.](../vsto/binding-data-to-controls-in-office-solutions.md)

### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Para crear un Elemento ListObject enlazado a una instancia del conjunto de datos

1. En la **ventana Orígenes de** datos, expanda el nodo **AdventureWorksLTDataSet** en **AdventureWorksDataSet**.

2. Seleccione el **nodo Producto,** haga clic en la flecha desplegable que aparece y seleccione **ListObject** en la lista desplegable.

     Si no aparece la flecha desplegable, confirme que el libro está abierto en el diseñador.

3. Arrastre la **tabla Product** a la celda A1.

     Se <xref:Microsoft.Office.Tools.Excel.ListObject> crea un control denominado en la hoja de `productListObject` cálculo, empezando en la celda A1. Al mismo tiempo, se agregan al proyecto un objeto de conjunto de datos denominado `adventureWorksLTDataSet` y una <xref:System.Windows.Forms.BindingSource> denominada `productBindingSource` . El <xref:Microsoft.Office.Tools.Excel.ListObject> se enlaza a <xref:System.Windows.Forms.BindingSource>, que a su vez se enlaza al objeto de conjunto de datos.

## <a name="add-the-dataset-to-the-data-cache"></a>Adición del conjunto de datos a la caché de datos
 Para permitir que el código fuera del proyecto de libro de Excel acceda al conjunto de datos del libro, debe agregar el conjunto de datos a la caché de datos. Para obtener más información sobre la caché de datos, vea [Datos almacenados en](../vsto/cached-data-in-document-level-customizations.md) caché en personalizaciones de nivel de documento y [Datos de caché.](../vsto/caching-data.md)

### <a name="to-add-the-dataset-to-the-data-cache"></a>Para agregar el conjunto de datos a la caché de datos

1. En el diseñador, haga clic **en adventureWorksLTDataSet**.

2. En la **ventana** Propiedades, establezca la **propiedad Modificadores** en **Público.**

3. Establezca la **propiedad CacheInDocument** en **True.**

## <a name="initialize-the-dataset-in-the-workbook"></a>Inicialización del conjunto de datos en el libro
 Para poder recuperar los datos del conjunto de datos almacenado en caché mediante la aplicación de consola, primero debe rellenar el conjunto de datos almacenado en caché con datos.

### <a name="to-initialize-the-dataset-in-the-workbook"></a>Para inicializar el conjunto de datos en el libro

1. En **Explorador de soluciones**, haga clic con el botón derecho **en el archivo Sheet1.cs** o **Sheet1.vb** y haga clic **en Ver código**.

2. Reemplace el controlador de eventos `Sheet1_Startup` por el siguiente código: Este código usa una instancia de la clase definida en el proyecto `ProductTableAdapter` **AdventureWorksDataSet** para rellenar el conjunto de datos almacenado en caché con datos, si está vacío actualmente.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb" id="Snippet8":::

## <a name="checkpoint"></a>Punto de control
 Compile y ejecute el proyecto de libro de Excel para asegurarse de que se compila y se ejecuta sin errores. Esta operación también rellena el conjunto de datos almacenado en caché y guarda los datos en el libro.

### <a name="to-build-and-run-the-project"></a>Para compilar y ejecutar el proyecto

1. En **Explorador de soluciones**, haga clic con el botón derecho en el **proyecto AdventureWorksReport,** elija **Depurar** y, a continuación, haga clic en Iniciar **nueva instancia.**

     El proyecto se ha creado y el libro se abre en Excel. Verifique lo siguiente:

    - rellena <xref:Microsoft.Office.Tools.Excel.ListObject> con datos.

    - El valor de la **columna ListPrice** de la primera fila de <xref:Microsoft.Office.Tools.Excel.ListObject> es 1431,5. Más adelante en este tutorial, usará una aplicación de consola para modificar los valores de la **columna ListPrice.**

2. Guarde el libro. No modifique el nombre de archivo ni la ubicación del libro.

3. Cierre Excel.

## <a name="create-a-console-application-project"></a>Creación de un proyecto de aplicación de consola
 Cree un proyecto de aplicación de consola que se usará para modificar los datos del conjunto de datos almacenado en caché en el libro.

### <a name="to-create-the-console-application-project"></a>Para crear el proyecto de aplicación de consola

1. En **Explorador de soluciones**, haga clic con el botón derecho en la **solución AdventureWorksDataSet,** seleccione Agregar **y,** a continuación, haga clic en **Nuevo proyecto.**

2. En el **panel Tipos de proyecto** , expanda Visual **C#** **o Visual Basic** y, a continuación, haga clic en **Windows**.

3. En el panel **Plantillas**, seleccione **Aplicación de consola**.

4. En el **cuadro** Nombre , escriba **DataWriter**. No modifique la ubicación.

5. Haga clic en **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]agrega el **proyecto DataWriter** a **Explorador de soluciones** y abre el archivo de **código Program.cs** o **Module1.vb.**

## <a name="change-data-in-the-cached-dataset-by-using-the-console-application"></a>Cambio de datos en el conjunto de datos almacenado en caché mediante la aplicación de consola
 Use la clase de la aplicación de consola para leer los datos en un objeto local, modificar estos datos y, a continuación, guardarlos de nuevo en <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> el conjunto de datos almacenado en `AdventureWorksLTDataSet` caché.

### <a name="to-change-data-in-the-cached-dataset"></a>Para cambiar los datos del conjunto de datos almacenado en caché

1. En **Explorador de soluciones**, haga clic con el botón derecho en el **proyecto DataWriter** y haga clic en Agregar **referencia.**

2. En la **pestaña .NET,** seleccione **Microsoft.VisualStudio.Tools.Applications**.

3. Haga clic en **OK**.

4. En **Explorador de soluciones**, haga clic con el botón derecho en el **proyecto DataWriter** y haga clic en Agregar **referencia.**

5. En la **pestaña Proyectos,** seleccione **AdventureWorksDataSet y** haga clic en **Aceptar.**

6. Abra el *archivo Program.cs* *o Module1.vb* en el Editor de código.

7. Agregue lo siguiente **mediante** (para C#) o la instrucción **Imports** (para Visual Basic) en la parte superior del archivo de código.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet1":::

8. Agregue el siguiente código al método `Main`. Este código declara los siguientes objetos:

   - Instancia del tipo `AdventureWorksLTDataSet` definido en el proyecto **AdventureWorksDataSet.**

   - Ruta de acceso al libro AdventureWorksReport en la carpeta de compilación del **proyecto AdventureWorksReport.**

   - Objeto <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> que se usará para tener acceso a la caché de datos del libro.

     > [!NOTE]
     > En el código siguiente se da por supuesto que está usando un libro que tiene la extensión de archivo *.xlsx.* Si el libro del proyecto tiene una extensión de archivo diferente, modifique la ruta de acceso según sea necesario.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet6":::

9. Agregue el código siguiente al `Main` método , después del código que agregó en el paso anterior. Este código realiza las tareas siguientes:

   - Usa la propiedad de la clase para tener acceso al conjunto de datos <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> almacenado en caché en el <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> libro.

   - Lee los datos del conjunto de datos almacenado en caché en el conjunto de datos local.

   - Cambia el valor `ListPrice` de cada producto en la tabla Product del conjunto de datos.

   - Guarda los cambios en el conjunto de datos almacenado en caché en el libro.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet7":::

10. En **Explorador de soluciones**, haga clic con el botón derecho en el **proyecto DataWriter,** seleccione **Depurar** y, a continuación, haga clic en Iniciar **nueva instancia**.

     La aplicación de consola muestra mensajes mientras lee el conjunto de datos almacenado en caché en el conjunto de datos local, modifica los precios del producto en el conjunto de datos local y guarda los nuevos valores en el conjunto de datos almacenado en caché. Presione **ENTRAR** para cerrar la aplicación.

## <a name="test-the-workbook"></a>Prueba del libro
 Al abrir el libro, ahora muestra los cambios realizados en la columna <xref:Microsoft.Office.Tools.Excel.ListObject> de datos del conjunto de datos almacenado en `ListPrice` caché.

### <a name="to-test-the-workbook"></a>Para probar el libro

1. Cierre el libro AdventureWorksReport en Visual Studio diseñador, si sigue abierto.

2. Abra el libro AdventureWorksReport que se encuentra en la carpeta de compilación del **proyecto AdventureWorksReport.** De forma predeterminada, la carpeta de compilación se encuentra en una de las siguientes ubicaciones:

    - *%UserProfile%\Mis documentos\AdventureWorksReport\bin\Debug* (para Windows XP y versiones anteriores)

    - *%UserProfile%\Documents\AdventureWorksReport\bin\Debug* (para Windows Vista)

3. Compruebe que el valor de la **columna ListPrice** de la primera fila de <xref:Microsoft.Office.Tools.Excel.ListObject> ahora es 1574,65.

4. Cierre el libro.

## <a name="see-also"></a>Consulte también

- [Tutorial: Insertar datos en un libro en un servidor](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)
