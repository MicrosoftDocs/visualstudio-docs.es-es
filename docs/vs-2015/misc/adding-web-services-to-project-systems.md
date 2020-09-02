---
title: Agregar servicios web a sistemas de proyecto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- project systems, adding Web services
- Web services, adding to VSPackage project systems
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: f5b192be8e5f68ad9314fe08fff963c032013cb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "63002655"
---
# <a name="adding-web-services-to-project-systems"></a>Agregar servicios web a sistemas de proyecto
Los servicios Web XML son, en general, recursos direccionables mediante URL que devuelven información de programación al sistema del proyecto mediante el protocolo SOAP (Protocolo simple de acceso a objetos). Puede integrar los servicios web en el sistema del proyecto de VSPackage mediante la <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> interfaz.  
  
### <a name="to-add-a-web-service-to-your-project-system"></a>Para agregar un servicio Web al sistema del proyecto  
  
1. Llame a `QueryService` para la <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> interfaz a través del <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> servicio.  
  
2. Llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> . Si pasa el `pDiscoverySession` parámetro como `NULL` , se crea una sesión de detección y la sesión se almacena en caché para que esté disponible para su uso posterior por parte de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> interfaz. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> el método devuelve un puntero a <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2> .  
  
3. Llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A> . Pase el objeto de automatización para la carpeta referencias del servicio web como `pUnkWebReferenceFolder` parámetro. A continuación, el entorno de Visual Studio comprueba si el servicio web ya está presente. Si el servicio Web no está presente, el entorno descarga y agrega el servicio Web a una carpeta y los archivos adicionales (como archivos. WSDL) a los nodos secundarios de la carpeta.  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>