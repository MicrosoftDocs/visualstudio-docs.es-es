---
title: En el Editor básico | Microsoft Docs
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
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2d9ec83c700f9166dc6b73860547bcacd265a15
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575331"
---
# <a name="inside-the-core-editor"></a>En el Editor básico
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [en el Editor básico](https://docs.microsoft.com/visualstudio/extensibility/inside-the-core-editor).  
  
El [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor básico es un conjunto de varios componentes que le permiten modificar y consultar información textual. Si ha personalizado el editor básico mediante el uso de la API heredada, aún puede usar estas personalizaciones, que se enrutarán a través de adaptadores de editor. Sin embargo, se recomienda que adaptar sus personalizaciones al nuevo editor de API.  
  
 Las áreas siguientes son algunos aspectos importantes del editor de núcleo:  
  
-   Búfer de texto  
  
-   Vista de texto  
  
-   Ventana Código  
  
-   Marcadores de texto  
  
-   Administrador de texto  
  
-   Integración con servicios de lenguaje  
  
## <a name="in-this-section"></a>En esta sección  
 [Creación de instancias del editor principal mediante la API heredada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Proporciona instrucciones paso a paso sobre cómo usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> para crear una instancia del núcleo del editor.  
  
 [Acceso al búfer de texto mediante la API heredada](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Describe el rol del búfer de texto en el editor básico, explica los sistemas asociados que se usan para tener acceso al búfer y proporciona una lista de las interfaces implementadas por el objeto de búfer de texto, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 [Eventos de búfer de texto en la API heredada](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Proporciona una lista de las interfaces que se usan para la notificación de eventos del búfer de texto.  
  
 [Cómo: Registrarse para eventos de búfer de texto con la API heredada](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Describe cómo notificar los eventos del búfer de texto.  
  
 [Uso del administrador de texto para supervisar la configuración global](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Describe cómo se usa el Administrador de texto para compartir información sobre las preferencias globales con los componentes principales del editor y cómo recibir notificaciones de eventos del Administrador de texto.  
  
 [Acceso a la vista de texto mediante la API heredada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Describe el rol de la vista de texto en el editor básico y se enumeran las interfaces implementadas por el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.  
  
 [Personalización de las ventanas de código mediante la API heredada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Proporciona información acerca de cómo una ventana de código se usa para delimitar la vista de texto, describe cómo el Administrador de ventanas de código se utilizan para proporcionar las decoraciones de la ventana de código y proporciona una notificación de nuevas vistas.  
  
 [Cambio de la configuración de vista mediante la API heredada API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Proporciona instrucciones paso a paso sobre cómo forzar la configuración de la vista y cómo quitar la configuración forzada.  
  
 [Servicios de lenguaje y editor principal](../extensibility/language-services-and-the-core-editor.md)  
 Describe la creación de instancias de un servicio de lenguaje decoraciones del código de control.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tutorial: Crear un editor principal y registrar un tipo de archivo del editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Proporciona instrucciones paso a paso sobre cómo iniciar el editor básico desde el código administrado.  
  
 [Barra desplegable](../extensibility/drop-down-bar.md)  
 Describe cómo la barra desplegable se usa en la ventana de código y describe las interfaces que se usan al implementar una barra desplegable.  
  
 [Uso de marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Explica el concepto de marcadores de texto y cómo se usan en el editor básico y enumera las interfaces que se usan para tener acceso y administrar marcadores de texto.  
  
 [Cómo: Agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md)  
 Proporciona instrucciones paso a paso sobre cómo crear un marcador de texto y cómo agregar un comando personalizado a un menú contextual.  
  
 [Cómo: Crear marcadores de texto personalizados](../extensibility/how-to-create-custom-text-markers.md)  
 Proporciona instrucciones paso a paso sobre cómo crear un marcador de texto personalizado y cómo proporcionar el tipo de marcador como un servicio.

