---
title: Usar DataRelation para crear relaciones entre los conjuntos de datos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 94fb9217b779d00314b2a188ae2fe6f7d0ba4bb1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="create-relationships-between-datasets"></a>Crear relaciones entre los conjuntos de datos
Uso de tablas de conjuntos de datos que contienen datos relacionados <xref:System.Data.DataRelation> objetos para representar una relación primaria-secundaria entre las tablas y devolver los registros relacionados entre sí. Agregar tablas relacionadas a conjuntos de datos mediante la **Asistente para configuración de orígenes de datos**, o la **Diseñador de Dataset**, crea y configura el <xref:System.Data.DataRelation> objeto automáticamente.  
  
La <xref:System.Data.DataRelation> objeto realiza dos funciones:  
  
-   Pueden disponer de los registros relacionados con un registro que está trabajando. Proporciona registros secundarios si se encuentra en un registro primario (<xref:System.Data.DataRow.GetChildRows%2A>) y un registro primario si se trabaja con un registro secundario (<xref:System.Data.DataRow.GetParentRow%2A>).  
  
-   Puede aplicar restricciones de integridad referencial, como la eliminación de registros secundarios relacionados cuando se elimina un registro primario.  
  
Es importante comprender la diferencia entre una combinación auténtica y la función de un <xref:System.Data.DataRelation> objeto. En una combinación es true, se toman de tablas primarias y secundarias registros y se colocan en un único conjunto de registros sin formato. Cuando se usa un <xref:System.Data.DataRelation> de objeto, no se crea ningún conjunto de registros nueva. En su lugar, DataRelation realiza un seguimiento de la relación entre las tablas y los mantiene sincronizados los registros primarios y secundarios.  
  
## <a name="datarelation-objects-and-constraints"></a>Las restricciones y los objetos DataRelation  
Un <xref:System.Data.DataRelation> objeto también se usa para crear y aplicar las siguientes restricciones:  
  
-   Una restricción unique, que garantiza que una columna en la tabla no contiene duplicados.  
  
-   Una restricción foreign key, que se puede usar para mantener la integridad referencial entre una tabla primaria y secundaria de un conjunto de datos.  
  
Las restricciones que especifican en un <xref:System.Data.DataRelation> objeto se implementan automáticamente creando objetos adecuados o establecer las propiedades. Si creas una restricción foreign key mediante el <xref:System.Data.DataRelation> (objeto), las instancias de la <xref:System.Data.ForeignKeyConstraint> clase se agregan a la <xref:System.Data.DataRelation> del objeto <xref:System.Data.DataRelation.ChildKeyConstraint%2A> propiedad.  
  
Se implementa una restricción unique, simplemente establezca la <xref:System.Data.DataColumn.Unique%2A> propiedad de una columna de datos para `true` o mediante la adición de una instancia de la <xref:System.Data.UniqueConstraint> clase a la <xref:System.Data.DataRelation> del objeto <xref:System.Data.DataRelation.ParentKeyConstraint%2A> propiedad. Para obtener información sobre la suspensión de las restricciones en un conjunto de datos, vea [desactivar restricciones al llenar un conjunto de datos](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
### <a name="referential-integrity-rules"></a>Reglas de integridad referencial  
Como parte de la restricción foreign key, puede especificar reglas de integridad referencial que se aplican en tres puntos:  
  
-   Cuando se actualiza un registro primario  
  
-   Cuando se elimina un registro primario  
  
-   Cuando se acepta o se rechaza un cambio  
  
Se especifican las reglas que se pueden realizar en el <xref:System.Data.Rule> enumeración y se muestran en la tabla siguiente.  
  
|Regla de restricción de clave externa|Acción|  
|----------------------------------|------------|  
|<xref:System.Data.Rule.Cascade>|El cambio (actualización o eliminación) realizado en el registro primario también se realiza en los registros relacionados en la tabla secundaria.|  
|<xref:System.Data.Rule.SetNull>|No se eliminan los registros secundarios, pero la clave externa de los registros secundarios se establece en <xref:System.DBNull>. Con esta configuración, los registros secundarios pueden dejarse como "huérfanos", es decir, no tienen ninguna relación con los registros primarios. **Nota:** el uso de esta regla puede generar datos no válidos en la tabla secundaria.|  
|<xref:System.Data.Rule.SetDefault>|La clave externa de los registros secundarios relacionados se establece en su valor predeterminado (según lo establecido por la columna <xref:System.Data.DataColumn.DefaultValue%2A> propiedad).|  
|<xref:System.Data.Rule.None>|No se realizarán cambios en los registros secundarios relacionados. Con esta configuración, los registros secundarios pueden contener referencias a registros primarios no válidos.|  
  
Para obtener más información acerca de las actualizaciones en las tablas del conjunto de datos, vea [guardar los datos en la base de datos](../data-tools/save-data-back-to-the-database.md).  
  
### <a name="constraint-only-relations"></a>Relaciones de sólo restricción  
Cuando se crea un <xref:System.Data.DataRelation> de objeto, tiene la opción de especificar que la relación se utilice únicamente para exigir restricciones, es decir, que no se utilice también para tener acceso a registros relacionados. Puede usar esta opción para generar un conjunto de datos que es algo más eficaz y que contiene menos métodos que uno con la capacidad de registros relacionados con. Sin embargo, no podrá tener acceso a registros relacionados. Por ejemplo, una relación de sólo restricción impide que se elimine un registro principal que todavía tiene registros secundarios, y no se puede obtener acceso a los registros secundarios a través del elemento primario.  
  
## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Creación manual de una relación de datos en el Diseñador de Dataset  
Al crear tablas de datos mediante las herramientas de diseño de datos en Visual Studio, las relaciones se crean automáticamente si se puede recopilar la información del origen de los datos. Si agrega manualmente las tablas de datos de la **conjunto de datos** pestaña de la **cuadro de herramientas**, puede que tenga que crear manualmente la relación. Para obtener información acerca de cómo crear <xref:System.Data.DataRelation> objetos mediante programación, vea [agregar objetos DataRelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/adding-datarelations).  
  
Las relaciones entre tablas de datos aparecen como líneas en la **Diseñador de Dataset**, con un glifo de clave e infinito que representan el aspecto de uno a varios de la relación. De forma predeterminada, el nombre de la relación no aparece en la superficie de diseño.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-a-relationship-between-two-data-tables"></a>Para crear una relación entre dos tablas de datos  
  
1.  Abra su conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, consulte [Tutorial: crear un conjunto de datos en el Diseñador de Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  Arrastre un **relación** objeto desde el **conjunto de datos** cuadro de herramientas a la tabla de datos secundaria en la relación.  
  
     El **relación** abre el cuadro de diálogo, rellenar el **tabla secundaria** cuadro con la tabla que se arrastró el **relación** objeto en.  
  
3.  Seleccione la tabla primaria de la **tabla primaria** cuadro. La tabla primaria contiene los registros en el lado "uno" de una relación uno a varios.  
  
4.  Compruebe que la tabla secundaria correcta se muestra en el **tabla secundaria** cuadro. La tabla secundaria contiene los registros en el lado "varios" de una relación uno a varios.  
  
5.  Escriba un nombre para la relación en la **nombre** cuadro o deje el nombre predeterminado basándose en las tablas seleccionadas. Este es el nombre de los datos reales <xref:System.Data.DataRelation> objeto en el código.  
  
6.  Seleccione las columnas que combinen las tablas en el **columnas de clave** y **las columnas de clave externa** enumera.  
  
7.  Seleccione si desea crear una relación, una restricción o ambas.   
  
8.  Active o desactive el **relación anidada** cuadro. Al seleccionar esta opción establece la <xref:System.Data.DataRelation.Nested%2A> propiedad `true`, y, las filas secundarias de la relación se anidan dentro de la columna primaria cuando se escriben como datos XML o se sincroniza con las filas <xref:System.Xml.XmlDataDocument>. Para obtener más información, consulte [anidar objetos DataRelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations).  
  
9. Establezca las reglas que se aplicará cuando está realizando cambios en los registros de estas tablas. Para obtener más información, consulta <xref:System.Data.Rule>.  
  
10. Haga clic en **Aceptar** para crear la relación. Aparece una línea de relación en el diseñador entre las dos tablas.  
  
#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Para mostrar el nombre de una relación en el Diseñador de Dataset  
  
1.  Abra su conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, consulte [Tutorial: crear un conjunto de datos en el Diseñador de Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  Desde el **datos** menú, seleccione la **Mostrar etiquetas de relación** comando para mostrar el nombre de relación. Desactive este comando para ocultar el nombre de relación.

## <a name="see-also"></a>Vea también
[Crear y configurar conjuntos de datos en Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)