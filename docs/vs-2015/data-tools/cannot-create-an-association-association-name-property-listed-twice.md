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
ms.openlocfilehash: dd366f6bc572798e1115991afccb2b39eb8f9f6d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091582"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>No se puede crear una asociación &lt;nombre de asociación&gt;; la propiedad aparece dos veces.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No se puede crear una asociación \<nombre de asociación>. La misma propiedad aparece más de una vez: \<nombre de propiedad>.  
  
 Las asociaciones las define el comando **Propiedades de la asociación** seleccionado en el cuadro de diálogo **Editor de asociaciones**. Las propiedades pueden aparecer solamente una vez para cada clase en la asociación.  
  
 La propiedad mencionada en el mensaje aparece más de una vez en las **Propiedades de la asociación** de la clase primaria o secundaria.  
  
### <a name="to-resolve-this-condition"></a>Para resolver esta condición  
  
- Lea el mensaje y fíjese en la propiedad especificada en el mensaje.  
  
- Haga clic en **Aceptar** para descartar el cuadro de mensaje.  
  
- Examine las **Propiedades de la asociación** y quite las entradas duplicadas.  
  
- Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL Tools en Visual Studio](http://msdn.microsoft.com/library/a57e82d5-f7e4-4894-8add-3d9ba4fce186)   
 [Cómo: Crear una asociación (relación) entre clases LINQ to SQL (Object Relational Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Tutorial: Crear clases LINQ to SQL (Object Relational Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
