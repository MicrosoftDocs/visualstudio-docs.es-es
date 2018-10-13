---
title: Servicios de lenguaje y el Editor básico | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9a1ccca0b20a681505ef197c4eefad1b3a813af6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218327"
---
# <a name="language-services-and-the-core-editor"></a>Servicios de lenguaje y el Editor básico
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editores de Visual Studio están asociados con frecuencia a un servicio de lenguaje. Entre otras cosas, un servicio de lenguaje proporciona colores de sintaxis, finalización de instrucciones, IntelliSense y el formato de texto.  
  
## <a name="core-editors-and-document-data-objects"></a>Los editores de núcleo y los objetos de datos de documento  
 Cuando tenga acceso al editor básico, no cree objetos de vista de documento y de datos del documento. El IDE crea y controla estos dos objetos, y obtener identificadores a ellos mediante la realización de las llamadas adecuadas en el editor del implementación del generador.  
  
 Para obtener más información, consulte [determinar qué Editor abre un archivo en un proyecto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Servicios de lenguaje y el Editor básico  
 Al implementar un servicio de lenguaje, puede controlar cómo se muestran los datos en la vista del documento. Un servicio de lenguaje proporciona información y el comportamiento que es específico de un idioma determinado, como Visual C++. Cuando se crea un búfer de texto y determinar la extensión de nombre de archivo para el documento que se abre, el búfer de texto determina el servicio de lenguaje asociado con esta extensión de nombre de archivo de una clave del registro, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Editors \\\Extensions {YourLanguageService GUID}. El VSPackage estándar del procedimiento de carga, a continuación, carga el VSPackage y se crea una instancia de su servicio de lenguaje.  
  
 Un servicio de lenguaje básico se muestra en la siguiente ilustración.  
  
 ![Gráfico del modelo de servicio de lenguaje](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Objetos de servicio de editor y lenguaje principales  
  
 El objeto de datos para el editor básico se llama a un búfer de texto y se representa mediante el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto. El objeto de vista de documento se llama a una vista de texto y se representa mediante el <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objeto. Estos dos objetos colaboran a través del servicio de lenguaje para proporcionar una vista unificada del editor de núcleo. Información desde el búfer de texto y la vista de texto se muestra en una ventana de documento llama a una ventana de código. El documento de la ventana de código es administrado por un administrador de ventana de código.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Proporcionar un contexto de servicio de lenguaje a través de la API heredada](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Hospedaje de IntelliSense](../extensibility/intellisense-hosting.md)   
 [Lenguajes contenidos](../extensibility/contained-languages.md)   
 [Desarrollo de un servicio de lenguaje heredado](../extensibility/internals/developing-a-legacy-language-service.md)

