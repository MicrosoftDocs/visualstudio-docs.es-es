---
title: Guardar datos en una transacción | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b30f51da001c62166a97c954b1416e35fd8b540f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671087"
---
# <a name="save-data-in-a-transaction"></a>Guardar datos en una transacción
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial se muestra cómo guardar los datos en una transacción mediante el espacio de nombres <xref:System.Transactions>. En este ejemplo se utilizan las tablas `Customers` y `Orders` de la base de datos de ejemplo Northwind.

## <a name="prerequisites"></a>Requisitos previos
 Este tutorial requiere acceso a la base de datos de ejemplo Northwind.

## <a name="create-a-windows-application"></a>Crear una aplicación para Windows
 El primer paso es crear una **aplicación para Windows**.

#### <a name="to-create-the-new-windows-project"></a>Para crear el nuevo proyecto de Windows

1. En Visual Studio, en el menú **archivo** , cree un nuevo **proyecto**.

2. Asigne al proyecto el nombre **SavingDataInATransactionWalkthrough**.

3. Seleccione **aplicación para Windows**y, después, haga clic en **Aceptar**. Para obtener más información, vea [aplicaciones cliente](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Se crea el proyecto **SavingDataInATransactionWalkthrough** y se agrega al **Explorador de soluciones**.

## <a name="create-a-database-data-source"></a>Crear un origen de datos de base de datos
 En este paso se usa el Asistente para la [configuración de orígenes de datos](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) para crear un origen de datos basado en las tablas `Customers` y `Orders` de la base de datos de ejemplo Northwind.

#### <a name="to-create-the-data-source"></a>Para crear el origen de datos

1. En el menú **datos** , seleccione**Mostrar orígenes de datos**.

2. En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

3. En la pantalla **elegir un tipo de origen de datos**, seleccione **base**de datos y, a continuación, seleccione **siguiente**.

4. En la pantalla **elegir la conexión de datos**, realice una de las acciones siguientes:

    - Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

         o bien

    - Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión** y cree una conexión con la base de datos Northwind.

5. Si la base de datos requiere una contraseña, seleccione la opción para incluir la información confidencial y, a continuación, seleccione **siguiente**.

6. En la página **Guardar cadena de conexión en el archivo de configuración de la aplicación** , seleccione **siguiente**.

7. En la pantalla **elegir los objetos de base de datos** , expanda el nodo **tablas** .

8. Seleccione las tablas `Customers` y `Orders` y, a continuación, seleccione **Finalizar**.

     **NorthwindDataSet** se agrega al proyecto y las tablas `Customers` y `Orders` aparecen en la ventana **Orígenes de datos**.

## <a name="addcontrols-to-the-form"></a>Addcontrols al formulario
 Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Para crear controles enlazados a datos en Windows Forms

- En la ventana **orígenes de datos** , expanda el nodo **Customers** .

- Arrastre el nodo principal **Customers** desde la ventana **Orígenes de datos** hasta **Form1**.

     En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.

- Arrastre el nodo **Orders** relacionado (no el nodo **Orders** principal, pero el nodo de tabla secundaria relacionado que se encuentra debajo de la columna **fax** ) al formulario situado debajo de **CustomersDataGridView**.

     En el formulario aparece una <xref:System.Windows.Forms.DataGridView>. Un OrdersTableAdapter y <xref:System.Windows.Forms.BindingSource> aparecen en la bandeja de componentes.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Agregar una referencia al ensamblado System. Transactions
 Las transacciones usan el espacio de nombres <xref:System.Transactions>. Una referencia de proyecto al ensamblado System. Transactions no se agrega de forma predeterminada, por lo que debe agregarla manualmente.

#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Para agregar una referencia al archivo DLL System.Transactions

1. En el menú **proyecto** , seleccione**Agregar referencia**.

2. Seleccione **System. Transactions**(en la pestaña **.net** ) y, después, haga clic en **Aceptar**.

     Se agrega una referencia a **System.Transactions** al proyecto.

## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>Modifythe código en el botón SaveItem de BindingNavigator
 En la primera tabla colocada en el formulario, se agrega código de forma predeterminada al evento `click` del botón Guardar en el <xref:System.Windows.Forms.BindingNavigator>. Para actualizar otras tablas, debe agregar el código manualmente. En este tutorial, se refactoriza el código de guardado existente del controlador de eventos Click del botón Guardar. También creamos algunos métodos más para proporcionar una funcionalidad de actualización específica basada en si es necesario agregar o eliminar la fila.

#### <a name="to-modify-the-auto-generated-save-code"></a>Para modificar el código de guardado generado automáticamente

1. Seleccione el botón **Guardar** en **CustomersBindingNavigator** (el botón con el icono de disquete).

2. Reemplace el método `CustomersBindingNavigatorSaveItem_Click` con el código siguiente:

    [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
    [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]

   El orden para conciliar los cambios a los datos relacionados es el siguiente:

- Eliminar registros secundarios. (En este caso, elimine los registros de la tabla `Orders`).

- Eliminar registros primarios. (En este caso, elimine los registros de la tabla `Customers`).

- Insertar registros primarios. (En este caso, inserte los registros en la tabla `Customers`).

- Insertar registros secundarios. (En este caso, inserte los registros en la tabla `Orders`).

#### <a name="to-delete-existing-orders"></a>Para eliminar pedidos existentes

- Agregue el siguiente método `DeleteOrders` a **Form1**:

     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]

#### <a name="to-delete-existing-customers"></a>Para eliminar clientes existentes

- Agregue el siguiente método `DeleteCustomers` a **Form1**:

     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]

#### <a name="to-add-new-customers"></a>Para agregar nuevos clientes

- Agregue el siguiente método `AddNewCustomers` a **Form1**:

     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]

#### <a name="to-add-new-orders"></a>Para agregar nuevos pedidos

- Agregue el siguiente método `AddNewOrders` a **Form1**:

     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]

## <a name="run-the-application"></a>Ejecutar la aplicación

#### <a name="to-run-the-application"></a>Para ejecutar la aplicación

- Seleccione **F5** para ejecutar la aplicación.

## <a name="see-also"></a>Vea también
 [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
