---
title: Comentarios al usuario | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3a5e31eb2acb50d9803bedd77e48d0821cbaea61
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="feedback-to-the-user"></a>Comentarios para el usuario
En el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE), los comentarios visuales sobre la funcionalidad disponible se basa en la selección actual y el contexto de selección global del usuario. La tabla siguiente muestra la funcionalidad que está disponible en selección diferentes contextos.  
  
|Contexto de selección|Funcionalidad disponible|  
|-----------------------|-----------------------------|  
|IDE|Global|  
|Conjunto de productos actual|Cada producto.|  
|Jerarquía activa|Específico del tipo de jerarquía|  
|Elemento de la jerarquía activa|Específicas de tipo de elemento de jerarquía|  
|Documento activo|Específico del tipo de documento|  
|Ventana de nivel superior interfaz de múltiples documentos (MDI)|Específico del tipo de ventana|  
|Contexto de la selección actual|Contexto de selección específico|  
  
 Si solo expuesta la funcionalidad de los usuarios necesitan y proporcionar continuamente selección coherente y comentarios de contexto del entorno, reducir la complejidad en el IDE. Cada vez que se abre una ventana en el IDE, se aplican las siguientes reglas:  
  
-   Si la ventana cambia su contexto de selección, comentarios de la selección se indicarán claramente en la ventana y la ventana Ayuda dinámica, si se muestra, se actualiza para reflejar el contexto actual.  
  
-   Si la ventana cambia el contexto de la selección global, todos los menús específicos del contexto, la ventana de la jerarquía activa y la barra de título de la aplicación se actualizan para reflejar el contexto actual.  
  
-   La ventana debe expuesta propiedades para la selección actual en el **propiedades** ventana y, opcionalmente, si se muestra, la **páginas de propiedades** cuadro de diálogo.  
  
-   Si la ventana no expuesta propiedades o cambiar el contexto de selección global, comentarios de la selección no deberían permanecer en la ventana cuando ya no es la ventana activa en el IDE.  
  
-   Todas las ventanas de herramienta específica del documento continuamente deben reflejar el documento activo.  
  
-   Los menús, barras de herramientas y la barra de título de la aplicación deben reflejar la ventana de cliente de nivel superior interfaz de múltiples documentos (MDI).  
  
 Por ejemplo, cuando se abre la vista HTML de un formulario Web Forms dentro de un proyecto de aplicación Web de Visual Basic y el usuario selecciona un `<td>` etiqueta, los comentarios se proporcionan en la siguiente manera:  
  
-   Selección se indica en la ventana activa y se refleja en el **propiedades** ventana.  
  
-   Específico del documento **cuadro de herramientas** se actualiza para reflejar el documento activo.  
  
-   El **Editor** barra de herramientas y **tabla** se muestra el menú y la barra de título se actualiza para reflejar la ventana del formulario Web Forms.  
  
-   La ventana de la jerarquía activa, que suele ser **el Explorador de soluciones**y su actualización de la barra de título para reflejar el contexto actual y la contextual **proyecto** comandos de menú se aplicarán ahora a la Web activo Proyecto de aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)   
 [Jerarquías y selección](../../extensibility/internals/hierarchies-and-selection.md)