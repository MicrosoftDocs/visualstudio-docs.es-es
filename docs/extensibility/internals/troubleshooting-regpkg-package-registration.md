---
title: Solución de problemas de registro de paquetes de RegPkg | Microsoft Docs
description: Use esta información para solucionar problemas de registro de paquetes de RegPkg en Visual Studio. Use la versión de RegPkg que sea adecuada para el paquete.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48e3699b095ed7b9d0e72cf7b09ad02e26ac5a51
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090764"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Solución de problemas del registro de paquete RegPkg
> [!NOTE]
> La mejor manera de registrar paquetes en Visual Studio es mediante el uso de archivos. pkgdef. Esto permite la implementación de la extensión sin tener que obtener acceso al registro del sistema. Los archivos Pkgdef se crean mediante la [utilidad CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).

 Para registrar un paquete mediante RegPkg en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , debe usar la versión de RegPkg que sea adecuada para el paquete.

## <a name="regpkg-versions-related-to-package-versions"></a>Versiones de RegPkg relacionadas con las versiones de paquete
 Hay dos versiones de RegPkg. Una versión se incluye en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Utilice esta versión para registrar los paquetes que se han compilado con uno de los siguientes ensamblados:

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   No puede registrar paquetes compilados con el ensamblado de Microsoft.VisualStudio.Shell.dll anterior.

   La versión anterior de RegPkg puede registrar paquetes compilados con el ensamblado de Microsoft.VisualStudio.Shell.dll. Sin embargo, no puede registrar los paquetes compilados con versiones posteriores de ese ensamblado.

## <a name="see-also"></a>Consulte también
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Solucionar problemas de Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
