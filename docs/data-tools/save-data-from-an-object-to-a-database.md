---
title: Guardar los datos de un objeto en una base de datos
description: Guardar datos de un objeto en una base de datos mediante las herramientas de conjunto de datos de Visual Studio. Vea cómo guardar nuevos registros, actualizar registros existentes y eliminar registros existentes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7ee06ef21be4076a1a0dee6319155144c468bafd
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436027"
---
# <a name="save-data-from-an-object-to-a-database"></a>Guardar los datos de un objeto en una base de datos

Puede guardar los datos de los objetos en una base de datos pasando los valores del objeto a uno de los métodos DBDirect del TableAdapter (por ejemplo, `TableAdapter.Insert` ). Para obtener más información, consulte [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Para guardar datos de una colección de objetos, recorra en iteración la colección de objetos (por ejemplo, un bucle for-Next) y envíe los valores de cada objeto a la base de datos mediante uno de los métodos de TableAdapter `DBDirect` .

De forma predeterminada, `DBDirect` los métodos se crean en un TableAdapter que se puede ejecutar directamente en la base de datos. Estos métodos se pueden llamar directamente y no requieren <xref:System.Data.DataSet> <xref:System.Data.DataTable> objetos o para conciliar los cambios a fin de enviar actualizaciones a una base de datos.

> [!NOTE]
> Al configurar un TableAdapter, la consulta principal debe proporcionar información suficiente para los `DBDirect` métodos que se van a crear. Por ejemplo, si un TableAdapter está configurado para consultar datos de una tabla que no tiene una columna de clave principal definida, no genera `DBDirect` métodos.

|Método de TableAdapter DBDirect|Descripción|
| - |-----------------|
|`TableAdapter.Insert`|Agrega nuevos registros a una base de datos y permite pasar valores de columna individuales como parámetros de método.|
|`TableAdapter.Update`|Actualiza los registros existentes en una base de datos. El `Update` método toma los valores de columna originales y nuevos como parámetros de método. Los valores originales se utilizan para buscar el registro original y los nuevos valores se usan para actualizar el registro.<br /><br /> El `TableAdapter.Update` método también se utiliza para reconciliar los cambios de un conjunto de datos en la base de datos tomando una <xref:System.Data.DataSet> ,, <xref:System.Data.DataTable> <xref:System.Data.DataRow> o una matriz de <xref:System.Data.DataRow> s como parámetros de método.|
|`TableAdapter.Delete`|Elimina los registros existentes de la base de datos en función de los valores de columna originales pasados como parámetros de método.|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>Para guardar nuevos registros de un objeto en una base de datos

- Cree los registros pasando los valores al `TableAdapter.Insert` método.

     En el ejemplo siguiente se crea un nuevo registro de cliente en la `Customers` tabla pasando los valores del `currentCustomer` objeto al `TableAdapter.Insert` método.

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>Para actualizar los registros existentes de un objeto a una base de datos

- Modifique los registros llamando al `TableAdapter.Update` método, pasando los nuevos valores para actualizar el registro y pasando los valores originales para buscar el registro.

    > [!NOTE]
    > El objeto debe mantener los valores originales para pasarlos al `Update` método. En este ejemplo se usan propiedades con un `orig` prefijo para almacenar los valores originales.

     En el siguiente ejemplo se actualiza un registro existente en la `Customers` tabla pasando los valores nuevos y originales del `Customer` objeto al `TableAdapter.Update` método.

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

## <a name="to-delete-existing-records-from-a-database"></a>Para eliminar los registros existentes de una base de datos

- Elimine los registros llamando al `TableAdapter.Delete` método y pasando los valores originales para buscar el registro.

    > [!NOTE]
    > El objeto debe mantener los valores originales para pasarlos al `Delete` método. En este ejemplo se usan propiedades con un `orig` prefijo para almacenar los valores originales.

     En el ejemplo siguiente se elimina un registro de la `Customers` tabla pasando los valores originales del `Customer` objeto al `TableAdapter.Delete` método.

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-security"></a>Seguridad de .NET

Debe tener permiso para realizar la selección `INSERT` , `UPDATE` o `DELETE` en la tabla de la base de datos.

## <a name="see-also"></a>Consulte también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
