---
title: La propiedad &lt;nombre de la propiedad&gt; no se puede eliminar porque participa en la asociación &lt;nombre de la asociación&gt; | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 52dc1d42ab8fff879bd290fe1a9c9aa2ca0a08c0
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700316"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>No se puede eliminar la propiedad &lt;nombre de propiedad&gt; porque participa en la asociación &lt;nombre de asociación&gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La propiedad seleccionada está establecida como **propiedad de asociación** para la asociación entre las clases indicadas en el mensaje de error. Las propiedades no se pueden eliminar si participan en una asociación entre clases de datos.  
  
 Establezca la **propiedad de asociación** en otra propiedad de la clase de datos para que se pueda eliminar correctamente la propiedad deseada.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1. En Object Relational Designer, seleccione la línea de asociación que conecta las clases de datos indicadas en el mensaje de error.  
  
2. Haga doble clic en la línea para abrir el cuadro de diálogo **Editor de asociaciones**.  
  
3. Quite la propiedad de **Propiedades de la asociación**.  
  
4. Intente de nuevo eliminar la propiedad.  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Cómo: Crear una asociación (relación) entre clases LINQ to SQL (Object Relational Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Tutorial: Crear clases LINQ to SQL (Object Relational Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
