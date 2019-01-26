---
title: En el Editor básico | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 243202b116af63a7d14672cd33d30030e8e987b0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959088"
---
# <a name="inside-the-core-editor"></a>Dentro del editor de núcleo
El [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor básico es un conjunto de varios componentes que le permiten modificar y consultar información textual. Si ha personalizado el editor básico mediante el uso de la API heredada, aún puede usar estas personalizaciones, que se enrutarán a través de adaptadores de editor. Sin embargo, se recomienda que adaptar sus personalizaciones al nuevo editor de API.  
  
 Las áreas siguientes son algunos aspectos importantes del editor de núcleo:  
  
-   Búfer de texto  
  
-   Vista de texto  
  
-   Ventana Código  
  
-   Marcadores de texto  
  
-   Administrador de texto  
  
-   Integración con servicios de lenguaje  
  
## <a name="in-this-section"></a>En esta sección  
 [Crear una instancia el editor básico mediante la API heredada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Proporciona instrucciones paso a paso sobre cómo usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> para crear una instancia del núcleo del editor.  
  
 [Tener acceso al búfer de texto mediante el uso de la API heredada](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Describe el rol del búfer de texto en el editor básico, explica los sistemas asociados que se usan para tener acceso al búfer y proporciona una lista de las interfaces implementadas por el objeto de búfer de texto, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 [Eventos del búfer de texto en la API heredada](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Proporciona una lista de las interfaces que se usan para la notificación de eventos del búfer de texto.  
  
 [Cómo: Registrarse para eventos de búfer de texto con la API heredada](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Describe cómo notificar los eventos del búfer de texto.  
  
 [Use el Administrador de texto para supervisar la configuración global](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Describe cómo se usa el Administrador de texto para compartir información sobre las preferencias globales con los componentes principales del editor y cómo recibir notificaciones de eventos del Administrador de texto.  
  
 [Vista de acceso a Text mediante el uso de la API heredada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Describe el rol de la vista de texto en el editor básico y se enumeran las interfaces implementadas por el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.  
  
 [Personalizar las ventanas de código mediante el uso de la API heredada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Proporciona información acerca de cómo una ventana de código se usa para delimitar la vista de texto, describe cómo el Administrador de ventanas de código se utilizan para proporcionar las decoraciones de la ventana de código y proporciona una notificación de nuevas vistas.  
  
 [Cambiar la configuración de vista mediante el uso de la API heredada](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Proporciona instrucciones paso a paso sobre cómo forzar la configuración de la vista y cómo quitar la configuración forzada.  
  
 [Servicios de lenguaje y el editor básico](../extensibility/language-services-and-the-core-editor.md)  
 Describe la creación de instancias de un servicio de lenguaje decoraciones del código de control.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tutorial: Crear un editor de núcleo y registrar un tipo de archivo del editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Proporciona instrucciones paso a paso sobre cómo iniciar el editor básico desde el código administrado.  
  
 [Barra desplegable](../extensibility/drop-down-bar.md)  
 Describe cómo la barra desplegable se usa en la ventana de código y describe las interfaces que se usan al implementar una barra desplegable.  
  
 [Utilice marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Explica el concepto de marcadores de texto y cómo se usan en el editor básico y enumera las interfaces que se usan para tener acceso y administrar marcadores de texto.  
  
 [Cómo: Agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md)  
 Proporciona instrucciones paso a paso sobre cómo crear un marcador de texto y cómo agregar un comando personalizado a un menú contextual.  
  
 [Cómo: Crear marcadores de texto personalizado](../extensibility/how-to-create-custom-text-markers.md)  
 Proporciona instrucciones paso a paso sobre cómo crear un marcador de texto personalizado y cómo proporcionar el tipo de marcador como un servicio.