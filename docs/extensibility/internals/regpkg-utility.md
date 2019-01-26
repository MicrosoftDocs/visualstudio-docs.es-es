---
title: Utilidad RegPkg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc1e818e576c4593eb890f1f31b4d67d4c7c4488
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979431"
---
# <a name="regpkg-utility"></a>Utilidad RegPkg
> [!NOTE]
>  Es la mejor manera de registrar paquetes en Visual Studio mediante el uso de los archivos .pkgdef. Esto permite la implementación de extensión sin necesidad de tener acceso al registro del sistema, que es un requisito para la implementación de VSIX. Archivos pkgdef se crean mediante el [utilidad CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Para obtener más información sobre la implementación de paquetes de Visual Studio, consulte [envío extensiones de Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).  
  
 La utilidad RegPkg.exe registra un VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y prepararlo para la implementación. Esta utilidad se usa en segundo plano durante el desarrollo de VSPackage. Se ejecuta como parte del proceso de compilación para que se puede compilar y ejecutar un paquete VSPackage en el subárbol experimental.  
  
 RegPkg puede generar scripts de registro del sistema en varios formatos. Puede incorporar estas secuencias de comandos en los proyectos de implementación como proyectos de .msi o archivos de Windows Installer XML Toolset.  
  
 Se suele encontrarse en RegPkg.exe \< *ruta de instalación del SDK de Visual Studio*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg sigue esta sintaxis:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root:root  
 Realiza el registro bajo especificado  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] raíz.  
  
 /regfile:FileName  
 Crea un archivo .reg en lugar de actualizar el registro.  No se puede usar con /vrgfile o /rgsfile o /wixfile.  
  
 /rgsfile:FileName  
 Crea un archivo .rgs en lugar de actualizar el registro.  No se puede usar con /vrgfile o /regfile o /wixfile.  
  
 /vrgfile:FileName  
 Crea un archivo .vrg en lugar de actualizar el registro.  No se puede usar con /regfile o /rgsfile o /wixfile.  
  
 /rgm  
 Crea un archivo .rgm además del archivo rgs.  Se debe combinar con /rgsfile.  
  
 /wixfile:FileName  
 Crea un archivo compatible con Windows Installer XML Toolset en lugar de actualizar el registro.  No se puede usar con /regfile o /rgsfile o /vrgfile.  
  
 /codebase  
 Registro de las fuerzas con código base en lugar de ensamblado.  
  
 /Assembly  
 Registro de fuerza con el ensamblado en lugar de código base.  
  
 /unregister  
 Anula el registro de este paquete.  No se puede usar  
  
 con /regfile o /vrgfile o /rgsfile o /wixfile.  
  
## <a name="see-also"></a>Vea también  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 [Solución de problemas del registro de paquete RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)