---
title: La propiedad &lt;nombre de la propiedad&gt; no se puede eliminar | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 98b065500c9c881a7190b59c4d70a0433eb8864c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186529"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>La propiedad &lt;nombre de la propiedad&gt; no se puede eliminar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
La propiedad \<nombre de propiedad > no se puede eliminar porque se está usando como propiedad Discriminator para la herencia entre \<nombre de clase > y \<nombre de clase >  
  
 La propiedad seleccionada está establecida como el **propiedad Discriminator** para la herencia entre las clases indicadas en el mensaje de error. Las propiedades no se pueden eliminar si participan en la configuración de la herencia entre clases de datos.  
  
 Establecer el **propiedad Discriminator** en otra propiedad de la clase de datos para habilitar la eliminación correcta de la propiedad deseada.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  En Object Relational Designer, seleccione la línea de herencia que conecta las clases de datos indicadas en el mensaje de error.  
  
2.  Establecer el **discriminador** propiedad en otra propiedad.  
  
3.  Intente de nuevo eliminar la propiedad.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: configurar la herencia mediante Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [Herencia de clases de datos (Object Relational Designer)](../data-tools/data-class-inheritance-o-r-designer.md)   
 [Tutorial: Crear clases de LINQ to SQL mediante la herencia de tabla única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)

