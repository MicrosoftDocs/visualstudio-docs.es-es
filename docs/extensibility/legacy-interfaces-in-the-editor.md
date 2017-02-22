---
title: "Interfaces heredadas en el Editor | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados"
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Interfaces heredadas en el Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El editor de Visual Studio puede tener acceso desde las interfaces heredadas. El SDK de Visual Studio incluye adaptadores conocidos como *las correcciones de compatibilidad*, que permiten estas interfaces interactuar con el nuevo editor. No obstante, se recomienda que actualice el código heredado para utilizar el nuevo editor de API. El código funciona mejor y puede usar nuevas tecnologías como Windows Presentation Foundation \(WPF\) y Managed Extensibility Framework \(MEF\).  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Adaptar el código heredado en el Editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Explica cómo adaptar el código al nuevo editor.|  
|[Comportamiento nuevo o cambiado con adaptadores de Editor](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Explica cómo el comportamiento de los adaptadores de editor difiere de las versiones anteriores del editor.|  
|[Dentro del Editor de núcleo](../extensibility/inside-the-core-editor.md)|Describe los diferentes componentes de las versiones anteriores del editor.|  
|[Crear una instancia del Editor principal mediante la API heredada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Explica cómo utilizar la API heredada para crear una instancia del editor principal.|  
|[Generadores de editores](../extensibility/editor-factories.md)|Explica cómo utilizar generadores de editores con la API heredada.|  
|[Cómo: registrar tipos de archivo del Editor](../extensibility/how-to-register-editor-file-types.md)|Explica cómo enlazar una extensión de nombre de archivo para el editor.|  
|[Tutorial: Crear un Editor principal y registrar un tipo de archivo del Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Explica cómo crear un núcleo de editor y vincular una extensión de nombre de archivo.|  
|[Cómo: proporcionar contexto para los editores](../extensibility/how-to-provide-context-for-editors.md)|Explica cómo proporcionar contexto para el editor.|  
|[Servicios de lenguaje y el Editor principal](../extensibility/language-services-and-the-core-editor.md)|Explica las interacciones entre un servicio de lenguaje y un editor.|  
|[Acceso al búfer de texto usando la API heredada](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Explica cómo obtener acceso al búfer de texto utilizando la API heredada.|  
|[Acceso a Text vista usando la API heredada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Explica cómo obtener acceso a la vista de texto mediante la API heredada.|  
|[Personalización de Windows de código mediante la API heredada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Explica cómo personalizar windows de código mediante la API heredada.|  
|[Obtener acceso a las capas de texto mediante la API heredada](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Explica cómo obtener acceso a diferentes capas de texto mediante la API heredada.|  
|[Uso de marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md)|Explica cómo agregar marcadores de texto mediante la API heredada.|  
|[Personalizar menús y controles de Editor utilizando la API heredada](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Explica cómo personalizar los controles de editor mediante la API heredada.|  
|[Administración de deshacer y rehacer mediante la API heredada](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Explica cómo administrar deshacer y rehacer, utilizando la API heredada.|  
|[Cómo: implementar la búsqueda y reemplazo mecanismo](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Explica cómo administrar buscar y reemplazar mediante la API heredada.|  
|[Cómo: suprimir las notificaciones de cambio de archivo](../extensibility/how-to-suppress-file-change-notifications.md)|Explica cómo suprimir notificaciones de cambio de archivo mediante la API heredada.|  
|[Creación de diseñadores y editores personalizados](../extensibility/creating-custom-editors-and-designers.md)|Explica cómo crear diseñadores y editores personalizados.|  
|[Desarrollar un servicio de lenguaje](../extensibility/internals/developing-a-legacy-language-service.md)|Proporciona vínculos a documentos acerca de las características que proporcionan capacidades de personalización para el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principal agregando compatibilidad para un servicio de lenguaje.|  
|[Utilizar fuentes y colores](../extensibility/using-fonts-and-colors.md)|Explica cómo utilizar fuentes y colores con interfaces heredadas.|