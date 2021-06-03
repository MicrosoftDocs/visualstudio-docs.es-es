---
title: Utilidad RegPkg | Microsoft Docs
description: Obtenga información sobre RegPkg.exe utilidad registra un VSPackage con Visual Studio y lo prepara para la implementación.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ffef522cb85816c36bee1cb623810fb254d1ddec
ms.sourcegitcommit: f50bbdb15c4f9fca0fa245ca765183c378960cc5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2021
ms.locfileid: "111351947"
---
# <a name="regpkg-utility"></a>Utilidad RegPkg
> [!NOTE]
> La manera preferida de registrar paquetes en Visual Studio es mediante archivos .pkgdef. Esto permite la implementación de extensiones sin tener que acceder al registro del sistema, que es un requisito para la implementación de VSIX. Los archivos Pkgdef se crean mediante la [utilidad CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Para obtener más información sobre Visual Studio implementación de paquetes, vea [Shipping Visual Studio Extensions](../../extensibility/shipping-visual-studio-extensions.md).

 La RegPkg.exe registra un VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y lo prepara para la implementación. Esta utilidad se usa en segundo plano durante el desarrollo de VSPackage. Se ejecuta como parte del proceso de compilación para que pueda compilar y ejecutar un VSPackage en el subárbol experimental.

 RegPkg puede generar scripts del Registro del sistema en varios formatos. Puede incorporar estos scripts en proyectos de implementación, como proyectos .msi o archivos Windows Installer conjunto de herramientas XML.

 RegPkg.exe suele encontrarse en \<*Visual Studio SDK installation path*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg sigue esta sintaxis:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root:root Realiza el registro en la raíz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] especificada.

 /regfile:FileName Crea un archivo .reg en lugar de actualizar el Registro.  No se puede usar con /vrgfile o /rgsfile o /wixfile.

 /rgsfile:FileName Crea un archivo .rgs en lugar de actualizar el Registro.  No se puede usar con /vrgfile o /regfile o /wixfile.

 /vrgfile:FileName Crea un archivo .vrg en lugar de actualizar el Registro.  No se puede usar con /regfile o /rgsfile o /wixfile.

 /rgm Crea un archivo .rgm además del archivo rgs.  Debe combinarse con /rgsfile.

 /wixfile:FileName Crea un archivo compatible Windows Installer conjunto de herramientas XML en lugar de actualizar el Registro.  No se puede usar con /regfile o /rgsfile o /vrgfile.

 /codebase Fuerza el registro con CodeBase en lugar de con Assembly.

 /assembly Fuerza el registro con Assembly en lugar de CodeBase.

 /unregister Anula el registro de este paquete.  No se puede usar

 con /regfile o /vrgfile o /rgsfile o /wixfile.

## <a name="see-also"></a>Consulte también
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Solución de problemas del registro de paquete RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
