---
title: Guardar datos con los métodos DBDirect de un TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ef1860274c9234774b8af42525a0215d9468a858
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304580"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Guardar datos con los métodos DBDirect de un TableAdapter

Este tutorial proporciona instrucciones detalladas para ejecutar instrucciones SQL directamente en una base de datos mediante los métodos DBDirect de un TableAdapter. Los métodos DBDirect de un TableAdapter proporcionan un nivel exhaustivo de control sobre las actualizaciones de la base de datos. Puede usar para ejecutar instrucciones SQL específicas y procedimientos almacenados mediante una llamada a la persona `Insert`, `Update`, y `Delete` métodos según sea necesario para la aplicación (en lugar de sobrecargado `Update` método que realiza la actualización Instrucciones INSERT y DELETE en una llamada).

Durante este tutorial aprenderá a:

-   Crear una nueva **aplicación de Windows Forms**.

-   Crear y configurar un conjunto de datos con el [Asistente para configuración de origen de datos](../data-tools/media/data-source-configuration-wizard.png).

-   Seleccionar el control que se va a crear en el formulario al arrastrar elementos desde la ventana **Orígenes de datos**. Para obtener más información, consulte [establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Cree un formulario enlazado a datos arrastrando elementos desde la ventana **Orígenes de datos** hasta el formulario.

-   Agregar métodos para tener acceso a la base de datos y realizar inserciones, actualizaciones y eliminaciones directamente.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1. Si no tiene SQL Server Express LocalDB, instálelo de desde el [página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o a través del **instalador de Visual Studio**. En el **instalador de Visual Studio**, puede instalar SQL Server Express LocalDB como parte de la **procesamiento y almacenamiento de datos** carga de trabajo, o como un componente individual.

2. Instalar la base de datos de ejemplo Northwind, siga estos pasos:

    1. En Visual Studio, abra el **Explorador de objetos de SQL Server** ventana. (Explorador de objetos de SQL Server se instala como parte de la **procesamiento y almacenamiento de datos** carga de trabajo en el instalador de Visual Studio.) Expanda el **SQL Server** nodo. Haga doble clic en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copia el [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el Portapapeles. Este script de Transact-SQL crea la base de datos Northwind desde el principio y lo rellena con datos.

    3. Pegue el script de Transact-SQL en el editor de consultas y, a continuación, elija el **Execute** botón.

       Después de un breve tiempo, finalice la consulta y se crea la base de datos Northwind.

## <a name="create-a-windows-forms-application"></a>Crear una aplicación de Windows Forms

El primer paso es crear un **aplicación de Windows Forms**.

1. En Visual Studio, en el **archivo** menú, seleccione **New** > **proyecto**.

2. Expanda el **Visual C#** o **Visual Basic** en el panel izquierdo, seleccione **Windows Desktop**.

3. En el panel central, seleccione la **aplicación de Windows Forms** tipo de proyecto.

4. Denomine el proyecto **TableAdapterDbDirectMethodsWalkthrough**y, a continuación, elija **Aceptar**.

     Se crea el proyecto **TableAdapterDbDirectMethodsWalkthrough** y se agrega al **Explorador de soluciones**.

## <a name="create-a-data-source-from-your-database"></a>Crear un origen de datos de la base de datos

En este paso se usa el **Asistente para configuración de orígenes de datos** para crear un origen de datos basado en la tabla `Region` de la base de datos de ejemplo Northwind. Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión. Para obtener información acerca de cómo configurar la base de datos de ejemplo Northwind, vea [Cómo: instalar bases de datos de ejemplo](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-data-source"></a>Para crear el origen de datos

1. En el **datos** menú, seleccione **Mostrar orígenes de datos**.

   Se abre la ventana **Orígenes de datos**.

2. En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

3. En el **elegir un tipo de origen de datos** pantalla, seleccione **base de datos**y, a continuación, seleccione **siguiente**.

4. En el **elegir la conexión de datos** pantalla, realice una de las siguientes acciones:

    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

         O bien

    -   Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión**.

5. Si la base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y, a continuación, seleccione **siguiente**.

6. En el **Guardar cadena de conexión en el archivo de configuración de la aplicación** pantalla, seleccione **siguiente**.

7. En el **elija los objetos de base de datos** pantalla, expanda el **tablas** nodo.

8. Seleccione el `Region` de tabla y, a continuación, seleccione **finalizar**.

     **NorthwindDataSet** se agrega al proyecto y la tabla `Region` aparece en la ventana **Orígenes de datos**.

## <a name="add-controls-to-the-form-to-display-the-data"></a>Agregar controles al formulario para mostrar los datos

Cree los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario.

Para crear controles enlazados a datos en el formulario de Windows, arrastre el método main **región** nodo desde el **orígenes de datos** ventana hasta el formulario.

En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. Un [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `RegionTableAdapter`, <xref:System.Windows.Forms.BindingSource>, y <xref:System.Windows.Forms.BindingNavigator> aparecen en la Bandeja de componentes.

### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Para agregar botones que llamarán a los métodos DbDirect de TableAdapter

1. Arrastre tres controles <xref:System.Windows.Forms.Button> desde el **Cuadro de herramientas** hasta **Form1** (debajo de **RegionDataGridView**).

2. Establezca las propiedades **Nombre** y **Texto** en cada botón.

    |nombre|Texto|
    |----------|----------|
    |`InsertButton`|**Insertar**|
    |`UpdateButton`|**Actualizar**|
    |`DeleteButton`|**Eliminar**|

### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Para agregar código para insertar nuevos registros en la base de datos

1. Seleccione **InsertButton** para crear un controlador de eventos para el evento de clic y abrir el formulario en el editor de código.

2. Reemplace el controlador de evento `InsertButton_Click` con el código siguiente:

     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]

### <a name="to-add-code-to-update-records-in-the-database"></a>Para agregar código para actualizar los registros de la base de datos

1. Haga doble clic en **UpdateButton** para crear un controlador para el evento de clic y abrir el formulario en el editor de código.

2. Reemplace el controlador de evento `UpdateButton_Click` con el código siguiente:

     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]

### <a name="to-add-code-to-delete-records-from-the-database"></a>Para agregar código para eliminar registros de la base de datos

1. Seleccione **DeleteButton** para crear un controlador de eventos para el evento de clic y abrir el formulario en el editor de código.

2. Reemplace el controlador de evento `DeleteButton_Click` con el código siguiente:

     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]

## <a name="run-the-application"></a>Ejecutar la aplicación

-   Seleccione **F5** para ejecutar la aplicación.

-   Seleccione el **insertar** botón y compruebe que el nuevo registro aparece en la cuadrícula.

-   Seleccione el **actualización** botón y compruebe que el registro se actualiza en la cuadrícula.

-   Seleccione el **eliminar** botón y compruebe que el registro se quita de la cuadrícula.

## <a name="next-steps"></a>Pasos siguientes

Dependiendo de los requisitos de la aplicación, hay varios pasos que se desea realizar después de crear un formulario enlazado a datos. Entre las mejoras que podría realizar se incluyen:

-   Agregar funcionalidad de búsqueda al formulario.

-   Agregar otras tablas al conjunto de datos seleccionando **Configurar DataSet con el asistente** en la ventana **Orígenes de datos**. Puede agregar controles que muestren los datos relacionados arrastrando los nodos relacionados al formulario. Para obtener más información, consulte [relaciones en conjuntos de datos](relationships-in-datasets.md).

## <a name="see-also"></a>Vea también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)