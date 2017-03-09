---
title: "Validar los datos en conjuntos de datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataTable.ColumnChanging"
  - "System.Data.DataTable.ColumnChanging"
  - "System.Data.DataTable.RowChanging"
  - "DataTable.RowChanging"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "validación de datos"
  - "validación de datos, conjuntos de datos"
  - "actualizar conjuntos de datos, validar datos"
  - "validar datos, conjuntos de datos"
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
caps.latest.revision: 24
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Validar los datos en conjuntos de datos
Validar datos es el proceso de confirmar que los valores que se especifican en los objetos de datos son compatibles con las restricciones dentro de un esquema del conjunto de datos, al igual que las reglas establecidas para su aplicación.  Validar datos antes de enviar actualizaciones a la base de datos subyacente es una buena práctica que reduce los errores y la cantidad potencial de acciones de ida y vuelta entre una aplicación y la base de datos.  Para confirmar que son válidos los datos que se escriben en un conjunto de datos, se pueden construir comprobaciones de validación en el propio conjunto de datos.  El conjunto de datos puede comprobar los datos independientemente de cómo se esté realizando la actualización, ya sea directamente mediante los controles de un formulario, desde dentro de un componente o de alguna otra manera.  Dado que el conjunto de datos forma parte de la aplicación, es lógico construir una validación específica de la aplicación \(a diferencia de integrar las mismas comprobaciones en el servidor de bases de datos\).  
  
 La ubicación sugerida para agregar validación en la aplicación es el archivo de clase parcial del conjunto de datos.  En [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], abra el **Diseñador de DataSet** y haga doble clic en la columna o tabla para la que desea crear la validación.  Esta acción crea en forma automática un controlador de eventos <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging>.  Para obtener más información, vea [Cómo: Validar datos mientras se modifica una columna](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md) o [Cómo: Validar datos mientras se modifica la fila](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md).  Para obtener un ejemplo completo, vea [Tutorial: Agregar validación a un conjunto de datos](../Topic/Walkthrough:%20Adding%20Validation%20to%20a%20Dataset.md).  
  
## Validar datos  
 Para integrar la validación en un conjunto de datos, se puede:  
  
-   Al crear su propia validación específica de la aplicación que pueda comprobar los datos durante los cambios a los valores en una columna de datos individual.  Para obtener más información, vea [Cómo: Validar datos mientras se modifica una columna](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md).  
  
-   Al crear su propia validación específica de la aplicación que pueda comprobar los datos durante los cambios a los valores mientras se cambia una fila de datos completa.  Para obtener más información, vea [Cómo: Validar datos mientras se modifica la fila](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md).  
  
-   Crear claves, restricciones UNIQUE, etc., como parte de la definición de esquema actual del conjunto de datos.  Para obtener más información sobre cómo incorporar la validación en la definición de esquema, vea [Restringir un objeto DataColumn para que contenga valores únicos](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md#SpecifyUniqueConstraint).  
  
-   Al establecer las propiedades del objeto <xref:System.Data.DataColumn>, como <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>y <xref:System.Data.DataColumn.Unique%2A>.  
  
 Cuando ocurre un cambio en un registro, el objeto <xref:System.Data.DataTable> produce una serie de eventos:  
  
-   Los eventos <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.ColumnChanged> se producen durante y después de cada cambio en una columna individual.  El evento <xref:System.Data.DataTable.ColumnChanging> es útil cuando se desea validar cambios en columnas específicas.  La información sobre el cambio propuesto se pasa como argumento con el evento.  Para obtener más información, vea [Cómo: Validar datos mientras se modifica una columna](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md).  
  
-   Los eventos <xref:System.Data.DataTable.RowChanging> y <xref:System.Data.DataTable.RowChanged> se producen durante y después de realizar algún cambio en una fila.  El evento <xref:System.Data.DataTable.RowChanging> es más general, ya que simplemente indica que se está produciendo un cambio en alguna parte de la fila, pero no se sabe qué columna ha cambiado.  Para obtener más información, vea [Cómo: Validar datos mientras se modifica la fila](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md).  
  
 De forma predeterminada, cada cambio a una columna produce cuatro eventos: primero los eventos <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.ColumnChanged> para la columna concreta en la cual se realizan los cambios y a continuación los eventos <xref:System.Data.DataTable.RowChanging> y <xref:System.Data.DataTable.RowChanged>.  Si se realizan varios cambios en la fila, los eventos se provocan para cada uno de los cambios.  
  
> [!NOTE]
>  El método <xref:System.Data.DataRow.BeginEdit%2A> de la fila de datos desactiva los eventos <xref:System.Data.DataTable.RowChanging> y <xref:System.Data.DataTable.RowChanged> después de cada cambio en las columnas individuales.  En ese caso, el evento no se produce hasta que se ha llamado al método <xref:System.Data.DataRow.EndEdit%2A>, cuando los eventos <xref:System.Data.DataTable.RowChanging> y <xref:System.Data.DataTable.RowChanged> se producen una sola vez.  Para obtener más información, vea [Cómo: Desactivar restricciones al llenar un conjunto de datos](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
 El evento que elija depende del nivel de detalle que desee aplicar a la validación.  Si es importante detectar un error inmediatamente después de modificar una columna, construya la validación con el evento <xref:System.Data.DataTable.ColumnChanging>.  De lo contrario, utilice el evento <xref:System.Data.DataTable.RowChanging>, el cual puede permitir detectar varios errores al mismo tiempo.  Además, si los datos están estructurados de tal forma que el valor de una columna se valida en base al contenido de otra columna, es necesario realizar la validación durante el evento <xref:System.Data.DataTable.RowChanging>.  
  
 Cuando se actualizan los registros, el objeto <xref:System.Data.DataTable> produce eventos a los que se puede responder a medida que se realizan los cambios y después de que éstos se han realizado.  
  
 Si su aplicación utiliza un conjunto de datos con tipo, puede crear controladores de eventos fuertemente tipados.  Esto agregará cuatro eventos adicionales con tipo para los cuales se pueden crear controladores; `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting` y `dataTableNameRowDeleted`.  Estos controladores de eventos con tipo pasan un argumento que incluye los nombres de columna de la tabla, lo que simplifica la lectura y escritura del código.  
  
## Eventos de actualización de datos  
  
|Evento|Descripción|  
|------------|-----------------|  
|<xref:System.Data.DataTable.ColumnChanging>|Se está modificando el valor de una columna.  El evento pasa la fila y la columna junto con el nuevo valor propuesto.|  
|<xref:System.Data.DataTable.ColumnChanged>|Se ha modificado el valor de una columna.  El evento pasa la fila y la columna junto con el valor propuesto.|  
|<xref:System.Data.DataTable.RowChanging>|Los cambios realizados a un objeto <xref:System.Data.DataRow> están a punto de confirmarse de regreso en el conjunto de datos.  Si no se llama al método <xref:System.Data.DataRow.BeginEdit%2A>, se produce el evento <xref:System.Data.DataTable.RowChanging> para cada cambio realizado en una columna, inmediatamente después de producirse el evento <xref:System.Data.DataTable.ColumnChanging>.  Si se llama a <xref:System.Data.DataRow.BeginEdit%2A> antes de realizar cambios, se produce el evento <xref:System.Data.DataTable.RowChanging> sólo cuando se llama al método <xref:System.Data.DataRow.EndEdit%2A>.<br /><br /> El evento pasa la fila y un valor que indica qué tipo de acción se está realizando \(cambiar, insertar, etc.\).|  
|<xref:System.Data.DataTable.RowChanged>|Se ha modificado una fila.  El evento pasa la fila y un valor que indica qué tipo de acción se está realizando \(cambiar, insertar, etc.\).|  
|<xref:System.Data.DataTable.RowDeleting>|Se está eliminando una fila.  El evento pasa la fila y un valor que indica qué tipo de acción se está realizando \(eliminar\).|  
|<xref:System.Data.DataTable.RowDeleted>|Se ha eliminado una fila.  El evento pasa la fila y un valor que indica qué tipo de acción se está realizando \(eliminar\).|  
  
 Los eventos <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging> y <xref:System.Data.DataTable.RowDeleting> se producen durante el proceso de actualización.  Puede utilizar estos eventos para validar datos o realizar otros tipos de procesos.  Debido a que las actualizaciones se están realizando mientras se ejecutan estos eventos, puede cancelarlas produciendo una excepción, lo que impide que se complete el cambio.  
  
 Los eventos <xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> y <xref:System.Data.DataTable.RowDeleted> son eventos de notificación que se producen cuando la actualización se ha realizado correctamente.  Estos eventos son útiles cuando se desea ejecutar acciones posteriores dependiendo de si la actualización se realizó correctamente.  
  
## Vea también  
 [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)   
 [Cómo: Conectarse a los datos de una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Cómo: Validar datos en el control DataGridView de formularios Windows Forms](../Topic/How%20to:%20Validate%20Data%20in%20the%20Windows%20Forms%20DataGridView%20Control.md)   
 [Cómo: Mostrar iconos de error para la validación de formularios con el componente ErrorProvider de formularios Windows Forms](../Topic/How%20to:%20Display%20Error%20Icons%20for%20Form%20Validation%20with%20the%20Windows%20Forms%20ErrorProvider%20Component.md)