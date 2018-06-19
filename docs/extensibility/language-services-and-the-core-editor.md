---
title: Servicios de lenguaje y el Editor principal | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cd9e0cdbcb10ac670ac1a0947fb9a43c16c7fccf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138485"
---
# <a name="language-services-and-the-core-editor"></a>Servicios de lenguaje y el Editor de núcleo
Editores de Visual Studio se asocian con frecuencia a un servicio de lenguaje. Entre otras cosas, un servicio de lenguaje proporciona color de sintaxis, finalización de instrucciones, IntelliSense y el formato de texto.  
  
## <a name="core-editors-and-document-data-objects"></a>Editores de núcleo y objetos de datos de documentos  
 Cuando se tiene acceso el editor básico, no cree datos del documento y los objetos de vista de documento. El IDE crea y controla estos dos objetos, y obtener identificadores a ellos mediante la realización de las llamadas adecuadas en el editor de la implementación del generador.  
  
 Para obtener más información, consulte [determinar qué Editor abre un archivo en un proyecto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Servicios de lenguaje y el Editor de núcleo  
 Al implementar un servicio de lenguaje, puede controlar cómo se muestran los datos en la vista de documento. Un servicio de lenguaje proporciona información y el comportamiento que es específico de un idioma determinado, como Visual C++. Al crear un búfer de texto y determinar la extensión de nombre de archivo para el documento que se abre, el búfer de texto determina el servicio de lenguaje asociado a esta extensión de nombre de archivo de una clave del registro, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Editors \\\Extensions {YourLanguageService GUID}. El VSPackage estándar cargar procedimiento, a continuación, carga el paquete de VS y se crea una instancia de su servicio de lenguaje.  
  
 Un servicio de lenguaje básico se muestra en la siguiente ilustración.  
  
 ![Gráfico del modelo de servicio de lenguaje](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Objetos de servicio de editor y el idioma principal  
  
 El objeto de datos de documento para el editor principal se denomina un búfer de texto y se representa mediante el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto. El objeto de vista de documento se denomina una vista de texto y se representa mediante el <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objeto. Estos dos objetos funcionan conjuntamente a través del servicio de lenguaje para proporcionar una vista unificada del editor principal. Obtener información desde el búfer de texto y la vista de texto se muestra en una ventana de documento llama una ventana de código. El documento de la ventana de código es administrado por un administrador de la ventana de código.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Proporciona un contexto de servicio de lenguaje mediante la API heredado](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Hospedaje de IntelliSense](../extensibility/intellisense-hosting.md)   
 [Idiomas independientes](../extensibility/contained-languages.md)   
 [Desarrollo de un servicio de lenguaje heredado](../extensibility/internals/developing-a-legacy-language-service.md)