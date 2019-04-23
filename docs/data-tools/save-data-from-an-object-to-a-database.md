---
title: Guardar los datos de un objeto en una base de datos
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c672103c0426f2d49eb47aa41014ee13ff0ecae9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60073444"
---
# <a name="save-data-from-an-object-to-a-database"></a>Guardar los datos de un objeto en una base de datos

Puede guardar datos de objetos de una base de datos pasando los valores desde el objeto a uno de los métodos DBDirect del TableAdapter (por ejemplo, `TableAdapter.Insert`). Para obtener más información, consulte [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Para guardar los datos de una colección de objetos, recorra en iteración la colección de objetos (por ejemplo, un bucle for-next) y envíe los valores para cada objeto a la base de datos mediante uno de lo TableAdapter `DBDirect` métodos.

De forma predeterminada, `DBDirect` métodos se crean en un TableAdapter que se puede ejecutar directamente en la base de datos. Estos métodos pueden llamarse directamente y no requieren <xref:System.Data.DataSet> o <xref:System.Data.DataTable> objetos para conciliar los cambios con el fin de enviar actualizaciones a una base de datos.

> [!NOTE]
> Cuando se configura un TableAdapter, la consulta principal debe proporcionar suficiente información para el `DBDirect` métodos que se va a crear. Por ejemplo, si un TableAdapter se configura para consultar los datos de una tabla que no tiene una columna de clave principal definida, no genera `DBDirect` métodos.

|Método de TableAdapter DBDirect|Descripción|
| - |-----------------|
|`TableAdapter.Insert`|Agrega nuevos registros a una base de datos y le permite pasar valores de columna individuales como parámetros de método.|
|`TableAdapter.Update`|Actualizaciones de registros existentes en una base de datos. El `Update` método toma los valores de columna originales y nuevos como parámetros de método. Los valores originales se usan para localizar el registro original y los nuevos valores se utilizan para actualizar el registro.<br /><br /> El `TableAdapter.Update` método también se utiliza para conciliar los cambios en un conjunto de datos a la base de datos realizando una <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, o una matriz de <xref:System.Data.DataRow>como parámetros de método.|
|`TableAdapter.Delete`|Elimina registros existentes de la base de datos según los valores de columna original pasados como parámetros de método.|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>Para guardar los nuevos registros de un objeto a una base de datos

- Cree los registros pasando los valores para el `TableAdapter.Insert` método.

     En el ejemplo siguiente se crea un nuevo registro de cliente en el `Customers` tabla pasando los valores de la `currentCustomer` de objeto para el `TableAdapter.Insert` método.

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>Para actualizar registros existentes de un objeto a una base de datos

- Modificar los registros mediante una llamada a la `TableAdapter.Update` método, pasando los nuevos valores para actualizar el registro y pasar los valores originales para buscar el registro.

    > [!NOTE]
    > El objeto necesita mantener los valores originales para pasarlos a la `Update` método. En este ejemplo usa las propiedades con un `orig` prefijo para almacenar los valores originales.

     En el ejemplo siguiente se actualiza un registro existente en el `Customers` tabla pasando los valores nuevos y originales de la `Customer` de objeto para el `TableAdapter.Update` método.

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

## <a name="to-delete-existing-records-from-a-database"></a>Para eliminar registros existentes de una base de datos

- Eliminar los registros mediante una llamada a la `TableAdapter.Delete` método y pasando los valores originales para buscar el registro.

    > [!NOTE]
    > El objeto necesita mantener los valores originales para pasarlos a la `Delete` método. En este ejemplo usa las propiedades con un `orig` prefijo para almacenar los valores originales.

     En el ejemplo siguiente se elimina un registro de la `Customers` tabla pasando los valores originales de la `Customer` de objeto para el `TableAdapter.Delete` método.

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-framework-security"></a>seguridad en .NET Framework

Debe tener permiso para realizar seleccionado `INSERT`, `UPDATE`, o `DELETE` en la tabla en la base de datos.

## <a name="see-also"></a>Vea también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)