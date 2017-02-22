---
title: "Servicios de lenguaje y el Editor principal | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - servicios de lenguaje"
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Servicios de lenguaje y el Editor principal
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los editores de Visual Studio suelen ser asociado a un servicio de lenguaje.  Entre otras cosas, un servicio de lenguaje ofrece el colorear la sintaxis, la finalización de instrucciones, IntelliSense, y formato de texto.  
  
## Editores básicos y objetos del documento  
 Cuando se tiene acceso al editor básico, no crea datos de documento y objetos de vista del documento.  El IDE crea y controla estos dos objetos, y se obtiene identificadores a ellos realizar llamadas adecuadas en la implementación del generador del editor.  
  
 Para obtener más información, vea [Determinar qué Editor se abre un archivo en un proyecto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## lenguaje Services y el editor básico  
 Implementar un servicio de, puede controlar cómo se muestran los datos en la vista del documento.  Un servicio de lenguaje proporciona información y el comportamiento específico de un idioma determinado, como Visual C\+\+.  Cuando se crea un búfer de texto y determina la extensión de nombre de archivo para el documento que está abriendo, el búfer de texto determina el servicio de lenguaje asociado a esta extensión de nombre de archivo de una clave del Registro, HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\Editors\\{YourLanguageService GUID}\\Extensions.  El procedimiento estándar de carga de VSPackage continuación carga el paquete VSPackage y una instancia del servicio de lenguaje se crea.  
  
 Un servicio de básico se muestra en la ilustración siguiente.  
  
 ![Gráfico del modelo de servicio de lenguaje](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Objetos de servicio básicos del publicador y del lenguaje  
  
 El objeto del documento para el editor básico se denomina un búfer de texto y está representado por el objeto de <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> .  El objeto de vista del documento se denomina una vista de texto y está representado por el objeto de <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> .  Estos dos objetos trabajan juntos con el servicio de lenguaje para proporcionar una vista unificada de editor básico.  La información del búfer de texto y muestra de la vista de texto en una ventana de documento a una ventana de código.  El documento de la ventana de código es administrado por un administrador de ventana de código.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Proporcionar un contexto de servicio de lenguaje a través de la API heredada](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Hospedaje de IntelliSense](../extensibility/intellisense-hosting.md)   
 [Idiomas contenidos](../extensibility/contained-languages.md)   
 [Desarrollar un servicio de lenguaje](../extensibility/internals/developing-a-legacy-language-service.md)