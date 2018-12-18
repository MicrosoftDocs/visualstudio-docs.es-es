---
title: 'Tutorial: Cambiar los datos almacenados en caché en un libro en un servidor'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f9f2ac3873bf59b30f8efa3e45d6cbdd0aebd4f6
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672874"
---
# <a name="walkthrough-change-cached-data-in-a-workbook-on-a-server"></a>Tutorial: Cambiar los datos almacenados en caché en un libro en un servidor
  Este tutorial muestra cómo modificar un conjunto de datos que se almacena en caché en un libro de Microsoft Office Excel sin iniciar Excel, mediante el <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Definir un conjunto de datos que contiene los datos de la base de datos AdventureWorksLT.

- Creación de instancias del conjunto de datos en un proyecto de libro de Excel y un proyecto de aplicación de consola.

- Creación de un <xref:Microsoft.Office.Tools.Excel.ListObject> que está enlazada al conjunto de datos en el libro y rellenar el <xref:Microsoft.Office.Tools.Excel.ListObject> con datos cuando se abre el libro.

- Agregar el conjunto de datos en el libro a la caché de datos.

- Modificar una columna de datos del conjunto de datos en caché mediante la ejecución de código en la aplicación de consola, sin iniciar Excel.

  Aunque en este tutorial se da por supuesto que se está ejecutando el código en el equipo de desarrollo, el código que se muestran en este tutorial puede usarse en un servidor que no tienen Excel instalado.

> [!NOTE]
>  Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesita los componentes siguientes para completar este tutorial:

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

-   Acceso a una instancia en ejecución de Microsoft SQL Server o Microsoft SQL Server Express que tiene la base de datos de ejemplo AdventureWorksLT conectada a ella. Puede descargar la base de datos AdventureWorksLT el [sitio Web de CodePlex](http://go.microsoft.com/fwlink/?linkid=87843). Para obtener más información sobre cómo asociar una base de datos, vea los siguientes temas:

    -   Para adjuntar una base de datos mediante SQL Server Management Studio o SQL Server Management Studio Express, vea [Cómo: adjuntar una base de datos (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

    -   Para adjuntar una base de datos mediante la línea de comandos, consulte [Cómo: adjuntar un archivo de base de datos a SQL Server Express](/previous-versions/sql/).

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Cree un proyecto de biblioteca de clases que define un conjunto de datos
 Para usar el mismo conjunto de datos en un proyecto de libro de Excel y una aplicación de consola, debe definir el conjunto de datos en un ensamblado independiente que se hace referencia por ambos proyectos. En este tutorial, defina el conjunto de datos en un proyecto de biblioteca de clases.

### <a name="to-create-the-class-library-project"></a>Para crear el proyecto de biblioteca de clases

1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2.  En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.

3.  En el panel Plantillas, expanda **Visual C#** o **Visual Basic**y, a continuación, haga clic en **Windows**.

4.  En la lista de plantillas de proyecto, seleccione **biblioteca de clases**.

5.  En el **nombre** , escriba **AdventureWorksDataSet**.

6.  Haga clic en **examinar**, vaya a su *%UserProfile%\My documentos* (para Windows XP y versiones anteriores) o *%UserProfile%\Documents* (para Windows Vista) carpeta y, a continuación, haga clic en **Seleccionar carpeta**.

7.  En el **nuevo proyecto** diálogo cuadro, asegúrese de que el **crear directorio para la solución** casilla de verificación no está seleccionada.

8.  Haga clic en **Aceptar**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Agrega el **AdventureWorksDataSet** proyecto a **el Explorador de soluciones** y abre el **Class1.cs** o **Class1.vb** archivo de código.

9. En **el Explorador de soluciones**, haga clic en **Class1.cs** o **Class1.vb**y, a continuación, haga clic en **eliminar**. No es necesario este archivo para este tutorial.

## <a name="define-a-dataset-in-the-class-library-project"></a>Definir un conjunto de datos en el proyecto de biblioteca de clases
 Definir un conjunto de datos con tipo que contiene los datos de la base de datos AdventureWorksLT para SQL Server 2005. Más adelante en este tutorial, hará referencia a este conjunto de datos desde un proyecto de libro de Excel y un proyecto de aplicación de consola.

 El conjunto de datos es un *con el tipo de conjunto de datos* que representa los datos en la tabla Product de la base de datos AdventureWorksLT. Para obtener más información acerca de los conjuntos de datos con tipo, consulte [herramientas de conjunto de datos en Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).

### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>Para definir un conjunto de datos con tipo en el proyecto de biblioteca de clases

1. En **el Explorador de soluciones**, haga clic en el **AdventureWorksDataSet** proyecto.

2. Si el **orígenes de datos** ventana no está visible, muéstrela; en la barra de menús, elija **vista** > **Other Windows**  >   **Orígenes de datos**.

3. Elija **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

4. Haga clic en **Base de datos**y luego en **Siguiente**.

5. Si tiene una conexión existente a la base de datos AdventureWorksLT, elija esa conexión y haga clic en **siguiente**.

    De lo contrario, haga clic en **Nueva conexión**y use el cuadro de diálogo **Agregar conexión** para crear la nueva conexión. Para obtener más información, consulte [agregar nuevas conexiones](../data-tools/add-new-connections.md).

6. En la página **Guardar cadena de conexión en el archivo de configuración de la aplicación** , haga clic en **Siguiente**.

7. En el **elija los objetos de base de datos** , expanda **tablas** y seleccione **Product (SalesLT)**.

8. Haga clic en **Finalizar**.

    El *AdventureWorksLTDataSet.xsd* archivo se agrega a la **AdventureWorksDataSet** proyecto. Este archivo define los siguientes elementos:

   - Un conjunto de datos con tipo denominado `AdventureWorksLTDataSet`. Este conjunto de datos representa el contenido de la tabla Product de la base de datos AdventureWorksLT.

   - Un TableAdapter llamado `ProductTableAdapter`. Este TableAdapter puede usarse para leer y escribir datos el `AdventureWorksLTDataSet`. Para obtener más información, consulte [información general sobre TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Estos dos objetos se usarán más adelante en este tutorial.

9. En **el Explorador de soluciones**, haga clic en **AdventureWorksDataSet** y haga clic en **compilar**.

     Compruebe que el proyecto se compila sin errores.

## <a name="create-an-excel-workbook-project"></a>Crear un proyecto de libro de Excel
 Cree un proyecto de libro de Excel para la interfaz a los datos. Más adelante en este tutorial, creará un <xref:Microsoft.Office.Tools.Excel.ListObject> que muestra los datos y agregará una instancia del conjunto de datos a la caché de datos en el libro.

### <a name="to-create-the-excel-workbook-project"></a>Para crear el proyecto de libro de Excel

1.  En **el Explorador de soluciones**, haga clic en el **AdventureWorksDataSet** solución, seleccione **agregar**y, a continuación, haga clic en **nuevo proyecto**.

2.  En el panel Plantillas, expanda **Visual C#** o **Visual Basic**y, a continuación, expanda **Office**.

3.  En el modo expandido **Office** nodo, seleccione el **2010** nodo.

4.  En la lista de plantillas de proyecto, seleccione el proyecto de libro de Excel.

5.  En el **nombre** , escriba **AdventureWorksReport**. No modifique la ubicación.

6.  Haga clic en **Aceptar**.

     Se abre el **Asistente para proyectos de Visual Studio Tools para Office** .

7.  Asegúrese de que **crear un nuevo documento** está seleccionada y haga clic en **Aceptar**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] se abre el **AdventureWorksReport** libro en el diseñador y agrega el **AdventureWorksReport** proyecto a **el Explorador de soluciones**.

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Agregar el conjunto de datos a orígenes de datos en el proyecto de libro de Excel
 Antes de poder mostrar el conjunto de datos del libro de Excel, primero debe agregar el conjunto de datos a orígenes de datos en el proyecto de libro de Excel.

### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>Para agregar el conjunto de datos a los orígenes de datos en el proyecto de libro de Excel

1.  En **el Explorador de soluciones**, haga doble clic en **Sheet1.cs** o **Sheet1.vb** bajo el **AdventureWorksReport** proyecto.

     El libro se abre en el diseñador.

2.  En el menú **Datos** , haga clic en **Agregar nuevo elemento**.

     El **Asistente para configuración de origen de datos** se abre.

3.  Haga clic en **objeto**y, a continuación, haga clic en **siguiente**.

4.  En el **seleccione el objeto que desee enlazar a** página, haga clic en **Agregar referencia**.

5.  En el **proyectos** , haga clic **AdventureWorksDataSet** y, a continuación, haga clic en **Aceptar**.

6.  En el **AdventureWorksDataSet** espacio de nombres de los **AdventureWorksDataSet** ensamblado, haga clic en **AdventureWorksLTDataSet** y, a continuación, haga clic en **finalizar** .

     El **orígenes de datos** abre la ventana, y **AdventureWorksLTDataSet** se agrega a la lista de orígenes de datos.

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Crear un control ListObject enlazado a una instancia del conjunto de datos
 Para mostrar el conjunto de datos en el libro, cree un <xref:Microsoft.Office.Tools.Excel.ListObject> que está enlazado a una instancia del conjunto de datos. Para obtener más información acerca de los controles de enlace a datos, vea [enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Para crear un control ListObject enlazado a una instancia del conjunto de datos

1.  En el **orígenes de datos** ventana, expanda el **AdventureWorksLTDataSet** nodo bajo **AdventureWorksDataSet**.

2.  Seleccione el **producto** nodo, haga clic en la flecha de lista desplegable que aparece y seleccione **ListObject** en la lista desplegable.

     Si no aparece la flecha de lista desplegable, confirme que el libro está abierto en el diseñador.

3.  Arrastre el **producto** tabla a la celda A1.

     Un <xref:Microsoft.Office.Tools.Excel.ListObject> control denominado `productListObject` se crea en la hoja de cálculo, comenzando en la celda A1. Al mismo tiempo, se agregan al proyecto un objeto de conjunto de datos denominado `adventureWorksLTDataSet` y un elemento <xref:System.Windows.Forms.BindingSource> con el nombre `productBindingSource`. El elemento <xref:Microsoft.Office.Tools.Excel.ListObject> se enlaza al elemento <xref:System.Windows.Forms.BindingSource>, que a su vez se enlaza al objeto de conjunto de datos.

## <a name="add-the-dataset-to-the-data-cache"></a>Agregar el conjunto de datos a la caché de datos
 Para permitir que el código fuera del proyecto de libro de Excel para tener acceso al conjunto de datos en el libro, debe agregar el conjunto de datos a la caché de datos. Para obtener más información acerca de la caché de datos, vea [en caché los datos en las personalizaciones de nivel de documento](../vsto/cached-data-in-document-level-customizations.md) y [almacenar en caché datos](../vsto/caching-data.md).

### <a name="to-add-the-dataset-to-the-data-cache"></a>Para agregar el conjunto de datos a la caché de datos

1.  En el diseñador, haga clic en **adventureWorksLTDataSet**.

2.  En el **propiedades** ventana, establezca el **modificadores** propiedad **pública**.

3.  Establecer el **CacheInDocument** propiedad **True**.

## <a name="initialize-the-dataset-in-the-workbook"></a>Inicializar el conjunto de datos en el libro
 Para poder recuperar los datos del conjunto de datos en caché mediante el uso de la aplicación de consola, primero debe rellenar el conjunto de datos en caché con los datos.

### <a name="to-initialize-the-dataset-in-the-workbook"></a>Para inicializar el conjunto de datos en el libro

1.  En **el Explorador de soluciones**, haga clic en el **Sheet1.cs** o **Sheet1.vb** de archivo y haga clic en **ver código**.

2.  Reemplace el controlador de eventos `Sheet1_Startup` por el siguiente código: Este código utiliza una instancia de la `ProductTableAdapter` clase que se define en el **AdventureWorksDataSet** proyecto para rellenar el conjunto de datos en caché con los datos, si está vacía actualmente.

     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]

## <a name="checkpoint"></a>Punto de control
 Compile y ejecute el proyecto de libro de Excel para asegurarse de que se compila y se ejecuta sin errores. Esta operación también rellena el conjunto de datos en caché y guarda los datos en el libro.

### <a name="to-build-and-run-the-project"></a>Para compilar y ejecutar el proyecto

1.  En **el Explorador de soluciones**, haga clic en el **AdventureWorksReport** del proyecto, elija **depurar**y, a continuación, haga clic en **Iniciar nueva instancia**.

     El proyecto se compila y se abre el libro en Excel. Compruebe lo siguiente:

    -   El <xref:Microsoft.Office.Tools.Excel.ListObject> rellena con datos.

    -   El valor de la **ListPrice** columna para la primera fila de la <xref:Microsoft.Office.Tools.Excel.ListObject> es 1431.5. Más adelante en este tutorial, usará una aplicación de consola para modificar los valores en el **ListPrice** columna.

2.  Guarde el libro. No modifique el nombre de archivo o la ubicación del libro.

3.  Cierre Excel.

## <a name="create-a-console-application-project"></a>Cree un proyecto de aplicación de consola
 Cree un proyecto de aplicación de consola a usar para modificar los datos del conjunto de datos en caché en el libro.

### <a name="to-create-the-console-application-project"></a>Para crear el proyecto de aplicación de consola

1.  En **el Explorador de soluciones**, haga clic en el **AdventureWorksDataSet** solución, seleccione **agregar**y, a continuación, haga clic en **nuevo proyecto**.

2.  En el **tipos de proyecto** panel, expanda **Visual C#** o **Visual Basic**y, a continuación, haga clic en **Windows**.

3.  En el **plantillas** panel, seleccione **aplicación de consola**.

4.  En el **nombre** , escriba **DataWriter**. No modifique la ubicación.

5.  Haga clic en **Aceptar**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Agrega el **DataWriter** proyecto a **el Explorador de soluciones** y abre el **Program.cs** o **Module1.vb** archivo de código.

## <a name="change-data-in-the-cached-dataset-by-using-the-console-application"></a>Cambiar los datos del conjunto de datos en caché mediante el uso de la aplicación de consola
 Use la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase en la aplicación de consola para leer los datos en una variable local `AdventureWorksLTDataSet` objeto, modificar estos datos y, a continuación, guardarla en el conjunto de datos en caché.

### <a name="to-change-data-in-the-cached-dataset"></a>Para cambiar los datos del conjunto de datos en caché

1. En **el Explorador de soluciones**, haga clic en el **DataWriter** del proyecto y haga clic en **Agregar referencia**.

2. En el **.NET** ficha, seleccione **Microsoft.VisualStudio.Tools.Applications**.

3. Haga clic en **Aceptar**.

4. En **el Explorador de soluciones**, haga clic en el **DataWriter** del proyecto y haga clic en **Agregar referencia**.

5. En el **proyectos** ficha, seleccione **AdventureWorksDataSet**y haga clic en **Aceptar**.

6. Abra el *Program.cs* o *Module1.vb* archivo en el Editor de código.

7. Agregue el siguiente **mediante** (para C#) o **importaciones** (para Visual Basic) instrucción a la parte superior del archivo de código.

    [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
    [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]

8. Agregue el código siguiente al método `Main`. Este código declara los siguientes objetos:

   - Una instancia de la `AdventureWorksLTDataSet` tipo que se define en el **AdventureWorksDataSet** proyecto.

   - La ruta de acceso al libro AdventureWorksReport en la carpeta de compilación de la **AdventureWorksReport** proyecto.

   - Un <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> objeto va a utilizar para tener acceso a la caché de datos en el libro.

     > [!NOTE]
     >  El código siguiente se da por supuesto que está usando un libro que tiene el *.xlsx* la extensión de archivo. Si el libro en el proyecto tiene una extensión de archivo diferente, modifique la ruta de acceso según sea necesario.

     [!code-csharp[Trin_CachedDataWalkthroughs#6](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#6)]
     [!code-vb[Trin_CachedDataWalkthroughs#6](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#6)]

9. Agregue el código siguiente a la `Main` método después del código que agregó en el paso anterior. Este código realiza las tareas siguientes:

   - Usa el <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> propiedad de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase para tener acceso el conjunto de datos en caché en el libro.

   - Lee los datos del conjunto de datos en caché en el conjunto de datos local.

   - Cambia el `ListPrice` valor de cada producto en la tabla Product del conjunto de datos.

   - Guarda los cambios en el conjunto de datos en caché en el libro.

     [!code-csharp[Trin_CachedDataWalkthroughs#7](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#7)]
     [!code-vb[Trin_CachedDataWalkthroughs#7](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#7)]

10. En **el Explorador de soluciones**, haga clic en el **DataWriter** , seleccione **depurar**y, a continuación, haga clic en **Iniciar nueva instancia**.

     La aplicación de consola muestra mensajes mientras lee el conjunto de datos en caché en el conjunto de datos local, modifica los precios de productos del conjunto de datos local y guardan los nuevos valores al conjunto de datos en caché. Presione **ENTRAR** para cerrar la aplicación.

## <a name="test-the-workbook"></a>Probar el libro
 Al abrir el libro, el <xref:Microsoft.Office.Tools.Excel.ListObject> ahora muestra los cambios realizados en el `ListPrice` columna de datos en el conjunto de datos en caché.

### <a name="to-test-the-workbook"></a>Para probar el libro

1.  Cierre el libro AdventureWorksReport en el Diseñador de Visual Studio, si aún está abierta.

2.  Abra el libro AdventureWorksReport que se encuentra en la carpeta de compilación de la **AdventureWorksReport** proyecto. De forma predeterminada, la carpeta de compilación está en una de las siguientes ubicaciones:

    -   *%USERPROFILE%\My documentos\AdventureWorksReport\bin\Debug* (para Windows XP y versiones anteriores)

    -   *%UserProfile%\Documents\AdventureWorksReport\bin\Debug* (para Windows Vista)

3.  Compruebe que el valor de la **ListPrice** columna para la primera fila de la <xref:Microsoft.Office.Tools.Excel.ListObject> es ahora 1574.65.

4.  Cierre el libro.

## <a name="see-also"></a>Vea también

- [Tutorial: Insertar datos en un libro en un servidor](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)