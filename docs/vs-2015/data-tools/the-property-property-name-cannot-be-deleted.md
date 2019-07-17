---
title: La propiedad &lt;nombre de la propiedad&gt; no se puede eliminar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 50e91c47ef848eda51fe71c9dce09cd1ea4893a8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152095"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>La propiedad &lt;nombre de la propiedad&gt; no se puede eliminar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La propiedad \<nombre de propiedad > no se puede eliminar porque se está usando como propiedad Discriminator para la herencia entre \<nombre de clase > y \<nombre de clase >  
  
 La propiedad seleccionada está establecida como **propiedad Discriminator** para la herencia entre las clases indicadas en el mensaje de error. Las propiedades no se pueden eliminar si participan en la configuración de la herencia entre clases de datos.  
  
 Establezca la **propiedad Discriminator** en otra propiedad de la clase de datos para que se pueda eliminar correctamente la propiedad deseada.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1. En Object Relational Designer, seleccione la línea de herencia que conecta las clases de datos indicadas en el mensaje de error.  
  
2. Establezca la **propiedad Discriminator** en otra propiedad.  
  
3. Intente de nuevo eliminar la propiedad.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Configurar la herencia mediante Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [Herencia de clases de datos (Object Relational Designer)](../data-tools/data-class-inheritance-o-r-designer.md)   
 [Tutorial: Crear clases de LINQ to SQL mediante la herencia de tabla única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
