---
title: "C&#243;mo: Crear una asociaci&#243;n (relaci&#243;n) entre las clases de LINQ to SQL (Object Relational Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Crear una asociaci&#243;n (relaci&#243;n) entre las clases de LINQ to SQL (Object Relational Designer)
Las asociaciones entre clases de entidades en [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] son similares a las relaciones entre tablas en una base de datos.Puede crear asociaciones entre clases de entidades mediante el cuadro de diálogo **Editor de asociaciones**.  
  
 Si utiliza el **Editor de asociaciones** para crear una asociación, deberá seleccionar una clase primaria y otra secundaria.La clase primaria es la clase de entidad que contiene la clave principal y la clase secundaria es la clase de entidad que contiene la clave externa.Por ejemplo, si se crearon clases de entidad y se asignaron a las tablas Customers y Orders de Northwind, la clase Customer sería la clase primaria y Order, la secundaria.  
  
> [!NOTE]
>  Al arrastrar las tablas desde el **Explorador de servidores**\/**Explorador de bases de datos** al [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\), las asociaciones se crearán automáticamente en función de las relaciones existentes entre las claves externas en la base de datos.  
  
 Una vez creada una asociación, al seleccionarla en el Object Relational Designer, se mostrarán algunas propiedades configurables en la ventana **Propiedades**.\(La asociación es la línea entre las clases relacionadas\). En la tabla siguiente, se proporcionan descripciones de las propiedades de una asociación.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|**Cardinality**|Controla si la asociación es de uno a varios o de uno a uno.|  
|**Child Property**|Especifica si se debe crear una propiedad en el registro primario que es una colección o se debe hacer referencia a los registros secundarios en el lado de las claves externas de la asociación.Por ejemplo, en la asociación entre Customer y Order, si la **Propiedad secundaria** se establece en **True**, en la clase primaria se creará una propiedad denominada Orders.|  
|**Parent Property**|La propiedad de la clase secundaria que hace referencia a la clase primaria asociada.Por ejemplo, en la asociación entre Customer y Order, en la clase Order se creará una propiedad denominada Customer que hará referencia al cliente asociado de un pedido.|  
|**Participating Properties**|Muestra las propiedades de asociación y proporciona un botón de **puntos suspensivos** \(...\) que abre de nuevo el cuadro de diálogo **Editor de asociaciones**.|  
|**Unique**|Especifica si las columnas de destino externas tienen una restricción de unicidad.|  
  
### Para crear una asociación entre clases de entidad  
  
1.  Haga clic con el botón secundario en la clase de entidad que represente la clase primaria de la asociación, seleccione **Agregar** y, a continuación, presione **Asociación**.  
  
2.  Compruebe que se haya seleccionado la **Clase primaria** correcta en el cuadro de diálogo **Editor de asociaciones**.  
  
3.  En el cuadro combinado, seleccione **Clase secundaria**.  
  
4.  Seleccione las **Propiedades de la asociación** que relacionan las clases.Por lo general, se asigna a la relación entre claves externas definida en la base de datos.Por ejemplo, en la asociación de Customers y Orders, las **Propiedades de la asociación** representan el CustomerID de cada clase.  
  
5.  Haga clic en **Aceptar** para crear la asociación.  
  
## Vea también  
 [Información general sobre Object Relational Designer](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Tutorial: Crear clases de LINQ to SQL \(Object Relational Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ a SQL](../Topic/LINQ%20to%20SQL.md)   
 [Métodos DataContext \(Object Relational Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Cómo: Representar claves principales](../Topic/How%20to:%20Represent%20Primary%20Keys.md)