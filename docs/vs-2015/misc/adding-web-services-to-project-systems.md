---
title: Agregar servicios Web a sistemas del proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project systems, adding Web services
- Web services, adding to VSPackage project systems
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
manager: douge
ms.openlocfilehash: 88966ee17567970d0807792c57c2483cadb22f63
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49280324"
---
# <a name="adding-web-services-to-project-systems"></a>Agregar servicios web a sistemas de proyecto
En general, los servicios Web XML son los recursos con direcciones URL que devuelven información mediante programación al sistema del proyecto mediante el protocolo SOAP (Simple Object Access Protocol). Puede integrar servicios Web en el sistema de proyecto de VSPackage mediante el <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> interfaz.  
  
### <a name="to-add-a-web-service-to-your-project-system"></a>Para agregar un servicio Web para el sistema del proyecto  
  
1.  Llame a `QueryService` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> a través de la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> service.  
  
2.  Llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A>. Si se pasa en `pDiscoverySession` parámetro como `NULL`, se crea una sesión de detección y la sesión se almacena en caché para que esté disponible para su uso posterior por el <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> interfaz. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> método devuelve un puntero a <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2>.  
  
3.  Llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A>. Pase el objeto de automatización para la carpeta de referencias de servicio Web como la `pUnkWebReferenceFolder` parámetro. El entorno de Visual Studio, a continuación, comprueba si el servicio Web ya está presente. Si el servicio Web no está presente, el entorno de descarga y agrega el servicio Web a una carpeta y los archivos adicionales (por ejemplo, los archivos .wsdl) que los nodos secundarios de la carpeta.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>