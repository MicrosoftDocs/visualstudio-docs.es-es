---
title: 'Tutorial: Mostrar datos relacionados en una aplicación de WPF | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 873f20383a3a35dcfc7b51128d07d5efc1d11519
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988349"
---
# <a name="walkthrough-displaying-related-data-in-a-wpf-application"></a>Tutorial: Mostrar datos relacionados en una aplicación WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial, creará una aplicación WPF que muestra los datos de tablas de base de datos que tienen una relación de elementos primarios y secundarios. Los datos se encapsulan en entidades en un Entity Data Model. La entidad primaria contiene información general de un conjunto de pedidos. Cada propiedad de esta entidad está enlazada a un control diferente de la aplicación. La entidad secundaria contiene detalles de cada pedido. Este conjunto de datos se enlaza a un <xref:System.Windows.Controls.DataGrid> control.  
  
 En este tutorial se muestran las tareas siguientes:  
  
- Creación de una aplicación de WPF y un Entity Data Model que se genera a partir de datos en la base de datos de ejemplo AdventureWorksLT.  
  
- Creación de un conjunto de controles enlazados a datos que muestran información general para un conjunto de pedidos. Crear los controles arrastrando una entidad primaria desde la **orígenes de datos** ventana **WPF Designer**.  
  
- Creación de un <xref:System.Windows.Controls.DataGrid> seleccionado de control que muestra los detalles relacionados para cada pedido. Crear los controles arrastrando una entidad secundaria desde la **orígenes de datos** ventana a una ventana de **WPF designer**.  
  
   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- Acceder a una instancia en ejecución de SQL Server o SQL Server Express que tenga asociada la base de datos de ejemplo AdventureWorksLT. Puede descargar la base de datos AdventureWorksLT el [sitio Web de CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
  El conocimiento previo de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial:  
  
- Entity Data Model y ADO.NET Entity Framework. Para obtener más información, consulte [Introducción a Entity Framework](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).  
  
- Trabajar con WPF Designer. Para obtener más información, consulte [WPF y Silverlight Designer Overview](http://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
- Enlace a datos de WPF. Para obtener más información, consulte [Información general sobre el enlace de datos](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).  
  
## <a name="creating-the-project"></a>Crear el proyecto  
 Cree un nuevo proyecto WPF para mostrar los registros de pedidos.  
  
#### <a name="to-create-a-new-wpf-project"></a>Para crear un proyecto de WPF  
  
1.  Inicie Visual Studio.  
  
2.  En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.  
  
3.  Expanda **Visual C#** o **Visual Basic**y, a continuación, seleccione **Windows**.  
  
4.  Asegúrese de que **.NET Framework 4** está seleccionado en el cuadro combinado en la parte superior del cuadro de diálogo. El <xref:System.Windows.Controls.DataGrid> control que se utiliza en este tutorial está disponible solo en .NET Framework 4.  
  
5.  Seleccione la plantilla de proyecto **Aplicación WPF**.  
  
6.  En el cuadro **Nombre** , escriba `AdventureWorksOrdersViewer`.  
  
7.  Haga clic en **Aceptar**.  
  
     Visual Studio crea el `AdventureWorksOrdersViewer` proyecto.  
  
## <a name="creating-an-entity-data-model-for-the-application"></a>Crear un Entity Data Model para la aplicación  
 Antes de crear controles enlazados a datos, debe definir un modelo de datos para la aplicación y agregarlo a la ventana **Orígenes de datos**. En este tutorial, el modelo de datos es un Entity Data Model.  
  
#### <a name="to-create-an-entity-data-model"></a>Para crear un Entity Data Model  
  
1. En el **datos** menú, haga clic en **Agregar nuevo origen de datos** para abrir el **Asistente para configuración de origen de datos**.  
  
2. En el **elegir un tipo de origen de datos** página, haga clic en **base de datos**y, a continuación, haga clic en **siguiente**.  
  
3. En el **elegir un modelo de base de datos** página, haga clic en **Entity Data Model**y, a continuación, haga clic en **siguiente**.  
  
4. En el **Elegir contenido de Model** página, haga clic en **generar desde la base de datos**y, a continuación, haga clic en **siguiente**.  
  
5. En el **elegir la conexión de datos** , realice una de las siguientes acciones:  
  
   - Si una conexión de datos a la base de datos de ejemplo AdventureWorksLT está disponible en la lista desplegable, selecciónela.  
  
      -o bien-  
  
   - Haga clic en **nueva conexión** y crear una conexión a la base de datos AdventureWorksLT.  
  
     Asegúrese de que el **Guardar configuración de conexión de entidad en App.Config como** opción está seleccionada y, a continuación, haga clic en **siguiente**.  
  
6. En el **elija los objetos de base de datos** , expanda **tablas**y, a continuación, seleccione las tablas siguientes:  
  
   -   **SalesOrderDetail**  
  
   -   **SalesOrderHeader**  
  
7. Haga clic en **Finalizar**.  
  
8. Compile el proyecto.  
  
## <a name="creating-data-bound-controls-that-display-the-orders"></a>Crear datos enlazados a controles que muestran los pedidos  
 Crear controles que muestren los registros de pedidos arrastrando el `SalesOrderHeaders` entidad desde la **orígenes de datos** ventana hasta WPF designer.  
  
#### <a name="to-create-data-bound-controls-that-display-the-order-records"></a>Para crear controles enlazados a datos que se muestran los registros de pedido  
  
1. En **el Explorador de soluciones**, haga doble clic en MainWindow.xaml.  
  
    La ventana se abre en WPF Designer.  
  
2. Editar el XAML para que el **alto** y **ancho** propiedades se establecen en 800  
  
3. En el **orígenes de datos** ventana, haga clic en el menú desplegable de la **SalesOrderHeaders** nodo y seleccione **detalles**.  
  
4. Expanda el nodo **SalesOrderHeaders**.  
  
5. Haga clic en el menú desplegable junto a **SalesOrderID** y seleccione **ComboBox**.  
  
6. Para cada uno de los siguientes nodos secundarios de la **SalesOrderHeaders** nodo, haga clic en el menú desplegable junto el nodo y seleccione **ninguno**:  
  
   - **RevisionNumber**  
  
   - **OnlineOrderFlag**  
  
   - **ShipToAddressID**  
  
   - **BillToAddressID**  
  
   - **CreditCardApprovalCode**  
  
   - **SubTotal**  
  
   - **TaxAmt**  
  
   - **Freight**  
  
   - **rowguid**  
  
   - **ModifiedDate**  
  
     Esta acción impide que Visual Studio cree controles enlazados a datos para estos nodos en el paso siguiente. En este tutorial, se da por hecho que el usuario final no necesita ver estos datos.  
  
7. Desde el **orígenes de datos** ventana, arrastre el **SalesOrderHeaders** nodo en la ventana de **WPF Designer**.  
  
    Visual Studio genera XAML que crea un conjunto de controles que están enlazados a datos en el **SalesOrderHeaders** entidad y el código que carga los datos. Para obtener más información sobre el XAML y el código generado, vea [WPF enlazar controles a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
8. En el diseñador, haga clic en el cuadro combinado junto a la **Id. de pedido de ventas** etiqueta.  
  
9. En la ventana **Propiedades**, active la casilla junto a la propiedad **IsReadOnly**.  
  
## <a name="creating-a-datagrid-that-displays-the-order-details"></a>Crear un control DataGrid que muestra los detalles del pedido  
 Crear un <xref:System.Windows.Controls.DataGrid> control que muestra los detalles de pedidos arrastrando el `SalesOrderDetails` entidad desde la **orígenes de datos** ventana hasta WPF designer.  
  
#### <a name="to-create-a-datagrid-that-displays-the-order-details"></a>Para crear una cuadrícula que muestra los detalles del pedido  
  
1. En el **orígenes de datos** ventana, busque la **SalesOrderDetails** nodo que es un elemento secundario de la **SalesOrderHeaders** nodo.  
  
   > [!NOTE]
   >  También hay un **SalesOrderDetails** nodo del mismo nivel de la **SalesOrderHeaders** nodo. Asegúrese de que selecciona el nodo secundario de la **SalesOrderHeaders** nodo.  
  
2. Expanda el elemento secundario **SalesOrderDetails** nodo.  
  
3. Para cada uno de los siguientes nodos secundarios de la **SalesOrderDetails** nodo, haga clic en el menú desplegable junto el nodo y seleccione **ninguno**:  
  
   - **SalesOrderID**  
  
   - **SalesOrderDetailID**  
  
   - **rowguid**  
  
   - **ModifiedDate**  
  
     Esta acción impide que Visual Studio incluya estos datos en el <xref:System.Windows.Controls.DataGrid> control que se cree en el paso siguiente. En este tutorial, se da por hecho que el usuario final no necesita ver estos datos.  
  
4. Desde el **orígenes de datos** ventana, arrastre el elemento secundario **SalesOrderDetails** nodo en la ventana de **WPF Designer**.  
  
    Visual Studio genera XAML para definir un nuevo enlace de datos <xref:System.Windows.Controls.DataGrid> control y el control aparece en el diseñador. Visual Studio también actualiza el generado `GetSalesOrderHeadersQuery` método en el archivo de código subyacente para incluir los datos en el **SalesOrderDetails** entidad.  
  
## <a name="testing-the-application"></a>Probar la aplicación  
 Compile y ejecute la aplicación para comprobar que muestra los registros de pedidos.  
  
#### <a name="to-test-the-application"></a>Para probar la aplicación  
  
1.  Presione **F5**.  
  
     La aplicación se compila y se ejecuta. Compruebe lo siguiente:  
  
    -   El **Id. de pedido de ventas** muestra el cuadro combinado **71774**. Este es el primer identificador de pedido en la entidad.  
  
    -   Para cada pedido seleccione en la **Id. de pedido de ventas** cuadro combinado, se muestra información detallada del pedido en el <xref:System.Windows.Controls.DataGrid>.  
  
2.  Cierre la aplicación.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Después de completar este tutorial, obtenga información sobre cómo usar el **orígenes de datos** controla la ventana de Visual Studio para enlazar WPF a otros tipos de orígenes de datos. Para obtener más información, consulte [WPF enlazar controles a un servicio de datos WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) y [WPF enlazar controles a un conjunto de datos](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
## <a name="see-also"></a>Vea también  
 [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Mostrar datos relacionados en aplicaciones WPF](../data-tools/display-related-data-in-wpf-applications.md)