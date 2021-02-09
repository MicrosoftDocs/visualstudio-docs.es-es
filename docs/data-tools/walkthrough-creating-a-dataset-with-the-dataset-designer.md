---
title: Cree un conjunto de DataSet con el Diseñador de DataSet
description: En este tutorial, creará un conjunto de DataSet mediante el Diseñador de DataSet. Entender el proceso de creación de un nuevo proyecto y de agregarle un nuevo elemento de conjunto de elementos.
ms.custom: SEO-VS-2020
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: b1fe1d75673dc47f423cf398118230cd1530def0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866234"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>Tutorial: crear un conjunto de DataSet con el Diseñador de DataSet

En este tutorial, creará un conjunto de DataSet mediante el **Diseñador de DataSet**. El artículo le guía por el proceso de crear un nuevo proyecto y agregarle un nuevo elemento de **conjunto** de elementos. Aprenderá a crear tablas basadas en tablas en una base de datos sin usar un asistente.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial se usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1. Si no tiene SQL Server Express LocalDB, instálelo desde la [Página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)o a través de la **instalador de Visual Studio**. En el Instalador de Visual Studio, SQL Server Express LocalDB se puede instalar como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** , o como un componente individual.

2. Instale la base de datos de ejemplo Northwind siguiendo estos pasos:

    1. En Visual Studio, abra la ventana **Explorador de objetos de SQL Server** . (Explorador de objetos de SQL Server se instala como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** en el instalador de Visual Studio). Expanda el nodo **SQL Server** . Haga clic con el botón secundario en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copie el [script de Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el portapapeles. Este script T-SQL crea la base de datos Northwind desde cero y la rellena con datos.

    3. Pegue el script T-SQL en el editor de consultas y, a continuación, elija el botón **Ejecutar** .

       Tras un breve período de tiempo, la consulta termina de ejecutarse y se crea la base de datos Northwind.

## <a name="create-a-new-windows-forms-application-project"></a>Crear un nuevo proyecto de aplicación de Windows Forms

1. En Visual Studio, en el menú **Archivo**, seleccione **Nuevo** > **Proyecto**.

2. Expanda **Visual C#** o **Visual Basic** en el panel izquierdo y, a continuación, seleccione **escritorio de Windows**.

3. En el panel central, seleccione el tipo de proyecto **Windows Forms aplicación** .

4. Asigne al proyecto el nombre **DatasetDesignerWalkthrough** y, a continuación, elija **Aceptar**.

     Visual Studio agrega el proyecto a **Explorador de soluciones** y muestra un nuevo formulario en el diseñador.

## <a name="add-a-new-dataset-to-the-application"></a>Agregar un nuevo conjunto de nuevos a la aplicación

1. En el menú **Proyecto**, seleccione **Agregar nuevo elemento**.

     Aparecerá el cuadro de diálogo **Agregar nuevo elemento** .

2. En el panel izquierdo, seleccione datos y, a continuación, seleccione **conjunto** de **datos** en el panel central.

3. Asigne al conjunto de los nombres **NorthwindDataSet** y, a continuación, elija **Agregar**.

     Visual Studio agrega un archivo denominado **NorthwindDataSet. xsd** al proyecto y lo abre en el **Diseñador de DataSet**.

## <a name="create-a-data-connection-in-server-explorer"></a>Crear una conexión de datos en Explorador de servidores

1. En el menú **Ver**, haga clic en el **Explorador de servidores**.

2. En el **Explorador de servidores**, haga clic en el botón **Conectar con base de datos**.

3. Crear una conexión a la base de datos de ejemplo Northwind.

## <a name="create-the-tables-in-the-dataset"></a>Crear las tablas en el conjunto de

En esta sección se explica cómo agregar tablas al conjunto de DataSet.

### <a name="to-create-the-customers-table"></a>Para crear la tabla Customers

1. Expanda la conexión de datos que creó en el **Explorador de servidores** y, a continuación, expanda el nodo **Tablas**.

2. Arrastre la tabla **Customers** desde el **Explorador de servidores** al **Diseñador de DataSet**.

     Se agregan una tabla de datos **Customers** y **CustomersTableAdapter** al conjunto de datos.

### <a name="to-create-the-orders-table"></a>Para crear la tabla Orders

- Arrastre la tabla **Orders** desde el **Explorador de servidores** al **Diseñador de DataSet**.

     Una tabla de datos **Orders**, **OrdersTableAdapter** y una relación de datos entre las tablas **Customers** y **Orders** se agregan al conjunto de datos.

### <a name="to-create-the-orderdetails-table"></a>Para crear la tabla OrderDetails

- Arrastre la tabla **Order Details** desde el **Explorador de servidores** hasta el **Diseñador de DataSet**.

     Una tabla de datos **Order Details** , **OrderDetailsTableAdapter**, y una relación de datos entre las tablas **Orders** y **OrderDetails** se agregan al conjunto de datos.

## <a name="next-steps"></a>Pasos siguientes

- Guarde el conjunto de datos.

- Seleccione elementos en la ventana **Orígenes de datos** y arrástrelos a un formulario. Para obtener más información, vea [enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

- Agregar más consultas a los TableAdapters.

- Agregar lógica de la validación a los eventos <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> de las tablas de datos en el conjunto de datos. Para obtener más información, vea [Validate Data in datasets](../data-tools/validate-data-in-datasets.md).

## <a name="see-also"></a>Vea también

- [Crear y configurar conjuntos de datos en Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Validación de datos](../data-tools/validate-data-in-datasets.md)
