---
title: Solución de problemas de registro de paquetes RegPkg Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ebae9f7c5b4d1a6dcfee20c3b36c02f8ead2e0bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704328"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Solución de problemas del registro de paquete RegPkg
> [!NOTE]
> La forma preferida de registrar paquetes en Visual Studio es mediante archivos .pkgdef. Esto permite la implementación de extensiones sin tener que acceder al registro del sistema. Los archivos Pkgdef se crean mediante [la utilidad CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).

 Para registrar un paquete mediante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]RegPkg en , debe usar la versión de RegPkg que sea adecuada para el paquete.

## <a name="regpkg-versions-related-to-package-versions"></a>Versiones reg/resctuyes relacionadas con versiones de paquetes
 Hay dos versiones de RegPkg. Una versión [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]se incluye en . Utilice esta versión para registrar los paquetes que se han compilado mediante uno de los ensamblados siguientes:

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   No puede registrar paquetes que se han compilado mediante el ensamblado Microsoft.VisualStudio.Shell.dll anterior.

   La versión anterior de RegPkg puede registrar paquetes que se han compilado mediante el ensamblado Microsoft.VisualStudio.Shell.dll. Sin embargo, no puede registrar paquetes compilados mediante versiones posteriores de ese ensamblado.

## <a name="see-also"></a>Vea también
- [VSPackages](../../extensibility/internals/vspackages.md)
