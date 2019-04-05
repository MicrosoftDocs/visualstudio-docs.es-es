---
title: Adjuntar cadenas de referencia a elementos del modelo UML | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending, reference strings
ms.assetid: 15dbed99-efce-42fe-a768-714a5804e7d1
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bd5a1ae4abc2e0b5c508b7b77160bbf8da3bb45e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988552"
---
# <a name="attach-reference-strings-to-uml-model-elements"></a>Adjuntar cadenas de referencia a elementos de modelo UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede escribir código para asociar cadenas arbitrarias a elementos de modelo. Una cadena podría ser, por ejemplo, un URI, el resultado almacenado en la caché de un cálculo o una referencia de ModelBus a un elemento de otro modelo. Cada cadena se incluye en un objeto IReference. Se puede asociar un número cualquiera de objetos IReference a cada elemento de modelo.  
  
 Cada objeto IReference tiene un nombre. Puede usar este nombre para indicar cómo se debe interpretar el valor de referencia. Por ejemplo, puede establecer el nombre como “URI” para indicar que el valor se debe interpretar como un URI. Hay algunos valores de nombres de referencia predefinidos que usan las herramientas de modelado.  
  
## <a name="attaching-a-reference-to-an-ielement"></a>Asociación de una referencia a un IElement  
 Para usar los siguientes métodos, debe agregar una referencia a:  
  
 Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll  
  
 Debe insertar esta directiva en el código:  
  
 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`  
  
|Llamada al método|Descripción|  
|-----------------|-----------------|  
|`element.AddReference (nameString, valueString, duplicatesAllowed)`|Crea un objeto `IReference` con el nombre y las cadenas de valores proporcionados, y lo vincula a `element`. Devuelve `IReference`.<br /><br /> Produce una excepción si `duplicatesAllowed` es false y ya hay un objeto `IReference` con el mismo nombre asociado a `element`.|  
|`element.GetReferences(name)`|Devuelve todos los objetos `IReference` vinculados a `element` que tienen el `name` proporcionado.|  
|`element.DeleteAllReferences(name)`|Elimina todos los objetos `IReference` vinculados al elemento que tienen el nombre proporcionado.|  
|`reference.Delete()`|Elimina este objeto `IReference`.|  
|`ReferenceConstants.WorkItem`|Valor usado para dar un nombre a las referencias de elemento de trabajo.|  
  
## <a name="see-also"></a>Vea también  
 [Definir un controlador de vínculo de elemento de trabajo](../modeling/define-a-work-item-link-handler.md)   
 [Definir e instalar una extensión de modelado](../modeling/define-and-install-a-modeling-extension.md)   
 [Programar con la API de UML](../modeling/programming-with-the-uml-api.md)
