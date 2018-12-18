---
title: Utilidad RegPkg | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d677aaf155e533c27a775f3995b53dd59b65385
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130961"
---
# <a name="regpkg-utility"></a>Utilidad RegPkg
> [!NOTE]
>  Es la mejor manera de registrar paquetes en Visual Studio mediante el uso de archivos .pkgdef. Esto permite para la implementación de extensión sin necesidad de tener acceso al registro del sistema, que es un requisito para la implementación de VSIX. Pkgdef archivos se crean mediante el [CreatePkgDef utilidad](../../extensibility/internals/createpkgdef-utility.md). Para obtener más información sobre la implementación de paquetes de Visual Studio, vea [trasvase extensiones de Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).  
  
 La utilidad RegPkg.exe registra un VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y lo prepara para la implementación. Esta utilidad se usa en segundo plano durante el desarrollo de VSPackage. Se ejecuta como parte del proceso de compilación para que pueda compilar y ejecutar un paquete VSPackage en el subárbol experimental.  
  
 RegPkg puede generar scripts de registro del sistema en varios formatos. Puede incorporar estos scripts en el proyecto de implementación, como .msi o archivos de Windows Installer XML Toolset.  
  
 Se suele encontrarse en RegPkg.exe \< *ruta de instalación del SDK de Visual Studio*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg sigue esta sintaxis:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root:root  
 Realiza el registro en el especificado  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] raíz.  
  
 /regfile:filename  
 Crea un archivo .reg en lugar de actualizar el registro.  No se puede usar con /vrgfile o /rgsfile o /wixfile.  
  
 /rgsfile:filename  
 Crea un archivo .rgs en lugar de actualizar el registro.  No se puede usar con /vrgfile o /regfile o /wixfile.  
  
 /vrgfile:filename  
 Crea un archivo .vrg en lugar de actualizar el registro.  No se puede usar con /regfile o /rgsfile o /wixfile.  
  
 /rgm  
 Crea un archivo .rgm además del archivo rgs.  Debe combinarse con /rgsfile.  
  
 /wixfile:filename  
 Crea un archivo compatible con Windows Installer XML Toolset en lugar de actualizar el registro.  No se puede usar con /regfile o /rgsfile o /vrgfile.  
  
 /codebase  
 Registro de las fuerzas con código base en lugar de ensamblado.  
  
 /Assembly  
 Registro de las fuerzas con el ensamblado en lugar de código base.  
  
 / unregister  
 Anula el registro de este paquete.  No se puede usar  
  
 con /regfile o /vrgfile o /rgsfile o /wixfile.  
  
## <a name="see-also"></a>Vea también  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 [Solución de problemas del registro de paquete RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)