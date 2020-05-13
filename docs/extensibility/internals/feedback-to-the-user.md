---
title: Comentarios al usuario ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46b9190b16b9aa444384847bf209ccca50c7f768
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708412"
---
# <a name="feedback-to-the-user"></a>Comentarios al usuario
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE), la retroalimentación visual con respecto a la funcionalidad disponible se basa en el contexto de selección actual y de selección global del usuario. En la tabla siguiente se muestra la funcionalidad que está disponible en diferentes contextos de selección.

|Contexto de selección|Funcionalidad disponible|
|-----------------------|-----------------------------|
|IDE|Global|
|Conjunto de productos actual|Producto específico|
|Jerarquía activa|Tipo de jerarquía específico|
|Elemento jerárquico activo|Tipo de artículo de jerarquía específico|
|Documento activo|Tipo de documento específico|
|Ventana de interfaz de varios documentos (MDI) superior|Tipo de ventana específico|
|Contexto de selección actual|Contexto de selección específico|

 Si solo expone la funcionalidad que necesitan los usuarios y proporciona continuamente una selección coherente y comentarios de contexto de entorno, reducirá la complejidad en el IDE. Las siguientes reglas se aplican cada vez que se abre una ventana en el IDE:

- Si la ventana cambia su contexto de selección, los comentarios de selección se indican claramente en la ventana y la ventana **Ayuda dinámica,** si se muestra, se actualiza para reflejar el contexto actual.

- Si la ventana cambia el contexto de selección global, todos los menús específicos del contexto, la ventana de jerarquía activa y la barra de título de la aplicación se actualizan para reflejar el contexto actual.

- La ventana debe exponer las propiedades de la selección actual en la ventana **Propiedades** y, opcionalmente, si se muestra, el cuadro de diálogo **Páginas** de propiedades.

- Si la ventana no expone las propiedades o cambia el contexto de selección global, los comentarios de selección no deben permanecer en la ventana cuando ya no es la ventana activa en el IDE.

- Todas las ventanas de herramientas específicas del documento deben reflejar continuamente el documento activo.

- Los menús, las barras de herramientas y la barra de título de la aplicación deben reflejar la ventana de cliente de interfaz de varios documentos (MDI) superior.

  Por ejemplo, cuando se abre la vista HTML de un **formulario web** dentro `<td>` de un proyecto de aplicación web de Visual Basic y el usuario selecciona una etiqueta, los comentarios se proporcionan de la siguiente manera:

- La selección se indica en la ventana activa y se refleja en la ventana **Propiedades.**

- El cuadro de **herramientas** específico del documento se actualiza para reflejar el documento activo.

- Se muestran la barra de herramientas **Editor** y el menú **Tabla** y la barra de título se actualiza para reflejar la ventana Formulario web.

- La ventana de jerarquía activa, que suele ser el Explorador de **soluciones,** y su barra de título se actualizan para reflejar el contexto actual y los comandos de menú **Proyecto** contextuales ahora se aplican al proyecto de aplicación web activo.

## <a name="see-also"></a>Vea también
- [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)
- [Jerarquías y selección](../../extensibility/internals/hierarchies-and-selection.md)
