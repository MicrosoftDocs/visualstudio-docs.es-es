---
title: No se puede eliminar la propiedad &lt;property nombre &gt; | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aca36919cb4c82d6ca76e0f3eecbbacd48cde768
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667239"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>No se puede eliminar la propiedad &lt;property nombre &gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No se puede eliminar la propiedad \<property nombre > porque está establecida como la propiedad Discriminator para la herencia entre \<class nombre > y \<class >

 La propiedad seleccionada está establecida como **propiedad Discriminator** para la herencia entre las clases indicadas en el mensaje de error. Las propiedades no se pueden eliminar si participan en la configuración de la herencia entre clases de datos.

 Establezca la **propiedad Discriminator** en otra propiedad de la clase de datos para que se pueda eliminar correctamente la propiedad deseada.

### <a name="to-correct-this-error"></a>Para corregir este error

1. En Object Relational Designer, seleccione la línea de herencia que conecta las clases de datos indicadas en el mensaje de error.

2. Establezca la **propiedad Discriminator** en otra propiedad.

3. Intente de nuevo eliminar la propiedad.

## <a name="see-also"></a>Vea también
 [Cómo: configurar la herencia mediante la](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) herencia de clases de datos de Object Relational Designer [(o/r Designer)](../data-tools/data-class-inheritance-o-r-designer.md) [tutorial: crear clases de LINQ to SQL con la herencia de tabla única (o/r Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
