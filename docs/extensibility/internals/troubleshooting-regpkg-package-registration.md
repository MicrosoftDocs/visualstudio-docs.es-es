---
title: Solución de problemas de registro de paquete RegPkg | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4857e41888962a92dced87d63fa2b63161ecac55
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137123"
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