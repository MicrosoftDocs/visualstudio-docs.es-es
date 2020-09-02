---
title: Servicios de lenguaje y editor principal | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e708ffe796bfc9342bc20c3e7f20d5cf0d05058
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180301"
---
# <a name="language-services-and-the-core-editor"></a>Servicios de lenguaje y editor principal
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los editores de Visual Studio suelen estar asociados a un servicio de lenguaje. Entre otras cosas, un servicio de lenguaje proporciona colores de sintaxis, finalización de instrucciones, IntelliSense y formato de texto.  
  
## <a name="core-editors-and-document-data-objects"></a>Editores principales y objetos de datos de documento  
 Al tener acceso al editor principal, no se crean datos de documento y objetos de vista de documento. El IDE crea y controla estos dos objetos y obtiene los identificadores para ellos mediante las llamadas adecuadas en la implementación del generador de editores.  
  
 Para obtener más información, vea [determinar qué editor abre un archivo en un proyecto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Servicios de lenguaje y editor principal  
 Mediante la implementación de un servicio de lenguaje, puede controlar cómo se muestran los datos en la vista de documento. Un servicio de lenguaje proporciona información y un comportamiento específico de un idioma determinado, como Visual C++. Al crear un búfer de texto y determinar la extensión de nombre de archivo del documento que está abriendo, el búfer de texto determina el servicio de lenguaje asociado a esta extensión de nombre de archivo de una clave del registro, HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Editors \\ {YOURLANGUAGESERVICE GUID} \Extensions. A continuación, el procedimiento de carga de VSPackage estándar carga el VSPackage y se crea una instancia del servicio de lenguaje.  
  
 En la ilustración siguiente se muestra un servicio de lenguaje básico.  
  
 ![Gráfico del modelo de servicio de lenguaje](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Editor de núcleo y objetos de servicio de lenguaje  
  
 El objeto de datos del documento para el editor principal se denomina búfer de texto y se representa mediante el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto. El objeto de vista de documento se denomina vista de texto y se representa mediante el <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objeto. Estos dos objetos funcionan juntos a través del servicio de lenguaje para proporcionar una vista unificada del editor básico. La información del búfer de texto y la vista de texto se muestra en una ventana de documento denominada ventana de código. El documento de la ventana de código se administra mediante un administrador de ventanas de código.  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Proporcionar un contexto de servicio de lenguaje mediante la API heredada](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Hospedaje de IntelliSense](../extensibility/intellisense-hosting.md)   
 [Lenguajes contenidos](../extensibility/contained-languages.md)   
 [Desarrollo de un servicio de lenguaje heredado](../extensibility/internals/developing-a-legacy-language-service.md)
