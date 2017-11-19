---
title: "Solución de problemas de registro de paquete RegPkg | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4a4162b91a9345c94b7bd6a7e2f1099da3d631e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="troubleshooting-regpkg-package-registration"></a>Solución de problemas de registro de paquete RegPkg
> [!NOTE]
>  Es la mejor manera de registrar paquetes en Visual Studio mediante el uso de archivos .pkgdef. Esto permite para la implementación de extensión sin necesidad de tener acceso al registro del sistema. Pkgdef archivos se crean mediante el [CreatePkgDef utilidad](../../extensibility/internals/createpkgdef-utility.md).  
  
 Para registrar un paquete mediante RegPkg en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], debe usar la versión de RegPkg que sea adecuada para el paquete.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Versiones de RegPkg relacionados con las versiones del paquete  
 Hay dos versiones de RegPkg. Una versión se incluye en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Utilice esta versión para registrar paquetes que se han generado mediante uno de los siguientes ensamblados:  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 No se registrará los paquetes que se han generado mediante el ensamblado Microsoft.VisualStudio.Shell.dll anterior.  
  
 La versión anterior de RegPkg puede registrar paquetes que se han generado mediante el ensamblado Microsoft.VisualStudio.Shell.dll. Sin embargo, no se registrará paquetes creados mediante versiones posteriores de ese ensamblado.  
  
## <a name="see-also"></a>Vea también  
 [VSPackages](../../extensibility/internals/vspackages.md)