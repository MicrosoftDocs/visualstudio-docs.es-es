---
title: Utilidad RegPkg | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: da637b365eec260a7c1c34bbe7ba96c785cc18fc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781288"
---
# <a name="regpkg-utility"></a>Utilidad RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
>  Es la mejor manera de registrar paquetes en Visual Studio mediante el uso de los archivos .pkgdef. Esto permite la implementación de extensión sin necesidad de tener acceso al registro del sistema, que es un requisito para la implementación de VSIX. Archivos pkgdef se crean mediante el [utilidad CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Para obtener más información sobre la implementación de paquetes de Visual Studio, consulte [envío extensiones de Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).  
  
 La utilidad RegPkg.exe registra un VSPackage con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] y prepararlo para la implementación. Esta utilidad se usa en segundo plano durante el desarrollo de VSPackage. Se ejecuta como parte del proceso de compilación para que se puede compilar y ejecutar un paquete VSPackage en el subárbol experimental.  
  
 RegPkg puede generar scripts de registro del sistema en varios formatos. Puede incorporar estas secuencias de comandos en los proyectos de implementación como proyectos de .msi o archivos de Windows Installer XML Toolset.  
  
 Se suele encontrarse en RegPkg.exe \< *ruta de instalación del SDK de Visual Studio*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg sigue esta sintaxis:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root:root  
 Realiza el registro bajo especificado  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] raíz.  
  
 /regfile:filename  
 Crea un archivo .reg en lugar de actualizar el registro.  No se puede usar con /vrgfile o /rgsfile o /wixfile.  
  
 /rgsfile:filename  
 Crea un archivo .rgs en lugar de actualizar el registro.  No se puede usar con /vrgfile o /regfile o /wixfile.  
  
 /vrgfile:filename  
 Crea un archivo .vrg en lugar de actualizar el registro.  No se puede usar con /regfile o /rgsfile o /wixfile.  
  
 /rgm  
 Crea un archivo .rgm además del archivo rgs.  Se debe combinar con /rgsfile.  
  
 /wixfile:filename  
 Crea un archivo compatible con Windows Installer XML Toolset en lugar de actualizar el registro.  No se puede usar con /regfile o /rgsfile o /vrgfile.  
  
 /codebase  
 Registro de las fuerzas con código base en lugar de ensamblado.  
  
 /Assembly  
 Registro de fuerza con el ensamblado en lugar de código base.  
  
 / unregister  
 Anula el registro de este paquete.  No se puede usar  
  
 con /regfile o /vrgfile o /rgsfile o /wixfile.  
  
## <a name="see-also"></a>Vea también  
 [Publicación de un producto](../../misc/releasing-a-visual-studio-integration-product.md)   
 [Solución de problemas del registro de paquete RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)

