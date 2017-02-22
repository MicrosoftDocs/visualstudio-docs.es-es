---
title: "Dentro del Editor de n&#250;cleo | Microsoft Docs"
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
  - "editores [Visual Studio SDK] heredados - editor principal"
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Dentro del Editor de n&#250;cleo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El editor básico de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] es un conjunto de varios componentes que permiten modificar y ver información textual.  Si ha personalizado el editor básico con heredado API, puede seguir utilizando estas personalizaciones, que se distribuirán a través de los adaptadores del editor.  Se recomienda, sin embargo, que se adapta las personalizaciones al nuevo editor API.  
  
 Las siguientes áreas son algunos aspectos importantes de editor básico:  
  
-   Búfer de texto  
  
-   vista de texto  
  
-   Ventana de código  
  
-   Marcadores de texto  
  
-   Administrador de texto  
  
-   Integración con servicios  
  
## En esta sección  
 [Crear una instancia del Editor principal mediante la API heredada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Proporciona instrucciones paso a paso sobre cómo utilizar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> para crear una instancia del editor básico.  
  
 [Acceso al búfer de texto usando la API heredada](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Explica el rol del búfer de texto en el editor básico, explica los sistemas asociado que se utilizan para tener acceso al búfer, y proporciona una lista de las interfaces implementadas por el objeto de búfer de texto, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 [Eventos del búfer de texto en la API heredada](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Proporciona una lista de las interfaces que se usan para la notificación de los eventos del búfer de texto.  
  
 [Cómo: registrar eventos del búfer de texto con la API heredada](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Describe cómo muestran eventos del búfer de texto.  
  
 [Mediante el Administrador de texto para supervisar la configuración Global](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Describe cómo se utiliza el administrador de texto para compartir información global de preferencia con los componentes básicos del editor y cómo recibir notificación de eventos del administrador de texto.  
  
 [Acceso a Text vista usando la API heredada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 describe el rol de la vista de texto en el editor básico y enumera las interfaces implementadas por el objeto de <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .  
  
 [Personalización de Windows de código mediante la API heredada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Proporciona información sobre cómo una ventana de código se utiliza para agregar la vista de texto, se explica cómo se utiliza el administrador de ventanas de códigos para proporcionar decoraciones a la ventana de código, y proporciona notificación de nuevas vistas.  
  
 [Cambiar la configuración de vista mediante la API heredada](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Proporciona instrucciones paso a paso sobre cómo forzar valores de vista y cómo quitar valores convertidos.  
  
 [Servicios de lenguaje y el Editor principal](../extensibility/language-services-and-the-core-editor.md)  
 Describe la creación de un servicio de a las ubicaciones de código.  
  
## Secciones relacionadas  
 [Tutorial: Crear un Editor principal y registrar un tipo de archivo del Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Proporciona instrucciones paso a paso sobre cómo iniciar el editor básico de código administrado.  
  
 [Barra desplegable](../extensibility/drop-down-bar.md)  
 Explica cómo la barra desplegable se utiliza en la ventana de código y describe las interfaces que se usan cuando se implementa una barra desplegable.  
  
 [Uso de marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Explica el concepto de marcadores de texto y cómo se utilizan en el editor básico, y muestra las interfaces que se usan para administrar y tener acceso a los marcadores de texto.  
  
 [Cómo: agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md)  
 Proporciona instrucciones paso a paso sobre cómo crear un marcador de texto y cómo agregar un comando personalizado a un menú contextual.  
  
 [Cómo: crear marcadores de texto personalizado](../extensibility/how-to-create-custom-text-markers.md)  
 Proporciona instrucciones paso a paso sobre cómo crear un marcador de texto personalizado y cómo proporcionar el marcador escrito como un servicio.