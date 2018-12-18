---
title: 'Cómo: crear una asociación (relación) entre clases LINQ to SQL (Object Relational Designer) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5c739fcf11cec7eb841b99e58b01ada32cfdfd49
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209370"
---
# <a name="how-to-create-an-association-relationship-between-linq-to-sql-classes-or-designer"></a>Cómo: crear una asociación (relación) entre clases LINQ to SQL (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Las asociaciones entre clases de entidades en [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] son similares a las relaciones entre tablas en una base de datos. Puede crear asociaciones entre las clases de entidad mediante el **Editor de asociaciones** cuadro de diálogo.  
  
 Debe seleccionar una clase primaria y otra secundaria cuando se usa el **Editor de asociaciones** cuadro de diálogo para crear una asociación. La clase primaria es la clase de entidad que contiene la clave principal y la clase secundaria es la clase de entidad que contiene la clave externa. Por ejemplo, si se crearon clases de entidad y se asignaron a las tablas Customers y Orders de Northwind, la clase Customer sería la clase primaria y Order, la secundaria.  
  
> [!NOTE]
>  Al arrastrar las tablas de **Explorador de servidores**/**Database Explorer** hasta la [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]), las asociaciones se crean automáticamente en función de las existentes relaciones de clave externa en la base de datos.  
  
 Después de crear una asociación, al seleccionar la asociación en el Object Relational Designer, hay algunas propiedades configurables en el **propiedades** ventana. (La asociación es la línea entre las clases relacionadas). En la tabla siguiente, se proporcionan descripciones de las propiedades de una asociación.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|**cardinalidad**|Controla si la asociación es de uno a varios o de uno a uno.|  
|**Propiedad secundaria**|Especifica si se debe crear una propiedad en el registro primario que es una colección o se debe hacer referencia a los registros secundarios en el lado de las claves externas de la asociación. Por ejemplo, en la asociación entre Customer y Order, si la **propiedad secundaria** está establecido en **True**, se crea una propiedad denominada Orders en la clase primaria.|  
|**Propiedad primaria**|La propiedad de la clase secundaria que hace referencia a la clase primaria asociada. Por ejemplo, en la asociación entre Customer y Order, en la clase Order se creará una propiedad denominada Customer que hará referencia al cliente asociado de un pedido.|  
|**Propiedades de participantes**|Muestra las propiedades de asociación y proporciona un **puntos suspensivos** botón (…) que abre de nuevo el **Editor de asociaciones** cuadro de diálogo.|  
|**único**|Especifica si las columnas de destino externas tienen una restricción de unicidad.|  
  
### <a name="to-create-an-association-between-entity-classes"></a>Para crear una asociación entre clases de entidad  
  
1.  Haga clic en la clase de entidad que representa la clase primaria de la asociación, seleccione **agregar**y, a continuación, haga clic en **asociación**.  
  
2.  Compruebe que el valor correcto **clase primaria** está seleccionado en el **Editor de asociaciones** cuadro de diálogo.  
  
3.  Seleccione el **clase secundaria** en el cuadro combinado.  
  
4.  Seleccione el **propiedades de la asociación** que relacionan las clases. Por lo general, se asigna a la relación entre claves externas definida en la base de datos. Por ejemplo, en la asociación de Customers y Orders, el **propiedades de la asociación** representan el CustomerID de cada clase.  
  
5.  Haga clic en **Aceptar** para crear la asociación.  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Tutorial: Crear clases LINQ to SQL (Object Relational Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Representación de claves principales](http://msdn.microsoft.com/library/63c65289-6539-42b2-8493-891c232018fa)

