---
title: Utilidad RegPkg (RegPkg Utility) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cebfd7a9782a2760eb33f7e56bfe16b126fc6251
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705639"
---
# <a name="regpkg-utility"></a>Utilidad RegPkg
> [!NOTE]
> La forma preferida de registrar paquetes en Visual Studio es mediante archivos .pkgdef. Esto permite la implementación de extensiones sin tener que tener acceso al registro del sistema, que es un requisito para la implementación de VSIX. Los archivos Pkgdef se crean mediante [la utilidad CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Para obtener más información sobre la implementación de paquetes de Visual Studio, vea Envío de [extensiones](../../extensibility/shipping-visual-studio-extensions.md)de Visual Studio .

 La utilidad RegPkg.exe registra un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage con y lo prepara para la implementación. Esta utilidad se usa en segundo plano durante el desarrollo de VSPackage. Se ejecuta como parte del proceso de compilación para que pueda compilar y ejecutar un VSPackage en el subárbol experimental.

 RegPkg puede generar scripts de registro del sistema en varios formatos. Puede incorporar estos scripts en proyectos de implementación como proyectos .msi o archivos de conjunto de herramientas XML de Windows Installer.

 RegPkg.exe se encuentra \<normalmente en la ruta de instalación del SDK de *Visual Studio*>. RegPkg sigue esta sintaxis:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root:root Realiza el registro en el

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] raíz.

 /regfile:FileName Crea un archivo .reg en lugar de actualizar el registro.  No se puede utilizar con /vrgfile o /rgsfile o /wixfile.

 /rgsfile:FileName Crea un archivo .rgs en lugar de actualizar el registro.  No se puede utilizar con /vrgfile o /regfile o /wixfile.

 /vrgfile:FileName Crea un archivo .vrg en lugar de actualizar el registro.  No se puede utilizar con /regfile o /rgsfile o /wixfile.

 /rgm Crea un archivo .rgm además del archivo rgs.  Debe combinarse con /rgsfile.

 /wixfile:FileName Crea un archivo compatible con el conjunto de herramientas XML de Windows Installer en lugar de actualizar el registro.  No se puede utilizar con /regfile o /rgsfile o /vrgfile.

 /codebase Fuerza el registro con CodeBase en lugar de Assembly.

 /assembly Fuerza el registro con Assembly en lugar de CodeBase.

 /unregister Anula el registro de este paquete.  No se puede utilizar

 con /regfile o /vrgfile o /rgsfile o /wixfile.

## <a name="see-also"></a>Vea también
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Solución de problemas del registro de paquete RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
