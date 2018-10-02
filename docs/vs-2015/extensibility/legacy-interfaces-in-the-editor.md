---
title: Las Interfaces heredadas en el Editor | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1ae8f087a9f52ca2eff130b7972c2cd9d68a139f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578127"
---
# <a name="legacy-interfaces-in-the-editor"></a>Interfaces heredadas en el Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Interfaces heredadas en el Editor de](https://docs.microsoft.com/visualstudio/extensibility/legacy-interfaces-in-the-editor).  
  
El editor de Visual Studio puede tener acceso desde las interfaces heredadas. El SDK de Visual Studio incluye los adaptadores que se conoce como *las correcciones de compatibilidad*, que permiten estas interfaces interactuar con el nuevo editor. No obstante, se recomienda que actualice el código heredado para usar el nuevo editor de API. El código funcionará mejor y puede usar las nuevas tecnologías como Windows Presentation Foundation (WPF) y Managed Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Adaptación del código heredado en el editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Explica cómo adaptar el código al nuevo editor.|  
|[Comportamiento nuevo o modificado con los adaptadores del editor](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Explica cómo el comportamiento de los adaptadores de editor difiere de las versiones anteriores del editor.|  
|[Dentro del editor principal](../extensibility/inside-the-core-editor.md)|Describe los distintos componentes de las versiones anteriores del editor.|  
|[Creación de instancias del editor principal mediante la API heredada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Explica cómo usar la API heredada para crear una instancia del editor de núcleo.|  
|[Generadores del editor](../extensibility/editor-factories.md)|Explica cómo usar generadores de editores con la API heredada.|  
|[Cómo: Registrar tipos de archivo del editor](../extensibility/how-to-register-editor-file-types.md)|Explica cómo vincular una extensión de nombre de archivo en el editor.|  
|[Tutorial: Crear un editor principal y registrar un tipo de archivo del editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Explica cómo crear un núcleo de editor y una extensión de nombre de archivo un vínculo a él.|  
|[Cómo: Proporcionar el contexto para los editores](../extensibility/how-to-provide-context-for-editors.md)|Se explica cómo proporcionar contexto para el editor.|  
|[Servicios de lenguaje y editor principal](../extensibility/language-services-and-the-core-editor.md)|Explica las interacciones entre un servicio de lenguaje y un editor.|  
|[Acceso al búfer de texto mediante la API heredada](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Explica cómo tener acceso al búfer de texto mediante el uso de la API heredada.|  
|[Acceso a la vista de texto mediante la API heredada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Explica cómo obtener acceso a la vista de texto mediante el uso de la API heredada.|  
|[Personalización de las ventanas de código mediante la API heredada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Explica cómo personalizar las ventanas de código mediante el uso de la API heredada.|  
|[Acceso a las capas de texto mediante la API heredada](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Explica cómo obtener acceso a diferentes capas de texto mediante el uso de la API heredada.|  
|[Uso de marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md)|Explica cómo agregar marcadores de texto mediante la API heredada.|  
|[Personalización de los controles y los menús del editor mediante la API heredada](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Explica cómo personalizar los controles de editor mediante el uso de la API heredada.|  
|[Administración de las fases de reversión y puesta al día mediante la API heredada](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Explica cómo administrar deshacer y rehacer mediante el uso de la API heredada.|  
|[Cómo: Implementar el mecanismo Buscar y reemplazar](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Explica cómo administrar buscar y reemplazar mediante la API heredada.|  
|[Cómo: Suprimir las notificaciones de cambios de archivos](../extensibility/how-to-suppress-file-change-notifications.md)|Explica cómo suprimir notificaciones de cambio de archivo mediante la API heredada.|  
|[Creación de diseñadores y editores personalizados](../extensibility/creating-custom-editors-and-designers.md)|Explica cómo crear editores y diseñadores personalizados.|  
|[Desarrollo de un servicio de lenguaje heredado](../extensibility/internals/developing-a-legacy-language-service.md)|Proporciona vínculos a documentos sobre las características que proporcionan capacidades de personalización para el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principal agregando compatibilidad para un servicio de lenguaje.|  
|[Uso de fuentes y colores](../extensibility/using-fonts-and-colors.md)|Explica cómo usar fuentes y colores con las interfaces heredadas.|

