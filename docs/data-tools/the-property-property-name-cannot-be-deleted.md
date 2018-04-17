---
title: La propiedad &lt;nombre de la propiedad&gt; no se puede eliminar | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: aa07de56e8763eb6da94e8846c97af0daf777620
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>La propiedad &lt;nombre de la propiedad&gt; no se puede eliminar
La propiedad \<nombre de propiedad > no se puede eliminar porque está establecido como el **propiedad Discriminator** para la herencia entre \<nombre de clase > y \<nombre de clase >  
  
 La propiedad seleccionada está establecida como la **propiedad Discriminator** para la herencia entre las clases indicadas en el mensaje de error. Las propiedades no se pueden eliminar si participan en la configuración de la herencia entre clases de datos.  
  
 Establecer el **propiedad Discriminator** en otra propiedad de la clase de datos para permitir la eliminación correcta de la propiedad deseada.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  En Object Relational Designer, seleccione la línea de herencia que conecta las clases de datos indicadas en el mensaje de error.  
  
2.  Establecer el **discriminador** propiedad en otra propiedad.  
  
3.  Intente de nuevo eliminar la propiedad.  
  
## <a name="see-also"></a>Vea también
[Mensajes de Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL de las herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)