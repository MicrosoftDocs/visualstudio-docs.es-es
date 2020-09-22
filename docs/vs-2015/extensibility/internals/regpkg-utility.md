---
title: Utilidad RegPkg | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1895d3b57e5109f824728021cb1d64f0c527384b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843034"
---
# <a name="regpkg-utility"></a>Utilidad RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> La mejor manera de registrar paquetes en Visual Studio es mediante el uso de archivos. pkgdef. Esto permite la implementación de la extensión sin tener que obtener acceso al registro del sistema, que es un requisito para la implementación de VSIX. Los archivos Pkgdef se crean mediante la [utilidad CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Para obtener más información sobre la implementación de paquetes de Visual Studio, vea [envío de extensiones de Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).  
  
 La utilidad RegPkg.exe registra un VSPackage con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] y lo prepara para la implementación. Esta utilidad se usa en segundo plano durante el desarrollo del VSPackage. Se ejecuta como parte del proceso de compilación para que pueda compilar y ejecutar un VSPackage en el subárbol experimental.  
  
 RegPkg puede generar scripts del registro del sistema en varios formatos. Puede incorporar estos scripts en proyectos de implementación como proyectos. msi o Windows Installer archivos de conjunto de herramientas XML.  
  
 Normalmente, RegPkg.exe se encuentra en \<*Visual Studio SDK installation path*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg sigue esta sintaxis:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root: raíz  
 Realiza el registro en el especificado.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] raíz.  
  
 /regfile: nombre de archivo  
 Crea un archivo. reg en lugar de actualizar el registro.  No se puede usar con/vrgfile o/rgsfile o/wixfile.  
  
 /rgsfile: nombre de archivo  
 Crea un archivo. RGS en lugar de actualizar el registro.  No se puede usar con/vrgfile o/regfile ni/wixfile.  
  
 /vrgfile: nombre de archivo  
 Crea un archivo. VRG en lugar de actualizar el registro.  No se puede usar con/regfile o/rgsfile ni/wixfile.  
  
 /rgm  
 Crea un archivo. RGM además del archivo RGS.  Debe combinarse con/rgsfile.  
  
 /wixfile: nombre de archivo  
 Crea un archivo compatible con el conjunto de herramientas de Windows Installer XML en lugar de actualizar el registro.  No se puede usar con/regfile o/rgsfile ni/vrgfile.  
  
 /codebase  
 Fuerza el registro con el código base en lugar del ensamblado.  
  
 /Assembly  
 Fuerza el registro con ensamblado en lugar de código base.  
  
 /unregister  
 Anula el registro de este paquete.  No se puede usar  
  
 con/regfile o/vrgfile o/rgsfile o/wixfile.  
  
## <a name="see-also"></a>Consulte también  
 [Lanzamiento de un producto](../../misc/releasing-a-visual-studio-integration-product.md)   
 [Solución de problemas del registro de paquete RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
