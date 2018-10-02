---
title: Pasar datos entre formularios | Documentos de Microsoft
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
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e046bdf38af09b5f7ea0e8beb296a2b3d32cff6d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577998"
---
# <a name="pass-data-between-forms"></a>Pasar datos de un formulario a otro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [pasar datos entre formularios](https://docs.microsoft.com/visualstudio/data-tools/pass-data-between-forms).  
  
  
En este tutorial se proporcionan instrucciones paso a paso para pasar datos de un formulario a otro. Con las tablas customers y orders de Northwind, un formulario permite a los usuarios seleccionar a un cliente y un segundo formulario muestra los pedidos del cliente seleccionado. Este tutorial muestra cómo crear un método en el segundo formulario que recibe los datos del primer formulario.  
  
> [!NOTE]
>  En este tutorial solo se muestra una manera de pasar datos de un formulario a otro. Hay otras opciones para pasar datos a un formulario, incluida la creación de un segundo constructor para recibir datos, o crear una propiedad pública que se puede establecer con los datos desde el primer formulario.  
  
 Las tareas ilustradas en este tutorial incluyen:  
  
-   Crear un nuevo **aplicación Windows** proyecto.  
  
-   Crear y configurar un conjunto de datos con el [Asistente para configuración de origen de datos](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Selecciona el control que se creará en el formulario al arrastrar elementos desde el **orígenes de datos** ventana. Para obtener más información, consulte [establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Creación de un control enlazado a datos arrastrando elementos desde la **orígenes de datos** ventana en un formulario.  
  
-   Crear un segundo formulario con una cuadrícula para mostrar datos.  
  
-   Crear una consulta de TableAdapter para buscar los pedidos de un cliente determinado.  
  
-   Pasar datos de un formulario a otro.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para completar las tareas de este tutorial, necesitará:  
  
-   Acceso a la base de datos de ejemplo Northwind. Para obtener más información, consulte [Cómo: instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-the-windows-application"></a>Crear la aplicación de Windows  
  
#### <a name="to-create-the-new-windows-project"></a>Para crear el nuevo proyecto de Windows  
  
1.  Desde el **archivo** menú, cree un nuevo proyecto.  
  
2.  Dé un nombre al proyecto `PassingDataBetweenForms`.  
  
3.  Seleccione **aplicación de Windows Forms**y haga clic en **Aceptar**. Para obtener más información, consulte [las aplicaciones cliente](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     El **PassingDataBetweenForms** se crea y agrega al proyecto **el Explorador de soluciones**.  
  
## <a name="create-the-data-source"></a>Crear el origen de datos  
  
#### <a name="to-create-the-data-source"></a>Para crear el origen de datos  
  
1.  En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.  
  
2.  En el **orígenes de datos** ventana, seleccione **Agregar nuevo origen de datos** para iniciar el **configuración origen de datos** asistente.  
  
3.  Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.  
  
4.  En el **elegir un modelo de base de datos** , comprueba que **Dataset** se especifica y, a continuación, haga clic en **siguiente**.  
  
5.  En el **elegir la conexión de datos** , realice una de las siguientes acciones:  
  
    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.  
  
    -   Seleccione **nueva conexión** para iniciar el **agregar o modificar conexión** cuadro de diálogo.  
  
6.  Si la base de datos requiere una contraseña y si está habilitada la opción para incluir datos confidenciales, seleccione la opción y, a continuación, haga clic en **siguiente**.  
  
7.  En el **Guardar cadena de conexión en el archivo de configuración de la aplicación** página, haga clic en **siguiente**.  
  
8.  En el **elija los objetos de base de datos** , expanda el **tablas** nodo.  
  
9. Seleccione el **clientes** y **pedidos** tablas y, a continuación, haga clic en **finalizar**.  
  
     El **NorthwindDataSet** se agrega al proyecto y el **clientes** y **pedidos** tablas aparecen en la **orígenes de datos** ventana.  
  
## <a name="create-the-first-form-form1"></a>Crear el primer formulario (Form1)  
 Puede crear una cuadrícula enlazada a datos (un <xref:System.Windows.Forms.DataGridView> control), arrastrando el **clientes** nodo desde el **orígenes de datos** ventana hasta el formulario.  
  
#### <a name="to-create-a-data-bound-grid-on-the-form"></a>Para crear una cuadrícula enlazada a datos en el formulario  
  
-   Arrastre el método main **clientes** nodo desde el **orígenes de datos** ventana hasta **Form1**.  
  
     Un <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros aparecen en **Form1**. Un [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, y <xref:System.Windows.Forms.BindingNavigator> aparecen en la Bandeja de componentes.  
  
## <a name="create-the-second-form-form2"></a>Crear el segundo formulario (Form2)  
  
#### <a name="to-create-a-second-form-to-pass-the-data-to"></a>Para crear un segundo formulario al que pasar los datos  
  
1.  En el menú **Proyecto**, elija **Agregar Windows Forms**.  
  
2.  Deje el nombre predeterminado de **Form2**y haga clic en **agregar**.  
  
3.  Arrastre el método main **pedidos** nodo desde el **orígenes de datos** ventana hasta **Form2**.  
  
     Un <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros aparecen en **Form2**. Un [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, y <xref:System.Windows.Forms.BindingNavigator> aparecen en la Bandeja de componentes.  
  
4.  Eliminar el **OrdersBindingNavigator** desde la Bandeja de componentes.  
  
     El **OrdersBindingNavigator** desaparece del **Form2**.  
  
## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>Agregar una consulta de TableAdapter al Form2 para cargar los pedidos del cliente seleccionado en Form1  
  
#### <a name="to-create-a-tableadapter-query"></a>Para crear una consulta de TableAdapter  
  
1.  Haga doble clic en el **NorthwindDataSet.xsd** archivo **el Explorador de soluciones**.  
  
2.  Haga clic en el **OrdersTableAdapter**y seleccione **Agregar consulta**.  
  
3.  Deje la opción predeterminada de **usar instrucciones SQL**y, a continuación, haga clic en **siguiente**.  
  
4.  Deje la opción predeterminada de **LECT que devuelve filas**y, a continuación, haga clic en **siguiente**.  
  
5.  Agregue una cláusula WHERE para que devuelva la consulta `Orders` según el `CustomerID`. La consulta debe ser similar a lo siguiente:  
  
    ```  
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry  
    FROM Orders   
    WHERE CustomerID = @CustomerID  
    ```  
  
    > [!NOTE]
    >  Compruebe que la sintaxis de los parámetros sea correcta para su base de datos. Por ejemplo, en Microsoft Access, la cláusula WHERE tendría el aspecto, como: `WHERE CustomerID = ?`.  
  
6.  Haga clic en **Siguiente**.  
  
7.  Para el **rellene un nombre DataTableMethod**, tipo `FillByCustomerID`.  
  
8.  Desactive el **devolver un DataTable** opción y, a continuación, haga clic en **siguiente**.  
  
9. Haga clic en **Finalizar**.  
  
## <a name="create-a-method-on-form2-to-pass-data-to"></a>Cree un método en Form2 para pasar datos a  
  
#### <a name="to-create-a-method-to-pass-data-to"></a>Para crear un método al que pasar datos  
  
1.  Haga clic en **Form2**y seleccione **ver código** para abrir **Form2** en el **Editor de código**.  
  
2.  Agregue el código siguiente al **Form2** después de que el `Form2_Load` método:  
  
     [!code-csharp[VbRaddataDisplaying#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form2.cs#1)]
     [!code-vb[VbRaddataDisplaying#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form2.vb#1)]  
  
## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Cree un método en Form1 para pasar datos y mostrar Form2  
  
#### <a name="to-create-a-method-to-pass-data-to-form2"></a>Para crear un método para pasar datos a Form2  
  
1.  En **Form1**, haga clic en la cuadrícula de datos de cliente y, a continuación, haga clic en **propiedades**.  
  
2.  En el **propiedades** ventana, haga clic en **eventos**.  
  
3.  Haga doble clic en el **CellDoubleClick** eventos.  
  
     Aparece el editor de código.  
  
4.  Actualice la definición del método para que coincida con el ejemplo siguiente:  
  
     [!code-csharp[VbRaddataDisplaying#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#2)]
     [!code-vb[VbRaddataDisplaying#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#2)]  
  
## <a name="run-the-application"></a>Ejecutar la aplicación  
  
#### <a name="to-run-the-application"></a>Para ejecutar la aplicación  
  
-   Presione F5 para ejecutar la aplicación.  
  
-   Haga doble clic en un registro de cliente en **Form1** para abrir **Form2** con los pedidos del cliente.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Dependiendo de los requisitos de la aplicación, existen varios pasos que se pueden realizar después de pasar los datos de un formulario a otro. Entre las mejoras que podría realizar se incluyen:  
  
-   Modificar el conjunto de datos agregando o quitando objetos de la base de datos. Para obtener más información, vea [Crear y configurar conjuntos de datos](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
-   Agregar funcionalidad para guardar los datos de nuevo en la base de datos. Para obtener más información, consulte [guardar los datos en la base de datos](../data-tools/save-data-back-to-the-database.md).  
  
## <a name="see-also"></a>Vea también  
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

