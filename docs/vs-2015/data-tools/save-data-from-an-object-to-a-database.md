---
title: Guardar datos de un objeto en una base de datos | Documentos de Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c079d3f85dbab87e30edb059c76202dd727f715c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425063"
---
# <a name="save-data-from-an-object-to-a-database"></a>Guardar los datos de un objeto en una base de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede guardar datos de objetos de una base de datos pasando los valores desde el objeto a uno de los métodos DBDirect del TableAdapter (por ejemplo, `TableAdapter.Insert`).
  
 Para guardar los datos de una colección de objetos, recorra en iteración la colección de objetos (por ejemplo, un bucle for-next) y envíe los valores para cada objeto a la base de datos mediante uno de los métodos DBDirect del TableAdapter.  
  
 De forma predeterminada, los métodos DBDirect se crean en un TableAdapter que se puede ejecutar directamente en la base de datos. Estos métodos pueden llamarse directamente y no requieren <xref:System.Data.DataSet> o <xref:System.Data.DataTable> objetos para conciliar los cambios con el fin de enviar actualizaciones a una base de datos.  
  
> [!NOTE]
> Cuando se configura un TableAdapter, la consulta principal debe proporcionar suficiente información para los métodos DBDirect que se va a crear. Por ejemplo, si un TableAdapter se configura para consultar los datos de una tabla que no tiene una columna de clave principal definida, no genera DBDirect (métodos).  
  
|Método de TableAdapter DBDirect|Descripción|  
|----------------------------------|-----------------|  
|`TableAdapter.Insert`|Agrega nuevos registros a una base de datos y le permite pasar valores de columna individuales como parámetros de método.|  
|`TableAdapter.Update`|Actualizaciones de registros existentes en una base de datos. El `Update` método toma los valores de columna originales y nuevos como parámetros de método. Los valores originales se usan para localizar el registro original y los nuevos valores se utilizan para actualizar el registro.<br /><br /> El `TableAdapter.Update` método también se utiliza para conciliar los cambios en un conjunto de datos a la base de datos realizando una <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, o una matriz de <xref:System.Data.DataRow>como parámetros de método.|  
|`TableAdapter.Delete`|Elimina registros existentes de la base de datos según los valores de columna original pasados como parámetros de método.|  
  
### <a name="to-save-new-records-from-an-object-to-a-database"></a>Para guardar los nuevos registros de un objeto a una base de datos  
  
- Cree los registros pasando los valores para el `TableAdapter.Insert` método.  
  
     En el ejemplo siguiente se crea un nuevo registro de cliente en el `Customers` tabla pasando los valores de la `currentCustomer` de objeto para el `TableAdapter.Insert` método.  
  
     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]  
  
### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Para actualizar registros existentes de un objeto a una base de datos  
  
- Modificar los registros mediante una llamada a la `TableAdapter.Update` método, pasando los nuevos valores para actualizar el registro y pasar los valores originales para buscar el registro.  
  
    > [!NOTE]
    > El objeto necesita mantener los valores originales para pasarlos a la `Update` método. En este ejemplo usa las propiedades con un `orig` prefijo para almacenar los valores originales.  
  
     En el ejemplo siguiente se actualiza un registro existente en el `Customers` tabla pasando los valores nuevos y originales de la `Customer` de objeto para el `TableAdapter.Update` método.  
  
     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]  
  
### <a name="to-delete-existing-records-from-a-database"></a>Para eliminar registros existentes de una base de datos  
  
- Eliminar los registros mediante una llamada a la `TableAdapter.Delete` método y pasando los valores originales para buscar el registro.  
  
    > [!NOTE]
    > El objeto necesita mantener los valores originales para pasarlos a la `Delete` método. En este ejemplo usa las propiedades con un `orig` prefijo para almacenar los valores originales.  
  
     En el ejemplo siguiente se elimina un registro de la `Customers` tabla pasando los valores originales de la `Customer` de objeto para el `TableAdapter.Delete` método.  
  
     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 Debe tener permiso para realizar la operación INSERT, UPDATE o DELETE en la tabla en la base de datos.  
  
## <a name="see-also"></a>Vea también  
 [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
