---
title: La propiedad &lt;nombre de la propiedad&gt; no se puede eliminar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: b3a896e64e048a5104bca84b726c730d4d9d524a
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
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