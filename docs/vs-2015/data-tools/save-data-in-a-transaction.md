---
title: Guardar datos en una transacción | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4b6d6befe4bbe29147a59b9700b8f148154e6c5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575996"
---
# <a name="save-data-in-a-transaction"></a>Guardar datos en una transacción
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [guardar datos en una transacción](https://docs.microsoft.com/visualstudio/data-tools/save-data-in-a-transaction).  
  
  
Este tutorial muestra cómo guardar datos en una transacción utilizando el <xref:System.Transactions> espacio de nombres. En este ejemplo se utilizan las tablas `Customers` y `Orders` de la base de datos de ejemplo Northwind.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Este tutorial requiere acceso a la base de datos de ejemplo Northwind. Para obtener información acerca de cómo configurar la base de datos de ejemplo Northwind, vea [Cómo: instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-a-windows-application"></a>Crear una aplicación de Windows  
 El primer paso es crear un **aplicación Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Para crear el nuevo proyecto de Windows  
  
1.  En Visual Studio, en el **archivo** menú, cree un nuevo **proyecto**.  
  
2.  Denomine el proyecto **SavingDataInATransactionWalkthrough**.  
  
3.  Seleccione **aplicación Windows**y, a continuación, seleccione**Aceptar**. Para obtener más información, consulte [las aplicaciones cliente](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     El **SavingDataInATransactionWalkthrough** se crea y se agrega al proyecto **el Explorador de soluciones**.  
  
## <a name="create-a-database-data-source"></a>Crear un origen de datos de la base de datos  
 Este paso se usa el [Asistente para configuración de origen de datos](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) para crear un origen de datos basado en la `Customers` y `Orders` tablas en la base de datos de ejemplo Northwind.  
  
#### <a name="to-create-the-data-source"></a>Para crear el origen de datos  
  
1.  En el **datos** menú, seleccione**Mostrar orígenes de datos**.  
  
2.  En el **orígenes de datos** ventana, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de origen de datos**.  
  
3.  En el **elegir un tipo de origen de datos**pantalla, seleccione **base de datos**y, a continuación, seleccione**siguiente**.  
  
4.  En el **elegir la conexión de datos**realice pantalla uno de los siguientes:  
  
    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.  
  
         O bien  
  
    -   Seleccione **nueva conexión** para iniciar el **agregar o modificar conexión** diálogo cuadro y crear una conexión a la base de datos Northwind.  
  
5.  Si la base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y, a continuación, seleccione**siguiente**.  
  
6.  En el **Guardar cadena de conexión en el archivo de configuración de la aplicación** pantalla, seleccione**siguiente**.  
  
7.  En el **elija los objetos de base de datos** pantalla, expanda el **tablas** nodo.  
  
8.  Seleccione el `Customers` y `Orders` tablas y, a continuación, seleccione**finalizar**.  
  
     El **NorthwindDataSet** se agrega al proyecto y la `Customers` y `Orders` tablas aparecen en la **orígenes de datos** ventana.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols al formulario  
 Puede crear los controles enlazados a datos arrastrando elementos desde la **orígenes de datos** ventana hasta su formulario.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Para crear datos enlazados a los controles del formulario de Windows  
  
-   En el **orígenes de datos** ventana, expanda el **clientes** nodo.  
  
-   Arrastre el método main **clientes** nodo desde el **orígenes de datos** ventana hasta **Form1**.  
  
     En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. Un [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md),<xref:System.Windows.Forms.BindingSource>, y <xref:System.Windows.Forms.BindingNavigator> aparecen en la Bandeja de componentes.  
  
-   Arrastre relacionado **pedidos** nodo (no principal **pedidos** nodo, pero el nodo de tabla secundaria relacionado siguiente el **Fax** columna) en el formulario debajo del  **CustomersDataGridView**.  
  
     En el formulario aparece una <xref:System.Windows.Forms.DataGridView>. Un [OrdersTableAdapter](../data-tools/tableadapter-overview.md) y <xref:System.Windows.Forms.BindingSource> aparecen en la Bandeja de componentes.  
  
## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Agregue una referencia al ensamblado System.Transactions  
 Las transacciones usan el espacio de nombres <xref:System.Transactions>. De forma predeterminada, no se agrega una referencia de proyecto al ensamblado system.transactions, por lo que tiene que agregarla manualmente.  
  
#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Para agregar una referencia al archivo DLL System.Transactions  
  
1.  En el **proyecto** menú, seleccione**Agregar referencia**.  
  
2.  Seleccione **System.Transactions**(en el **.NET** pestaña) y, a continuación, seleccione**Aceptar**.  
  
     Una referencia a **System.Transactions** se agrega al proyecto.  
  
## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>Modifythe código en el botón SaveItem de BindingNavigator  
 Para la primera tabla colocada en su formulario, el código se agrega de forma predeterminada para el `click` eventos de la operación de guardar situado en la <xref:System.Windows.Forms.BindingNavigator>. Para actualizar otras tablas, debe agregar el código manualmente. En este tutorial, se refactoriza el código fuera de la operación de guardar de guardado existente controlador de eventos de clic del botón. También creamos algunos métodos más para proporcionar la funcionalidad de actualización específica según si necesita agregar o eliminar la fila.  
  
#### <a name="to-modify-the-auto-generated-save-code"></a>Para modificar el código de guardado generado automáticamente  
  
1.  Seleccione el **guardar** situado en la **CustomersBindingNavigator** (el botón con el icono del disquete).  
  
2.  Reemplace el método `CustomersBindingNavigatorSaveItem_Click` con el código siguiente:  
  
     [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
     [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]  
  
 El orden para conciliar los cambios a los datos relacionados es el siguiente:  
  
-   Eliminar los registros secundarios. (En este caso, eliminar los registros de la `Orders` tabla.)  
  
-   Eliminar los registros primarios. (En este caso, eliminar los registros de la `Customers` tabla.)  
  
-   Insertar registros primarios. (En este caso, insertar registros en el `Customers` tabla.)  
  
-   Insertar registros secundarios. (En este caso, insertar registros en el `Orders` tabla.)  
  
#### <a name="to-delete-existing-orders"></a>Para eliminar pedidos existentes  
  
-   Agregue el siguiente `DeleteOrders` método **Form1**:  
  
     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]  
  
#### <a name="to-delete-existing-customers"></a>Para eliminar clientes existentes  
  
-   Agregue el siguiente `DeleteCustomers` método **Form1**:  
  
     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]  
  
#### <a name="to-add-new-customers"></a>Para agregar nuevos clientes  
  
-   Agregue el siguiente `AddNewCustomers` método **Form1**:  
  
     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]  
  
#### <a name="to-add-new-orders"></a>Para agregar nuevos pedidos  
  
-   Agregue el siguiente `AddNewOrders` método **Form1**:  
  
     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]  
  
## <a name="run-the-application"></a>Ejecutar la aplicación  
  
#### <a name="to-run-the-application"></a>Para ejecutar la aplicación  
  
-   Seleccione**F5** para ejecutar la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)

