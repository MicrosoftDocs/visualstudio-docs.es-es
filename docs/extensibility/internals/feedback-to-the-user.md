---
title: Comentarios al usuario | Microsoft Docs
description: Obtenga información sobre cómo proporcionar comentarios visuales al usuario sobre la funcionalidad disponible en el entorno de desarrollo integrado (IDE) de Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d8f3f79a61729a641ee7c046ddd196a648469fb3
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480530"
---
# <a name="feedback-to-the-user"></a>Comentarios al usuario
En el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE), los comentarios visuales sobre la funcionalidad disponible se basan en la selección actual del usuario y en el contexto de selección global. En la tabla siguiente se enumeran las funciones que están disponibles en diferentes contextos de selección.

|Contexto de selección|Funcionalidad disponible|
|-----------------------|-----------------------------|
|IDE|Global|
|Conjunto de productos actual|Específico del producto|
|Jerarquía activa|Específico del tipo de jerarquía|
|Elemento de la jerarquía activa|Específico del tipo de elemento de la jerarquía|
|Documento activo|Específico del tipo de documento|
|Ventana de la interfaz de múltiples documentos (MDI) de nivel superior|Específico del tipo de ventana|
|Contexto de selección actual|Específico del contexto de selección|

 Si solo tiene la funcionalidad que necesitan los usuarios y proporciona continuamente una selección coherente y comentarios sobre el contexto del entorno, reduce la complejidad en el IDE. Siempre que se abre una ventana en el IDE, se aplican las siguientes reglas:

- Si la ventana cambia su contexto de selección, los comentarios de la selección se indican claramente en la ventana y la ventana **Ayuda dinámica** , si se muestra, se actualiza para reflejar el contexto actual.

- Si la ventana cambia el contexto de selección global, todos los menús específicos del contexto, la ventana de jerarquía activa y la barra de título de la aplicación se actualizan para reflejar el contexto actual.

- La ventana debe mostrar las propiedades de la selección actual en la ventana **propiedades** y, opcionalmente, si se muestra, el cuadro de diálogo **páginas de propiedades** .

- Si la ventana no tiene propiedades o cambia el contexto de selección global, los comentarios de la selección no deben permanecer en la ventana cuando ya no sea la ventana activa en el IDE.

- Todas las ventanas de herramientas específicas del documento deben reflejar continuamente el documento activo.

- Los menús, las barras de herramientas y la barra de título de la aplicación deben reflejar la ventana de cliente de la interfaz de múltiples documentos (MDI).

  Por ejemplo, cuando se abre la vista HTML de un **formulario web** dentro de un proyecto de aplicación web de Visual Basic y el usuario selecciona una `<td>` etiqueta, los comentarios se proporcionan de la siguiente manera:

- La selección se indica en la ventana activa y se refleja en la ventana **propiedades** .

- El **cuadro de herramientas** específico del documento se actualiza para reflejar el documento activo.

- Se muestran la barra de herramientas y el menú de **tabla** del **Editor** y la barra de título se actualiza para reflejar la ventana formulario Web.

- La ventana de jerarquía activa, que normalmente se **Explorador de soluciones**, y la actualización de la barra de título para reflejar el contexto actual y los comandos del menú contextual del **proyecto** se aplican ahora al proyecto de aplicación Web activo.

## <a name="see-also"></a>Consulte también
- [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)
- [Jerarquías y selección](../../extensibility/internals/hierarchies-and-selection.md)
