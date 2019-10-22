---
title: Rellenar conjuntos de valores mediante TableAdapters | Microsoft Docs
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
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5fd1dcf464b7628e345845ca9f371ef6de1efe88
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672348"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Rellenar conjuntos de datos mediante TableAdapters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un componente TableAdapter rellena un conjunto de datos con datos de la base de datos, basándose en una o más consultas o procedimientos almacenados especificados. Los TableAdapters también pueden realizar adiciones, actualizaciones y eliminaciones en la base de datos para conservar los cambios que se realicen en el conjunto de datos. También puede emitir comandos globales que no están relacionados con ninguna tabla específica.

> [!NOTE]
> Los diseñadores de Visual Studio generan los TableAdapters. Si va a crear conjuntos de valores mediante programación, use DataAdapter, que es una clase .NET Framework.

 Para obtener información detallada acerca de las operaciones de TableAdapter, puede ir directamente a uno de estos temas:

|Tema|Descripción|
|-----------|-----------------|
|[Crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md)|Cómo usar los diseñadores para crear y configurar TableAdapters|
|[Crear consultas parametrizadas de TableAdapter](../data-tools/create-parameterized-tableadapter-queries.md)|Cómo permitir que los usuarios proporcionen argumentos a procedimientos o consultas de TableAdapter|
|[Obtener acceso directamente a la base de datos con un TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Cómo usar los métodos DbDirect de TableAdapters|
|[Desactivar restricciones al llenar un conjunto de datos](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Cómo trabajar con restricciones Foreign Key al actualizar datos|
|[Cómo extender la funcionalidad de un TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Cómo agregar código personalizado a los TableAdapters|
|[Leer datos XML en un conjunto de datos](../data-tools/read-xml-data-into-a-dataset.md)|Cómo trabajar con XML|

## <a name="tableadapters-overview"></a>Información general de TableAdapters
 Los TableAdapters son componentes generados por el diseñador que se conectan a una base de datos, ejecutan consultas o procedimientos almacenados y rellenan su DataTable con los datos devueltos. Los TableAdapters también envían datos actualizados desde la aplicación a la base de datos. Puede ejecutar tantas consultas como desee en un TableAdapter, siempre y cuando devuelvan datos que se ajusten al esquema de la tabla a la que está asociado el TableAdapter. En el diagrama siguiente se muestra cómo interactúan los TableAdapters con las bases de datos y otros objetos de la memoria:

 ![Flujo de datos en una aplicación cliente](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")

 Aunque los TableAdapters están diseñados con el **Diseñador de DataSet**, las clases de TableAdapter no se generan como clases anidadas de <xref:System.Data.DataSet>. Se encuentran en espacios de nombres independientes que son específicos de cada conjunto de información. Por ejemplo, si tiene un conjunto de objetos denominado `NorthwindDataSet`, los TableAdapters asociados a <xref:System.Data.DataTable>s de la `NorthwindDataSet`rían en el espacio de nombres `NorthwindDataSetTableAdapters`. Para tener acceso a un TableAdapter determinado mediante programación, debe declarar una nueva instancia del TableAdapter. Por ejemplo:

 [!code-csharp[VbRaddataTableAdapters#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs#7)]
 [!code-vb[VbRaddataTableAdapters#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb#7)]

## <a name="associated-datatable-schema"></a>Esquema de DataTable asociado
 Cuando se crea un TableAdapter, se usa la consulta inicial o el procedimiento almacenado para definir el esquema del <xref:System.Data.DataTable> asociado del TableAdapter. Ejecute esta consulta o procedimiento almacenado inicial llamando al método `Fill` del TableAdapter (que rellena el <xref:System.Data.DataTable> asociado del TableAdapter). Cualquier cambio que se realice en la consulta principal del TableAdapter se refleja en el esquema de la tabla de datos asociada. Por ejemplo, al quitar una columna de la consulta principal, también se quita la columna de la tabla de datos asociada. Si alguna consulta adicional en el TableAdapter usa instrucciones SQL que devuelven columnas que no están en la consulta principal, el diseñador intenta sincronizar los cambios de la columna entre la consulta principal y las consultas adicionales. Para obtener más información, vea [Cómo: editar TableAdapters](https://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).

## <a name="tableadapter-update-commands"></a>Comandos de actualización de TableAdapter
 La funcionalidad de actualización de un TableAdapter depende de la cantidad de información disponible en la consulta principal en el Asistente de TableAdapter. Por ejemplo, los TableAdapter configurados para obtener valores de varias tablas (consultas JOIN), valores escalares, vistas o los resultados de funciones de agregado no se crean inicialmente con la capacidad de enviar actualizaciones a la base de datos subyacente. Sin embargo, puede configurar los comandos INSERT, UPDATE y DELETE manualmente en la ventana **propiedades** .

## <a name="tableadapter-queries"></a>consultas TableAdapter
 ![TableAdapter con varias consultas](../data-tools/media/tableadapter.gif "TableAdapter")

 Los TableAdapters pueden contener varias consultas para rellenar las tablas de datos asociadas. Puede definir tantas consultas para un TableAdapter como requiera la aplicación, con tal de que cada consulta devuelva datos que cumplan el mismo esquema que la tabla de datos asociada. Esta funcionalidad permite a un TableAdapter cargar resultados diferentes en función de criterios diferentes.

 Por ejemplo, si la aplicación contiene una tabla con nombres de cliente, puede crear una consulta que rellene la tabla con todos los nombres de clientes que comiencen con una letra determinada y otro que rellene la tabla con todos los clientes que se encuentran en el mismo estado. Para rellenar una tabla de `Customers` con los clientes en un estado determinado, puede crear una consulta de `FillByState` que tome un parámetro para el valor de estado de la manera siguiente: `SELECT * FROM Customers WHERE State = @State`. Ejecute la consulta llamando al método `FillByState` y pasando el valor del parámetro como este: `CustomerTableAdapter.FillByState("WA")`.

 Además de agregar consultas que devuelven datos del mismo esquema que la tabla de datos del TableAdapter, puede Agregar consultas que devuelvan valores escalares (únicos). Por ejemplo, una consulta que devuelve un recuento de clientes (`SELECT Count(*) From Customers`) es válida para un `CustomersTableAdapter,` a pesar de que los datos devueltos no se ajustan al esquema de la tabla.

## <a name="clearbeforefill-property"></a>Propiedad ClearBeforeFill
 De forma predeterminada, cada vez que se ejecuta una consulta para rellenar la tabla de datos de un TableAdapter, se borran los datos existentes y solo se cargan en la tabla los resultados de la consulta. Establezca la propiedad `ClearBeforeFill` del TableAdapter en `false` si desea agregar o combinar los datos devueltos de una consulta con los datos existentes en una tabla de datos. Independientemente de si borra los datos, deberá volver a enviar explícitamente las actualizaciones a la base de datos, si desea que se conserven. Por lo tanto, no olvide guardar los cambios realizados en los datos de la tabla antes de ejecutar otra consulta que llene la tabla. Para obtener más información, vea [actualizar datos mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>Herencia de TableAdapter
 Los TableAdapters amplían la funcionalidad de los adaptadores de datos estándar encapsulando una clase <xref:System.Data.Common.DataAdapter> configurada? qualifyHint = false & AutoUpgrade = true. De forma predeterminada, el TableAdapter hereda de la clase <xref:System.ComponentModel.Component> y no se puede convertir a la clase <xref:System.Data.Common.DataAdapter>. Al convertir un TableAdapter a la clase <xref:System.Data.Common.DataAdapter> se produce un error de <xref:System.InvalidCastException>? qualifyHint = false & AutoUpgrade = true. Para cambiar la clase base de un TableAdapter, puede escribir una clase que derive de <xref:System.ComponentModel.Component> en la propiedad de la **clase base** de TableAdapter en el **Diseñador de DataSet**.

## <a name="tableadapter-methods-and-properties"></a>Métodos y propiedades de TableAdapter
 La clase TableAdapter no forma parte de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Esto significa que no se puede buscar en la documentación o en el **Examinador de objetos**. Se crea en tiempo de diseño cuando se usa uno de los asistentes mencionados anteriormente. El nombre que se asigna a un TableAdapter al crearlo se basa en el nombre de la tabla con la que está trabajando. Por ejemplo, cuando se crea un TableAdapter basado en una tabla de una base de datos denominada `Orders`, el TableAdapter se denomina `OrdersTableAdapter`. Se puede cambiar el nombre de clase del TableAdapter utilizando la propiedad **Name** en el **Diseñador de DataSet**.

 A continuación se muestran los métodos y las propiedades de TableAdapters que se usan habitualmente:

|Miembro|Descripción|
|------------|-----------------|
|`TableAdapter.Fill`|Rellena la tabla de datos asociada del TableAdapter con los resultados del comando SELECT del TableAdapter.|
|`TableAdapter.Update`|Vuelve a enviar los cambios a la base de datos y devuelve un entero que representa el número de filas afectadas por la actualización. Para obtener más información, vea [actualizar datos mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Devuelve un nuevo <xref:System.Data.DataTable> que se rellena con datos.|
|`TableAdapter.Insert`|Crea una nueva fila en la tabla de datos. Para obtener más información, vea [Insertar nuevos registros en una base de datos](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|Determina si se vacía una tabla de datos antes de llamar a uno de los métodos `Fill`.|

## <a name="tableadapter-update-method"></a>Método de actualización de TableAdapter
 Los TableAdapter utilizan comandos de datos para leer y escribir en la base de datos. La consulta inicial `Fill` (Main) del TableAdapter se utiliza como base para crear el esquema de la tabla de datos asociada, así como los comandos `InsertCommand`, `UpdateCommand` y `DeleteCommand` que están asociados con el método `TableAdapter.Update`. La llamada al método `Update` de un TableAdapter ejecuta las instrucciones que se crearon cuando se configuró originalmente el TableAdapter, no una de las consultas adicionales que se agregaron con el **Asistente para configuración de consultas de TableAdapter**.

 Cuando utiliza un TableAdapter, éste realiza las mismas operaciones con los comandos que realizaría habitualmente. Por ejemplo, al llamar al método `Fill` del adaptador, el adaptador ejecuta el comando de datos en su propiedad `SelectCommand` y utiliza un lector de datos (por ejemplo, <xref:System.Data.SqlClient.SqlDataReader>) para cargar el conjunto de resultados en la tabla de datos. Del mismo modo, cuando se llama al método `Update` del adaptador, se ejecuta el comando adecuado (en las propiedades `UpdateCommand`, `InsertCommand` y `DeleteCommand`) para cada registro cambiado en la tabla de datos.

> [!NOTE]
> Si hay bastante información en la consulta principal, se crean los comandos `InsertCommand`, `UpdateCommand` y `DeleteCommand` de manera predeterminada cuando se genera el TableAdapter. Si la consulta principal del TableAdapter es más que una instrucción SELECT de una sola tabla, es posible que el diseñador no pueda generar `InsertCommand`, `UpdateCommand` y `DeleteCommand`. Si no se generan estos comandos, es posible que reciba un error al ejecutar el método `TableAdapter.Update`.

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods
 Además de `InsertCommand`, `UpdateCommand` y `DeleteCommand`, los TableAdapters se crean con métodos que se pueden ejecutar directamente en la base de datos. Se puede llamar a estos métodos (`TableAdapter.Insert`, `TableAdapter.Update` y `TableAdapter.Delete`) para manipular los datos directamente en la base de datos. Esto significa que puede llamar a estos métodos individuales desde el código en lugar de llamar a `TableAdapter.Update` para controlar las inserciones, las actualizaciones y las eliminaciones pendientes de la tabla de datos asociada.

 Si no desea crear estos métodos directos, establezca la propiedad **GenerateDbDirectMethods** de TableAdapter en `false` (en la ventana **propiedades** ). Las consultas adicionales que se agregan a TableAdapter son consultas independientes; no generan estos métodos.

## <a name="tableadapter-support-for-nullable-types"></a>Compatibilidad del objeto TableAdapter con los tipos que aceptan valores NULL
 Los TableAdapters admiten tipos que aceptan valores NULL `Nullable(Of T)` y `T?`. Para más información sobre los tipos que aceptan valores NULL en Visual Basic, vea [Tipos que admiten valores null](https://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6). Para obtener más información sobre los tipos que C#aceptan valores NULL en, vea [usar tipos que aceptan valores NULL](https://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28).

## <a name="security"></a>Seguridad
 Al utilizar comandos de datos con una propiedad `CommandType` establecida en <xref:System.Data.CommandType>, compruebe cuidadosamente la información que se envía desde un cliente antes de pasarla a la base de datos. Usuarios con malas intenciones podrían intentar enviar (inyectar) instrucciones de SQL modificadas o adicionales con el fin de obtener acceso no autorizado o dañar la base de datos. Antes de transferir la entrada del usuario a una base de datos, compruebe siempre que la información es válida. Un procedimiento recomendado es usar siempre consultas con parámetros o procedimientos almacenados cuando sea posible.

## <a name="see-also"></a>Vea también
 [Herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
