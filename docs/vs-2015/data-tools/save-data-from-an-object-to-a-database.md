---
title: Guardar datos de un objeto en una base de datos | Microsoft Docs
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
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c1470c831177e74e7670d696b44fc2b0119a9a9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607456"
---
# <a name="save-data-from-an-object-to-a-database"></a>Guardar los datos de un objeto en una base de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede guardar los datos de los objetos en una base de datos pasando los valores del objeto a uno de los métodos DBDirect del TableAdapter (por ejemplo, `TableAdapter.Insert`).

 Para guardar datos de una colección de objetos, recorra en iteración la colección de objetos (por ejemplo, un bucle for-Next) y envíe los valores de cada objeto a la base de datos mediante uno de los métodos DBDirect del TableAdapter.

 De forma predeterminada, los métodos DBDirect se crean en un TableAdapter que se puede ejecutar directamente en la base de datos. Estos métodos se pueden llamar directamente y no requieren <xref:System.Data.DataSet> o <xref:System.Data.DataTable> objetos para conciliar los cambios a fin de enviar actualizaciones a una base de datos.

> [!NOTE]
> Al configurar un TableAdapter, la consulta principal debe proporcionar suficiente información para que se creen los métodos DBDirect. Por ejemplo, si un TableAdapter está configurado para consultar datos de una tabla que no tiene una columna de clave principal definida, no genera métodos DBDirect.

|Método de TableAdapter DBDirect|Descripción|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Agrega nuevos registros a una base de datos y permite pasar valores de columna individuales como parámetros de método.|
|`TableAdapter.Update`|Actualiza los registros existentes en una base de datos. El método `Update` toma los valores de columna originales y nuevos como parámetros de método. Los valores originales se utilizan para buscar el registro original y los nuevos valores se usan para actualizar el registro.<br /><br /> El método `TableAdapter.Update` también se utiliza para reconciliar los cambios de un conjunto de datos en la base de datos tomando un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> o una matriz de <xref:System.Data.DataRow>s como parámetros de método.|
|`TableAdapter.Delete`|Elimina los registros existentes de la base de datos en función de los valores de columna originales pasados como parámetros de método.|

### <a name="to-save-new-records-from-an-object-to-a-database"></a>Para guardar nuevos registros de un objeto en una base de datos

- Cree los registros pasando los valores al método `TableAdapter.Insert`.

     En el ejemplo siguiente se crea un nuevo registro de cliente en la tabla `Customers` pasando los valores del objeto `currentCustomer` al método `TableAdapter.Insert`.

     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Para actualizar los registros existentes de un objeto a una base de datos

- Modifique los registros llamando al método `TableAdapter.Update`, pasando los nuevos valores para actualizar el registro y pasando los valores originales para buscar el registro.

    > [!NOTE]
    > El objeto debe mantener los valores originales para pasarlos al método `Update`. En este ejemplo se usan propiedades con un prefijo `orig` para almacenar los valores originales.

     En el siguiente ejemplo se actualiza un registro existente en la tabla `Customers` pasando los valores nuevos y originales del objeto `Customer` al método `TableAdapter.Update`.

     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]

### <a name="to-delete-existing-records-from-a-database"></a>Para eliminar los registros existentes de una base de datos

- Elimine los registros llamando al método `TableAdapter.Delete` y pasando los valores originales para buscar el registro.

    > [!NOTE]
    > El objeto debe mantener los valores originales para pasarlos al método `Delete`. En este ejemplo se usan propiedades con un prefijo `orig` para almacenar los valores originales.

     En el ejemplo siguiente se elimina un registro de la tabla `Customers` pasando los valores originales del objeto `Customer` al método `TableAdapter.Delete`.

     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]

## <a name="net-framework-security"></a>Seguridad de .NET Framework
 Debe tener permiso para realizar las operaciones de inserción, actualización o eliminación seleccionadas en la tabla de la base de datos.

## <a name="see-also"></a>Vea también
 [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
