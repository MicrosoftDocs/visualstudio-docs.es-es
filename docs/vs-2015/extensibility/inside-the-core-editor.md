---
title: Dentro del editor principal | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cf9bc42aec3aac5acc996487f99c7e1f29ca252c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203954"
---
# <a name="inside-the-core-editor"></a>Dentro del editor principal
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principal es un conjunto de varios componentes que permiten modificar y consultar información textual. Si ha personalizado el editor principal mediante la API heredada, puede seguir usando estas personalizaciones, que se enrutarán a través de los adaptadores del editor. No obstante, se recomienda adaptar las personalizaciones a la nueva API del editor.  
  
 Las siguientes áreas son algunos aspectos importantes del editor básico:  
  
- Búfer de texto  
  
- Vista de texto  
  
- Ventana de código  
  
- Marcadores de texto  
  
- Administrador de texto  
  
- Integración con servicios de lenguaje  
  
## <a name="in-this-section"></a>En esta sección  
 [Creación de instancias del editor principal mediante la API heredada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Proporciona instrucciones paso a paso sobre cómo usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> para crear una instancia del editor básico.  
  
 [Acceso al búfer de texto mediante la API heredada](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Describe el rol del búfer de texto en el editor principal, explica los sistemas asociados que se usan para tener acceso al búfer y proporciona una lista de las interfaces implementadas por el objeto de búfer de texto, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> .  
  
 [Eventos de búfer de texto en la API heredada](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Proporciona una lista de las interfaces que se usan para la notificación de eventos de búfer de texto.  
  
 [Cómo: Registrarse para eventos de búfer de texto con la API heredada](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Describe cómo avisar a los eventos de búfer de texto.  
  
 [Uso del administrador de texto para supervisar la configuración global](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Describe cómo se usa el administrador de texto para compartir información de preferencias globales con los componentes principales del editor y sobre cómo recibir notificaciones de eventos del administrador de texto.  
  
 [Acceso a la vista de texto mediante la API heredada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Describe el rol de la vista de texto en el editor principal y enumera las interfaces implementadas por el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.  
  
 [Personalización de las ventanas de código mediante la API heredada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Proporciona información sobre cómo se utiliza una ventana de código para incluir la vista de texto, explica cómo se utiliza el administrador de ventanas de código para proporcionar decoraciones a la ventana de código y proporciona una notificación de nuevas vistas.  
  
 [Cambio de la configuración de vista mediante la API heredada API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Proporciona instrucciones paso a paso sobre cómo forzar la configuración de la vista y cómo quitar la configuración forzada.  
  
 [Servicios de lenguaje y editor principal](../extensibility/language-services-and-the-core-editor.md)  
 Describe la creación de instancias de un servicio de lenguaje para controlar las decoraciones de código.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tutorial: Crear un editor principal y registrar un tipo de archivo del editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Proporciona instrucciones paso a paso sobre cómo iniciar el editor básico desde código administrado.  
  
 [Barra desplegable](../extensibility/drop-down-bar.md)  
 Describe cómo se usa la barra desplegable en la ventana de código y describe las interfaces que se usan al implementar una barra desplegable.  
  
 [Uso de marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Explica el concepto de marcadores de texto y cómo se usan en el editor básico, y enumera las interfaces que se usan para obtener acceso a los marcadores de texto y administrarlos.  
  
 [Cómo: Agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md)  
 Proporciona instrucciones paso a paso sobre cómo crear un marcador de texto y cómo agregar un comando personalizado a un menú contextual.  
  
 [Cómo: Crear marcadores de texto personalizados](../extensibility/how-to-create-custom-text-markers.md)  
 Proporciona instrucciones paso a paso sobre cómo crear un marcador de texto personalizado y cómo proporcionar el tipo de marcador como un servicio.
