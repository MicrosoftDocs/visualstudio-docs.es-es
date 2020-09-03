---
title: No se &lt; puede eliminar el nombre de la propiedad de propiedad &gt; | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667239"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>No se &lt; puede eliminar el nombre de la propiedad de propiedad &gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No se \<property name> puede eliminar la propiedad porque está establecida como la propiedad Discriminator para la herencia entre \<class name> y \<class name>

 La propiedad seleccionada está establecida como **propiedad Discriminator** para la herencia entre las clases indicadas en el mensaje de error. Las propiedades no se pueden eliminar si participan en la configuración de la herencia entre clases de datos.

 Establezca la **propiedad Discriminator** en otra propiedad de la clase de datos para que se pueda eliminar correctamente la propiedad deseada.

### <a name="to-correct-this-error"></a>Para corregir este error

1. En Object Relational Designer, seleccione la línea de herencia que conecta las clases de datos indicadas en el mensaje de error.

2. Establezca la **propiedad Discriminator** en otra propiedad.

3. Intente de nuevo eliminar la propiedad.

## <a name="see-also"></a>Consulte también
 [Cómo: configurar la herencia mediante la](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) herencia de clases de datos de Object Relational Designer [(o/r Designer)](../data-tools/data-class-inheritance-o-r-designer.md) [tutorial: crear clases de LINQ to SQL con la herencia de tabla única (o/r Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
