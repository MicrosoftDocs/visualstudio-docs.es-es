---
title: Dentro del Editor de núcleo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 95745cbef015e9f6ceddb9b84d75b52ec9805dea
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="inside-the-core-editor"></a>Dentro del Editor de núcleo
El [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principal es un conjunto de varios componentes que le permiten modificar y consultar información textual. Si ha personalizado el editor básico mediante el uso de la API heredada, puede seguir usar estas personalizaciones, que se enrutará a través de adaptadores de editor. Sin embargo, se recomienda que los adapte sus personalizaciones al nuevo editor de API.  
  
 Las áreas siguientes son algunos aspectos importantes del editor principal:  
  
-   Búfer de texto  
  
-   Vista de texto  
  
-   Ventana Código  
  
-   Marcadores de texto  
  
-   Administrador de texto  
  
-   Integración con servicios de lenguaje  
  
## <a name="in-this-section"></a>En esta sección  
 [Crear una instancia el Editor básico mediante la API heredado](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Proporciona instrucciones paso a paso sobre cómo usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> para crear una instancia del núcleo del editor.  
  
 [Obtener acceso al búfer de texto mediante la API heredado](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Describe el rol del búfer de texto en el editor básico, explica los sistemas asociados que se usan para tener acceso al búfer y proporciona una lista de las interfaces implementadas por el objeto de búfer de texto, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 [Eventos de búfer de texto de la API heredado](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Proporciona una lista de las interfaces que se utilizan para recibir notificaciones de eventos de búfer de texto.  
  
 [Cómo: registrar eventos de búfer de texto con la API de heredado de](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Describe cómo informar de eventos de búfer de texto.  
  
 [Uso del Administrador de texto para supervisar la configuración Global](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Describe cómo se utiliza el Administrador de texto para compartir información sobre las preferencias globales con los componentes principales del editor y cómo recibir una notificación de eventos del Administrador de texto.  
  
 [Obtener acceso a Text vista mediante la API heredado](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Describe el rol de la vista de texto en el editor de núcleo y enumera las interfaces implementadas por el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.  
  
 [Personalización de ventanas de código mediante la API heredado](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Proporciona información acerca de cómo una ventana de código se usa para delimitar la vista de texto, describe cómo se utiliza el Administrador de ventanas de código para proporcionar decoraciones a la ventana de código y proporciona notificaciones de nuevas vistas.  
  
 [Cambiar la configuración de la vista mediante la API heredado](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Proporciona instrucciones paso a paso acerca de cómo forzar la configuración de vista y cómo quitar la configuración forzada.  
  
 [Servicios de lenguaje y el Editor de núcleo](../extensibility/language-services-and-the-core-editor.md)  
 Describe la creación de instancias de un servicio de lenguaje para decoraciones de código de control.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tutorial: Crear un Editor de núcleo y registrar un tipo de archivo del Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Proporciona instrucciones paso a paso sobre cómo iniciar el editor básico desde el código administrado.  
  
 [Barra de la lista desplegable](../extensibility/drop-down-bar.md)  
 Describe cómo la barra de la lista desplegable se utiliza en la ventana de código y describe las interfaces que se usan al implementar una barra de la lista desplegable.  
  
 [Uso de marcadores de texto con la API heredado](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Explica el concepto de marcadores de texto y cómo se utilizan en el editor principal y se enumeran las interfaces que se usan para tener acceso y administrar marcadores de texto.  
  
 [Cómo: agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md)  
 Proporciona instrucciones paso a paso acerca de cómo crear un marcador de texto y cómo agregar un comando personalizado a un menú contextual.  
  
 [Cómo: crear marcadores de texto personalizado](../extensibility/how-to-create-custom-text-markers.md)  
 Proporciona instrucciones paso a paso acerca de cómo crear un marcador de texto personalizado y cómo proporcionar el tipo de marcador como un servicio.