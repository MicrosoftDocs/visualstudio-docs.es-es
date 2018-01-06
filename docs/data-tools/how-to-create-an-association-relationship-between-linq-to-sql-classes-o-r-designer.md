---
title: "Cómo crear una relación entre clases LINQ to SQL con Object Relational Designer | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 5c86eff5c25dbabb368d7d90ed46be718b8db8e7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Cómo: crear una asociación entre clases LINQ to SQL (Object Relational Designer)
Las asociaciones entre clases de entidades en [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] son similares a las relaciones entre tablas en una base de datos. Puede crear asociaciones entre las clases de entidad mediante el **Editor de asociaciones** cuadro de diálogo.  
  
Debe seleccionar una clase primaria y secundaria cuando se usa el **Editor de asociaciones** cuadro de diálogo para crear una asociación. La clase primaria es la clase de entidad que contiene la clave principal y la clase secundaria es la clase de entidad que contiene la clave externa. Por ejemplo, si se crearon clases de entidad y se asignaron a las tablas Customers y Orders de Northwind, la clase Customer sería la clase primaria y Order, la secundaria.  
  
> [!NOTE]
>  Al arrastrar las tablas de **Explorador de servidores**/**el Explorador de base de datos** en el [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]), las asociaciones se crearán automáticamente en función de las existentes relaciones de clave externa en la base de datos.  

## <a name="association-properties"></a>Propiedades de la asociación
Después de crear una asociación, al seleccionar la asociación en el Object Relational Designer, hay algunas propiedades configurables en la **propiedades** ventana. (La asociación es la línea entre las clases relacionadas). En la tabla siguiente, se proporcionan descripciones de las propiedades de una asociación.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|**Cardinalidad**|Controla si la asociación es de uno a varios o de uno a uno.|  
|**Propiedad secundaria**|Especifica si se debe crear una propiedad en el registro primario que es una colección o se debe hacer referencia a los registros secundarios en el lado de las claves externas de la asociación. Por ejemplo, en la asociación entre Customer y Order, si la **propiedad secundaria** está establecido en **True**, se crea una propiedad denominada Orders en la clase primaria.|  
|**Propiedad primaria**|La propiedad de la clase secundaria que hace referencia a la clase primaria asociada. Por ejemplo, en la asociación entre Customer y Order, en la clase Order se creará una propiedad denominada Customer que hará referencia al cliente asociado de un pedido.|  
|**Propiedades de participantes**|Muestra las propiedades de asociación y proporciona un **puntos suspensivos** botón (…) que abre de nuevo el **Editor de asociaciones** cuadro de diálogo.|  
|**Único**|Especifica si las columnas de destino externas tienen una restricción de unicidad.|  
  
## <a name="to-create-an-association-between-entity-classes"></a>Para crear una asociación entre clases de entidad
  
1.  Haga clic en la clase de entidad que representa la clase primaria de la asociación, seleccione **agregar**y, a continuación, haga clic en **asociación**.  
  
2.  Compruebe que el valor correcto **clase primaria** está seleccionado en el **Editor de asociaciones** cuadro de diálogo.  
  
3.  Seleccione el **clase secundaria** en el cuadro combinado.  
  
4.  Seleccione el **propiedades de la asociación** que relacionan las clases. Por lo general, se asigna a la relación entre claves externas definida en la base de datos. Por ejemplo, en la asociación de Customers y Orders, el **propiedades de la asociación** representan el CustomerID de cada clase.  
  
5.  Haga clic en **Aceptar** para crear la asociación.  
  
## <a name="see-also"></a>Vea también
[LINQ to SQL herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[Tutorial: Crear clases LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
[Métodos de DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
[Representación de claves principales](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)