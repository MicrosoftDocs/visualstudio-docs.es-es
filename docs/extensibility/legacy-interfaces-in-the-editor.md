---
title: Las Interfaces heredadas en el Editor | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 64e867430c2ae55f530bdb66844240a887bd5545
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="legacy-interfaces-in-the-editor"></a>Interfaces heredadas en el Editor
El editor de Visual Studio se puede acceder desde las interfaces heredadas. El SDK de Visual Studio incluye los adaptadores que se conoce como *correcciones de compatibilidad*, que permiten estas interfaces interactuar con el nuevo editor. No obstante, se recomienda que actualice el código heredado para usar el nuevo editor de API. El código funciona mejor y pueden usar nuevas tecnologías como Windows Presentation Foundation (WPF) y Managed Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Adaptar el código heredado en el Editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Explica cómo adaptar el código al nuevo editor.|  
|[Comportamiento nuevo o cambiado con adaptadores de Editor](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Explica cómo el comportamiento de los adaptadores de editor difiere del de las versiones anteriores del editor.|  
|[Dentro del Editor de núcleo](../extensibility/inside-the-core-editor.md)|Describe los diferentes componentes de las versiones anteriores del editor.|  
|[Crear una instancia el Editor básico mediante la API heredado](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Explica cómo utilizar la API heredada para crear una instancia del editor principal.|  
|[Generadores de editores](../extensibility/editor-factories.md)|Explica cómo utilizar generadores de editores con la API heredada.|  
|[Cómo: registrar tipos de archivo del Editor](../extensibility/how-to-register-editor-file-types.md)|Explica cómo enlazar una extensión de nombre de archivo para el editor.|  
|[Tutorial: Crear un Editor de núcleo y registrar un tipo de archivo del Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Explica cómo crear un núcleo de editor y vincula una extensión de nombre de archivo a él.|  
|[Cómo: proporcionar un contexto para los editores](../extensibility/how-to-provide-context-for-editors.md)|Explica cómo proporcionar contexto para el editor.|  
|[Servicios de lenguaje y el Editor de núcleo](../extensibility/language-services-and-the-core-editor.md)|Explica las interacciones entre un servicio de lenguaje y un editor.|  
|[Obtener acceso al búfer de texto mediante la API heredado](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Explica cómo tener acceso al búfer de texto mediante el uso de la API heredada.|  
|[Obtener acceso a Text vista mediante la API heredado](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Explica cómo obtener acceso a la vista de texto utilizando la API heredada.|  
|[Personalización de ventanas de código mediante la API heredado](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Explica cómo personalizar windows de código mediante la API heredada.|  
|[Obtener acceso a las capas de texto mediante la API heredado](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Explica cómo obtener acceso a diferentes capas de texto utilizando la API heredada.|  
|[Uso de marcadores de texto con la API heredado](../extensibility/using-text-markers-with-the-legacy-api.md)|Explica cómo agregar marcadores de texto mediante el uso de la API heredada.|  
|[Personalizar menús y controles de Editor mediante la API heredado](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Explica cómo personalizar los controles de editor mediante el uso de la API heredada.|  
|[Administración de deshacer y rehacer mediante la API heredado](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Explica cómo administrar deshacer y rehacer mediante el uso de la API heredada.|  
|[Cómo: implementar la buscar y reemplazar el mecanismo de](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Explica cómo administrar buscar y reemplazar con la API heredada.|  
|[Cómo: suprimir las notificaciones de cambio de archivo](../extensibility/how-to-suppress-file-change-notifications.md)|Explica cómo suprimir las notificaciones de cambio de archivo mediante la API heredada.|  
|[Creación de diseñadores y editores personalizados](../extensibility/creating-custom-editors-and-designers.md)|Explica cómo crear editores y diseñadores personalizados.|  
|[Desarrollo de un servicio de lenguaje heredado](../extensibility/internals/developing-a-legacy-language-service.md)|Proporciona vínculos a documentos acerca de las características que proporcionan capacidades de personalización para el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principal agregando compatibilidad para un servicio de lenguaje.|  
|[Utilizar fuentes y colores](../extensibility/using-fonts-and-colors.md)|Explica cómo usar fuentes y colores con interfaces heredadas.|