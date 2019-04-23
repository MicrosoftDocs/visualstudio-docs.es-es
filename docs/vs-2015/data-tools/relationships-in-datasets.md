---
title: Las relaciones en conjuntos de datos | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9991adc9d770487c646c97da81b6245ae65ba5f5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60075381"
---
# <a name="relationships-in-datasets"></a>Relaciones en conjuntos de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uso de tablas de conjuntos de datos que contienen datos relacionados <xref:System.Data.DataRelation> objetos para representar una relación primaria-secundaria entre las tablas y devolver los registros relacionados entre sí. Agregar tablas relacionadas a conjuntos de datos mediante el **Asistente para configuración de origen de datos**, o el **Diseñador de Dataset**, crea y configura el <xref:System.Data.DataRelation> objeto automáticamente.  
  
 La <xref:System.Data.DataRelation> objeto desempeña dos funciones:  
  
- Pueden disponer de los registros relacionados con un registro que está trabajando. Proporciona registros secundarios si se encuentra en un registro primario (<xref:System.Data.DataRow.GetChildRows%2A>) y un registro primario si está trabajando con un registro secundario (<xref:System.Data.DataRow.GetParentRow%2A>).  
  
- Puede aplicar restricciones de integridad referencial, como la eliminación de registros secundarios relacionados cuando se elimina un registro primario.  
  
  Es importante comprender la diferencia entre una combinación es true y la función de un <xref:System.Data.DataRelation> objeto. En una combinación es true, se toman de las tablas primarias y secundarias registros y se colocan en un único conjunto de registros sin formato. Cuando se usa un <xref:System.Data.DataRelation> de objeto, no se crea ningún conjunto de registros nuevos. En su lugar, DataRelation realiza un seguimiento de la relación entre las tablas y los mantiene sincronizados los registros primarios y secundarios.  
  
## <a name="datarelation-objects-and-constraints"></a>Las restricciones y los objetos DataRelation  
 Un <xref:System.Data.DataRelation> objeto también se usa para crear y aplicar las siguientes restricciones:  
  
- Una restricción unique, lo que garantiza que una columna en la tabla no contiene duplicados.  
  
- Una restricción foreign key, que puede usarse para mantener la integridad referencial entre una tabla primaria y secundaria de un conjunto de datos.  
  
  Las restricciones que se especifican en un <xref:System.Data.DataRelation> objeto se implementan automáticamente creando objetos adecuados o establecer las propiedades. Si creas una restricción foreign key mediante el <xref:System.Data.DataRelation> (objeto), las instancias de la <xref:System.Data.ForeignKeyConstraint> clase se agregan a la <xref:System.Data.DataRelation> del objeto <xref:System.Data.DataRelation.ChildKeyConstraint%2A> propiedad.  
  
  Se implementa una restricción unique, simplemente establezca el <xref:System.Data.DataColumn.Unique%2A> propiedad de una columna de datos para `true` o mediante la adición de una instancia de la <xref:System.Data.UniqueConstraint> clase a la <xref:System.Data.DataRelation> del objeto <xref:System.Data.DataRelation.ParentKeyConstraint%2A> propiedad. Para obtener información sobre la suspensión de las restricciones en un conjunto de datos, vea [desactivar restricciones al llenar un conjunto de datos](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
### <a name="referential-integrity-rules"></a>Reglas de integridad referencial  
 Como parte de la restricción foreign key, puede especificar reglas de integridad referencial que se aplican en tres puntos:  
  
- Cuando se actualiza un registro primario  
  
- Cuando se elimina un registro primario  
  
- Cuando se acepta o se rechaza un cambio  
  
  Se especifican las reglas que se pueden realizar en el <xref:System.Data.Rule> enumeración y se muestran en la tabla siguiente.  
  
|Regla de restricción de clave externa|Acción|  
|----------------------------------|------------|  
|<xref:System.Data.Rule>|También se realiza el cambio realizado en el registro primario (update o delete) en los registros relacionados en la tabla secundaria.|  
|<xref:System.Data.Rule>|No se eliminan los registros secundarios, pero la clave externa en los registros secundarios se establece en <xref:System.DBNull>. Con esta configuración, los registros secundarios pueden dejarse como "huérfanos", es decir, no tienen ninguna relación con los registros primarios. **Nota:**  Mediante esta regla puede dar lugar a que los datos no válidos en la tabla secundaria.|  
|<xref:System.Data.Rule>|La clave externa en los registros secundarios relacionados se establece en su valor predeterminado (según lo establecido por la columna <xref:System.Data.DataColumn.DefaultValue%2A> propiedad).|  
|<xref:System.Data.Rule>|No se realiza ningún cambio en los registros secundarios relacionados. Con esta configuración, los registros secundarios pueden contener referencias a los registros primarios no válido.|  
  
 Para obtener más información acerca de las actualizaciones en las tablas del conjunto de datos, vea [guardar los datos en la base de datos](../data-tools/save-data-back-to-the-database.md).  
  
### <a name="constraint-only-relations"></a>Relaciones de sólo restricción  
 Cuando creas un <xref:System.Data.DataRelation> objeto, tiene la opción de especificar que la relación se usa únicamente para exigir restricciones, es decir, no se usa también para tener acceso a registros relacionados. Puede usar esta opción para generar un conjunto de datos que es ligeramente más eficaz y que contiene los métodos de la que tenga la capacidad de registros relacionados con los menos. Sin embargo, no podrá tener acceso a registros relacionados. Por ejemplo, una relación de restricción evita que se elimine un registro principal que todavía tiene registros secundarios, y no se puede obtener acceso a los registros secundarios a través del elemento primario.  
  
## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Creación manual de una relación de datos en el Diseñador de Dataset  
 Al crear tablas de datos mediante las herramientas de diseño de datos en Visual Studio, las relaciones se crean automáticamente si se puede recopilar la información desde el origen de datos. Si agrega manualmente las tablas de datos de la **DataSet** pestaña de la **cuadro de herramientas**, es posible que deba crear manualmente la relación. Para obtener información sobre cómo crear <xref:System.Data.DataRelation> objetos mediante programación, vea [agregar objetos DataRelation](http://msdn.microsoft.com/library/a4a564fb-c1c4-4135-b6c2-b030e51195e4).  
  
 Las relaciones entre tablas de datos aparecen como líneas en el **Diseñador de Dataset**, con un glifo de clave e infinito que describe el aspecto de uno a varios de la relación. De forma predeterminada, el nombre de la relationshipCommentEnd Id = '1c8c78e19b7fa441' no aparece en la superficie de diseño.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-relationship-between-two-data-tables"></a>Para crear una relación entre dos tablas de datos  
  
1. Abra su conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, vea [Cómo: Abrir un conjunto de datos en el Diseñador de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2. Arrastre un **relación** objeto desde el **DataSet** cuadro de herramientas a la tabla de datos secundaria en la relación.  
  
     El **relación** abre el cuadro de diálogo, rellenar el **tabla secundaria** cuadro con la tabla que se arrastró el **relación** objeto a.  
  
3. Seleccione la tabla primaria desde la **tabla primaria** cuadro. La tabla primaria contiene los registros en el lado "uno" de una relación uno a varios.  
  
4. Compruebe que la tabla secundaria correcta se muestra en el **tabla secundaria** cuadro. La tabla secundaria contiene los registros en el lado "varios" de una relación uno a varios.  
  
5. Escriba un nombre para la relación en el **nombre** cuadro o deje el nombre predeterminado basándose en las tablas seleccionadas. Éste es el nombre de los datos reales <xref:System.Data.DataRelation> objeto en el código.  
  
6. Seleccione las columnas que se unen las tablas en el **columnas de clave** y **columnas de clave externa** enumera.  
  
7. Seleccione si desea crear una relación, la restricción o ambas. Para obtener información, consulte [Introducción a los objetos DataRelation](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).  
  
8. Active o desactive el **relación anidada** cuadro. Seleccione esta opción establece la <xref:System.Data.DataRelation.Nested%2A> propiedad `true`, y hace que el elemento secundario filas de la relación se anidan dentro de la columna primaria cuando se escribe como datos XML o sincronizadas con esas filas <xref:System.Xml.XmlDataDocument>. Para obtener más información, consulte [anidar objetos DataRelation](http://msdn.microsoft.com/library/9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab).  
  
9. Establezca las reglas que se aplicará cuando se va a realizar cambios en los registros en estas tablas. Para obtener más información, consulta <xref:System.Data.Rule>.  
  
10. Haga clic en **Aceptar** para crear la relación. Aparece una línea de relación en el diseñador entre las dos tablas.  
  
#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Para mostrar el nombre de una relación en el Diseñador de Dataset  
  
1. Abra su conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, vea [Cómo: Abrir un conjunto de datos en el Diseñador de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2. Desde el **datos** menú, seleccione el **Mostrar etiquetas de relación** comando para mostrar el nombre de relación. Borrar ese comando para ocultar el nombre de relación.
