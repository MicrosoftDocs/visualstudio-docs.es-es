---
title: 'Cómo: guardar los cambios del conjunto de datos en una base de datos | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DbDataAdapter.Update
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], saving
- databases, updating
- updating datasets, writing changes to data source
ms.assetid: c9970150-b71b-4c9d-a355-5efb6b510dca
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 60bb855202cfb333820fe2292fedc0b31608c5c6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949024"
---
# <a name="how-to-save-dataset-changes-to-a-database"></a>Cómo: Guardar cambios de un conjunto de datos en una base de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Después de modificar y validar los datos en el conjunto de datos, probablemente desee devolver los datos actualizados a una base de datos. Para enviar los datos modificados a una base de datos, llame a la `Update` método de un [TableAdapter](../data-tools/tableadapter-overview.md) o adaptador de datos. El método `Update` del adaptador actualiza una sola tabla de datos y ejecuta el comando correcto (INSERT, UPDATE o DELETE) basándose en el <xref:System.Data.DataRow.RowState%2A> de cada fila de datos de la tabla.  
  
 Cuando se guardan datos en tablas relacionadas, Visual Studio proporciona un nuevo componente TableAdapterManager que permite guardar en el orden correcto basándose en las restricciones FOREIGN KEY definidas en la base de datos. Para obtener más información, consulte [información general de actualización jerárquica](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6).  
  
> [!NOTE]
>  Dado que intentar actualizar un origen de datos con el contenido de un conjunto de datos puede dar lugar a errores, debe colocar el código que llama el adaptador `Update` método dentro de un `try` / `catch` bloque.  
  
 Aunque el procedimiento exacto para actualizar un origen de datos varía dependiendo de las necesidades de la empresa, la aplicación debe incluir los siguientes pasos:  
  
1.  Ejecute el código que intenta enviar actualizaciones a la base de datos dentro de un `try` / `catch` bloque.  
  
2.  Si se detecta una excepción, buscar la fila de datos que causó el error. Para obtener más información, consulte [Cómo: localizar filas que tienen errores](http://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c).  
  
3.  Concilie el problema de la fila de datos (si es posible, mediante programación o presentando la fila incorrecta al usuario para que la modifique) y después vuelva a intentar la actualización (propiedad <xref:System.Data.DataRow.HasErrors%2A>, método <xref:System.Data.DataTable.GetErrors%2A>).  
  
## <a name="saving-data-to-a-database"></a>Guardar los datos en una base de datos  
 Llame al método `Update` de un objeto TableAdapter o adaptador de datos, pasando el nombre de la tabla de datos que contiene los valores que se van a escribir en la base de datos. Para obtener más información sobre cómo guardar datos de una sola tabla de datos a una base de datos, vea [Tutorial: guardar datos en una base de datos (tabla única)](http://msdn.microsoft.com/library/68befa96-7463-43e8-abcf-dc2f42ccd53d).  
  
#### <a name="to-update-a-database-with-a-dataset-using-a-tableadapter"></a>Para actualizar una base de datos con un conjunto de datos utilizando un objeto TableAdapter  
  
-   Encierre la `TableAdapter.Update` método dentro de un `try` / `catch` bloque. El ejemplo siguiente muestra cómo intentar una actualización con el contenido de la tabla `Customers` del conjunto de datos `NorthwindDataSet`.  
  
     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]  
  
#### <a name="to-update-a-database-with-a-dataset-using-a-data-adapter"></a>Para actualizar una base de datos con un conjunto de datos utilizando un adaptador de datos  
  
-   Encierre la `DataAdapter.Update` método dentro de un `try` / `catch` bloque. El ejemplo siguiente muestra cómo intentar una actualización en un origen de datos con el contenido de `Table1` en `DataSet1`.  
  
     [!code-csharp[VbRaddataSaving#26](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#26)]
     [!code-vb[VbRaddataSaving#26](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#26)]  
  
## <a name="updating-two-related-tables-in-a-dataset"></a>Actualizar dos tablas relacionadas de un conjunto de datos  
 Al actualizar tablas relacionadas en un conjunto de datos, es importante hacerlo en el orden correcto para reducir la posibilidad de infringir las restricciones de integridad referencial. El orden de ejecución de los comandos también seguirá los índices de <xref:System.Data.DataRowCollection> en el conjunto de datos. Para evitar que se produzcan errores de integridad de datos, se recomienda actualizar la base de datos en el siguiente orden:  
  
1. Tabla secundaria: eliminar registros.  
  
2. Tabla principal: insertar, actualizar y eliminar registros.  
  
3. Tabla secundaria: insertar y actualizar registros.  
  
   Para obtener información detallada sobre cómo guardar los datos de varias tablas, vea [guardar datos en una base de datos (varias tablas)](../data-tools/save-data-to-a-database-multiple-tables.md).  
  
   Si va a actualizar dos o más tablas relacionadas, debe incluir toda la lógica de actualización dentro de una transacción. Una transacción es un proceso que asegura que todos los cambios relacionados con una base de datos son correctos antes de confirmar cualquier cambio. Para obtener más información, vea [transacciones y simultaneidad](http://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b).  
  
#### <a name="to-update-two-related-tables-using-a-tableadapter"></a>Para actualizar dos tablas relacionadas mediante un objeto TableAdapter  
  
1.  Cree tres <xref:System.Data.DataTable>s temporales para contener los registros que no son iguales.  
  
2.  Llame a la `Update` método para cada subconjunto de filas desde dentro un `try` / `catch` bloque. Si se producen errores de actualización, la acción sugerida es separarlos y resolverlos.  
  
3.  Confirmar los cambios desde el conjunto de datos en la base de datos.  
  
4.  Elimine las tablas de datos temporales para liberar los recursos.  
  
     [!code-csharp[VbRaddataSaving#27](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#27)]
     [!code-vb[VbRaddataSaving#27](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#27)]  
  
#### <a name="to-update-two-related-tables-using-a-data-adapter"></a>Para actualizar dos tablas relacionadas mediante un adaptador de datos  
  
-   Llame al método `Update` de cada adaptador de datos.  
  
     En el ejemplo siguiente, se muestra cómo actualizar un origen de datos con un conjunto de datos que contiene tablas relacionadas. Para seguir el orden anterior, se crean tres tablas <xref:System.Data.DataTable>s temporales donde se incluirán los registros que no son iguales. El `Update` método se llamará para cada subconjunto de filas desde dentro un `try` / `catch` bloque. Si se producen errores de actualización, la acción sugerida es separarlos y resolverlos. Después, el conjunto de datos confirma los cambios. Por último, las tablas de datos provisionales se eliminan para liberar los recursos.  
  
     [!code-csharp[VbRaddataSaving#28](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#28)]
     [!code-vb[VbRaddataSaving#28](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Vea también  
 [Tutoriales de datos](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar su aplicación para recibir datos](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Captura de datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edición de datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validación de datos](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Guardar datos](../data-tools/saving-data.md)