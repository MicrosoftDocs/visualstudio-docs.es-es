---
title: Guardar datos en una base de datos (varias tablas)
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8d4dd98a622a3aa09b2ec11f4f3521ce1839ce8c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586255"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Guardar datos en una base de datos (varias tablas)

Uno de los escenarios más comunes en el desarrollo de aplicaciones consiste en mostrar los datos en un formulario de una aplicación Windows, editar los datos y devolverlos actualizados a la base de datos. Este tutorial crea un formulario en el que aparecen datos de dos tablas relacionadas y muestra cómo editar los registros y volver a guardar los cambios en la base de datos. En este ejemplo se utilizan las tablas `Customers` y `Orders` de la base de datos de ejemplo Northwind.

Puede guardar los datos de su aplicación en la base de datos llamando al método `Update` de un TableAdapter. Al arrastrar las tablas desde la ventana **orígenes de datos** hasta un formulario, se agrega automáticamente el código necesario para guardar los datos. Cualquier tabla adicional que se agregue a un formulario requiere la adición manual de este código. Este tutorial muestra cómo agregar código para guardar las actualizaciones de varias tablas.

Las tareas ilustradas en este tutorial incluyen:

- Crear y configurar un origen de datos en la aplicación con el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png).

- Establecer los controles de los elementos en la [ventana orígenes de datos](add-new-data-sources.md#data-sources-window). Para obtener más información, vea [establecer el control que se creará al arrastrar desde la ventana orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Crear controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** hasta el formulario.

- Modificar algunos registros de cada tabla del conjunto de registros.

- Modificar el código para devolver los datos actualizados del conjunto de datos a la base de datos.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial se usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1. Si no tiene SQL Server Express LocalDB, instálelo desde la [Página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)o a través de la **instalador de Visual Studio**. En el **instalador de Visual Studio**, puede instalar SQL Server Express LocalDB como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** , o como un componente individual.

2. Instale la base de datos de ejemplo Northwind siguiendo estos pasos:

    1. En Visual Studio, abra la ventana **Explorador de objetos de SQL Server** . (Explorador de objetos de SQL Server se instala como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** en el instalador de Visual Studio). Expanda el nodo **SQL Server** . Haga clic con el botón secundario en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copie el [script de Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el portapapeles. Este script T-SQL crea la base de datos Northwind desde cero y la rellena con datos.

    3. Pegue el script T-SQL en el editor de consultas y, a continuación, elija el botón **Ejecutar** .

       Tras un breve período de tiempo, la consulta termina de ejecutarse y se crea la base de datos Northwind.

## <a name="create-the-windows-forms-application"></a>Creación de la aplicación Windows Forms

Cree un nuevo proyecto de **aplicación** de Windows Forms C# para o Visual Basic. Asigne al proyecto el nombre **UpdateMultipleTablesWalkthrough**.

## <a name="create-the-data-source"></a>Crear el origen de datos

Este paso crea un origen de datos a partir de la base de datos Northwind utilizando el **Asistente para la configuración de orígenes de datos**. Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión. Para obtener información acerca de cómo configurar la base de datos de ejemplo Northwind, vea [Cómo: instalar bases](../data-tools/installing-database-systems-tools-and-samples.md)de datos de ejemplo.

1. En el menú **datos** , seleccione **Mostrar orígenes de datos**.

   Se abre la ventana **Orígenes de datos**.

2. En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

3. En la pantalla **elegir un tipo de origen de datos** , seleccione **base**de datos y, a continuación, seleccione **siguiente**.

4. En la pantalla **elegir la conexión de datos** , realice una de las acciones siguientes:

    - Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

         O bien,

    - Seleccione **Nueva conexión** para abrir el cuadro de diálogo **Agregar o modificar conexión**.

5. Si la base de datos requiere una contraseña, seleccione la opción para incluir la información confidencial y, a continuación, seleccione **siguiente**.

6. En **Guardar cadena de conexión en el archivo de configuración de la aplicación**, seleccione **siguiente**.

7. En la pantalla **elegir los objetos de base de datos** , expanda el nodo **tablas** .

8. Seleccione las tablas **Customers** y **Orders** y, a continuación, seleccione **Finish (finalizar**).

     Se agrega **NorthwindDataSet** al proyecto y las tablas aparecen en la ventana **Orígenes de datos**.

## <a name="set-the-controls-to-be-created"></a>Establecer los controles que se van a crear

En este tutorial, los datos de la tabla `Customers` están en un diseño de **detalles** en el que los datos se muestran en controles individuales. Los datos de la tabla `Orders` se muestran en un diseño de **cuadrícula** que se muestra en un control <xref:System.Windows.Forms.DataGridView>.

### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Para establecer el tipo de acción de colocación de los elementos de la ventana Orígenes de datos

1. En la ventana **orígenes de datos** , expanda el nodo **Customers** .

2. En el nodo **Customers** , seleccione **detalles** en la lista de controles para cambiar el control de la tabla **Customers** a controles individuales. Para obtener más información, vea [establecer el control que se creará al arrastrar desde la ventana orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="create-the-data-bound-form"></a>Crear el formulario enlazado a datos

Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario.

1. Arrastre el nodo principal **Customers** desde la ventana **Orígenes de datos** hasta **Form1**.

     Los controles enlazados a datos con etiquetas descriptivas aparecen en el formulario, junto con una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>y <xref:System.Windows.Forms.BindingNavigator>.

2. Arrastre el nodo **Orders** relacionado desde la ventana **Orígenes de datos** hasta **Form1**.

    > [!NOTE]
    > El nodo **Orders** relacionado se encuentra debajo de la columna **Fax** y es un nodo secundario del nodo **Customers**.

     En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. En la bandeja de componentes aparecen un `OrdersTableAdapter` y un <xref:System.Windows.Forms.BindingSource>.

## <a name="add-code-to-update-the-database"></a>Agregar código para actualizar la base de datos

Puede actualizar la base de datos llamando a los métodos `Update` de los TableAdapters **Customers** y **Orders**. De forma predeterminada, se agrega un controlador de eventos para el botón **Guardar** del<xref:System.Windows.Forms.BindingNavigator> al código del formulario para enviar las actualizaciones a la base de datos. Este procedimiento modifica el código para enviar las actualizaciones en el orden correcto. Esto elimina la posibilidad de que se produzcan errores de integridad referencial. El código también implementa el control de errores colocando la llamada de actualización en un bloque try-catch. Puede modificar el código para satisfacer las necesidades de la aplicación.

> [!NOTE]
> Para mayor claridad, este tutorial no utiliza una transacción. Sin embargo, si va a actualizar dos o más tablas relacionadas, incluya toda la lógica de actualización dentro de una transacción. Una transacción es un proceso que garantiza que todos los cambios relacionados con una base de datos se realicen correctamente antes de que se confirmen los cambios. Para obtener más información, consulte [transacciones y simultaneidad](/dotnet/framework/data/adonet/transactions-and-concurrency).

### <a name="to-add-update-logic-to-the-application"></a>Para agregar la lógica de actualización a la aplicación

1. Seleccione el botón **Guardar** en el <xref:System.Windows.Forms.BindingNavigator>. Se abrirá el editor de código para el controlador de eventos `bindingNavigatorSaveItem_Click`.

2. Reemplace el código del controlador de eventos para que llame a los métodos `Update` de los TableAdapters relacionados. El código siguiente crea en primer lugar tres tablas de datos temporales para la información actualizada de cada <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState.Deleted>, <xref:System.Data.DataRowState.Added> y <xref:System.Data.DataRowState.Modified>). Las actualizaciones se ejecutan en el orden correcto. El código debe tener este aspecto:

     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-csharp[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]

## <a name="test-the-application"></a>Probar la aplicación

1. Presione **F5**.

2. Realice algunos cambios en los datos de uno o más registros de cada tabla.

3. Seleccione el botón **Guardar**.

4. Compruebe los valores de la base de datos para verificar que se guardaron los cambios.

## <a name="see-also"></a>Vea también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
