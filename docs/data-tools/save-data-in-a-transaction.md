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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 2829e1dffa0975a1970b8727f9baf79febf9b32c
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174892"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>Tutorial: Guardar datos en una transacción
Este tutorial muestra cómo guardar datos en una transacción utilizando el <xref:System.Transactions> espacio de nombres. En este tutorial, creará una aplicación de Windows Forms. Usará al Asistente para configuración de orígenes de datos para crear un conjunto de datos de dos tablas en la base de datos de ejemplo Northwind. Agregará controles enlazados a datos a un formulario de Windows y se modificará el código de BindingNavigator botón Guardar actualizar la base de datos dentro de un TransactionScope.

## <a name="prerequisites"></a>Requisitos previos
En este tutorial usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1.  Si no tiene SQL Server Express LocalDB, instálelo de desde el [página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o a través del **instalador de Visual Studio**. En el instalador de Visual Studio, se puede instalar SQL Server Express LocalDB como parte de la **desarrollo de escritorio de .NET** carga de trabajo, o como un componente individual.

2.  Instalar la base de datos de ejemplo Northwind, siga estos pasos:

    1. En Visual Studio, abra el **Explorador de objetos de SQL Server** ventana. (Explorador de objetos de SQL Server se instala como parte de la **procesamiento y almacenamiento de datos** carga de trabajo en el instalador de Visual Studio.) Expanda el **SQL Server** nodo. Haga doble clic en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copia el [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el Portapapeles. Este script de Transact-SQL crea la base de datos Northwind desde el principio y lo rellena con datos.

    3. Pegue el script de Transact-SQL en el editor de consultas y, a continuación, elija el **Execute** botón.

       Después de un breve tiempo, finalice la consulta y se crea la base de datos Northwind.

## <a name="create-a-windows-forms-application"></a>Crear una aplicación de Windows Forms
 El primer paso es crear un **aplicación de Windows Forms**.

#### <a name="to-create-the-new-windows-project"></a>Para crear el nuevo proyecto de Windows

1. En Visual Studio, en el **archivo** menú, seleccione **New** > **proyecto**.

2. Expanda el **Visual C#** o **Visual Basic** en el panel izquierdo, seleccione **Windows Desktop**.

3. En el panel central, seleccione la **aplicación de Windows Forms** tipo de proyecto.

4. Denomine el proyecto **SavingDataInATransactionWalkthrough**y, a continuación, elija **Aceptar**.

     El **SavingDataInATransactionWalkthrough** se crea y se agrega al proyecto **el Explorador de soluciones**.

## <a name="create-a-database-data-source"></a>Crear un origen de datos de la base de datos
 Este paso se usa el **Asistente para configuración de origen de datos** para crear un origen de datos basado en la `Customers` y `Orders` tablas en la base de datos de ejemplo Northwind.

#### <a name="to-create-the-data-source"></a>Para crear el origen de datos

1.  En el **datos** menú, seleccione **Mostrar orígenes de datos**.

2.  En el **orígenes de datos** ventana, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de origen de datos**.

3.  En el **elegir un tipo de origen de datos** pantalla, seleccione **base de datos**y, a continuación, seleccione **siguiente**.

4.  En el **elegir la conexión de datos** realice pantalla uno de los siguientes:

    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

         O bien

    -   Seleccione **nueva conexión** para iniciar el **agregar o modificar conexión** diálogo cuadro y crear una conexión a la base de datos Northwind.

5.  Si la base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y, a continuación, seleccione **siguiente**.

6.  En el **Guardar cadena de conexión en el archivo de configuración de la aplicación** pantalla, seleccione **siguiente**.

7.  En el **elija los objetos de base de datos** pantalla, expanda el **tablas** nodo.

8.  Seleccione el `Customers` y `Orders` tablas y, a continuación, seleccione **finalizar**.

     El **NorthwindDataSet** se agrega al proyecto y la `Customers` y `Orders` tablas aparecen en la **orígenes de datos** ventana.

## <a name="add-controls-to-the-form"></a>Agregar controles al formulario
 Puede crear los controles enlazados a datos arrastrando elementos desde la **orígenes de datos** ventana hasta su formulario.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Para crear datos enlazados a los controles del formulario de Windows

-   En el **orígenes de datos** ventana, expanda el **clientes** nodo.

-   Arrastre el método main **clientes** nodo desde el **orígenes de datos** ventana hasta **Form1**.

     En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. Un [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, y <xref:System.Windows.Forms.BindingNavigator> aparecen en la Bandeja de componentes.

-   Arrastre relacionado **pedidos** nodo (no principal **pedidos** nodo, pero el nodo de tabla secundaria relacionado siguiente el **Fax** columna) en el formulario debajo del  **CustomersDataGridView**.

     En el formulario aparece una <xref:System.Windows.Forms.DataGridView>. Un `OrdersTableAdapter` y <xref:System.Windows.Forms.BindingSource> aparecen en la Bandeja de componentes.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Agregue una referencia al ensamblado System.Transactions
 Las transacciones usan el espacio de nombres <xref:System.Transactions>. De forma predeterminada, no se agrega una referencia de proyecto al ensamblado system.transactions, por lo que tiene que agregarla manualmente.

#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Para agregar una referencia al archivo DLL System.Transactions

1.  En el **proyecto** menú, seleccione **Agregar referencia**.

2.  Seleccione **System.Transactions** (en el **.NET** pestaña) y, a continuación, seleccione **Aceptar**.

     Una referencia a **System.Transactions** se agrega al proyecto.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>Modifique el código de botón SaveItem de BindingNavigator
 Para la primera tabla colocada en su formulario, el código se agrega de forma predeterminada para el `click` eventos de la operación de guardar situado en la <xref:System.Windows.Forms.BindingNavigator>. Para actualizar otras tablas, debe agregar el código manualmente. En este tutorial, se refactoriza el código fuera de la operación de guardar de guardado existente controlador de eventos de clic del botón. También creamos algunos métodos más para proporcionar la funcionalidad de actualización específica según si necesita agregar o eliminar la fila.

#### <a name="to-modify-the-auto-generated-save-code"></a>Para modificar el código de guardado generado automáticamente

1.  Seleccione el **guardar** situado en la **CustomersBindingNavigator** (el botón con el icono del disquete).

2.  Reemplace el método `CustomersBindingNavigatorSaveItem_Click` con el código siguiente:

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

El orden para conciliar los cambios a los datos relacionados es el siguiente:

-   Eliminar los registros secundarios. (En este caso, eliminar los registros de la `Orders` tabla.)

-   Eliminar los registros primarios. (En este caso, eliminar los registros de la `Customers` tabla.)

-   Insertar registros primarios. (En este caso, insertar registros en el `Customers` tabla.)

-   Insertar registros secundarios. (En este caso, insertar registros en el `Orders` tabla.)

#### <a name="to-delete-existing-orders"></a>Para eliminar pedidos existentes

-   Agregue el siguiente `DeleteOrders` método **Form1**:

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

#### <a name="to-delete-existing-customers"></a>Para eliminar clientes existentes

-   Agregue el siguiente `DeleteCustomers` método **Form1**:

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

#### <a name="to-add-new-customers"></a>Para agregar nuevos clientes

-   Agregue el siguiente `AddNewCustomers` método **Form1**:

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

#### <a name="to-add-new-orders"></a>Para agregar nuevos pedidos

-   Agregue el siguiente `AddNewOrders` método **Form1**:

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>Ejecutar la aplicación

#### <a name="to-run-the-application"></a>Para ejecutar la aplicación

-   Seleccione **F5** para ejecutar la aplicación.

## <a name="see-also"></a>Vea también

- [Cómo: guardar datos mediante el uso de una transacción](../data-tools/save-data-by-using-a-transaction.md)
- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)