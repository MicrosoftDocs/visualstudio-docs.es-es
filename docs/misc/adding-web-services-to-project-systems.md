---
title: "Agregar servicios web a sistemas de proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sistemas de proyecto, agregar servicios web"
  - "servicios web, agregar a sistemas de proyecto de VSPackage"
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# Agregar servicios web a sistemas de proyecto
Los servicios Web XML son, normalmente los recursos Dirección URL\-direccionables que devuelven información de programación al sistema de proyectos mediante el protocolo SOAP \(protocolo de acceso de objeto Simple\).  Puede integrar los servicios web al sistema de proyectos de VSPackage mediante la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> .  
  
### Para agregar un servicio web al sistema de proyectos  
  
1.  Llame a `QueryService` para la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> con el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> .  
  
2.  Llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A>.  Si pasa en el parámetro de `pDiscoverySession` como `NULL`, crea una sesión de detección para usted, y almacena en memoria caché la sesión de modo que esté disponible para el uso posterior por la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> .  el método de<xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> devuelve un puntero a <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2>.  
  
3.  Llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A>.  El paso en el objeto de automatización para el servicio web hace referencia a la carpeta como parámetro de `pUnkWebReferenceFolder` .  Comprueba el entorno de Visual Studio a continuación si el servicio web ya está presente.  Si el servicio web no está presente, el entorno descarga y agrega el servicio web en una carpeta y a cualquier archivo adicional \(como archivos .wsdl\) a los nodos secundarios de la carpeta.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>