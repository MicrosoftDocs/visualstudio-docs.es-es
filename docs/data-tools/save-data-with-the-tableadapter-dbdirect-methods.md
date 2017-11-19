---
title: "Guardar los datos con el TableAdapter DBDirect métodos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 3ed52a167b607236b8493e4c8c1736ee597162b9
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Guardar los datos con el TableAdapter DBDirect métodos
Este tutorial proporciona instrucciones detalladas para ejecutar instrucciones SQL directamente en una base de datos mediante los métodos DBDirect de un TableAdapter. Los métodos DBDirect de un TableAdapter proporcionan un nivel exhaustivo de control sobre las actualizaciones de base de datos. Puede usarlas para ejecutar instrucciones SQL específicas y procedimientos almacenados mediante una llamada a la persona `Insert`, `Update`, y `Delete` métodos según sea necesario por la aplicación (en lugar de sobrecargado `Update` método que realiza la actualización Instrucciones INSERT y DELETE en una llamada).  
  
 Durante este tutorial aprenderá a:  
  
-   Crear un nuevo **aplicación de Windows Forms**.  
  
-   Crear y configurar un conjunto de datos con la [Asistente para configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Seleccione el control que se creará en el formulario al arrastrar elementos desde la **orígenes de datos** ventana. Para obtener más información, consulte [establecer el control que se creará al arrastrar desde la ventana de orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Crear un formulario enlazado a datos arrastrando elementos desde la **orígenes de datos** ventana hasta el formulario.  
  
-   Agregar métodos para tener acceso a la base de datos y realizar inserciones, actualizaciones y eliminaciones directamente...  
  
## <a name="prerequisites"></a>Requisitos previos  
Este tutorial usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.  
  
1.  Si no tiene SQL Server Express LocalDB, puede instalarlo desde el [página de descarga de ediciones de SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), o a través del **instalador de Visual Studio**. El instalador de Visual Studio, se puede instalar SQL Server Express LocalDB como parte de la **almacenamiento de datos y el procesamiento** carga de trabajo, o como un componente individual.  
  
2.  Instalar la base de datos de ejemplo Northwind, siga estos pasos:  

    1. En Visual Studio, abra el **Explorador de objetos de SQL Server** ventana. (Explorador de objetos de SQL Server se instala como parte de la **almacenamiento de datos y el procesamiento** carga de trabajo en el instalador de Visual Studio.) Expanda el **SQL Server** nodo. Haga doble clic en la instancia de LocalDB y seleccione **nueva consulta...** .  

       Se abre una ventana del editor de consultas.  

    2. Copia la [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el Portapapeles. Este script de T-SQL crea la base de datos Northwind desde el principio y lo rellena con datos.  

    3. Pegue el script de T-SQL en el editor de consultas y, a continuación, elija la **Execute** botón.  

       Después de unos minutos, finaliza la ejecución de la consulta y se crea la base de datos Northwind.  
  
## <a name="create-a-windows-forms-application"></a>Crear una aplicación de formularios Windows Forms  
 El primer paso es crear un **aplicación de Windows Forms**.  
  
#### <a name="to-create-the-new-windows-project"></a>Para crear el nuevo proyecto de Windows  
  
1. En Visual Studio, en el **archivo** menú, seleccione **New**, **proyecto...** .  
  
2. Expanda **Visual C#** o **Visual Basic** en el panel izquierdo, seleccione **escritorio clásico de Windows**.  

3. En el panel central, seleccione la **aplicación de Windows Forms** tipo de proyecto.  

4. Denomine el proyecto **nombre TableAdapterDbDirectMethodsWalkthrough**y, a continuación, elija **Aceptar**. 
  
     El **nombre TableAdapterDbDirectMethodsWalkthrough** se crea y se agrega al proyecto **el Explorador de soluciones**.  
  
## <a name="create-a-data-source-from-your-database"></a>Crear un origen de datos de la base de datos  
 Este paso se utiliza el **Asistente para configuración de orígenes de datos** para crear un origen de datos basado en la `Region` tabla en la base de datos de ejemplo Northwind. Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión. Para obtener información acerca de cómo configurar la base de datos de ejemplo Northwind, vea [Cómo: instalar bases de datos de ejemplo](../data-tools/installing-database-systems-tools-and-samples.md).  
  
#### <a name="to-create-the-data-source"></a>Para crear el origen de datos  
  
1.  En el **datos** menú, seleccione **Mostrar orígenes de datos**.  
  
2.  En el **orígenes de datos** ventana, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.  
  
3.  En el **elegir un tipo de origen de datos** pantalla, seleccione **base de datos**y, a continuación, seleccione **siguiente**.  
  
4.  En el **elegir la conexión de datos** pantalla, realice una de las siguientes acciones:  
  
    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.  
  
         O bien  
  
    -   Seleccione **nueva conexión** para iniciar el **agregar o modificar conexión** cuadro de diálogo.  
  
5.  Si la base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y, a continuación, seleccione **siguiente**.  
  
6.  En el **Guardar cadena de conexión en el archivo de configuración de la aplicación** pantalla, seleccione **siguiente**.  
  
7.  En el **elija los objetos de base de datos** pantalla, expanda la **tablas** nodo.  
  
8.  Seleccione el `Region` de tabla y, a continuación, seleccione **finalizar**.  
  
     El **NorthwindDataSet** se agrega al proyecto y la `Region` tabla aparece en la **orígenes de datos** ventana.  
  
## <a name="add-controls-to-the-form-to-display-the-data"></a>Agregar controles al formulario para mostrar los datos  
 Crear los controles enlazados a datos arrastrando elementos desde la **orígenes de datos** ventana hasta el formulario.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Para crear datos enlazados a controles en el formulario Windows Forms  
  
-   Arrastre el método main **región** nodo desde el **orígenes de datos** ventana hasta el formulario.  
  
     En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `RegionTableAdapter`, <xref:System.Windows.Forms.BindingSource>, y <xref:System.Windows.Forms.BindingNavigator> aparecen en la Bandeja de componentes.  
  
#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Para agregar botones que llamarán a los métodos DbDirect de TableAdapter  
  
1.  Arrastre tres <xref:System.Windows.Forms.Button> controla desde el **cuadro de herramientas** en **Form1** (debajo de la **RegionDataGridView**).  
  
2.  Establece las siguientes opciones **nombre** y **texto** propiedades en cada botón.  
  
    |Name|Texto|  
    |----------|----------|  
    |`InsertButton`|**Insertar**|  
    |`UpdateButton`|**Actualizar**|  
    |`DeleteButton`|**Eliminar**|  
  
#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Para agregar código para insertar nuevos registros en la base de datos  
  
1.  Seleccione **InsertButton** para crear un controlador de eventos para el evento de clic y abrir el formulario en el editor de código.  
  
2.  Reemplace el controlador de evento `InsertButton_Click` con el código siguiente:  
  
     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]  
  
#### <a name="to-add-code-to-update-records-in-the-database"></a>Para agregar código para actualizar los registros de la base de datos  
  
1.  Haga doble clic en el **UpdateButton** para crear un controlador de eventos para el evento de clic y abrir el formulario en el editor de código.  
  
2.  Reemplace el controlador de evento `UpdateButton_Click` con el código siguiente:  
  
     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]  
  
#### <a name="to-add-code-to-delete-records-from-the-database"></a>Para agregar código para eliminar registros de la base de datos  
  
1.  Seleccione **DeleteButton** para crear un controlador de eventos para el evento de clic y abrir el formulario en el editor de código.  
  
2.  Reemplace el controlador de evento `DeleteButton_Click` con el código siguiente:  
  
     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]  
  
## <a name="run-the-application"></a>Ejecutar la aplicación  
  
#### <a name="to-run-the-application"></a>Para ejecutar la aplicación  
  
-   Seleccione **F5** para ejecutar la aplicación.  
  
-   Seleccione el **insertar** botón y compruebe que el nuevo registro aparece en la cuadrícula.  
  
-   Seleccione el **actualización** botón y compruebe que el registro se actualiza en la cuadrícula.  
  
-   Seleccione el **eliminar** botón y compruebe que el registro se quita de la cuadrícula.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Dependiendo de los requisitos de la aplicación, hay varios pasos que podría desear realizar después de crear un formulario enlazado a datos. Entre las mejoras que podría realizar se incluyen:  
  
-   Agregar funcionalidad de búsqueda al formulario.  
  
-   Agregar tablas adicionales al conjunto de datos seleccionando **configurar DataSet con el asistente** desde el **orígenes de datos** ventana. Puede agregar controles que muestren los datos relacionados arrastrando los nodos relacionados al formulario. Para obtener más información, consulte [relaciones en conjuntos de datos](relationships-in-datasets.md).  
  
## <a name="see-also"></a>Vea también  
 [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)