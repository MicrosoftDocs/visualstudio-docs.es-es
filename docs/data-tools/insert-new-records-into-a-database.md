---
title: Insertar nuevos registros en una base de datos
ms.date: 11/04/2016
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: aaca23e6aa81fab958fc813fa5e2331f8906a562
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648314"
---
# <a name="insert-new-records-into-a-database"></a>Insertar nuevos registros en una base de datos

Para insertar nuevos registros en una base de datos, puede utilizar el método `TableAdapter.Update` o uno de los métodos DBDirect del TableAdapter (específicamente el método `TableAdapter.Insert`). Para obtener más información, consulte [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Si la aplicación no usa TableAdapters, puede utilizar objetos de comando (por ejemplo, <xref:System.Data.SqlClient.SqlCommand>) para insertar nuevos registros en la base de datos.

Si la aplicación usa conjuntos de datos para almacenar datos, use el método `TableAdapter.Update`. El método `Update` envía todos los cambios (actualizaciones, inserciones y eliminaciones) a la base de datos.

Si la aplicación usa objetos para almacenar datos, o si desea un control más preciso sobre la creación de nuevos registros en la base de datos, use el método `TableAdapter.Insert`.

Si el TableAdapter no tiene un método `Insert`, significa que el TableAdapter está configurado para usar procedimientos almacenados o que su propiedad `GenerateDBDirectMethods` está establecida en `false`. Intente establecer la propiedad `GenerateDBDirectMethods` del TableAdapter en `true` desde el **Diseñador de DataSet**y, a continuación, guarde el conjunto de contenido. Esto volverá a generar el TableAdapter. Si el TableAdapter todavía no tiene un método `Insert`, es probable que la tabla no proporcione suficiente información de esquema para distinguir entre las filas individuales (por ejemplo, puede que no haya ningún conjunto de claves principales en la tabla).

## <a name="insert-new-records-by-using-tableadapters"></a>Insertar nuevos registros mediante TableAdapters

Los TableAdapters proporcionan diferentes maneras de insertar nuevos registros en una base de datos, en función de los requisitos de la aplicación.

Si su aplicación usa conjuntos de datos para almacenar datos, puede agregar nuevos registros al <xref:System.Data.DataTable> deseado en el conjunto de datos y, a continuación, llamar al método `TableAdapter.Update`. El método `TableAdapter.Update` envía los cambios del <xref:System.Data.DataTable> a la base de datos (incluidos los registros modificados y eliminados).

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Para insertar nuevos registros en una base de datos mediante el método TableAdapter. Update

1. Agregue nuevos registros a la <xref:System.Data.DataTable> deseada creando un nuevo <xref:System.Data.DataRow> y agregándolo a la colección de <xref:System.Data.DataTable.Rows%2A>.

2. Una vez agregadas las nuevas filas a la <xref:System.Data.DataTable>, llame al método `TableAdapter.Update`. Puede controlar la cantidad de datos que se van a actualizar pasando en una <xref:System.Data.DataSet> completa, en una <xref:System.Data.DataTable>, en una matriz de <xref:System.Data.DataRow>s o en un solo <xref:System.Data.DataRow>.

   En el código siguiente se muestra cómo agregar un nuevo registro a un <xref:System.Data.DataTable> y, a continuación, llamar al método `TableAdapter.Update` para guardar la nueva fila en la base de datos. (En este ejemplo se utiliza la tabla `Region` de la base de datos Northwind).

   [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
   [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Para insertar nuevos registros en una base de datos mediante el método TableAdapter. Insert

Si la aplicación utiliza objetos para almacenar datos, puede utilizar el método `TableAdapter.Insert` para crear nuevas filas directamente en la base de datos. El método `Insert` acepta los valores individuales de cada columna como parámetros. Al llamar al método, se inserta un nuevo registro en la base de datos con los valores de parámetro pasados.

- Llame al método `Insert` del TableAdapter, pasando los valores de cada columna como parámetros.

En el procedimiento siguiente se muestra cómo utilizar el método `TableAdapter.Insert` para insertar filas. En este ejemplo se insertan datos en la tabla `Region` de la base de datos Northwind.

> [!NOTE]
> Si no tiene una instancia disponible, cree una instancia del TableAdapter que desee usar.

[!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
[!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>Insertar nuevos registros mediante objetos de comando

Puede insertar nuevos registros directamente en una base de datos mediante objetos de comando.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Para insertar nuevos registros en una base de datos mediante objetos de comando

- Cree un nuevo objeto de comando y, a continuación, establezca sus propiedades `Connection`, `CommandType` y `CommandText`.

En el ejemplo siguiente se muestra cómo insertar registros en una base de datos mediante el objeto de comando. Inserta datos en la tabla de `Region` de la base de datos Northwind.

[!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
[!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-security"></a>Seguridad de .NET

Debe tener acceso a la base de datos a la que está intentando conectarse, así como permiso para realizar inserciones en la tabla deseada.

## <a name="see-also"></a>Vea también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)