---
title: Guardar datos con los métodos DBDirect de un TableAdapter
description: En este tutorial, ejecute instrucciones SQL directamente en una base de datos mediante los métodos DBDirect de un TableAdapter.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 00f508163dc039d5c29013538a78fa7dab6091fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858454"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Guardar datos con los métodos DBDirect de un TableAdapter

En este tutorial se proporcionan instrucciones detalladas para ejecutar instrucciones SQL directamente en una base de datos mediante los métodos DBDirect de un TableAdapter. Los métodos DBDirect de un TableAdapter proporcionan un nivel exhaustivo de control sobre las actualizaciones de la base de datos. Puede utilizarlos para ejecutar instrucciones SQL y procedimientos almacenados específicos mediante una llamada a los `Insert` métodos individuales, `Update` y `Delete` según sea necesario para la aplicación (en contraposición al método sobrecargado `Update` que realiza las instrucciones Update, INSERT y DELETE en una llamada).

Durante este tutorial aprenderá a:

- Cree una nueva **aplicación Windows Forms**.

- Crear y configurar un conjunto de datos con el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png).

- Seleccionar el control que se va a crear en el formulario al arrastrar elementos desde la ventana **Orígenes de datos**. Para obtener más información, vea [establecer el control que se creará al arrastrar desde la ventana orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Cree un formulario enlazado a datos arrastrando elementos desde la ventana **Orígenes de datos** hasta el formulario.

- Agregue métodos para tener acceso directamente a la base de datos y realizar inserciones, actualizaciones y eliminaciones.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial se usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1. Si no tiene SQL Server Express LocalDB, instálelo desde la [Página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)o a través de la **instalador de Visual Studio**. En el **instalador de Visual Studio**, puede instalar SQL Server Express LocalDB como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** , o como un componente individual.

2. Instale la base de datos de ejemplo Northwind siguiendo estos pasos:

    1. En Visual Studio, abra la ventana **Explorador de objetos de SQL Server** . (Explorador de objetos de SQL Server se instala como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** en el instalador de Visual Studio). Expanda el nodo **SQL Server** . Haga clic con el botón secundario en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copie el [script de Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el portapapeles. Este script T-SQL crea la base de datos Northwind desde cero y la rellena con datos.

    3. Pegue el script T-SQL en el editor de consultas y, a continuación, elija el botón **Ejecutar** .

       Tras un breve período de tiempo, la consulta termina de ejecutarse y se crea la base de datos Northwind.

## <a name="create-a-windows-forms-application"></a>Crear una aplicación de Windows Forms

El primer paso es crear una **aplicación Windows Forms**.

1. En Visual Studio, en el menú **Archivo**, seleccione **Nuevo** > **Proyecto**.

2. Expanda **Visual C#** o **Visual Basic** en el panel izquierdo y, a continuación, seleccione **escritorio de Windows**.

3. En el panel central, seleccione el tipo de proyecto **Windows Forms aplicación** .

4. Asigne al proyecto el nombre **TableAdapterDbDirectMethodsWalkthrough** y, a continuación, elija **Aceptar**.

     Se crea el proyecto **TableAdapterDbDirectMethodsWalkthrough** y se agrega al **Explorador de soluciones**.

## <a name="create-a-data-source-from-your-database"></a>Crear un origen de datos a partir de la base de datos

En este paso se usa el **Asistente para configuración de orígenes de datos** para crear un origen de datos basado en la tabla `Region` de la base de datos de ejemplo Northwind. Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión. Para obtener información acerca de cómo configurar la base de datos de ejemplo Northwind, vea [Cómo: instalar bases](../data-tools/installing-database-systems-tools-and-samples.md)de datos de ejemplo.

### <a name="to-create-the-data-source"></a>Para crear el origen de datos

1. En el menú **Datos**, seleccione **Mostrar orígenes de datos**.

   Se abre la ventana **Orígenes de datos**.

2. En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

3. En la pantalla **elegir un tipo de origen de datos** , seleccione **base** de datos y, a continuación, seleccione **siguiente**.

4. En la pantalla **elegir la conexión de datos** , realice una de las acciones siguientes:

    - Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

         o bien

    - Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión**.

5. Si la base de datos requiere una contraseña, seleccione la opción para incluir la información confidencial y, a continuación, seleccione **siguiente**.

6. En la página **Guardar cadena de conexión en el archivo de configuración de la aplicación** , seleccione **siguiente**.

7. En la pantalla **elegir los objetos de base de datos** , expanda el nodo **tablas** .

8. Seleccione la `Region` tabla y, a continuación, seleccione **Finalizar**.

     **NorthwindDataSet** se agrega al proyecto y la tabla `Region` aparece en la ventana **Orígenes de datos**.

## <a name="add-controls-to-the-form-to-display-the-data"></a>Agregar controles al formulario para mostrar los datos

Cree los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario.

Para crear controles enlazados a datos en Windows Forms, arrastre el nodo de la **región** principal desde la ventana **orígenes de datos** hasta el formulario.

En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. [](../data-tools/dataset-tools-in-visual-studio.md) `RegionTableAdapter` <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingNavigator> En la bandeja de componentes aparecen NorthwindDataSet,, y.

### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Para agregar botones que llamarán a los métodos DbDirect de TableAdapter

1. Arrastre tres controles <xref:System.Windows.Forms.Button> desde el **Cuadro de herramientas** hasta **Form1** (debajo de **RegionDataGridView**).

2. Establezca las propiedades **Nombre** y **Texto** en cada botón.

    |Nombre|Texto|
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

## <a name="run-the-application"></a>Ejecución de la aplicación

- Seleccione **F5** para ejecutar la aplicación.

- Seleccione el botón **Insertar** y compruebe que el nuevo registro aparece en la cuadrícula.

- Seleccione el botón **Actualizar** y compruebe que el registro se actualiza en la cuadrícula.

- Seleccione el botón **eliminar** y compruebe que el registro se ha quitado de la cuadrícula.

## <a name="next-steps"></a>Pasos siguientes

En función de los requisitos de la aplicación, hay varios pasos que se pueden realizar después de crear un formulario enlazado a datos. Entre las mejoras que podría realizar se incluyen:

- Agregar funcionalidad de búsqueda al formulario.

- Agregar otras tablas al conjunto de datos seleccionando **Configurar DataSet con el asistente** en la ventana **Orígenes de datos**. Puede agregar controles que muestren los datos relacionados arrastrando los nodos relacionados al formulario. Para obtener más información, vea [relaciones en conjuntos de](relationships-in-datasets.md)datos.

## <a name="see-also"></a>Vea también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
