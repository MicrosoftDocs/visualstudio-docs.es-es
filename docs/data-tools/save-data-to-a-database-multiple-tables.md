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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c4e5ca1e9903089cbcc9daf99e8c8d49d170b1c8
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388824"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Guardar datos en una base de datos (varias tablas)

Uno de los escenarios más comunes en el desarrollo de aplicaciones consiste en mostrar los datos en un formulario de una aplicación Windows, editar los datos y devolverlos actualizados a la base de datos. Este tutorial crea un formulario en el que aparecen datos de dos tablas relacionadas y muestra cómo editar los registros y volver a guardar los cambios en la base de datos. En este ejemplo se utilizan las tablas `Customers` y `Orders` de la base de datos de ejemplo Northwind.

Puede guardar los datos de su aplicación en la base de datos llamando al método `Update` de un TableAdapter. Al arrastrar las tablas de la **orígenes de datos** ventana en un formulario, el código necesario para guardar los datos se agrega automáticamente. Cualquier tabla adicional que se agrega a un formulario requiere la adición manual de este código. Este tutorial muestra cómo agregar código para guardar las actualizaciones de varias tablas.

Las tareas ilustradas en este tutorial incluyen:

-   Crear un proyecto nuevo de aplicación Windows Forms **.

-   Crear y configurar un origen de datos en la aplicación con el [Asistente para configuración de origen de datos](../data-tools/media/data-source-configuration-wizard.png).

-   Establecer los controles de los elementos de la [ventana Orígenes de datos](add-new-data-sources.md#data-sources-window). Para obtener más información, consulte [establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Crear controles enlazados a datos arrastrando elementos desde la ventana Orígenes de datos** hasta el formulario.

-   Modificación de algunos registros de cada tabla en el conjunto de datos.

-   Modificar el código para devolver los datos actualizados del conjunto de datos a la base de datos.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1. Si no tiene SQL Server Express LocalDB, instálelo de desde el [página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o a través del **instalador de Visual Studio**. En el **instalador de Visual Studio**, puede instalar SQL Server Express LocalDB como parte de la **procesamiento y almacenamiento de datos** carga de trabajo, o como un componente individual.

2. Instalar la base de datos de ejemplo Northwind, siga estos pasos:

    1. En Visual Studio, abra el **Explorador de objetos de SQL Server** ventana. (Explorador de objetos de SQL Server se instala como parte de la **procesamiento y almacenamiento de datos** carga de trabajo en el instalador de Visual Studio.) Expanda el **SQL Server** nodo. Haga doble clic en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copia el [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el Portapapeles. Este script de Transact-SQL crea la base de datos Northwind desde el principio y lo rellena con datos.

    3. Pegue el script de Transact-SQL en el editor de consultas y, a continuación, elija el **Execute** botón.

       Después de un breve tiempo, finalice la consulta y se crea la base de datos Northwind.

## <a name="create-the-windows-forms-application"></a>Crear la aplicación de Windows Forms

El primer paso es crear un **aplicación de Windows Forms**. Asignar un nombre al proyecto es opcional durante este paso, pero se lo entregaremos un nombre dado que se guardará el proyecto más adelante.

1. En Visual Studio, en el **archivo** menú, seleccione **New** > **proyecto**.

2. Expanda el **Visual C#** o **Visual Basic** en el panel izquierdo, seleccione **Windows Desktop**.

3. En el panel central, seleccione la **aplicación de Windows Forms** tipo de proyecto.

4. Denomine el proyecto **UpdateMultipleTablesWalkthrough**y, a continuación, elija **Aceptar**.

     Se crea el proyecto UpdateMultipleTablesWalkthrough **y se agrega al Explorador de soluciones**.

## <a name="create-the-data-source"></a>Crear el origen de datos

Este paso crea un origen de datos a partir de la base de datos Northwind utilizando el Asistente para la configuración de orígenes de datos **. Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión. Para obtener información acerca de cómo configurar la base de datos de ejemplo Northwind, vea [Cómo: instalar bases de datos de ejemplo](../data-tools/installing-database-systems-tools-and-samples.md).

1. En el **datos** menú, seleccione **Mostrar orígenes de datos**.

   Se abre la ventana Orígenes de datos **.

2. En la ventana Orígenes de datos **, seleccione Agregar nuevo origen de datos** para iniciar el Asistente para configuración de orígenes de datos **.

3. En el **elegir un tipo de origen de datos** pantalla, seleccione **base de datos**y, a continuación, seleccione **siguiente**.

4. En el **elegir la conexión de datos** pantalla, realice una de las siguientes acciones:

    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

         O bien

    -   Seleccione Nueva conexión **para abrir el cuadro de diálogo Agregar o modificar conexión**.

5. Si la base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y, a continuación, seleccione **siguiente**.

6. En el **Guardar cadena de conexión en el archivo de configuración de la aplicación**, seleccione **siguiente**.

7. En el **elija los objetos de base de datos** pantalla, expanda el **tablas** nodo.

8. Seleccione el **clientes** y **pedidos** tablas y, a continuación, seleccione **finalizar**.

     Se agrega NorthwindDataSet **al proyecto y las tablas aparecen en la ventana Orígenes de datos**.

## <a name="set-the-controls-to-be-created"></a>Establecer los controles que se puede crear

En este tutorial, los datos en el `Customers` la tabla está en un **detalles** diseño donde se muestran los datos en controles individuales. Los datos de la `Orders` la tabla está en un **cuadrícula** diseño que se muestra en un <xref:System.Windows.Forms.DataGridView> control.

### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Para establecer el tipo de acción de colocación de los elementos de la ventana Orígenes de datos

1. En el **orígenes de datos** ventana, expanda el **clientes** nodo.

2. En el **clientes** nodo, seleccione **detalles** en la lista de control para cambiar el control de la **clientes** tabla a controles individuales. Para obtener más información, consulte [establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="create-the-data-bound-form"></a>Crear el formulario enlazado a datos

Puede crear los controles enlazados a datos arrastrando elementos desde la ventana Orígenes de datos** al formulario.

1. Arrastre el nodo principal Customers **desde la ventana Orígenes de datos** hasta Form1.

     Los controles enlazados a datos con etiquetas descriptivas aparecen en el formulario, junto con una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. Un [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, y <xref:System.Windows.Forms.BindingNavigator> aparecen en la Bandeja de componentes.

2. Arrastre el nodo Orders **relacionado desde la ventana Orígenes de datos** hasta Form1 **.

    > [!NOTE]
    > El nodo Orders **relacionado se encuentra debajo de la columna Fax** y es un nodo secundario del nodo Customers **.

     En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. Un `OrdersTableAdapter` y <xref:System.Windows.Forms.BindingSource> aparecen en la Bandeja de componentes.

## <a name="add-code-to-update-the-database"></a>Agregue código para actualizar la base de datos

Puede actualizar la base de datos llamando a los métodos `Update` de los TableAdapters Customers **y Orders**. De forma predeterminada, un controlador de eventos para el **guardar** botón de la<xref:System.Windows.Forms.BindingNavigator> se agrega al código del formulario para enviar actualizaciones a la base de datos. Este procedimiento modifica el código para enviar las actualizaciones en el orden correcto. Esto elimina la posibilidad de generar errores de integridad referencial. El código también implementa el control de errores colocando la llamada de actualización en un bloque try-catch. Puede modificar el código para satisfacer las necesidades de la aplicación.

> [!NOTE]
> Para mayor claridad, este tutorial no utiliza una transacción. Sin embargo, si va a actualizar dos o más tablas relacionadas, incluir toda la lógica de actualización dentro de una transacción. Una transacción es un proceso que asegura que todos los cambios relacionados en una base de datos sean correctos antes de confirmados los cambios. Para obtener más información, consulte [transacciones y simultaneidad](/dotnet/framework/data/adonet/transactions-and-concurrency).

### <a name="to-add-update-logic-to-the-application"></a>Para agregar la lógica de actualización a la aplicación

1. Seleccione el **guardar** situado en la <xref:System.Windows.Forms.BindingNavigator>. Se abrirá el Editor de código para el `bindingNavigatorSaveItem_Click` controlador de eventos.

2. Reemplace el código del controlador de eventos para que llame a los métodos `Update` de los TableAdapters relacionados. El código siguiente crea en primer lugar tres tablas de datos temporales para la información actualizada de cada <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState.Deleted>, <xref:System.Data.DataRowState.Added> y <xref:System.Data.DataRowState.Modified>). Las actualizaciones se ejecutan en el orden correcto. El código debe tener este aspecto:

     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-csharp[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]

## <a name="test-the-application"></a>Probar la aplicación

1. Presione **F5**.

2. Realice algunos cambios en los datos de uno o más registros de cada tabla.

3. Seleccione el **guardar** botón.

4. Compruebe los valores de la base de datos para verificar que se guardaron los cambios.

## <a name="see-also"></a>Vea también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)