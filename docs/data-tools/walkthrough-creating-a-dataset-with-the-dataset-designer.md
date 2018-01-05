---
title: "Tutorial: Crear un conjunto de datos con el Diseñador de Dataset | Documentos de Microsoft"
ms.custom: 
ms.date: 09/11/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 44139e06a09fc2883c7a42202129bfd3c82343d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-dataset-with-the-dataset-designer"></a>Tutorial: Crear un conjunto de datos con el Diseñador de Dataset

En este tutorial creará un conjunto de datos mediante la **Diseñador de Dataset**. Éste lo guiará a través del proceso de crear un nuevo proyecto y agregar un nuevo **conjunto de datos** elemento a él. Obtendrá información sobre cómo crear tablas de acuerdo con una base de datos sin utilizar un asistente.  

Las tareas ilustradas en este tutorial incluyen:  

-   Crear un nuevo **aplicación de Windows Forms** proyecto.  

-   Agregar vacío **conjunto de datos** elemento al proyecto.  

-   Crear y configurar un origen de datos en la aplicación mediante la creación de un conjunto de datos con la **Diseñador de Dataset**.  
 
-   Crear una conexión a la base de datos Northwind en **Explorador de servidores**.  

-   Crear tablas con TableAdapters del conjunto de datos basadas en tablas de la base de datos.  

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
Este tutorial usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.  
  
1.  Si no tiene SQL Server Express LocalDB, puede instalarlo desde el [página de descarga de ediciones de SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), o a través del **instalador de Visual Studio**. El instalador de Visual Studio, se puede instalar SQL Server Express LocalDB como parte de la **almacenamiento de datos y el procesamiento** carga de trabajo, o como un componente individual.  
  
2.  Instalar la base de datos de ejemplo Northwind, siga estos pasos:  

    1. En Visual Studio, abra el **Explorador de objetos de SQL Server** ventana. (Explorador de objetos de SQL Server se instala como parte de la **almacenamiento de datos y el procesamiento** carga de trabajo en el instalador de Visual Studio.) Expanda el **SQL Server** nodo. Haga doble clic en la instancia de LocalDB y seleccione **nueva consulta...** .  

       Se abre una ventana del editor de consultas.  

    2. Copia la [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el Portapapeles. Este script de T-SQL crea la base de datos Northwind desde el principio y lo rellena con datos.  

    3. Pegue el script de T-SQL en el editor de consultas y, a continuación, elija la **Execute** botón.  

       Después de unos minutos, finaliza la ejecución de la consulta y se crea la base de datos Northwind.  
  
## <a name="creating-a-new-windows-forms-application-project"></a>Crear un nuevo proyecto de aplicación de Windows Forms  
  
#### <a name="to-create-a-new-windows-forms-application-project"></a>Para crear un nuevo proyecto de aplicación de Windows Forms  
  
1. En Visual Studio, en el **archivo** menú, seleccione **New**, **proyecto...** .  
  
2. Expanda **Visual C#** o **Visual Basic** en el panel izquierdo, seleccione **escritorio clásico de Windows**.  

3. En el panel central, seleccione la **aplicación de Windows Forms** tipo de proyecto.  

4. Denomine el proyecto **DatasetDesignerWalkthrough**y, a continuación, elija **Aceptar**.  
  
     Visual Studio agrega el proyecto al **el Explorador de soluciones** y mostrará un nuevo formulario en el diseñador.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Agregar un nuevo conjunto de datos a la aplicación  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Para agregar un nuevo elemento del conjunto de datos al proyecto  
  
1.  En el **proyecto** menú, seleccione **Agregar nuevo elemento...** .  
  
     Aparecerá el cuadro de diálogo **Agregar nuevo elemento**.  
  
2.  En el panel izquierdo, seleccione **datos**, a continuación, seleccione **conjunto de datos** en el panel central.  
  
3.  Nombre del conjunto de datos **NorthwindDataset**y, a continuación, elija **agregar**.  
  
     Visual Studio agrega un archivo denominado **NorthwindDataset.xsd** al proyecto y lo abre en el **Diseñador de Dataset**.  
  
## <a name="creating-a-data-connection-in-server-explorer"></a>Crear una conexión de datos en el Explorador de servidores  
  
#### <a name="to-create-a-connection-to-the-northwind-database"></a>Para crear una conexión a la base de datos Northwind  
  
1.  En el **vista** menú, haga clic en **Explorador de servidores**.  
  
2.  En **Explorador de servidores**, haga clic en el **conectar con base de datos** botón.  
  
3.  Crear una conexión a la base de datos de ejemplo Northwind.  
  
## <a name="creating-the-tables-in-the-dataset"></a>Crear las tablas del conjunto de datos  
Esta sección explica cómo agregar tablas al conjunto de datos.  
  
#### <a name="to-create-the-customers-table"></a>Para crear la tabla Customers  
  
1.  Expanda la conexión de datos que creó en **Explorador de servidores**y, a continuación, expanda el **tablas** nodo.  
  
2.  Arrastre el **clientes** tabla **Explorador de servidores** en el **Diseñador de Dataset**.  
  
     A **clientes** tabla de datos y **CustomersTableAdapter** se agregan al conjunto de datos.  
  
#### <a name="to-create-the-orders-table"></a>Para crear la tabla Orders  
  
-   Arrastre el **pedidos** tabla **Explorador de servidores** en el **Diseñador de Dataset**.  
  
     Un **pedidos** tabla de datos, **OrdersTableAdapter**y la relación de datos entre el **clientes** y **pedidos** tablas se agregarán a la conjunto de datos.  
  
#### <a name="to-create-the-orderdetails-table"></a>Para crear la tabla OrderDetails  
  
-   Arrastre el **Order Details** tabla **Explorador de servidores** en el **Diseñador de Dataset**.  
  
     Un **Order Details** tabla de datos, **OrderDetailsTableAdapter**y una relación de datos entre el **pedidos** y **OrderDetails** tablas se agregan al conjunto de datos.  
  
## <a name="next-steps"></a>Pasos siguientes  
  
### <a name="to-add-functionality-to-your-application"></a>Para agregar funcionalidad a la aplicación  
  
-   Guarde el conjunto de datos.  
  
-   Seleccione los elementos en el **orígenes de datos** ventana y arrástrelos hasta un formulario. Para obtener más información, consulte [enlazar controles formularios Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
-   Agregar más consultas a los TableAdapters. 
  
-   Agregar lógica de la validación a los eventos <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> de las tablas de datos en el conjunto de datos. Para obtener más información, consulte [validar los datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Vea también
[Crear y configurar conjuntos de datos en Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)  
[Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
[Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
[Validar datos](../data-tools/validate-data-in-datasets.md)   
[Guardar datos](../data-tools/saving-data.md)