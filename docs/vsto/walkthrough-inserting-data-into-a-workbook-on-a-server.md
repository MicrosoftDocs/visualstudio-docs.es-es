---
title: 'Tutorial: Insertar datos en un libro en un servidor | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
- workbooks [Office development in Visual Studio], inserting data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7257094aa0fb29c1b03878f5ac39c3d4f4864022
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-inserting-data-into-a-workbook-on-a-server"></a>Tutorial: Insertar datos en un libro de trabajo de un servidor
  Este tutorial muestra cómo insertar datos en un conjunto de datos que se almacena en caché en un libro de Microsoft Office Excel sin iniciar Excel, mediante la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Definir un conjunto de datos que contiene los datos de la base de datos AdventureWorksLT.  
  
-   Creación de instancias del conjunto de datos en un proyecto de libro de Excel y un proyecto de aplicación de consola.  
  
-   Crear un <xref:Microsoft.Office.Tools.Excel.ListObject> que está enlazada al conjunto de datos en el libro.  
  
-   Agregue el conjunto de datos en el libro a la caché de datos.  
  
-   Insertar datos en el conjunto de datos almacenados en memoria caché cuando se ejecuta código en la aplicación de consola, sin iniciar Excel.  
  
 Aunque en este tutorial se da por supuesto que está ejecutando el código en el equipo de desarrollo, el código que se muestran en este tutorial se puede utilizar en un servidor que no tienen Excel instalado.  
  
> [!NOTE]  
>  Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Acceso a una instancia en ejecución de Microsoft SQL Server o Microsoft SQL Server Express que tenga adjunta la base de datos de ejemplo AdventureWorksLT. Puede descargar la base de datos AdventureWorksLT del [sitio Web de CodePlex](http://go.microsoft.com/fwlink/?linkid=87843). Para obtener más información sobre cómo asociar una base de datos, vea los siguientes temas:  
  
    -   Para asociar una base de datos mediante SQL Server Management Studio o SQL Server Management Studio Express, vea [Cómo: asociar una base de datos (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Para asociar una base de datos mediante la línea de comandos, vea [Cómo: asociar un archivo de base de datos a SQL Server Express](http://msdn.microsoft.com/en-us/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## <a name="creating-a-class-library-project-that-defines-a-dataset"></a>Crear un proyecto de biblioteca de clases que define un conjunto de datos  
 Para utilizar el mismo conjunto de datos en un proyecto de libro de Excel y una aplicación de consola, debe definir el conjunto de datos en un ensamblado independiente que se hace referencia a dos de estos proyectos. En este tutorial, defina el conjunto de datos en un proyecto de biblioteca de clases.  
  
#### <a name="to-create-the-class-library-project"></a>Para crear el proyecto de biblioteca de clases  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.  
  
3.  En el panel Plantillas, expanda **Visual C#** o **Visual Basic**y, a continuación, haga clic en **Windows**.  
  
4.  En la lista de plantillas de proyecto, seleccione **biblioteca de clases**.  
  
5.  En el **nombre** , escriba **AdventureWorksDataSet**.  
  
6.  Haga clic en **examinar**, desplácese hasta la %UserProfile%\My documentos (para Windows XP y versiones anteriores) o la carpeta %UserProfile%\Documents (para Windows Vista) y, a continuación, haga clic en **seleccionar la carpeta**.  
  
7.  En el **nuevo proyecto** diálogo cuadro, asegúrese de que el **crear directorio para la solución** casilla de verificación no está activada.  
  
8.  Haga clic en **Aceptar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Agrega el **AdventureWorksDataSet** proyecto al **el Explorador de soluciones** y abre el **Class1.cs** o **Class1.vb** archivo de código.  
  
9. En **el Explorador de soluciones**, haga clic en **Class1.cs** o **Class1.vb**y, a continuación, haga clic en **eliminar**. No es necesario este archivo para este tutorial.  
  
## <a name="defining-a-dataset-in-the-class-library-project"></a>Definir un conjunto de datos en el proyecto de biblioteca de clases  
 Definir un conjunto de datos con tipo que contiene los datos de la base de datos AdventureWorksLT para SQL Server 2005. Más adelante en este tutorial, hará referencia a este conjunto de datos de un proyecto de libro de Excel y un proyecto de aplicación de consola.  
  
 El conjunto de datos es un *con el tipo de conjunto de datos* que representa los datos en la tabla Product de la base de datos AdventureWorksLT. Para obtener más información acerca de los conjuntos de datos, vea [herramientas de conjunto de datos en Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
#### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>Para definir un conjunto de datos con tipo en el proyecto de biblioteca de clases  
  
1.  En **el Explorador de soluciones**, haga clic en el **AdventureWorksDataSet** proyecto.  
  
2.  Si la ventana **Orígenes de datos** no es visible, muéstrela; para ello, en la barra de menús, elija **Ver**, **Otras ventanas**, **Orígenes de datos**.  
  
3.  Elija **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.  
  
4.  Haga clic en **Base de datos**y luego en **Siguiente**.  
  
5.  Si tiene una conexión existente a la base de datos AdventureWorksLT, elija esta conexión y haga clic en **siguiente**.  
  
     De lo contrario, haga clic en **Nueva conexión**y use el cuadro de diálogo **Agregar conexión** para crear la nueva conexión. Para obtener más información, consulte [Cómo: conectarse a los datos en una base de datos](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md).  
  
6.  En la página **Guardar cadena de conexión en el archivo de configuración de la aplicación** , haga clic en **Siguiente**.  
  
7.  En el **elija los objetos de base de datos** página, expanda **tablas** y seleccione **Product (SalesLT)**.  
  
8.  Haga clic en **Finalizar**.  
  
     El archivo AdventureWorksLTDataSet.xsd se agrega a la **AdventureWorksDataSet** proyecto. Este archivo define los siguientes elementos:  
  
    -   Un conjunto de datos con tipo denominado `AdventureWorksLTDataSet`. Este conjunto de datos representa el contenido de la tabla Product de la base de datos AdventureWorksLT.  
  
    -   Un TableAdapter llamado `ProductTableAdapter`. Este TableAdapter puede usarse para leer y escribir datos el `AdventureWorksLTDataSet`. Para obtener más información, consulta [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     Estos dos objetos se usarán más adelante en este tutorial.  
  
9. En **el Explorador de soluciones**, haga clic en **AdventureWorksDataSet** y haga clic en **generar**.  
  
     Compruebe que el proyecto se compila sin errores.  
  
## <a name="creating-an-excel-workbook-project"></a>Crear un proyecto de libro de Excel  
 Crear un proyecto de libro de Excel para la interfaz a los datos. Más adelante en este tutorial, creará un <xref:Microsoft.Office.Tools.Excel.ListObject> que muestre los datos y agregará una instancia del conjunto de datos a la caché de datos en el libro.  
  
#### <a name="to-create-the-excel-workbook-project"></a>Para crear el proyecto de libro de Excel  
  
1.  En **el Explorador de soluciones**, haga clic en el **AdventureWorksDataSet** solución, seleccione **agregar**y, a continuación, haga clic en **nuevo proyecto**.  
  
2.  En el panel de plantillas, expanda **Visual C#** o **Visual Basic**y luego expanda **Office/SharePoint**.  
  
3.  En el nodo **Office/SharePoint** expandido, seleccione el nodo **Complementos de Office** .  
  
4.  En la lista de plantillas de proyecto, seleccione el proyecto **Libro de Excel 2010** o **Libro de Excel 2013** .  
  
5.  En el **nombre** , escriba **AdventureWorksReport**. No modifique la ubicación.  
  
6.  Haga clic en **Aceptar**.  
  
     Se abre el **Asistente para proyectos de Visual Studio Tools para Office** .  
  
7.  Asegúrese de que **crear un nuevo documento** está seleccionada y haga clic en **Aceptar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] se abre la **AdventureWorksReport** libro en el diseñador y agrega el **AdventureWorksReport** proyecto al **el Explorador de soluciones**.  
  
## <a name="adding-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Agregar el conjunto de datos a orígenes de datos en el proyecto de libro de Excel  
 Antes de poder mostrar el conjunto de datos en el libro de Excel, primero debe agregar el conjunto de datos a orígenes de datos en el proyecto de libro de Excel.  
  
#### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>Para agregar el conjunto de datos a los orígenes de datos en el proyecto de libro de Excel  
  
1.  En **el Explorador de soluciones**, haga doble clic en **Sheet1.cs** o **Sheet1.vb** en el **AdventureWorksReport** proyecto.  
  
     El libro se abre en el diseñador.  
  
2.  En el menú **Datos** , haga clic en **Agregar nuevo elemento**.  
  
     El **Asistente para configuración de orígenes de datos** se abre.  
  
3.  Haga clic en **objeto**y, a continuación, haga clic en **siguiente**.  
  
4.  En el **seleccione el objeto que se va a enlazar** a la página, haga clic en **Agregar referencia**.  
  
5.  En el **proyectos** , haga clic en **AdventureWorksDataSet** y, a continuación, haga clic en **Aceptar**.  
  
6.  En el **AdventureWorksDataSet** espacio de nombres de la **AdventureWorksDataSet** ensamblado, haga clic en **AdventureWorksLTDataSet** y, a continuación, haga clic en **finalizar** .  
  
     El **orígenes de datos** abre la ventana, y **AdventureWorksLTDataSet** se agrega a la lista de orígenes de datos.  
  
## <a name="creating-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Crear un control ListObject enlazado a una instancia del conjunto de datos  
 Para mostrar el conjunto de datos en el libro, cree un <xref:Microsoft.Office.Tools.Excel.ListObject> que está enlazado a una instancia del conjunto de datos. Para más información sobre el enlace de controles a datos, consulte [Binding Data to Controls in Office Solutions](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Para crear un control ListObject enlazado a una instancia del conjunto de datos  
  
1.  En el **orígenes de datos** ventana, expanda la **AdventureWorksLTDataSet** nodo bajo **AdventureWorksDataSet**.  
  
2.  Seleccione el **producto** nodo, haga clic en la flecha de lista desplegable que aparece y seleccione **ListObject** en la lista desplegable.  
  
     Si no aparece la flecha de lista desplegable, confirme que el libro está abierto en el diseñador.  
  
3.  Arrastre el **producto** tabla a la celda A1.  
  
     A <xref:Microsoft.Office.Tools.Excel.ListObject> control denominado `productListObject` se crea en la hoja de cálculo, empezando por la celda A1. Al mismo tiempo, un objeto de conjunto de datos denominado `adventureWorksLTDataSet` y un <xref:System.Windows.Forms.BindingSource> denominado `productBindingSource` se agregan al proyecto. El <xref:Microsoft.Office.Tools.Excel.ListObject> se enlaza a <xref:System.Windows.Forms.BindingSource>, que a su vez se enlaza al objeto de conjunto de datos.  
  
## <a name="adding-the-dataset-to-the-data-cache"></a>Agregue el conjunto de datos a la caché de datos  
 Para que el código fuera del proyecto de libro de Excel para tener acceso el conjunto de datos en el libro, debe agregar el conjunto de datos a la caché de datos. Para obtener más información acerca de la caché de datos, vea [datos almacenados en memoria caché en las personalizaciones de nivel de documento](../vsto/cached-data-in-document-level-customizations.md) y [almacenar datos en caché](../vsto/caching-data.md).  
  
#### <a name="to-add-the-dataset-to-the-data-cache"></a>Para agregar el conjunto de datos a la caché de datos  
  
1.  En el diseñador, haga clic en **adventureWorksLTDataSet**.  
  
2.  En el **propiedades** ventana, establezca el **modificadores** propiedad **público**.  
  
3.  Establecer el **CacheInDocument** propiedad **True**.  
  
## <a name="checkpoint"></a>Punto de control  
 Compile y ejecute el proyecto de libro de Excel para asegurarse de que se compila y se ejecuta sin errores.  
  
#### <a name="to-build-and-run-the-project"></a>Para compilar y ejecutar el proyecto  
  
1.  En **el Explorador de soluciones**, haga clic en el **AdventureWorksReport** proyecto, elija **depurar**y, a continuación, haga clic en **Iniciar nueva instancia**.  
  
     Se compila el proyecto y se abre el libro en Excel. El <xref:Microsoft.Office.Tools.Excel.ListObject> en **Sheet1** está vacía, porque la `adventureWorksLTDataSet` objeto en la caché de datos no aún ningún dato. En la sección siguiente, utilizará una aplicación de consola para rellenar el `adventureWorksLTDataSet` objeto con datos.  
  
2.  Cierre Excel. No guardar los cambios.  
  
## <a name="creating-a-console-application-project"></a>Crear un proyecto de aplicación de consola  
 Cree un proyecto de aplicación de consola se utiliza para insertar datos en el conjunto de datos almacenado en caché en el libro.  
  
#### <a name="to-create-the-console-application-project"></a>Para crear el proyecto de aplicación de consola  
  
1.  En **el Explorador de soluciones**, haga clic en el **AdventureWorksDataSet** solución, seleccione **agregar**y, a continuación, haga clic en **nuevo proyecto**.  
  
2.  En el **tipos de proyecto** panel, expanda **Visual C#** o **Visual Basic**y, a continuación, haga clic en **Windows**.  
  
3.  En el **plantillas** panel, seleccione **aplicación de consola**.  
  
4.  En el **nombre** , escriba **DataWriter**. No modifique la ubicación.  
  
5.  Haga clic en **Aceptar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Agrega el **DataWriter** proyecto al **el Explorador de soluciones** y abre el **Program.cs** o **Module1.vb** archivo de código.  
  
## <a name="adding-data-to-the-cached-dataset-by-using-the-console-application"></a>Agregar datos al conjunto de datos almacenado en caché mediante el uso de la aplicación de consola  
 Use la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase en la aplicación de consola para rellenar el conjunto de datos almacenado en caché en el libro con datos.  
  
#### <a name="to-add-data-to-the-cached-dataset"></a>Para agregar datos al conjunto de datos almacenados en caché  
  
1.  En **el Explorador de soluciones**, haga clic en el **DataWriter** del proyecto y haga clic en **Agregar referencia**.  
  
2.  En el **.NET** ficha, seleccione **Microsoft.VisualStudio.Tools.Applications.ServerDocument**.  
  
3.  Haga clic en **Aceptar**.  
  
4.  En **el Explorador de soluciones**, haga clic en el **DataWriter** del proyecto y haga clic en **Agregar referencia**.  
  
5.  En el **proyectos** ficha, seleccione **AdventureWorksDataSet**y haga clic en **Aceptar**.  
  
6.  Abra el archivo Program.cs o Module1.vb en el Editor de código.  
  
7.  Agregue el siguiente **con** (en C#) o **importaciones** (en Visual Basic) instrucción al principio del archivo de código.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
     [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]  
  
8.  Agregue el código siguiente al método `Main` . Este código declara los siguientes objetos:  
  
    -   Instancias de la `AdventureWorksLTDataSet` y `ProductTableAdapter` tipos que se definen en el **AdventureWorksDataSet** proyecto.  
  
    -   La ruta de acceso al libro AdventureWorksReport en la carpeta de compilación de la **AdventureWorksReport** proyecto.  
  
    -   Un <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> objeto que se va a utilizar para tener acceso a la caché de datos en el libro.  
  
        > [!NOTE]  
        >  El código siguiente se da por supuesto que está usando un libro que tiene la extensión de archivo .xlsx. Si el libro en el proyecto tiene una extensión de archivo diferente, modifique la ruta de acceso según sea necesario.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#3](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#3)]
     [!code-vb[Trin_CachedDataWalkthroughs#3](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#3)]  
  
9. Agregue el código siguiente a la `Main` método después del código que agregó en el paso anterior. Este código realiza las tareas siguientes:  
  
    -   Rellena el objeto de conjunto de datos con tipo mediante el adaptador de tabla.  
  
    -   Usa el <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> propiedad de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase para tener acceso el conjunto de datos almacenado en caché en el libro.  
  
    -   Usa el <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> método para rellenar el conjunto de datos almacenados en memoria caché con datos del conjunto de datos con tipo local.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#4](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#4)]
     [!code-vb[Trin_CachedDataWalkthroughs#4](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#4)]  
  
10. En **el Explorador de soluciones**, haga clic en el **DataWriter** , seleccione **depurar**y, a continuación, haga clic en **Iniciar nueva instancia**.  
  
     Se compila el proyecto y la aplicación de consola muestra varios mensajes de estado cuando se llena el conjunto de datos local y cuando la aplicación guarda los datos en el conjunto de datos almacenado en caché en el libro. Presione ENTRAR para cerrar la aplicación.  
  
## <a name="testing-the-workbook"></a>Probar el libro  
 Cuando se abre el libro, la <xref:Microsoft.Office.Tools.Excel.ListObject> muestra ahora los datos que se ha agregado al conjunto de datos almacenado en caché mediante el uso de la aplicación de consola.  
  
#### <a name="to-test-the-workbook"></a>Para probar el libro  
  
1.  Cierre el libro AdventureWorksReport en el Diseñador de Visual Studio, si aún está abierto.  
  
2.  En el Explorador de archivos, abra el libro AdventureWorksReport que se encuentra en la carpeta de compilación de la **AdventureWorksReport** proyecto. De forma predeterminada, la carpeta de compilación se encuentra en una de las siguientes ubicaciones:  
  
    -   %USERPROFILE%\My documentos\AdventureWorksReport\bin\Debug (para Windows XP y versiones anteriores)  
  
    -   %UserProfile%\Documents\AdventureWorksReport\bin\Debug (para Windows Vista)  
  
3.  Compruebe que la <xref:Microsoft.Office.Tools.Excel.ListObject> se rellena con datos después de abrir el libro.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Se puede obtener más información sobre cómo trabajar con datos almacenados en caché en estos temas:  
  
-   Cambiar los datos en un conjunto de datos almacenados en memoria caché sin iniciar Excel. Para obtener más información, consulte [Tutorial: cambiar los datos almacenados en memoria caché en un libro en un servidor](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Cambiar los datos almacenados en caché en un libro en un servidor](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)   
 [Conectar a los datos en aplicaciones de Windows Forms](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)  
  
  