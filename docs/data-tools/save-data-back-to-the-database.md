---
title: Guardar los datos de nuevo en la base de datos
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], validating data
- data validation, datasets
- data [Visual Studio], saving
- row version
- updating datasets, constraints
- datasets [Visual Basic], about datasets
- datasets [Visual Basic], merging
- updates, constraints in datasets
- saving data, about saving data
- datasets [Visual Basic], constraints
- TableAdapters
ms.assetid: afe6cb8a-dc6a-428b-b07b-903ac02c890b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: ef3d2b5fd9f5172a79daef185d7153905976ba88
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989140"
---
# <a name="save-data-back-to-the-database"></a>Guardar los datos de nuevo en la base de datos

El conjunto de datos es una copia en memoria de datos. Si modifica datos, es una buena práctica para guardar los cambios en la base de datos. Para ello en uno de tres maneras:

- Llamando a uno de los `Update` métodos de un TableAdapter

- Llamando a uno de `DBDirect` métodos de TableAdapter

- Mediante una llamada a la `UpdateAll` método TableAdapterManager que Visual Studio genera automáticamente cuando el conjunto de datos contiene tablas que están relacionadas con otras tablas del conjunto de datos

Al enlazar datos las tablas del conjunto de datos a controles en una página de formulario de Windows o en XAML, la arquitectura de enlace de datos hace todo el trabajo por usted.

Si está familiarizado con los TableAdapters, puede ir directamente a uno de estos temas:

|Tema|Descripción|
|-----------|-----------------|
|[Insertar nuevos registros en una base de datos](../data-tools/insert-new-records-into-a-database.md)|Cómo realizar actualizaciones e inserta mediante objetos TableAdapters o comando|
|[Actualizar datos mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)|Cómo realizar las actualizaciones con los TableAdapters|
|[Actualización jerárquica](../data-tools/hierarchical-update.md)|Cómo realizar actualizaciones desde un conjunto de datos con dos o más tablas relacionadas|
|[Tratar las excepciones de simultaneidad](../data-tools/handle-a-concurrency-exception.md)|Cómo controlar las excepciones cuando dos usuarios intentan cambiar los mismos datos en una base de datos al mismo tiempo|
|[Cómo: Guardado de los datos mediante una transacción](../data-tools/save-data-by-using-a-transaction.md)|Cómo guardar datos en una transacción utilizando el sistema. Espacio de nombres de las transacciones y un objeto TransactionScope|
|[Guardar datos en una transacción](../data-tools/save-data-in-a-transaction.md)|Tutorial que crea una aplicación de Windows Forms para mostrar guardar datos en una base de datos dentro de una transacción|
|[Guardar datos en una base de datos (varias tablas)](../data-tools/save-data-to-a-database-multiple-tables.md)|Cómo editar los registros y guardar los cambios en varias tablas en la base de datos|
|[Guardar los datos de un objeto en una base de datos](../data-tools/save-data-from-an-object-to-a-database.md)|Cómo pasar datos a partir de un objeto que no está en un conjunto de datos a una base de datos mediante el uso de un método DbDirect de TableAdapter|
|[Guardar datos con los métodos DBDirect de un TableAdapter](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|Cómo utilizar el TableAdapter para enviar consultas SQL directamente a la base de datos|
|[Guardar un conjunto de datos como XML](../data-tools/save-a-dataset-as-xml.md)|Cómo guardar un conjunto de datos en un documento XML|

## <a name="two-stage-updates"></a>Actualizaciones en dos fases

Actualización de un origen de datos es un proceso de dos pasos. El primer paso es actualizar el conjunto de datos con los registros eliminados, los registros cambiados o nuevos registros. Si la aplicación nunca envía esos cambios en el origen de datos, a continuación, habrá terminado con la actualización.

Si envía los cambios a la base de datos, un segundo paso es necesario. Si no está utilizando los controles enlazados a datos, debe llamar manualmente a la `Update` método del mismo TableAdapter (o adaptador de datos) que usa para rellenar el conjunto de datos. Sin embargo, también puede utilizar adaptadores diferentes, por ejemplo, para mover datos desde un origen de datos a otro o para actualizar varios orígenes de datos. Si no está usando el enlace de datos y está guardando los cambios para las tablas relacionadas, deberá instancias manualmente de una variable de la autogenerado `TableAdapterManager` clase y, a continuación, llame a su `UpdateAll` método.

![Diagrama conceptual de las actualizaciones del conjunto de datos](../data-tools/media/vbdatasetupdates.gif)

Un conjunto de datos contiene colecciones de las tablas que contienen una colección de filas. Si tiene previsto actualizar un origen de datos subyacente más adelante, debe utilizar los métodos en el `DataTable.DataRowCollection` propiedad al agregar o quitar filas. Esos métodos realizan el seguimiento de cambios que se necesita para actualizar el origen de datos. Si se llama a la `RemoveAt` colección en la propiedad de filas, la eliminación no se comunican a la base de datos.

## <a name="merge-datasets"></a>Combinar conjuntos de datos

Puede actualizar el contenido de un conjunto de datos por *combinación* con otro conjunto de datos. Esto implica copiar el contenido de un *origen* conjunto de datos en el conjunto de datos que realiza la llamada (denominados el *destino* conjunto de datos). Cuando se fusionan mediante combinación conjuntos de datos, los registros nuevos del conjunto de datos de origen se agregan al conjunto de datos de destino. Asimismo, las columnas adicionales del conjunto de datos de origen se agregan al conjunto de datos de destino. Combinar conjuntos de datos es útil cuando tiene un conjunto de datos local y recibe un segundo conjunto de datos desde otra aplicación. También es útil cuando reciba un segundo conjunto de datos de un componente como un servicio web XML, o cuando sea necesario integrar datos de varios conjuntos de datos.

Cuando se mezclan los conjuntos de datos, puede pasar un argumento booleano (`preserveChanges`) que indica la <xref:System.Data.DataSet.Merge%2A> método si desea conservar las modificaciones existentes del conjunto de datos de destino. Debido a que los conjuntos de datos mantienen varias versiones de los registros, es importante recordar que se está combinado más de una versión de los registros. En la tabla siguiente se muestra cómo se combina un registro en dos conjuntos de datos:

|DataRowVersion|Conjunto de datos de destino|Conjunto de datos de origen|
| - | - | - |
|Original|James Wilson|James C. Wilson|
|Current|Jim Wilson|James C. Wilson|

Una llamada a la <xref:System.Data.DataSet.Merge%2A> método en la tabla anterior con `preserveChanges=false targetDataset.Merge(sourceDataset)` da como resultado los datos siguientes:

|DataRowVersion|Conjunto de datos de destino|Conjunto de datos de origen|
| - | - | - |
|Original|James C. Wilson|James C. Wilson|
|Current|James C. Wilson|James C. Wilson|

Una llamada a la <xref:System.Data.DataSet.Merge%2A> método con `preserveChanges = true targetDataset.Merge(sourceDataset, true)` da como resultado los datos siguientes:

|DataRowVersion|Conjunto de datos de destino|Conjunto de datos de origen|
| - | - | - |
|Original|James C. Wilson|James C. Wilson|
|Current|Jim Wilson|James C. Wilson|

> [!CAUTION]
> En el `preserveChanges = true` escenario, si la <xref:System.Data.DataSet.RejectChanges%2A> se llama al método en un registro en el conjunto de datos de destino y, después, vuelve a los datos originales de la *origen* conjunto de datos. Esto significa que si se intenta actualizar el origen de datos original con el conjunto de datos de destino, es posible que no pueda encontrar la fila original para actualizar. Puede evitar que una infracción de simultaneidad rellenando otro conjunto de datos con los registros actualizados del origen de datos y, a continuación, realizar una combinación para evitar una infracción de simultaneidad. (Una infracción de simultaneidad se produce cuando otro usuario modifica un registro del origen de datos después de que se ha rellenado el conjunto de datos.)

## <a name="update-constraints"></a>Restricciones de actualización

Para realizar cambios en una fila de datos existente, agregar o actualizar datos en las columnas individuales. Si el conjunto de datos contiene restricciones (como claves externas o restricciones que no aceptan valores NULL), es posible que el registro pueda encontrarse temporalmente en un estado de error como que la actualización. Es decir, puede ser en un estado de error cuando termine de actualizar una columna pero antes de pasar a la siguiente.

Para impedir que se produzcan infracciones de restricciones prematuras, puede suspender temporalmente las restricciones de actualización. Esta suspensión tiene dos fines:

- Impide que un error que se produce después de haber terminado de actualizar una columna pero no ha iniciado la actualización de otro.

- Evita que determinadas actualizaciones eventos que generan (eventos que se usan a menudo para la validación).

> [!NOTE]
> En Windows Forms, la arquitectura de enlace de datos que está integrada en la cuadrícula de datos suspende hasta que el foco sale de una fila, y no es necesario llamar explícitamente a la comprobación de restricción del <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, o <xref:System.Data.DataRow.CancelEdit%2A> métodos.

Las restricciones se deshabilitan automáticamente cuando se invoca el método <xref:System.Data.DataSet.Merge%2A> en un conjunto de datos. Cuando se complete, si no hay ninguna restricción en el conjunto de datos que no se puede habilitar la fusión mediante combinación un <xref:System.Data.ConstraintException> se produce. En esta situación, la propiedad <xref:System.Data.DataSet.EnforceConstraints%2A> se establece en `false,` y todas las infracciones de las restricciones se deben resolver antes de restablecer la propiedad <xref:System.Data.DataSet.EnforceConstraints%2A> a `true`.

Después de completar una actualización, puede volver a Habilitar comprobación de restricciones, que también vuelve a habilitar eventos de actualización e iniciarlos.

Para obtener más información sobre la suspensión de eventos, consulte [desactivar restricciones al llenar un conjunto de datos](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

## <a name="dataset-update-errors"></a>Errores de actualización de conjuntos de datos

Cuando se actualiza un registro de un conjunto de datos, existe la posibilidad de que se produzca un error. Por ejemplo, podría escribir accidentalmente datos de un tipo incorrecto a una columna, o datos que es demasiado largos o datos que tenga algún otro problema de integridad. O bien, es posible que tenga las comprobaciones de validación específica de la aplicación que generen errores personalizados durante cualquier fase de un evento de actualización. Para obtener más información, consulte [validar datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md).

## <a name="maintain-information-about-changes"></a>Mantener la información sobre los cambios

Información sobre los cambios en un conjunto de datos se mantiene de dos formas: marcando las filas que indiquen que han cambiado (<xref:System.Data.DataRow.RowState%2A>) y manteniendo varias copias de un registro (<xref:System.Data.DataRowVersion>). Con esta información, los procesos pueden determinar qué ha cambiado en el conjunto de datos y pueden enviar las actualizaciones correspondientes al origen de datos.

### <a name="rowstate-property"></a>Propiedad RowState

La propiedad <xref:System.Data.DataRow.RowState%2A> de un objeto <xref:System.Data.DataRow> es un valor que proporciona información sobre el estado de una fila de datos determinada.

En la tabla siguiente se detallan los posibles valores de la enumeración <xref:System.Data.DataRowState>:

|Valor de DataRowState|Descripción|
| - |-----------------|
|<xref:System.Data.DataRowState.Added>|La fila se ha agregado como elemento a <xref:System.Data.DataRowCollection>. (Una fila en este estado no tiene una versión original correspondiente, ya que no existía cuando la última <xref:System.Data.DataRow.AcceptChanges%2A> se llamó al método).|
|<xref:System.Data.DataRowState.Deleted>|La fila se eliminó utilizando el método <xref:System.Data.DataRow.Delete%2A> de un objeto <xref:System.Data.DataRow>.|
|<xref:System.Data.DataRowState.Detached>|La fila se ha creado pero no forma parte de ninguna <xref:System.Data.DataRowCollection>. Un <xref:System.Data.DataRow> objeto está en este estado inmediatamente después de que ha creado, antes de que se ha agregado a una colección, y después de que se ha quitado de una colección.|
|<xref:System.Data.DataRowState.Modified>|Un valor de columna en la fila ha cambiado de alguna manera.|
|<xref:System.Data.DataRowState.Unchanged>|La fila no ha cambiado desde la última vez que se llamó a <xref:System.Data.DataRow.AcceptChanges%2A>.|

### <a name="datarowversion-enumeration"></a>DataRowVersion (enumeración)

Los conjuntos de datos mantienen varias versiones de los registros. El <xref:System.Data.DataRowVersion> campos se utilizan al recuperar el valor encontrado en un <xref:System.Data.DataRow> utilizando el <xref:System.Data.DataRow.Item%2A> propiedad o el <xref:System.Data.DataRow.GetChildRows%2A> método de la <xref:System.Data.DataRow> objeto.

En la tabla siguiente se detallan los posibles valores de la enumeración <xref:System.Data.DataRowVersion>:

|Valor de DataRowVersion|Descripción|
| - |-----------------|
|<xref:System.Data.DataRowVersion.Current>|La versión actual de un registro contiene todas las modificaciones que se han realizado en el registro desde la última vez <xref:System.Data.DataRow.AcceptChanges%2A> llamó. Si la fila se ha eliminado, no existe una versión actual.|
|<xref:System.Data.DataRowVersion.Default>|Es el valor predeterminado de un registro, tal como se define en el esquema del conjunto de datos o en el origen de datos.|
|<xref:System.Data.DataRowVersion.Original>|La versión original de un registro es una copia del registro tal como se encontraba la última vez que se confirmaron cambios en el conjunto de datos. En términos prácticos, suele ser la versión de un registro leído de un origen de datos.|
|<xref:System.Data.DataRowVersion.Proposed>|Es la versión propuesta de un registro que está disponible temporalmente, mientras está en curso una actualización, es decir, el intervalo que transcurre desde que se llama al método <xref:System.Data.DataRow.BeginEdit%2A> hasta que se llama al método <xref:System.Data.DataRow.EndEdit%2A>. Normalmente, se obtiene acceso a la versión propuesta de un registro en un controlador de un evento tal como <xref:System.Data.DataTable.RowChanging>. Al invocar al método <xref:System.Data.DataRow.CancelEdit%2A>, se anulan los cambios y se elimina la versión propuesta de la fila de datos.|

Las versiones original y actual son de utilidad cuando se transmite la información de actualización a un origen de datos. Normalmente, cuando envía una actualización al origen de datos, la nueva información de la base de datos está en la versión actual de un registro. Para buscar el registro que actualizar se utiliza información de la versión original.

Por ejemplo, en un caso donde se cambia la clave principal de un registro, necesita una manera de buscar el registro correcto en el origen de datos con el fin de actualizar los cambios. Si no existiese una versión original, lo más probable es que el registro se agregase al final del origen de datos, con lo que se obtendría no sólo un registro adicional no deseado, sino que, además, sería inexacto y obsoleto. Las dos versiones también se usan en el control de simultaneidad. Puede comparar la versión original con un registro en el origen de datos para determinar si el registro ha cambiado desde que se cargó en el conjunto de datos.

La versión propuesta es de utilidad cuando se necesita realizar una validación antes de confirmar los cambios en el conjunto de datos.

Incluso aunque los registros hayan cambiado, no siempre hay versiones originales o actuales de esa fila. Cuando se inserta una fila nueva en la tabla, no hay versión original, sólo una versión actual. Lo mismo sucede si se elimina una fila mediante una llamada al método `Delete` de la tabla: hay una versión original, pero no hay versión actual.

Para comprobar si existe una versión específica de un registro, haga una consulta al método <xref:System.Data.DataRow.HasVersion%2A> de una fila de datos. Para obtener acceso a cualquiera de las versiones de un registro, pase un valor de la enumeración <xref:System.Data.DataRowVersion> como argumento opcional cuando solicite el valor de una columna.

## <a name="get-changed-records"></a>Obtener los registros modificados

Es una práctica común no se actualizan todos los registros en un conjunto de datos. Por ejemplo, un usuario puede estar trabajando con un control <xref:System.Windows.Forms.DataGridView> de formularios Windows Forms que muestre muchos registros, pero puede actualizar sólo algunos, eliminar uno e insertar otro. Los conjuntos de datos y las tablas de datos proporcionan un método (`GetChanges`) para devolver sólo las filas que se hayan modificado.

Es posible crear subconjuntos de registros modificados con el método `GetChanges` de cualquiera de las tablas de datos (<xref:System.Data.DataTable.GetChanges%2A>) o del propio conjunto de datos (<xref:System.Data.DataSet.GetChanges%2A>). Si se llama al método de la tabla de datos, devuelve una copia de la tabla donde sólo se muestran los registros cambiados. De igual forma, si llama al método en el conjunto de datos, obtiene un nuevo conjunto de datos solo con los registros modificados.

`GetChanges` por sí solo devuelve todos los registros modificados. En cambio, pasando el deseado <xref:System.Data.DataRowState> como un parámetro a la `GetChanges` método, puede especificar qué subconjunto de registros cambiados desea: recién agregado registros, registros marcados para su eliminación, registros desasociados o registros modificados.

Obtener un subconjunto de registros modificados es útil cuando desea enviar registros a otro componente para su procesamiento. En lugar de enviar todo el conjunto de datos, se puede reducir la sobrecarga de la comunicación con el otro componente al obtener únicamente los registros necesarios.

## <a name="commit-changes-in-the-dataset"></a>Confirmar cambios en el conjunto de datos

Cuando se realizan cambios en el conjunto de datos, se establece la propiedad <xref:System.Data.DataRow.RowState%2A> de las filas modificadas. Las versiones originales y actuales de registros se establezcan, mantienen y a su disposición mediante la <xref:System.Data.DataRowView.RowVersion%2A> propiedad. Los metadatos que se almacenan en las propiedades de estas filas cambiadas están necesario para enviar las actualizaciones correctas para el origen de datos.

Si los cambios reflejan el estado actual del origen de datos, ya no es necesario mantener esta información. Normalmente, el conjunto de datos y su origen están sincronizados en dos ocasiones:

- Inmediatamente después de haber cargado información en el conjunto de datos; por ejemplo, cuando lee datos del origen.

- Después de enviar los cambios del conjunto de datos al origen de datos (pero no antes, porque se perdería la información de cambios que se necesita para enviar los cambios a la base de datos).

Para confirmar los cambios pendientes en el conjunto de datos, puede llamar al método <xref:System.Data.DataSet.AcceptChanges%2A>. Por lo general, <xref:System.Data.DataSet.AcceptChanges%2A> se llama en los momentos siguientes:

- Después de cargar el conjunto de datos. Si se carga un conjunto de datos mediante una llamada al método `Fill` del TableAdapter, este adaptador confirma los cambios automáticamente. Sin embargo, si carga un conjunto de datos mediante la combinación de otro conjunto de datos, los cambios se deben confirmar manualmente.

    > [!NOTE]
    > Puede impedir que el adaptador confirme los cambios automáticamente al llamar a la `Fill` método estableciendo el `AcceptChangesDuringFill` propiedad del adaptador para `false`. Si se establece en `false`, el <xref:System.Data.DataRow.RowState%2A> de cada fila insertada durante el relleno se establece en <xref:System.Data.DataRowState.Added>.

- Después de enviar los cambios del conjunto de datos a otro proceso, como un servicio web XML.

    > [!CAUTION]
    > Si confirma el cambio de este modo, se borra la información sobre cambios existente. No confirmar los cambios hasta después de finalizar la realización de operaciones que requieren que la aplicación para saber qué cambios se realizaron en el conjunto de datos.

Este método realiza las funciones siguientes:

- Escribe el <xref:System.Data.DataRowVersion.Current> versión de un registro en su <xref:System.Data.DataRowVersion.Original> versión y sobrescribe la versión original.

- Quita cualquier fila donde el <xref:System.Data.DataRow.RowState%2A> propiedad está establecida en <xref:System.Data.DataRowState.Deleted>.

- Establece la propiedad <xref:System.Data.DataRow.RowState%2A> de un registro en <xref:System.Data.DataRowState.Unchanged>.

El método <xref:System.Data.DataSet.AcceptChanges%2A> está disponible en tres niveles. Puede llamarlo en un <xref:System.Data.DataRow> objeto confirmaciones cambia sólo para esa fila. También puede llamarlo en un <xref:System.Data.DataTable> objeto para confirmar todas las filas de una tabla. Por último, se pueden llamar en el <xref:System.Data.DataSet> objeto confirmar todos los cambios pendientes en todos los registros de todas las tablas del conjunto de datos.

En la tabla siguiente se describen los cambios que se confirman en función del objeto en el que se llame el método:

|Método|Resultado|
|------------|------------|
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Los cambios se confirman solo en una fila específica.|
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Los cambios se confirman en todas las filas de una tabla específica.|
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Los cambios se confirman en todas las filas de todas las tablas del conjunto de datos.|

> [!NOTE]
> Si carga un conjunto de datos mediante una llamada a un TableAdapter `Fill` método, no tendrá que aceptar los cambios explícitamente. De forma predeterminada, el `Fill` llamadas al método el `AcceptChanges` método una vez que termine de rellenar la tabla de datos.

Un método relacionado, <xref:System.Data.DataSet.RejectChanges%2A>, deshace el efecto de los cambios copiando la <xref:System.Data.DataRowVersion.Original> versión en el <xref:System.Data.DataRowVersion.Current> versión de registros. También establece la <xref:System.Data.DataRow.RowState%2A> de cada registro de nuevo en <xref:System.Data.DataRowState.Unchanged>.

## <a name="data-validation"></a>Validación de datos

Para comprobar que los datos de una aplicación satisfacen los requisitos de los procesos a los que se pasan, normalmente se agrega validación. Esto puede implicar la comprobación de que una entrada del usuario en un formulario es correcta, validación de datos que se envían a la aplicación por otra aplicación, o incluso comprobar que la información que se calcula dentro de un componente se encuentra dentro de las restricciones del origen de datos y los requisitos de la aplicación.

Los datos se pueden validar de distintas maneras:

- En la capa de empresa, agregando código a la aplicación para validar los datos. Un lugar en el que puede hacerlo es en el conjunto de datos. El conjunto de datos proporciona algunas ventajas de validación back end, como la capacidad de validar los cambios a medida que se modifican los valores de las columnas y las filas. Para obtener más información, consulte [validar datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md).

- En la capa de presentación, agregando validación a los formularios. Para obtener más información, consulte [validación en Windows Forms de entrada de usuario](/dotnet/framework/winforms/user-input-validation-in-windows-forms).

- En el servidor de datos, al enviar los datos al origen de datos, por ejemplo la base de datos, y dejar que éste los acepte o los rechace. Si trabaja con una base de datos que incluye funciones sofisticadas para validar datos y proporcionar información sobre errores, puede ser un planteamiento práctico, porque los datos se pueden validar sea cual sea su procedencia. Sin embargo, este enfoque puede no adaptarse a los requisitos de validación específicos de la aplicación. Además, tener el origen de datos de validar los datos puede causar numerosas acciones de ida y en el origen de datos, dependiendo de cómo la aplicación facilita la resolución de errores de validación provocados por el back-end.

   > [!IMPORTANT]
   > Cuando utilice comandos de datos con un <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> propiedad que se establece en <xref:System.Data.CommandType.Text>, cuidadosamente Compruebe la información que se envía desde un cliente antes de pasarla a la base de datos. Usuarios con malas intenciones podrían intentar enviar (inyectar) instrucciones de SQL modificadas o adicionales con el fin de obtener acceso no autorizado o dañar la base de datos. Antes de transferir la entrada del usuario a una base de datos, compruebe siempre que la información es válida. Es una práctica recomendada para que siempre utilice consultas parametrizadas o procedimientos almacenados cuando sea posible.

## <a name="transmit-updates-to-the-data-source"></a>Transmitir actualizaciones al origen de datos

Después de modificar un conjunto de datos, se pueden transmitir los cambios a un origen de datos. Lo más frecuente será hacerlo mediante una llamada al método `Update` del TableAdapter (o adaptador de datos). El método recorre cada registro en una tabla de datos, determina qué tipo de actualización se requiere (actualizar, insertar o eliminar), si los hubiera, y, a continuación, se ejecuta el comando adecuado.

Para ilustrar cómo se realizan las actualizaciones, supongamos que la aplicación utiliza un conjunto de datos que contiene una sola tabla de datos. La aplicación obtiene dos filas de la base de datos. Después de recuperarlas, la tabla de datos en memoria sería como la siguiente:

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Unchanged)    c400         Nancy Buchanan    Pending
```

Su aplicación cambia el estado de Nancy Buchanan a "Preferred". Como resultado de este cambio, el valor de la propiedad <xref:System.Data.DataRow.RowState%2A> de esa fila cambia de <xref:System.Data.DataRowState.Unchanged> a <xref:System.Data.DataRowState.Modified>. El valor de la propiedad <xref:System.Data.DataRow.RowState%2A> de la primera fila se mantiene como <xref:System.Data.DataRowState.Unchanged>. Ahora, la tabla de datos tiene este aspecto:

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Modified)     c400         Nancy Buchanan    Preferred
```

Llegados a este punto, su aplicación llama al método `Update` para transmitir el conjunto de datos a la base de datos. El método inspecciona cada fila de una en una. En la primera fila, el método no transmite ninguna instrucción SQL a la base de datos, porque esa fila no ha cambiado desde la primera vez que se obtuvo de la base de datos.

Para la segunda fila, sin embargo, el `Update` automáticamente, el método invoca el comando de datos correcto y la transmite a la base de datos. La sintaxis específica de la instrucción SQL depende del dialecto de SQL que sea compatible con el almacén de datos subyacente. Con todo, cabe señalar los siguientes rasgos generales de la instrucción SQL transmitida:

- Es una instrucción UPDATE. El adaptador sabe cómo utilizar una instrucción UPDATE, porque el valor de la propiedad <xref:System.Data.DataRow.RowState%2A> es <xref:System.Data.DataRowState.Modified>.

- Incluye una cláusula WHERE que indica que el destino de la instrucción UPDATE es la fila donde `CustomerID = 'c400'`. Esta parte de la instrucción SELECT distingue la fila de destino de las demás porque `CustomerID` es la clave principal de la tabla de destino. La información de la cláusula WHERE se deriva de la versión original del registro (`DataRowVersion.Original`), en caso de los valores que son necesarios para identificar la fila han cambiado.

- Incluye la cláusula SET para establecer los nuevos valores de las columnas modificadas.

   > [!NOTE]
   > Si la propiedad `UpdateCommand` del TableAdapter se ha establecido en el nombre de un procedimiento almacenado, el adaptador no construye una instrucción SQL. En su lugar, invoca al procedimiento almacenado pasando los parámetros correspondientes.

## <a name="pass-parameters"></a>Pasar parámetros

Suelen usar parámetros para pasar los valores para los registros que se van a actualizarse en la base de datos. Cuando el TableAdapter `Update` método ejecuta una instrucción UPDATE, debe rellenar los valores de parámetro. Dichos valores los obtiene de la colección `Parameters` del comando de datos correspondiente, en este caso, el objeto `UpdateCommand` de TableAdapter.

Si ha utilizado las herramientas de Visual Studio para generar un adaptador de datos, la `UpdateCommand` objeto contiene una colección de parámetros que corresponden a cada marcador de posición de parámetro en la instrucción.

La propiedad <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> de cada parámetro señala a una columna en la tabla de datos. Por ejemplo, la propiedad `SourceColumn` para `au_id` y los parámetros `Original_au_id` están establecidos en la columna de la tabla de datos que contenga el identificador del autor. Cuando el adaptador `Update` método ejecuciones, lee el autor de la columna de identificador del registro que se está actualizando y rellena los valores de la instrucción.

En una instrucción UPDATE, deberá especificar los valores nuevos (los que se escribirán en el registro), así como los valores antiguos (para que el registro puede encontrarse en la base de datos). Por tanto, hay dos parámetros para cada valor: uno para la cláusula SET y otro diferente para la cláusula WHERE. Ambos parámetros leen los datos del registro que se está actualizando, pero obtienen versiones diferentes del valor de columna en función del parámetro <xref:System.Data.SqlClient.SqlParameter.SourceVersion> propiedad. El parámetro de la cláusula SET obtiene la versión actual y el parámetro de la cláusula WHERE obtiene la versión original.

> [!NOTE]
> También puede establecer los valores de la colección `Parameters` en el código; en ese caso, sería necesario hacerlo en un controlador de eventos para el evento <xref:System.Data.DataTable.RowChanging> del adaptador de datos.

## <a name="see-also"></a>Vea también

- [Herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Crear y configurar TableAdapters](create-and-configure-tableadapters.md)
- [Actualizar datos mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Validar datos](validate-data-in-datasets.md)
- [Cómo: Agregar, modificar y eliminar entidades (WCF data services)](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)