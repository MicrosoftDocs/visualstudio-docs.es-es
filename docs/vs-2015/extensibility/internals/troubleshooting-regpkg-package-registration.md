---
title: Solución de problemas de registro de paquetes de RegPkg | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 241975e475252a18d5e5a91c6e8c4fb40c067a95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842815"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Solución de problemas del registro de paquete RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> La mejor manera de registrar paquetes en Visual Studio es mediante el uso de archivos. pkgdef. Esto permite la implementación de la extensión sin tener que obtener acceso al registro del sistema. Los archivos Pkgdef se crean mediante la [utilidad CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).  
  
 Para registrar un paquete mediante RegPkg en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , debe usar la versión de RegPkg que sea adecuada para el paquete.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Versiones de RegPkg relacionadas con las versiones de paquete  
 Hay dos versiones de RegPkg. Una versión se incluye en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Utilice esta versión para registrar los paquetes que se han compilado con uno de los siguientes ensamblados:  
  
1. Microsoft.VisualStudioShell.9.0.dll  
  
2. Microsoft.VisualStudioShell.10.0.dll  
  
3. Microsoft.VisualStudioShell.11.0.dll  
  
   No puede registrar paquetes compilados con el ensamblado de Microsoft.VisualStudio.Shell.dll anterior.  
  
   La versión anterior de RegPkg puede registrar paquetes compilados con el ensamblado de Microsoft.VisualStudio.Shell.dll. Sin embargo, no puede registrar los paquetes compilados con versiones posteriores de ese ensamblado.  
  
## <a name="see-also"></a>Consulte también  
 [Publicar un producto](../../misc/releasing-a-visual-studio-integration-product.md)
