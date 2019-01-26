---
title: Comentarios para el usuario | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a9213440d0c3c3dbaa7c95e45bbf61386b60ff46
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55016193"
---
# <a name="feedback-to-the-user"></a>Comentarios para el usuario
En el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE), los comentarios visuales sobre la funcionalidad disponible se basa en la selección actual y el contexto de la selección global del usuario. En la tabla siguiente se enumera la funcionalidad que está disponible en los contextos de selección diferente.  
  
|Contexto de selección|Funcionalidad disponible|  
|-----------------------|-----------------------------|  
|IDE|Global|  
|Conjunto de productos actual|Cada producto.|  
|Jerarquía activa|Específico del tipo de jerarquía|  
|Elemento de la jerarquía activa|Específicos del tipo de elemento de jerarquía|  
|Documento activo|Específico del tipo de documento|  
|Ventana de nivel superior interfaz de múltiples documentos (MDI)|Específico del tipo de ventana|  
|Contexto de selección actual|Contexto de selección específico|  
  
 Si solo se muestran la funcionalidad de los usuarios necesitan y proporcionar continuamente selección coherente y comentarios del contexto de entorno, reducir la complejidad en el IDE. Las siguientes reglas se aplican siempre que se abre una ventana en el IDE:  
  
- Si la ventana cambia su contexto de selección, los comentarios de selección se indicarán claramente en la ventana y el **Ayuda dinámica** ventana, si se muestra, se actualiza para reflejar el contexto actual.  
  
- Si la ventana cambia el contexto de la selección global, todos los menús específicos del contexto, la ventana de la jerarquía activa y la barra de título de la aplicación se actualizan para reflejar el contexto actual.  
  
- La ventana debe exponer las propiedades de la selección actual en el **propiedades** ventana y, opcionalmente, si se muestra, el **páginas de propiedades** cuadro de diálogo.  
  
- Si no, la ventana Propiedades de la superficie o cambiar el contexto de la selección global, comentarios de selección no deben permanecer en la ventana cuando ya no es la ventana activa en el IDE.  
  
- Todas las ventanas de documento específico continuamente deben reflejar el documento activo.  
  
- Menús, barras de herramientas y la barra de título de la aplicación deben reflejar la ventana de cliente de la interfaz de múltiples documentos (MDI) superior.  
  
  Por ejemplo, al ver el código HTML de un **formulario Web Forms** dentro de una aplicación Web de Visual Basic se abre el proyecto y el usuario selecciona un `<td>` etiqueta, los comentarios se proporcionan en la siguiente manera:  
  
- Selección se indica en la ventana activa y se refleja en el **propiedades** ventana.  
  
- Específico del documento **cuadro de herramientas** se actualiza para reflejar el documento activo.  
  
- El **Editor** barra de herramientas y **tabla** se muestra el menú y la barra de título se actualiza para reflejar la ventana del formulario Web.  
  
- La ventana de la jerarquía activa, que suele ser **el Explorador de soluciones**y su actualización de la barra de título para reflejar el contexto actual y la información contextual **proyecto** comandos de menú aplican ahora a la Web activo Proyecto de aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)   
 [Las jerarquías y selección](../../extensibility/internals/hierarchies-and-selection.md)