---
title: Las Interfaces heredadas en el Editor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 044bf36845be70290291b79dee255c452f56f0a0
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694418"
---
# <a name="legacy-interfaces-in-the-editor"></a>Interfaces heredadas en el editor
El editor de Visual Studio puede tener acceso desde las interfaces heredadas. El SDK de Visual Studio incluye los adaptadores que se conoce como *las correcciones de compatibilidad*, que permiten estas interfaces interactuar con el nuevo editor. No obstante, se recomienda que actualice el código heredado para usar el nuevo editor de API. El código funcionará mejor y puede usar las nuevas tecnologías como Windows Presentation Foundation (WPF) y Managed Extensibility Framework (MEF).

## <a name="related-topics"></a>Temas relacionados

| Título | Descripción |
| - | - |
| [Adaptar código heredado en el editor](../extensibility/adapting-legacy-code-to-the-editor.md) | Explica cómo adaptar el código al nuevo editor. |
| [Comportamiento nuevo o modificado con los adaptadores de editor](../extensibility/new-or-changed-behavior-with-editor-adapters.md) | Explica cómo el comportamiento de los adaptadores de editor difiere de las versiones anteriores del editor. |
| [Dentro del editor de núcleo](../extensibility/inside-the-core-editor.md) | Describe los distintos componentes de las versiones anteriores del editor. |
| [Crear una instancia el editor básico mediante la API heredada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md) | Explica cómo usar la API heredada para crear una instancia del editor de núcleo. |
| [Generadores de editores](../extensibility/editor-factories.md) | Explica cómo usar generadores de editores con la API heredada. |
| [Cómo: Registrar tipos de archivo del editor](../extensibility/how-to-register-editor-file-types.md) | Explica cómo vincular una extensión de nombre de archivo en el editor. |
| [Tutorial: Crear un núcleo de editor y registrar un tipo de archivo del editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md) | Explica cómo crear un núcleo de editor y una extensión de nombre de archivo un vínculo a él. |
| [Cómo: Proporcionar contexto para los editores](../extensibility/how-to-provide-context-for-editors.md) | Se explica cómo proporcionar contexto para el editor. |
| [Servicios de lenguaje y el editor básico](../extensibility/language-services-and-the-core-editor.md) | Explica las interacciones entre un servicio de lenguaje y un editor. |
| [Tener acceso al búfer de texto mediante el uso de la API heredada](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md) | Explica cómo tener acceso al búfer de texto mediante el uso de la API heredada. |
| [Vista de acceso a Text mediante el uso de la API heredada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md) | Explica cómo obtener acceso a la vista de texto mediante el uso de la API heredada. |
| [Personalizar las ventanas de código mediante el uso de la API heredada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md) | Explica cómo personalizar las ventanas de código mediante el uso de la API heredada. |
| [Niveles de acceso a texto mediante el uso de la API heredada](../extensibility/accessing-text-layers-by-using-the-legacy-api.md) | Explica cómo obtener acceso a diferentes capas de texto mediante el uso de la API heredada. |
| [Utilice marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md) | Explica cómo agregar marcadores de texto mediante la API heredada. |
| [Personalizar menús y controles de editor mediante el uso de la API heredada](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md) | Explica cómo personalizar los controles de editor mediante el uso de la API heredada. |
| [Administración de deshacer y rehacer mediante el uso de la API heredada](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md) | Explica cómo administrar deshacer y rehacer mediante el uso de la API heredada. |
| [Cómo: Implementar la buscar y reemplazar el mecanismo de](../extensibility/how-to-implement-the-find-and-replace-mechanism.md) | Explica cómo administrar buscar y reemplazar mediante la API heredada. |
| [Cómo: Suprimir notificaciones de cambio de archivo](../extensibility/how-to-suppress-file-change-notifications.md) | Explica cómo suprimir notificaciones de cambio de archivo mediante la API heredada. |
| [Creación de diseñadores y editores personalizados](../extensibility/creating-custom-editors-and-designers.md) | Explica cómo crear editores y diseñadores personalizados. |
| [Desarrollar un servicio de lenguaje heredado](../extensibility/internals/developing-a-legacy-language-service.md) | Proporciona vínculos a documentos sobre las características que proporcionan capacidades de personalización para el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principal agregando compatibilidad para un servicio de lenguaje. |
| [Utilizar fuentes y colores](../extensibility/using-fonts-and-colors.md) | Explica cómo usar fuentes y colores con las interfaces heredadas. |
