---
title: Información general sobre TableAdapter | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DataAccessor
- vbdata.Microsoft.VSDesigner.DataSource.DataAccessor
- TableAdapter
- vs.data.TableAdapter
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], table adapters
- TableAdapters, queries
- data [Visual Studio], TableAdapters
- query data in Visual Studio
- TableAdapter.GetData
- TableAdapter.Fill
- data [Visual Studio], datasets
- TableAdapters
- table adapters
ms.assetid: a87c46a0-52ab-432a-a864-9ba55069f9eb
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 1d5aabd4892011aa5c59abafc5d08840d1c8f5a8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580021"
---
# <a name="tableadapter-overview"></a>Información general sobre TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los TableAdapters son componentes generados por diseñador que se conectan a una base de datos, ejecutan consultas o procedimientos almacenados y completar su DataTable con los datos devueltos. Los TableAdapters también se utilizan para devolver los datos actualizados desde la aplicación a la base de datos. Puede tener tantas consultas como desee en un TableAdapter, siempre se devuelven los datos que se ajustan al esquema de la tabla que está asociado al TableAdapter. El siguiente diagrama muestra cómo interactúan los TableAdapters con bases de datos y otros objetos en memoria:  
  
 ![Flujo de datos en una aplicación cliente](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 Aunque los TableAdapters están diseñados con la **Diseñador de Dataset**, las clases TableAdapter generadas no se generan como clases anidadas de la <xref:System.Data.DataSet>. Se encuentran en un espacio de nombres separado y específico para cada conjunto de datos. Por ejemplo, si tiene un conjunto de datos denominado `NorthwindDataSet`, los TableAdapter asociados al control <xref:System.Data.DataTable> en `NorthwindDataSet` estarían en el espacio de nombres `NorthwindDataSetTableAdapters`. Para tener acceso a un TableAdapter determinado mediante programación, debe declarar una nueva instancia del TableAdapter. Por ejemplo:  
  
 [!code-csharp[VbRaddataTableAdapters#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs#7)]
 [!code-vb[VbRaddataTableAdapters#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb#7)]  
  
## <a name="associated-datatable-schema"></a>Esquema de DataTable asociado  
 Al crear un objeto TableAdapter, se utiliza la consulta inicial o el procedimiento almacenado para definir el esquema de <xref:System.Data.DataTable> asociado al TableAdapter. Ejecute esta consulta inicial o procedimiento almacenado mediante una llamada del TableAdapter `Fill` método (que rellena el TableAdapter asociado <xref:System.Data.DataTable>). Cualquier cambio realizado en la consulta principal del TableAdapter se refleja en el esquema de la tabla de datos asociada. Por ejemplo, al quitar una columna de la consulta principal, se quita la columna de la tabla de datos asociada. Si alguna consulta adicional del TableAdapter utiliza instrucciones SQL que devuelven columnas que no están en la consulta principal, el diseñador intentará sincronizar los cambios de columna entre la consulta principal y cualquier consulta adicional. Para obtener más información, consulte [Cómo: editar TableAdapters](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).  
  
## <a name="tableadapter-update-commands"></a>Comandos de actualización de TableAdapter  
 La funcionalidad de actualización de un objeto TableAdapter depende de la cantidad de información disponible, en función de la consulta principal proporcionada en el Asistente de TableAdapter. Por ejemplo, los TableAdapter configurados para obtener valores de varias tablas (consultas JOIN), valores escalares, vistas o los resultados de funciones de agregado no se crean inicialmente con la capacidad de enviar actualizaciones a la base de datos subyacente. Sin embargo, puede configurar los comandos INSERT, UPDATE y DELETE manualmente en el **propiedades** ventana.  
  
## <a name="tableadapter-queries"></a>Consultas de TableAdapter  
 ![TableAdapter con varias consultas](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 Los TableAdapter pueden contener varias consultas que rellenan las tablas de datos asociados. Puede definir tantas consultas para un TableAdapter como requiera la aplicación, con tal de que cada consulta devuelva datos que cumplan el mismo esquema que la tabla de datos asociada. De esta forma se habilita la carga de datos que satisface distintos criterios. Por ejemplo, si la aplicación contiene una tabla de clientes, puede crear una consulta para rellenar la tabla con todos los clientes cuyo nombre comience con una letra determinada y otra consulta para rellenar la tabla con todos los clientes del mismo estado o provincia. Para rellenar una tabla `Customers` con clientes de un estado concreto, puede crear una consulta `FillByState` que toma un parámetro para el valor del estado: `SELECT * FROM Customers WHERE State = @State`. Ejecute la consulta llamando al método `FillByState` y pasando un valor del parámetro como: `CustomerTableAdapter.FillByState("WA")`. Para obtener más información, consulte [Cómo: crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
 Además de consultas que devuelven datos del mismo esquema como tabla de datos del TableAdapter, también puede agregar consultas que devuelvan valores escalares (únicos). Por ejemplo, la creación de una consulta que devuelve un recuento de clientes (`SELECT Count(*) From Customers`) es una consulta válida para `CustomersTableAdapter`, aunque los datos devueltos no cumplan el esquema de la tabla.  
  
## <a name="clearbeforefill-property"></a>Propiedad ClearBeforeFill  
 De manera predeterminada, cada vez que ejecuta una consulta para rellenar la tabla de datos del TableAdapter, se borran los datos y sólo se cargan en la tabla los resultados de la consulta. Establezca la propiedad `ClearBeforeFill` del TableAdapter en `false` si desea agregar o combinar los datos devueltos de una consulta con los datos existentes en una tabla de datos. Sin tener en cuenta si borra los datos, es necesario enviar explícitamente las actualizaciones a la base de datos, si lo desea. Por tanto, recuerde guardar los cambios realizados en los datos de la tabla antes de ejecutar otra consulta que rellene la tabla. Para obtener más información, consulte [actualizar datos mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).  
  
## <a name="tableadapter-inheritance"></a>Herencia de TableAdapter  
 Los TableAdapter amplían la funcionalidad de los adaptadores de datos estándar encapsulando un control <xref:System.Data.Common.DataAdapter>. De manera predeterminada, el objeto TableAdapter hereda de <xref:System.ComponentModel.Component> y no se puede convertir a la clase <xref:System.Data.Common.DataAdapter>. Convertir un TableAdapter a un control <xref:System.Data.Common.DataAdapter> produce un <xref:System.InvalidCastException>. Para cambiar la clase base de un TableAdapter, puede escribir una clase que derive de <xref:System.ComponentModel.Component> en el **clase Base** propiedad del TableAdapter en el **Diseñador de Dataset**.  
  
## <a name="tableadapter-methods-and-properties"></a>Métodos y propiedades de TableAdapter  
 La clase TableAdapter no es parte de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], y por lo tanto, no puede buscarla en la documentación o **Examinador de objetos**. Se crea en tiempo de diseño cuando utiliza uno de los asistentes anteriormente mencionados. El nombre asignado a un TableAdapter en el momento de su creación se basa en el nombre de la tabla con la que está trabajando. Por ejemplo, si se crea un TableAdapter basado en una tabla de una base de datos denominada `Orders`, los TableAdapter se denominan en consecuencia `OrdersTableAdapter`. Se puede cambiar el nombre de clase del TableAdapter utilizando la **nombre** propiedad en el **Diseñador de Dataset**.  
  
 A continuación se muestran los métodos y propiedades de TableAdapter más utilizados:  
  
|Miembro|Descripción|  
|------------|-----------------|  
|`TableAdapter.Fill`|Rellena la tabla de datos asociada del TableAdapter con los resultados del comando SELECT del TableAdapter. Para obtener más información, consulte [Cómo: rellenar un conjunto de datos con datos](../data-tools/how-to-fill-a-dataset-with-data.md).|  
|`TableAdapter.Update`|Envía los cambios de vuelta a la base de datos y devuelve un entero que representa el número de filas a las que afecta la actualización. Para obtener más información, consulte [actualizar datos mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|  
|`TableAdapter.GetData`|Devuelve una nueva <xref:System.Data.DataTable> rellena con datos.|  
|`TableAdapter.Insert`|Crea una nueva fila en la tabla de datos. Para obtener más información, consulte [Cómo: agregar filas a un objeto DataTable](http://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).|  
|`TableAdapter.ClearBeforeFill`|Determina si se vacía una tabla de datos antes de llamar a uno de los métodos `Fill`.|  
  
## <a name="tableadapter-update-method"></a>Método de actualización de TableAdapter  
 Los TableAdapter utilizan comandos de datos para leer y escribir en la base de datos. La consulta (principal) `Fill` inicial de TableAdapter se utiliza como base para crear el esquema de la tabla de datos asociada, así como los comandos `InsertCommand`, `UpdateCommand` y `DeleteCommand` asociados al método `TableAdapter.Update`. Esto significa que una llamada a un TableAdapter `Update` método ejecuta las instrucciones creadas cuando el TableAdapter se configuró originalmente, y no una de las consultas adicionales se agrega con el **TableAdapter Query Configuration Wizard**.  
  
 Cuando utiliza un TableAdapter, éste realiza las mismas operaciones con los comandos que realizaría habitualmente. Por ejemplo, cuando se llama al método `Fill` del adaptador, éste ejecuta el comando de datos en la propiedad `SelectCommand` y utiliza un lector de datos (por ejemplo, <xref:System.Data.SqlClient.SqlDataReader>) para cargar el conjunto de resultados en la tabla de datos. De igual forma, cuando se llama al método `Update` del adaptador, se ejecuta el comando adecuado (en las propiedades `UpdateCommand`, `InsertCommand` y `DeleteCommand`) para cada registro modificado de la tabla de datos.  
  
> [!NOTE]
>  Si hay bastante información en la consulta principal, se crean los comandos `InsertCommand`, `UpdateCommand` y `DeleteCommand` de manera predeterminada cuando se genera el TableAdapter. Si la consulta principal de TableAdapter es más que una instrucción SELECT de una única tabla, es posible que el diseñador no pueda generar los comandos `InsertCommand`, `UpdateCommand` y `DeleteCommand`. Si no se han generado estos comandos, puede recibir un error al ejecutar el método `TableAdapter.Update`.  
  
## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods  
 Además de con los comandos `InsertCommand`, `UpdateCommand` y `DeleteCommand`, los TableAdapters se crean con métodos que se pueden ejecutar directamente en la base de datos. Se puede llamar a estos métodos (`TableAdapter.Insert`, `TableAdapter.Update` y `TableAdapter.Delete`) para manipular los datos directamente en la base de datos. Esto significa que puede llamar a estos métodos individuales de su código en lugar de llamar a TableAdapter.Update para controlar las inserciones, actualizaciones, y eliminar lo que está pendiente para la tabla de datos asociada.  
  
 Si no desea crear estos métodos directos, establezca el TableAdapter **GenerateDbDirectMethods** propiedad `false` (en el **propiedades** ventana). Las consultas adicionales agregadas al objeto TableAdapter son consultas independientes y no generan estos métodos.  
  
## <a name="tableadapter-support-for-nullable-types"></a>Compatibilidad del objeto TableAdapter con los tipos que aceptan valores NULL  
 Los TableAdapters admiten tipos que aceptan valores NULL `Nullable(Of T)` y `T?`. Para obtener más información sobre los tipos que aceptan valores NULL en Visual Basic, vea [los tipos de valor que acepta valores NULL](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6). Para obtener más información sobre los tipos que aceptan valores NULL en C#, vea [utilizar tipos que aceptan valores NULL](http://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28).  
  
## <a name="see-also"></a>Vea también  
 [Tutoriales de datos](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Cómo: Conectarse a los datos de una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Tutorial: Conectarse a datos en una base de datos (formularios Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)   
 [Preparar su aplicación para recibir datos](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Captura de datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edición de datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validación de datos](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Guardar datos](../data-tools/saving-data.md)