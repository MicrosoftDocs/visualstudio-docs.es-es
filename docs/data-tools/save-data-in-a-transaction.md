---
title: 'Tutorial: Guardar datos en una transacción'
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 0b3262b6123a496cda7025e369c99193ea8b6fd2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72641096"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>Tutorial: Guardar datos en una transacción

En este tutorial se muestra cómo guardar los datos en una transacción mediante el espacio de nombres <xref:System.Transactions>. En este tutorial, creará una aplicación Windows Forms. Utilizará el Asistente para la configuración de orígenes de datos para crear un conjunto de datos para dos tablas en la base de datos de ejemplo Northwind. Agregará controles enlazados a datos a un formulario de Windows Forms y modificará el código para que el botón Guardar de BindingNavigator actualice la base de datos dentro de un TransactionScope.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial se usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1. Si no tiene SQL Server Express LocalDB, instálelo desde la [Página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)o a través de la **instalador de Visual Studio**. En el Instalador de Visual Studio, SQL Server Express LocalDB puede instalarse como parte de la carga de trabajo de **desarrollo de escritorio de .net** o como un componente individual.

2. Instale la base de datos de ejemplo Northwind siguiendo estos pasos:

    1. En Visual Studio, abra la ventana **Explorador de objetos de SQL Server** . (Explorador de objetos de SQL Server se instala como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** en el instalador de Visual Studio). Expanda el nodo **SQL Server** . Haga clic con el botón secundario en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copie el [script de Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el portapapeles. Este script T-SQL crea la base de datos Northwind desde cero y la rellena con datos.

    3. Pegue el script T-SQL en el editor de consultas y, a continuación, elija el botón **Ejecutar** .

       Tras un breve período de tiempo, la consulta termina de ejecutarse y se crea la base de datos Northwind.

## <a name="create-a-windows-forms-application"></a>Crear una aplicación de Windows Forms

El primer paso es crear una **aplicación Windows Forms**.

1. En Visual Studio, en el menú **archivo** , seleccione **nuevo** **proyecto**de  > .

2. Expanda **Visual C#**  o **Visual Basic** en el panel izquierdo y, a continuación, seleccione **escritorio de Windows**.

3. En el panel central, seleccione el tipo de proyecto **Windows Forms aplicación** .

4. Asigne al proyecto el nombre **SavingDataInATransactionWalkthrough**y, a continuación, elija **Aceptar**.

     Se crea el proyecto **SavingDataInATransactionWalkthrough** y se agrega al **Explorador de soluciones**.

## <a name="create-a-database-data-source"></a>Crear un origen de datos de base de datos

En este paso se usa el Asistente para la **configuración de orígenes de datos** para crear un origen de datos basado en las tablas `Customers` y `Orders` de la base de datos de ejemplo Northwind.

1. Para abrir la ventana **orígenes de datos** , en el menú **datos** , seleccione **Mostrar orígenes de datos**.

2. En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

3. En la pantalla **elegir un tipo de origen de datos** , seleccione **base**de datos y, a continuación, seleccione **siguiente**.

4. En la pantalla **elegir la conexión de datos** , realice una de las acciones siguientes:

    - Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

         o bien

    - Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión** y cree una conexión con la base de datos Northwind.

5. Si la base de datos requiere una contraseña, seleccione la opción para incluir la información confidencial y, a continuación, seleccione **siguiente**.

6. En la página **Guardar cadena de conexión en el archivo de configuración de la aplicación** , seleccione **siguiente**.

7. En la pantalla **elegir los objetos de base de datos** , expanda el nodo **tablas** .

8. Seleccione las tablas `Customers` y `Orders` y, a continuación, seleccione **Finalizar**.

     **NorthwindDataSet** se agrega al proyecto y las tablas `Customers` y `Orders` aparecen en la ventana **Orígenes de datos**.

## <a name="add-controls-to-the-form"></a>Agregar controles al formulario

Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario.

1. En la ventana **orígenes de datos** , expanda el nodo **Customers** .

2. Arrastre el nodo principal **Customers** desde la ventana **Orígenes de datos** hasta **Form1**.

   En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.

3. Arrastre el nodo **Orders** relacionado (no el nodo **Orders** principal, pero el nodo de tabla secundaria relacionado que se encuentra debajo de la columna **fax** ) al formulario situado debajo de **CustomersDataGridView**.

   En el formulario aparece una <xref:System.Windows.Forms.DataGridView>. En la bandeja de componentes aparecen un `OrdersTableAdapter` y un <xref:System.Windows.Forms.BindingSource>.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Agregar una referencia al ensamblado System. Transactions

Las transacciones usan el espacio de nombres <xref:System.Transactions>. De forma predeterminada, no se agrega una referencia de proyecto al ensamblado system.transactions, por lo que tiene que agregarla manualmente.

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Para agregar una referencia al archivo DLL System.Transactions

1. En el menú **proyecto** , seleccione **Agregar referencia**.

2. Seleccione **System. Transactions** (en la pestaña **.net** ) y, después, haga clic en **Aceptar**.

     Se agrega una referencia a **System.Transactions** al proyecto.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>Modificar el código en el botón SaveItem de BindingNavigator

En la primera tabla colocada en el formulario, se agrega código de forma predeterminada al evento `click` del botón Guardar en el <xref:System.Windows.Forms.BindingNavigator>. Para actualizar otras tablas, debe agregar el código manualmente. En este tutorial, se refactoriza el código de guardado existente del controlador de eventos Click del botón Guardar. También creamos algunos métodos más para proporcionar una funcionalidad de actualización específica basada en si es necesario agregar o eliminar la fila.

### <a name="to-modify-the-auto-generated-save-code"></a>Para modificar el código de guardado generado automáticamente

1. Seleccione el botón **Guardar** en **CustomersBindingNavigator** (el botón con el icono de disquete).

2. Reemplace el método `CustomersBindingNavigatorSaveItem_Click` con el código siguiente:

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

El orden para conciliar los cambios a los datos relacionados es el siguiente:

- Eliminar registros secundarios. (En este caso, elimine los registros de la tabla `Orders`).

- Eliminar registros primarios. (En este caso, elimine los registros de la tabla `Customers`).

- Insertar registros primarios. (En este caso, inserte los registros en la tabla `Customers`).

- Insertar registros secundarios. (En este caso, inserte los registros en la tabla `Orders`).

### <a name="to-delete-existing-orders"></a>Para eliminar pedidos existentes

- Agregue el siguiente método `DeleteOrders` a **Form1**:

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

### <a name="to-delete-existing-customers"></a>Para eliminar clientes existentes

- Agregue el siguiente método `DeleteCustomers` a **Form1**:

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

### <a name="to-add-new-customers"></a>Para agregar nuevos clientes

- Agregue el siguiente método `AddNewCustomers` a **Form1**:

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

### <a name="to-add-new-orders"></a>Para agregar nuevos pedidos

- Agregue el siguiente método `AddNewOrders` a **Form1**:

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>Ejecutar la aplicación

Presione **F5** para ejecutar la aplicación.

## <a name="see-also"></a>Vea también

- [Cómo: guardar datos mediante el uso de una transacción](../data-tools/save-data-by-using-a-transaction.md)
- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)