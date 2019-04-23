---
title: No se puede crear una asociación &lt;nombre de la asociación&gt; -propiedad aparece dos veces | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b9592605a25c76b4ea17b6efe91363d59585f56e
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59660975"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>No se puede crear una asociación &lt;nombre de asociación&gt;; la propiedad aparece dos veces.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No se puede crear una asociación \<nombre de asociación>. La misma propiedad aparece más de una vez: \<nombre de propiedad>.  
  
 Las asociaciones las define el comando **Propiedades de la asociación** seleccionado en el cuadro de diálogo **Editor de asociaciones**. Las propiedades pueden aparecer solamente una vez para cada clase en la asociación.  
  
 La propiedad mencionada en el mensaje aparece más de una vez en las **Propiedades de la asociación** de la clase primaria o secundaria.  
  
### <a name="to-resolve-this-condition"></a>Para resolver esta condición  
  
-   Lea el mensaje y fíjese en la propiedad especificada en el mensaje.  
  
-   Haga clic en **Aceptar** para descartar el cuadro de mensaje.  
  
-   Examine las **Propiedades de la asociación** y quite las entradas duplicadas.  
  
-   Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL Tools en Visual Studio](http://msdn.microsoft.com/library/a57e82d5-f7e4-4894-8add-3d9ba4fce186)   
 [Cómo: Crear una asociación (relación) entre clases LINQ to SQL (Object Relational Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Tutorial: Crear clases LINQ to SQL (Object Relational Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
