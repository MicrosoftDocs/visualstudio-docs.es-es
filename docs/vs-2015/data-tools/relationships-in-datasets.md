---
title: Relaciones en conjuntos de valores | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eb13ad7db9a4f13ce9bf983ce6327045f885f4d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652886"
---
# <a name="relationships-in-datasets"></a>Relaciones en conjuntos de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los conjuntos de datos que contienen tablas de datos relacionadas usan <xref:System.Data.DataRelation> objetos para representar una relación de elementos primarios y secundarios entre las tablas y devolver los registros relacionados entre sí. Agregar tablas relacionadas a conjuntos de datos mediante el **Asistente para la configuración de orígenes de datos**, o la **Diseñador de DataSet**, crea y configura el <xref:System.Data.DataRelation> objeto.

 El <xref:System.Data.DataRelation> objeto realiza dos funciones:

- Puede hacer que estén disponibles los registros relacionados con un registro con el que está trabajando. Proporciona registros secundarios si está en un registro primario ( <xref:System.Data.DataRow.GetChildRows%2A> ) y un registro primario si está trabajando con un registro secundario ( <xref:System.Data.DataRow.GetParentRow%2A> ).

- Puede aplicar restricciones para la integridad referencial, como eliminar los registros secundarios relacionados cuando se elimina un registro primario.

  Es importante comprender la diferencia entre una combinación verdadera y la función de un <xref:System.Data.DataRelation> objeto. En una combinación true, los registros se toman de las tablas primarias y secundarias y se colocan en un único conjunto de registros plano. Cuando se usa un <xref:System.Data.DataRelation> objeto, no se crea ningún nuevo conjunto de registros. En su lugar, la DataRelation realiza un seguimiento de la relación entre las tablas y mantiene los registros primarios y secundarios sincronizados.

## <a name="datarelation-objects-and-constraints"></a>Objetos DataRelation y restricciones
 <xref:System.Data.DataRelation>También se utiliza un objeto para crear y aplicar las restricciones siguientes:

- Una restricción UNIQUE, que garantiza que una columna de la tabla no contiene duplicados.

- Una restricción FOREIGN KEY, que se puede utilizar para mantener la integridad referencial entre una tabla primaria y una tabla secundaria en un conjunto de elementos.

  Las restricciones que se especifican en un <xref:System.Data.DataRelation> objeto se implementan mediante la creación automática de objetos adecuados o el establecimiento de propiedades. Si crea una restricción FOREIGN KEY mediante el <xref:System.Data.DataRelation> objeto, las instancias de la <xref:System.Data.ForeignKeyConstraint> clase se agregan a la <xref:System.Data.DataRelation> propiedad del objeto <xref:System.Data.DataRelation.ChildKeyConstraint%2A> .

  Una restricción UNIQUE se implementa simplemente estableciendo la <xref:System.Data.DataColumn.Unique%2A> propiedad de una columna de datos en `true` o agregando una instancia de la <xref:System.Data.UniqueConstraint> clase a la <xref:System.Data.DataRelation> propiedad del objeto <xref:System.Data.DataRelation.ParentKeyConstraint%2A> . Para obtener información sobre la suspensión de restricciones en un conjunto de datos, vea [desactivar restricciones al llenar un conjunto](../data-tools/turn-off-constraints-while-filling-a-dataset.md)de datos.

### <a name="referential-integrity-rules"></a>Reglas de integridad referencial
 Como parte de la restricción FOREIGN KEY, puede especificar reglas de integridad referencial que se aplican en tres puntos:

- Cuando se actualiza un registro primario

- Cuando se elimina un registro primario

- Cuando se acepta o se rechaza un cambio

  Las reglas que puede crear se especifican en la <xref:System.Data.Rule> enumeración y se muestran en la tabla siguiente.

|Regla de restricción FOREIGN KEY|Acción|
|----------------------------------|------------|
|<xref:System.Data.Rule>|El cambio (actualización o eliminación) realizado en el Registro primario también se realiza en los registros relacionados de la tabla secundaria.|
|<xref:System.Data.Rule>|Los registros secundarios no se eliminan, pero la clave externa de los registros secundarios está establecida en <xref:System.DBNull> . Con esta configuración, los registros secundarios se pueden dejar como "huérfanos", es decir, no tienen ninguna relación con los registros primarios. **Nota:**  El uso de esta regla puede dar lugar a datos no válidos en la tabla secundaria.|
|<xref:System.Data.Rule>|La clave externa de los registros secundarios relacionados se establece en su valor predeterminado (establecido por la propiedad de la columna <xref:System.Data.DataColumn.DefaultValue%2A> ).|
|<xref:System.Data.Rule>|No se realiza ningún cambio en los registros secundarios relacionados. Con esta configuración, los registros secundarios pueden contener referencias a registros primarios no válidos.|

 Para obtener más información acerca de las actualizaciones en tablas de conjuntos de datos, vea [guardar datos en la base de datos](../data-tools/save-data-back-to-the-database.md).

### <a name="constraint-only-relations"></a>Relaciones solo de restricción
 Al crear un <xref:System.Data.DataRelation> objeto, tiene la opción de especificar que la relación se use solo para aplicar restricciones, es decir, que no se utilizará también para tener acceso a los registros relacionados. Puede usar esta opción para generar un conjunto de registros que sea ligeramente más eficaz y que contenga menos métodos que uno con la funcionalidad de registros relacionados. Sin embargo, no podrá tener acceso a los registros relacionados. Por ejemplo, una relación de solo restricción evita que se elimine un registro primario que todavía tenga registros secundarios, y no se puede tener acceso a los registros secundarios a través del elemento primario.

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Crear manualmente una relación de datos en el Diseñador de DataSet
 Al crear tablas de datos mediante las herramientas de diseño de datos de Visual Studio, las relaciones se crean automáticamente si la información se puede recopilar desde el origen de los datos. Si agrega manualmente tablas de datos desde la pestaña **conjunto** de datos del **cuadro de herramientas**, es posible que tenga que crear la relación manualmente. Para obtener información sobre cómo crear <xref:System.Data.DataRelation> objetos mediante programación, vea [Agregar DataRelations](https://msdn.microsoft.com/library/a4a564fb-c1c4-4135-b6c2-b030e51195e4).

 Las relaciones entre las tablas de datos aparecen como líneas en el **Diseñador de DataSet**, con un glifo de clave y infinito que representa el aspecto uno a varios de la relación. De forma predeterminada, el nombre de relationshipCommentEnd ID = ' 1c8c78e19b7fa441 ' no aparece en la superficie de diseño.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>Para crear una relación entre dos tablas de datos

1. Abra su conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, consulte [Cómo: abrir un conjunto de datos en el diseñador de DataSet](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Arrastre un objeto **Relation** desde el cuadro de herramientas del **conjunto** de datos a la tabla de datos secundaria de la relación.

     Se abrirá el cuadro de diálogo **relación** y rellenará el cuadro de **tabla secundaria** con la tabla a la que arrastró el objeto de **relación** .

3. Seleccione la tabla primaria en el cuadro **tabla primaria** . La tabla primaria contiene registros en el lado "uno" de una relación de uno a varios.

4. Compruebe que se muestra la tabla secundaria correcta en el cuadro **tabla secundaria** . La tabla secundaria contiene registros en el lado "varios" de una relación de uno a varios.

5. Escriba un nombre para la relación en el cuadro **nombre** o deje el nombre predeterminado en función de las tablas seleccionadas. Es el nombre del <xref:System.Data.DataRelation> objeto real en el código.

6. Seleccione las columnas que unen las tablas en las listas **columnas de clave** y columnas de **clave externa** .

7. Seleccione si desea crear una relación, una restricción o ambas. Para obtener más información, vea [Introducción a los objetos DataRelation](https://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).

8. Active o desactive el cuadro **relación anidada** . Al seleccionar esta opción, la propiedad se establece <xref:System.Data.DataRelation.Nested%2A> en `true` y se hace que las filas secundarias de la relación se aniden dentro de la columna primaria cuando dichas filas se escriben como datos XML o se sincronizan con <xref:System.Xml.XmlDataDocument> . Para obtener más información, consulte anidamiento de objetos [DataRelation](https://msdn.microsoft.com/library/9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab).

9. Establezca las reglas que se aplicarán al realizar cambios en los registros de estas tablas. Para obtener más información, vea <xref:System.Data.Rule>.

10. Haga clic en **Aceptar** para crear la relación. Una línea de relación aparece en el diseñador entre las dos tablas.

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Para mostrar un nombre de relación en el Diseñador de DataSet

1. Abra su conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, consulte [Cómo: abrir un conjunto de datos en el diseñador de DataSet](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. En el menú **datos** , seleccione el comando **Mostrar etiquetas de relación** para mostrar el nombre de la relación. Desactive ese comando para ocultar el nombre de la relación.
