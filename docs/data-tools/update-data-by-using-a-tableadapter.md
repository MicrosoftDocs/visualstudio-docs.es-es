---
title: Actualizar datos mediante un TableAdapter
description: Actualice los datos de un conjunto de datos. Devolver los datos a la base de datos llamando al método Update de un TableAdapter.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: f3054c5c74c8844f780c3562327353fca164f1f4
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215648"
---
# <a name="update-data-by-using-a-tableadapter"></a>Actualizar datos mediante un TableAdapter

Una vez que los datos del conjunto de datos se han modificado y validado, puede devolver los datos actualizados a una base de datos llamando al `Update` método de un [TableAdapter](../data-tools/create-and-configure-tableadapters.md). El `Update` método actualiza una sola tabla de datos y ejecuta el comando correcto (insertar, actualizar o eliminar) en función de la <xref:System.Data.DataRow.RowState%2A> de cada fila de datos de la tabla. Cuando un conjunto de elementos tiene tablas relacionadas, Visual Studio genera una clase TableAdapterManager que se usa para realizar las actualizaciones. La clase TableAdapterManager garantiza que las actualizaciones se realicen en el orden correcto en función de las restricciones Foreign Key definidas en la base de datos. Cuando se usan controles enlazados a datos, la arquitectura de enlace de datos crea una variable miembro de la clase TableAdapterManager denominada tableAdapterManager.

> [!NOTE]
> Al intentar actualizar un origen de datos con el contenido de un conjunto de datos, puede obtener errores. Para evitar errores, se recomienda colocar el código que llama al método del adaptador `Update` dentro de un `try` / `catch` bloque.

El procedimiento exacto para actualizar un origen de datos puede variar en función de las necesidades empresariales, pero incluye los pasos siguientes:

1. Llame al método del adaptador `Update` en un `try` / `catch` bloque.

2. Si se detecta una excepción, buscar la fila de datos que causó el error.

3. Reconciliar el problema en la fila de datos (mediante programación si puede, o presentando la fila no válida al usuario para su modificación) y, a continuación, vuelva a intentar la actualización ( <xref:System.Data.DataRow.HasErrors%2A> , <xref:System.Data.DataTable.GetErrors%2A> ).

## <a name="save-data-to-a-database"></a>Guardar datos en una base de datos

Llame al `Update` método de un TableAdapter. Pase el nombre de la tabla de datos que contiene los valores que se van a escribir en la base de datos.

### <a name="to-update-a-database-by-using-a-tableadapter"></a>Para actualizar una base de datos mediante un TableAdapter

- Incluya el método del TableAdapter `Update` en un `try` / `catch` bloque. En el ejemplo siguiente se muestra cómo actualizar el contenido de la `Customers` tabla en `NorthwindDataSet` desde dentro de un `try` / `catch` bloque.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet9":::

## <a name="see-also"></a>Consulte también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
