---
title: Insertar nuevos registros en una base de datos
description: Inserte nuevos registros en una base de datos mediante el método TableAdapter. Update, uno de los métodos DBDirect de TableAdapter o los objetos de comando.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3586cf45e152cd8a0149140556916b11544a00bb
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436281"
---
# <a name="insert-new-records-into-a-database"></a>Insertar nuevos registros en una base de datos

Para insertar nuevos registros en una base de datos, puede usar el `TableAdapter.Update` método o uno de los métodos DbDirect del TableAdapter (en concreto, el `TableAdapter.Insert` método). Para obtener más información, consulte [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Si la aplicación no usa TableAdapters, puede utilizar objetos de comando (por ejemplo,  <xref:System.Data.SqlClient.SqlCommand> ) para insertar nuevos registros en la base de datos.

Si la aplicación usa conjuntos de datos para almacenar datos, use el `TableAdapter.Update` método. El `Update` método envía todos los cambios (actualizaciones, inserciones y eliminaciones) a la base de datos.

Si la aplicación utiliza objetos para almacenar datos, o si desea tener un mayor control sobre la creación de nuevos registros en la base de datos, use el `TableAdapter.Insert` método.

Si el TableAdapter no tiene un `Insert` método, significa que el TableAdapter está configurado para usar procedimientos almacenados o su `GenerateDBDirectMethods` propiedad está establecida en `false` . Intente establecer la propiedad del TableAdapter `GenerateDBDirectMethods` en `true` desde el **Diseñador de DataSet** y, a continuación, guarde el conjunto de contenido. Esto volverá a generar el TableAdapter. Si el TableAdapter todavía no tiene un `Insert` método, es probable que la tabla no proporcione suficiente información de esquema para distinguir entre las filas individuales (por ejemplo, puede que no haya ninguna clave principal establecida en la tabla).

## <a name="insert-new-records-by-using-tableadapters"></a>Insertar nuevos registros mediante TableAdapters

Los TableAdapters proporcionan diferentes maneras de insertar nuevos registros en una base de datos, en función de los requisitos de la aplicación.

Si la aplicación utiliza conjuntos de datos para almacenar datos, puede agregar nuevos registros a los que desee <xref:System.Data.DataTable> en el conjunto de datos y, a continuación, llamar al `TableAdapter.Update` método. El `TableAdapter.Update` método envía cualquier cambio en la <xref:System.Data.DataTable> base de datos (incluidos los registros modificados y eliminados).

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Para insertar nuevos registros en una base de datos mediante el método TableAdapter. Update

1. Agregue nuevos registros al deseado <xref:System.Data.DataTable> creando un nuevo <xref:System.Data.DataRow> y agregándolo a la <xref:System.Data.DataTable.Rows%2A> colección.

2. Una vez agregadas las nuevas filas a <xref:System.Data.DataTable> , llame al `TableAdapter.Update` método. Puede controlar la cantidad de datos que se van a actualizar pasando en todo <xref:System.Data.DataSet> , una <xref:System.Data.DataTable> matriz de <xref:System.Data.DataRow> s o en un único <xref:System.Data.DataRow> .

   En el código siguiente se muestra cómo agregar un nuevo registro a <xref:System.Data.DataTable> y, a continuación, llamar al `TableAdapter.Update` método para guardar la nueva fila en la base de datos. (En este ejemplo se utiliza la `Region` tabla de la base de datos Northwind).

   [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
   [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Para insertar nuevos registros en una base de datos mediante el método TableAdapter. Insert

Si la aplicación utiliza objetos para almacenar datos, puede utilizar el `TableAdapter.Insert` método para crear nuevas filas directamente en la base de datos. El `Insert` método acepta los valores individuales de cada columna como parámetros. Al llamar al método, se inserta un nuevo registro en la base de datos con los valores de parámetro pasados.

- Llame al método del TableAdapter `Insert` , pasando los valores de cada columna como parámetros.

En el procedimiento siguiente se muestra cómo utilizar el `TableAdapter.Insert` método para insertar filas. En este ejemplo se insertan datos en la `Region` tabla de la base de datos Northwind.

> [!NOTE]
> Si no tiene una instancia disponible, cree una instancia del TableAdapter que desee usar.

[!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
[!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>Insertar nuevos registros mediante objetos de comando

Puede insertar nuevos registros directamente en una base de datos mediante objetos de comando.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Para insertar nuevos registros en una base de datos mediante objetos de comando

- Cree un nuevo objeto de comando y, a continuación, establezca sus `Connection` `CommandType` propiedades, y `CommandText` .

En el ejemplo siguiente se muestra cómo insertar registros en una base de datos mediante el objeto de comando. Inserta datos en la `Region` tabla de la base de datos Northwind.

[!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
[!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-security"></a>Seguridad de .NET

Debe tener acceso a la base de datos a la que está intentando conectarse, así como permiso para realizar inserciones en la tabla deseada.

## <a name="see-also"></a>Consulte también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
