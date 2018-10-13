---
title: 'Tutorial: Crear un conjunto de datos con el Diseñador de Dataset | Microsoft Docs'
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
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
ms.assetid: 12360f54-db6c-45d2-a91f-fee43214b555
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 1a9d47431497f05fd5538510b39b44298587dd0e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287370"
---
# <a name="walkthrough-creating-a-dataset-with-the-dataset-designer"></a>Tutorial: Crear un conjunto de datos con el Diseñador de Dataset
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial creará un conjunto de datos mediante el **Diseñador de Dataset**. Le guiará a través del proceso de crear un nuevo proyecto y agregar un nuevo **DataSet** elemento a él. Obtendrá información sobre cómo crear tablas de acuerdo con una base de datos sin utilizar un asistente.  
  
 Las tareas ilustradas en este tutorial incluyen:  
  
-   Crear un nuevo **aplicación Windows** proyecto.  
  
-   Adición de un valor vacío **DataSet** al proyecto.  
  
-   Crear y configurar un origen de datos en la aplicación mediante la creación de un conjunto de datos con el **Diseñador de Dataset**.  
  
-   Crear una conexión a la base de datos Northwind en **Explorador de servidores**.  
  
-   Crear tablas con TableAdapters del conjunto de datos basadas en tablas de la base de datos.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para completar las tareas de este tutorial, necesitará:  
  
-   Acceso a la base de datos de ejemplo Northwind (versión de SQL Server o Access). Para obtener más información, consulte [Cómo: instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-a-new-windows-application-project"></a>Crear un nuevo proyecto de aplicación para Windows  
  
#### <a name="to-create-a-new-windows-application-project"></a>Para crear un proyecto de aplicación para Windows nuevo  
  
1.  Desde el **archivo** menú, cree un nuevo proyecto.  
  
2.  Elija un lenguaje de programación en el **tipos de proyecto** panel.  
  
3.  Haga clic en **aplicación Windows** en el **plantillas** panel.  
  
4.  Denomine el proyecto `DatasetDesignerWalkthrough`y, a continuación, haga clic en **Aceptar**.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] agregará el proyecto a **el Explorador de soluciones** y mostrar un formulario nuevo en el diseñador.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Agregar un nuevo conjunto de datos a la aplicación  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Para agregar un nuevo elemento del conjunto de datos al proyecto  
  
1.  En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.  
  
     Aparecerá el cuadro de diálogo **Agregar nuevo elemento**.  
  
2.  En el **plantillas** cuadro de la **Agregar nuevo elemento** cuadro de diálogo, haga clic en **DataSet**.  
  
3.  Nombre del conjunto de datos `NorthwindDataset`y, a continuación, haga clic en **agregar**.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] agregará un archivo denominado **NorthwindDataset.xsd** al proyecto y ábralo en el **Diseñador de Dataset**.  
  
## <a name="creating-a-data-connection-in-server-explorer"></a>Crear una conexión de datos en el Explorador de servidores  
  
#### <a name="to-create-a-connection-to-the-northwind-database"></a>Para crear una conexión a la base de datos Northwind  
  
1.  En el **vista** menú, haga clic en **Explorador de servidores**.  
  
2.  En **Explorador de servidores**, haga clic en el **conectar con base de datos** botón.  
  
3.  Crear una conexión a la base de datos de ejemplo Northwind.  
  
    > [!NOTE]
    >  Puede conectar a la versión SQL Server o Access de Northwind para este tutorial.  
  
## <a name="creating-the-tables-in-the-dataset"></a>Crear las tablas del conjunto de datos  
 En esta sección se explicará cómo agregar tablas al conjunto de datos.  
  
#### <a name="to-create-the-customers-table"></a>Para crear la tabla Customers  
  
1.  Expanda la conexión de datos que creó en **Explorador de servidores**y, a continuación, expanda el **tablas** nodo.  
  
2.  Arrastre el **clientes** desde la tabla **Explorador de servidores** hasta la **Diseñador de Dataset**.  
  
     Un **clientes** tabla de datos y **CustomersTableAdapter** se agregan al conjunto de datos.  
  
#### <a name="to-create-the-orders-table"></a>Para crear la tabla Orders  
  
-   Arrastre el **pedidos** desde la tabla **Explorador de servidores** hasta la **Diseñador de Dataset**.  
  
     Un **pedidos** tabla de datos, **OrdersTableAdapter**y la relación de datos entre el **clientes** y **pedidos** tablas se agregarán a la conjunto de datos.  
  
#### <a name="to-create-the-orderdetails-table"></a>Para crear la tabla OrderDetails  
  
-   Arrastre el **Order Details** desde la tabla **Explorador de servidores** hasta la **Diseñador de Dataset**.  
  
     Un **Order Details** tabla de datos, **Order DetailsTableAdapter**y una relación de datos entre el **pedidos** y **Order Details** tablas se agregan al conjunto de datos.  
  
## <a name="next-steps"></a>Pasos siguientes  
  
### <a name="to-add-functionality-to-your-application"></a>Para agregar funcionalidad a la aplicación  
  
-   Guarde el conjunto de datos.  
  
-   Seleccione los elementos en el **orígenes de datos** ventana y arrástrelos hasta un formulario. Para obtener más información, consulte [controla el enlace Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
-   Agregar más consultas a los TableAdapters. Para obtener más información, consulte [Cómo: crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
-   Agregar lógica de la validación a los eventos <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> de las tablas de datos en el conjunto de datos. Para obtener más información, consulte [validar datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Vea también  
 [Tutoriales de datos](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar su aplicación para recibir datos](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Captura de datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edición de datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validación de datos](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Guardar datos](../data-tools/saving-data.md)