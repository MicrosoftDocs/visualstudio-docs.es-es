---
title: 'Tutorial: Mostrar datos relacionados en una aplicación WPF | Microsoft Docs'
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
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: c44b949daabf587dbca5d8a5d1d932afca2c1f9c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602460"
---
# <a name="walkthrough-displaying-related-data-in-a-wpf-application"></a>Tutorial: Mostrar datos relacionados en una aplicación WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial, creará una aplicación WPF que muestra los datos de las tablas de base de datos que tienen una relación de elementos primarios y secundarios. Los datos se encapsulan en entidades en un Entity Data Model. La entidad primaria contiene información general de un conjunto de pedidos. Cada propiedad de esta entidad está enlazada a un control diferente en la aplicación. La entidad secundaria contiene detalles para cada pedido. Este conjunto de datos se enlaza a un control de <xref:System.Windows.Controls.DataGrid>.

 En este tutorial se muestran las tareas siguientes:

- Crear una aplicación de WPF y un Entity Data Model que se genera a partir de los datos de la base de datos de ejemplo AdventureWorksLT.

- Crear un conjunto de controles enlazados a datos que muestran información general de un conjunto de pedidos. Los controles se crean arrastrando una entidad primaria desde la ventana **orígenes de datos** hasta **WPF Designer**.

- Creación de un control de <xref:System.Windows.Controls.DataGrid> que muestra los detalles relacionados de cada pedido seleccionado. Los controles se crean arrastrando una entidad secundaria desde la ventana **orígenes de datos** hasta una ventana en **WPF Designer**.

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesita los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Operador

- Acceder a una instancia en ejecución de SQL Server o SQL Server Express que tenga asociada la base de datos de ejemplo AdventureWorksLT. Puede descargar la base de datos AdventureWorksLT desde el [sitio web de CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).

  El conocimiento previo de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial:

- Entity Data Model y ADO.NET Entity Framework. Para obtener más información, vea [información general sobre Entity Framework](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).

- Trabajar con WPF Designer. Para obtener más información, vea [información general sobre WPF y Silverlight Designer](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).

- Enlace a datos de WPF. Para obtener más información, consulte [Información general sobre el enlace de datos](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="creating-the-project"></a>Crear el proyecto
 Cree un nuevo proyecto de WPF para mostrar los registros de pedidos.

#### <a name="to-create-a-new-wpf-project"></a>Para crear un proyecto de WPF

1. Inicie Visual Studio.

2. En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.

3. Expanda  **C# visual** o **Visual Basic**y, a continuación, seleccione **Windows**.

4. Asegúrese de que **.NET Framework 4** está seleccionado en el cuadro combinado de la parte superior del cuadro de diálogo. El control <xref:System.Windows.Controls.DataGrid> que se utiliza en este tutorial solo está disponible en el .NET Framework 4.

5. Seleccione la plantilla de proyecto **Aplicación WPF**.

6. En el cuadro **Nombre** , escriba `AdventureWorksOrdersViewer`.

7. Haga clic en **Aceptar**.

     Visual Studio crea el proyecto de `AdventureWorksOrdersViewer`.

## <a name="creating-an-entity-data-model-for-the-application"></a>Crear un Entity Data Model para la aplicación
 Antes de crear controles enlazados a datos, debe definir un modelo de datos para la aplicación y agregarlo a la ventana **Orígenes de datos**. En este tutorial, el modelo de datos es un Entity Data Model.

#### <a name="to-create-an-entity-data-model"></a>Para crear un Entity Data Model

1. En el menú **datos** , haga clic en **Agregar nuevo origen de datos** para abrir el Asistente para la configuración de orígenes de **datos**.

2. En la página **elegir un tipo de origen de datos** , haga clic en **base**de datos y, a continuación, en **siguiente**.

3. En la página **elegir un modelo de base de datos** , haga clic en **Entity Data Model**y, a continuación, en **siguiente**.

4. En la página **elegir contenido del modelo** , haga clic en **generar desde la base de datos**y, a continuación, haga clic en **siguiente**.

5. En la página **elegir la conexión de datos** , realice una de las acciones siguientes:

   - Si una conexión de datos a la base de datos de ejemplo AdventureWorksLT está disponible en la lista desplegable, selecciónela.

      o bien

   - Haga clic en **nueva conexión** y cree una conexión con la base de datos AdventureWorksLT.

     Asegúrese de que la opción **Guardar configuración de conexión de entidad en App. config como** esté seleccionada y, a continuación, haga clic en **siguiente**.

6. En la página **Elija los objetos de base de datos** , expanda **tablas**y, a continuación, seleccione las tablas siguientes:

   - **SalesOrderHeader**

   - **SalesOrderDetail**

7. Haga clic en **Finalizar**.

8. Compile el proyecto.

## <a name="creating-data-bound-controls-that-display-the-orders"></a>Crear controles enlazados a datos que muestren los pedidos
 Cree controles que muestren los registros de pedidos arrastrando la entidad `SalesOrderHeaders` desde la ventana **orígenes de datos** hasta WPF Designer.

#### <a name="to-create-data-bound-controls-that-display-the-order-records"></a>Para crear controles enlazados a datos que muestren los registros de pedidos

1. En **Explorador de soluciones**, haga doble clic en MainWindow. Xaml.

    La ventana se abre en WPF Designer.

2. Edite el código XAML para que las propiedades **height** y **width** se establezcan en 800

3. En la ventana **orígenes de datos** , haga clic en el menú desplegable del nodo **SalesOrderHeaders** y seleccione **detalles**.

4. Expanda el nodo **SalesOrderHeaders**.

5. Haga clic en el menú desplegable situado junto a **SalesOrderID** y seleccione **ComboBox**.

6. Para cada uno de los siguientes nodos secundarios del nodo **SalesOrderHeaders** , haga clic en el menú desplegable situado junto al nodo y seleccione **ninguno**:

   - **RevisionNumber**

   - **OnlineOrderFlag**

   - **ShipToAddressID**

   - **BillToAddressID**

   - **CreditCardApprovalCode**

   - **SubTotal**

   - **TaxAmt**

   - **Marítimo**

   - **rowguid**

   - **ModifiedDate**

     Esta acción impide que Visual Studio cree controles enlazados a datos para estos nodos en el paso siguiente. En este tutorial, se da por hecho que el usuario final no necesita ver estos datos.

7. Desde la ventana **orígenes de datos** , arrastre el nodo **SalesOrderHeaders** a la ventana de **WPF Designer**.

    Visual Studio genera XAML que crea un conjunto de controles que se enlazan a los datos de la entidad **SalesOrderHeaders** y el código que los carga. Para obtener más información sobre el código XAML y el código generado, vea [enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

8. En el diseñador, haga clic en el cuadro combinado que se encuentra junto a la etiqueta **sales Order ID** .

9. En la ventana **Propiedades**, active la casilla junto a la propiedad **IsReadOnly**.

## <a name="creating-a-datagrid-that-displays-the-order-details"></a>Crear un control DataGrid que muestre los detalles del pedido
 Cree un control de <xref:System.Windows.Controls.DataGrid> que muestre los detalles del pedido arrastrando la entidad `SalesOrderDetails` desde la ventana **orígenes de datos** hasta WPF Designer.

#### <a name="to-create-a-datagrid-that-displays-the-order-details"></a>Para crear un control DataGrid que muestre los detalles del pedido

1. En la ventana **orígenes de datos** , busque el nodo **SalesOrderDetails** que es un elemento secundario del nodo **SalesOrderHeaders** .

   > [!NOTE]
   > También hay un nodo de **SalesOrderDetails** que es un elemento del mismo nivel que el nodo **SalesOrderHeaders** . Asegúrese de seleccionar el nodo secundario del nodo **SalesOrderHeaders** .

2. Expanda el nodo secundario **SalesOrderDetails** .

3. Para cada uno de los siguientes nodos secundarios del nodo **SalesOrderDetails** , haga clic en el menú desplegable situado junto al nodo y seleccione **ninguno**:

   - **SalesOrderID**

   - **SalesOrderDetailID**

   - **rowguid**

   - **ModifiedDate**

     Esta acción evita que Visual Studio incluya estos datos en el control <xref:System.Windows.Controls.DataGrid> que cree en el paso siguiente. En este tutorial, se da por hecho que el usuario final no necesita ver estos datos.

4. Desde la ventana **orígenes de datos** , arrastre el nodo secundario **SalesOrderDetails** hasta la ventana de **WPF Designer**.

    Visual Studio genera XAML para definir un nuevo control de <xref:System.Windows.Controls.DataGrid> enlazado a datos y el control aparece en el diseñador. Visual Studio también actualiza el método de `GetSalesOrderHeadersQuery` generado en el archivo de código subyacente para incluir los datos en la entidad **SalesOrderDetails** .

## <a name="testing-the-application"></a>Probar la aplicación
 Compile y ejecute la aplicación para comprobar que muestra los registros de pedidos.

#### <a name="to-test-the-application"></a>Para probar la aplicación

1. Presione **F5**.

     La aplicación se compila y se ejecuta. Compruebe lo siguiente:

    - El cuadro combinado **sales Order ID** muestra **71774**. Este es el primer identificador de orden de la entidad.

    - Para cada pedido que seleccione en el cuadro combinado **sales Order ID** , se muestra información detallada del pedido en el <xref:System.Windows.Controls.DataGrid>.

2. Cierre la aplicación.

## <a name="next-steps"></a>Pasos siguientes
 Después de completar este tutorial, obtenga información sobre cómo usar la ventana **orígenes de datos** de Visual Studio para enlazar controles WPF a otros tipos de orígenes de datos. Para obtener más información, vea [enlazar controles de WPF a un servicio de datos de WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) y [enlazar controles de WPF a un conjunto](../data-tools/bind-wpf-controls-to-a-dataset.md)de datos.

## <a name="see-also"></a>Vea también
 [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [Mostrar datos relacionados en aplicaciones WPF](../data-tools/display-related-data-in-wpf-applications.md)