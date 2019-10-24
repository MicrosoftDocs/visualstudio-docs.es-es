---
title: Solución de problemas de registro de paquetes de RegPkg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 386a1a17c036207d122e4b3c7cb142a628dcfe38
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722280"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Solución de problemas del registro de paquete RegPkg
> [!NOTE]
> La mejor manera de registrar paquetes en Visual Studio es mediante el uso de archivos. pkgdef. Esto permite la implementación de la extensión sin tener que obtener acceso al registro del sistema. Los archivos Pkgdef se crean mediante la [utilidad CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).

 Para registrar un paquete mediante RegPkg en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], debe usar la versión de RegPkg que sea adecuada para el paquete.

## <a name="regpkg-versions-related-to-package-versions"></a>Versiones de RegPkg relacionadas con las versiones de paquete
 Hay dos versiones de RegPkg. Se incluye una versión en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Utilice esta versión para registrar los paquetes que se han compilado con uno de los siguientes ensamblados:

1. Microsoft. VisualStudioShell. 9.0. dll

2. Microsoft. VisualStudioShell. 10.0. dll

3. Microsoft. VisualStudioShell. 11.0. dll

   No puede registrar paquetes compilados con el ensamblado Microsoft. VisualStudio. Shell. dll anterior.

   La versión anterior de RegPkg puede registrar paquetes compilados mediante el ensamblado Microsoft. VisualStudio. Shell. dll. Sin embargo, no puede registrar los paquetes compilados con versiones posteriores de ese ensamblado.

## <a name="see-also"></a>Vea también
- [VSPackages](../../extensibility/internals/vspackages.md)