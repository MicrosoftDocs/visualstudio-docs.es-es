---
title: 'Tutorial: Mostrar datos relacionados en un formulario de Windows | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
- displaying data on forms, walkthroughs
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- master-details lists, displaying on Windows Forms
- data [Visual Studio], master-details
- displaying tables, related data
- displaying table data
- displaying table information
ms.assetid: fc4b9055-2bf3-4028-8aad-9489820d69f6
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 882c8229c105920efe247a54e9525a262e6a3246
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282677"
---
# <a name="walkthrough-displaying-related-data-on-a-windows-form"></a>Tutorial: Mostrar datos relacionados en Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En muchos escenarios de aplicaciones, es posible que desee trabajar con los datos que provienen de más de una tabla y, con frecuencia, con datos de tablas relacionadas. Es decir, trabajar con una relación primaria-secundaria. Por ejemplo, puede crear un formulario donde, al seleccionar un registro de cliente, se muestren los pedidos de ese cliente. La visualización de los registros relacionados en el formulario se realiza estableciendo la propiedad <xref:System.Windows.Forms.BindingSource.DataSource%2A> del <xref:System.Windows.Forms.BindingSource> secundario del <xref:System.Windows.Forms.BindingSource> primario (no la tabla secundaria) y estableciendo la propiedad <xref:System.Windows.Forms.BindingSource.DataMember%2A> del <xref:System.Windows.Forms.BindingSource> secundario de la relación de datos que enlaza las tablas primaria y secundaria.  
  
 Las tareas ilustradas en este tutorial incluyen:  
  
-   Creación de un **aplicación Windows** proyecto.  
  
-   Crear y configurar un conjunto de datos en la aplicación según el `Customers` y `Orders` tablas en la base de datos Northwind utilizando el [Asistente para configuración de origen de datos](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Agregar controles para mostrar datos de la tabla `Customers`.  
  
-   Agregar controles para mostrar los pedidos (`Orders`) basados en el cliente (`Customer`) seleccionado.  
  
-   Probar la aplicación seleccionando diferentes clientes y comprobando que se muestran los pedidos correctos del cliente seleccionado.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para completar las tareas de este tutorial, necesitará:  
  
-   Acceso a la base de datos de ejemplo Northwind. Para configurar las bases de datos, vea [Cómo: instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-the-project"></a>Crear el proyecto  
 El primer paso es crear un **aplicación Windows**.  
  
#### <a name="to-create-the-windows-application-project"></a>Para crear el proyecto de aplicación para Windows  
  
1.  Desde el **archivo** menú, cree un nuevo proyecto.  
  
2.  Dé un nombre al proyecto `RelatedDataWalkthrough`.  
  
3.  Seleccione **aplicación Windows** y haga clic en **Aceptar**. Para obtener más información, consulte [las aplicaciones cliente](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     El **RelatedDataWalkthrough** se crea y se agrega al proyecto **el Explorador de soluciones**.  
  
## <a name="creating-the-data-source"></a>Crear el origen de datos  
 Este paso crea un conjunto de datos basado en las tablas `Customers` y `Orders` de la base de datos de ejemplo Northwind.  
  
#### <a name="to-create-the-data-source"></a>Para crear el origen de datos  
  
1.  En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.  
  
2.  En el **orígenes de datos** ventana, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de origen de datos**.  
  
3.  Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.  
  
4.  En el **elegir la conexión de datos** realice página uno de los siguientes:  
  
    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.  
  
         O bien  
  
    -   Seleccione **nueva conexión** para iniciar el **agregar o modificar conexión** cuadro de diálogo.  
  
5.  Si la base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y, a continuación, haga clic en **siguiente**.  
  
6.  Haga clic en **siguiente** en el **Guardar cadena de conexión en el archivo de configuración de la aplicación** página.  
  
7.  Expanda el **tablas** nodo en el **elija los objetos de base de datos** página.  
  
8.  Seleccione el **clientes** y **pedidos** tablas y, a continuación, haga clic en **finalizar**.  
  
     El **NorthwindDataSet** se agrega al proyecto y la **clientes** tabla aparece en el **orígenes de datos** ventana.  
  
## <a name="creating-controls-to-display-data-from-the-customers-table"></a>Crear controles para mostrar datos de la tabla Customers  
  
#### <a name="to-create-controls-to-display-the-customer-data-parent-records"></a>Para crear los controles que muestren los datos del cliente (registros primarios)  
  
1.  En el **orígenes de datos** ventana, seleccione el **clientes** de tabla y, a continuación, haga clic en la flecha de lista desplegable.  
  
2.  Elija **detalles** en el menú.  
  
3.  Arrastre el método main **clientes** nodo desde el **orígenes de datos** ventana hasta la parte superior de **Form1**.  
  
     Los controles enlazados a datos con etiquetas descriptivas aparecen en el formulario, junto con una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. Un [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, y <xref:System.Windows.Forms.BindingNavigator> aparecen en la Bandeja de componentes.  
  
## <a name="creating-controls-to-display-data-from-the-orders-table"></a>Crear controles para mostrar datos de la tabla Orders  
 ![Ventana de orígenes de datos que muestra la relación](../data-tools/media/datasources2.gif "DataSources2")  
  
#### <a name="to-create-controls-to-display-the-orders-for-each-customer-child-records"></a>Para crear controles que muestren los pedidos de cada cliente (registros secundarios)  
  
-   En el **orígenes de datos** ventana, expanda el **clientes** nodo y seleccione la última columna de la **clientes** tabla, que es un expansible **pedidos** nodo y arrástrela hasta la parte inferior de **Form1**.  
  
     Se agrega un control <xref:System.Windows.Forms.DataGridView> al formulario y, a la bandeja de componentes, un nuevo componente <xref:System.Windows.Forms.BindingSource> (`OrdersBindingSource`) y un TableAdapter (`OrdersTableAdapter`).  
  
    > [!NOTE]
    >  Abra el [ventana propiedades](../ide/reference/properties-window.md) y seleccione el **OrdersBindingSource**. Inspeccione las propiedades <xref:System.Windows.Forms.BindingSource.DataSource%2A> y <xref:System.Windows.Forms.BindingSource.DataMember%2A> para ver cómo está configurado el enlace para mostrar los registros relacionados. <xref:System.Windows.Forms.BindingSource.DataSource%2A> se establece en `CustomersBindingSource` (el <xref:System.Windows.Forms.BindingSource> de la tabla primaria), en lugar de en la tabla `Orders`. La propiedad <xref:System.Windows.Forms.BindingSource.DataMember%2A> se establece en `FK_Orders_Customers`, que es el nombre del objeto <xref:System.Data.DataRelation> que relaciona las tablas entre sí.  
  
## <a name="testing-the-application"></a>Probar la aplicación  
  
#### <a name="to-test-the-application"></a>Para probar la aplicación  
  
1.  Presione F5 para ejecutar la aplicación.  
  
2.  Seleccione distintos clientes mediante la **CustomersBindingNavigator** para comprobar los pedidos correctos se muestran en el <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Dependiendo de los requisitos de la aplicación, hay varios pasos que se pueden realizar después de crear un formulario principal-detalle. Entre las mejoras que podría realizar a este tutorial se incluye:  
  
-   Filtrar los registros de `Customers` agregando parametrización a la tabla `Customers`. Para ello, seleccione cualquier control que muestra los datos de la `Customers` de tabla, haga clic en la etiqueta inteligente y elija **Agregar consulta**. Completar la [cuadro de diálogo del generador de criterios de búsqueda](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d). Para obtener más información, consulte [Cómo: agregar una consulta parametrizada a una aplicación de Windows Forms](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
## <a name="see-also"></a>Vea también  
 [Tutoriales de datos](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Ventana Orígenes de datos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Cómo: mostrar relacionados con la aplicación de datos en un Windows Forms](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)   
 [Información general sobre el componente BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)   
 [Información general sobre el control BindingNavigator](http://msdn.microsoft.com/library/4423eede-f8d1-4d02-822f-5bf8432680d0)