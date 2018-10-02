---
title: La propiedad &lt;nombre de la propiedad&gt; no se puede eliminar porque participa en la asociación &lt;nombre de la asociación&gt; | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6983d52615219c386b049eea33f9f911956c6d59
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575046"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>La propiedad &lt;nombre de la propiedad&gt; no se puede eliminar porque participa en la asociación &lt;nombre de asociación&gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [la propiedad &lt;nombre de la propiedad&gt; no se puede eliminar porque participa en la asociación &lt;nombre de la asociación&gt;](https://docs.microsoft.com/visualstudio/data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name).  
  
  
La propiedad seleccionada está establecida como el **propiedad de asociación** para la asociación entre las clases indicadas en el mensaje de error. Las propiedades no se pueden eliminar si participan en una asociación entre clases de datos.  
  
 Establecer el **propiedad de asociación** en otra propiedad de la clase de datos para habilitar la eliminación correcta de la propiedad deseada.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  En Object Relational Designer, seleccione la línea de asociación que conecta las clases de datos indicadas en el mensaje de error.  
  
2.  Haga doble clic en la línea para abrir el **Editor de asociaciones** cuadro de diálogo.  
  
3.  Quite la propiedad de la **propiedades de la asociación**.  
  
4.  Intente de nuevo eliminar la propiedad.  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Cómo: crear una asociación (relación) entre clases LINQ to SQL (Object Relational Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Tutorial: Crear clases LINQ to SQL (Object Relational Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)

