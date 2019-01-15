---
title: 'Tutorial: Creación de un conjunto de datos con el Diseñador de Dataset'
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: e79646609bf592b7a8d71d3e0ba8660c65520715
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868526"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>Tutorial: Crear un conjunto de datos con el Diseñador de Dataset

En este tutorial creará un conjunto de datos mediante el **Diseñador de Dataset**. El artículo le guiará por el proceso de crear un nuevo proyecto y agregar un nuevo **DataSet** elemento a él. Obtendrá información sobre cómo crear tablas basadas en tablas de una base de datos sin utilizar a un asistente.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1.  Si no tiene SQL Server Express LocalDB, instálelo de desde el [página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o a través del **instalador de Visual Studio**. En el instalador de Visual Studio, se puede instalar SQL Server Express LocalDB como parte de la **procesamiento y almacenamiento de datos** carga de trabajo, o como un componente individual.

2.  Instalar la base de datos de ejemplo Northwind, siga estos pasos:

    1. En Visual Studio, abra el **Explorador de objetos de SQL Server** ventana. (Explorador de objetos de SQL Server se instala como parte de la **procesamiento y almacenamiento de datos** carga de trabajo en el instalador de Visual Studio.) Expanda el **SQL Server** nodo. Haga doble clic en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copia el [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el Portapapeles. Este script de Transact-SQL crea la base de datos Northwind desde el principio y lo rellena con datos.

    3. Pegue el script de Transact-SQL en el editor de consultas y, a continuación, elija el **Execute** botón.

       Después de un breve tiempo, la consulta termine de ejecutarse y se crea la base de datos Northwind.

## <a name="create-a-new-windows-forms-application-project"></a>Crear un nuevo proyecto de aplicación de Windows Forms

1. En Visual Studio, en el **archivo** menú, seleccione **New** > **proyecto**.

2. Expanda el **Visual C#** o **Visual Basic** en el panel izquierdo, seleccione **Windows Desktop**.

3. En el panel central, seleccione la **aplicación de Windows Forms** tipo de proyecto.

4. Denomine el proyecto **DatasetDesignerWalkthrough**y, a continuación, elija **Aceptar**.

     Visual Studio agrega el proyecto al **el Explorador de soluciones** y mostrar un formulario nuevo en el diseñador.

## <a name="add-a-new-dataset-to-the-application"></a>Agregar un nuevo conjunto de datos a la aplicación

1.  En el menú **Proyecto**, seleccione **Agregar nuevo elemento**.

     Aparecerá el cuadro de diálogo **Agregar nuevo elemento**.

2.  En el panel izquierdo, seleccione **datos**, a continuación, seleccione **DataSet** en el panel central.

3.  Nombre del conjunto de datos **NorthwindDataset**y, a continuación, elija **agregar**.

     Visual Studio agrega un archivo denominado **NorthwindDataset.xsd** al proyecto y lo abre en el **Diseñador de Dataset**.

## <a name="create-a-data-connection-in-server-explorer"></a>Crear una conexión de datos en el Explorador de servidores

1.  En el menú **Ver**, haga clic en el **Explorador de servidores**.

2.  En el **Explorador de servidores**, haga clic en el botón **Conectar con base de datos**.

3.  Crear una conexión a la base de datos de ejemplo Northwind.

## <a name="create-the-tables-in-the-dataset"></a>Crear las tablas del conjunto de datos

Esta sección explica cómo agregar tablas al conjunto de datos.

### <a name="to-create-the-customers-table"></a>Para crear la tabla Customers

1.  Expanda la conexión de datos que creó en el **Explorador de servidores** y, a continuación, expanda el nodo **Tablas**.

2.  Arrastre la tabla **Customers** desde el **Explorador de servidores** al **Diseñador de DataSet**.

     Se agregan una tabla de datos **Customers** y **CustomersTableAdapter** al conjunto de datos.

### <a name="to-create-the-orders-table"></a>Para crear la tabla Orders

-   Arrastre la tabla **Orders** desde el **Explorador de servidores** al **Diseñador de DataSet**.

     Una tabla de datos **Orders**, **OrdersTableAdapter** y una relación de datos entre las tablas **Customers** y **Orders** se agregan al conjunto de datos.

### <a name="to-create-the-orderdetails-table"></a>Para crear la tabla OrderDetails

-   Arrastre la tabla **Order Details** desde el **Explorador de servidores** hasta el **Diseñador de DataSet**.

     Un **Order Details** tabla de datos, **OrderDetailsTableAdapter**y una relación de datos entre el **pedidos** y **OrderDetails** tablas se agregan al conjunto de datos.

## <a name="next-steps"></a>Pasos siguientes

-   Guarde el conjunto de datos.

-   Seleccione elementos en la ventana **Orígenes de datos** y arrástrelos a un formulario. Para obtener más información, consulte [controla el enlace Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

-   Agregar más consultas a los TableAdapters.

-   Agregar lógica de la validación a los eventos <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> de las tablas de datos en el conjunto de datos. Para obtener más información, consulte [validar datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md).

## <a name="see-also"></a>Vea también

- [Crear y configurar conjuntos de datos en Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Validar datos](../data-tools/validate-data-in-datasets.md)