---
title: Elegir el directorio de instalación de un paquete VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 41a5016c528e754e452ee1248e85b705c41a44ac
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56621076"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>Elija el directorio de instalación de un VSPackage
Un VSPackage y sus archivos auxiliares deben estar en el sistema de archivos de un usuario. La ubicación depende de si VSPackage está administrado o no administrados, el esquema de versiones en paralelo y la elección del usuario.

## <a name="unmanaged-vspackages"></a>VSPackages no administrados
 Un VSPackage no administrado es un servidor COM que se puede instalar en cualquier ubicación. La información de registro debe reflejar con precisión su ubicación. La interfaz de usuario (UI) de installer debe proporcionar una ubicación predeterminada como un subdirectorio de la `ProgramFilesFolder` valor de propiedad de Windows Installer. Por ejemplo:

*&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\V1.0\\*

 El usuario debería poder cambiar el directorio predeterminado para dar cabida a los usuarios que tenga una partición de arranque pequeño y prefiera instalar aplicaciones y herramientas en otro volumen.

 Si el esquema de side-by-side usa un VSPackage con control de versiones, puede usar los subdirectorios para almacenar versiones diferentes. Por ejemplo:

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2002\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2003\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2005\\*

## <a name="managed-vspackages"></a>VSPackages administrado
 VSPackages administrado también puede instalarse en cualquier ubicación. Sin embargo, debe considerar siempre su instalación en la caché global de ensamblados (GAC) para reducir los tiempos de carga de ensamblado. Dado que los paquetes VSPackage administrados siempre son ensamblados con nombre seguro, su instalación en la GAC significa que toma su comprobación de firma de nombre seguro solo durante la instalación. Ensamblados con nombre seguro instalados en otro lugar en el sistema de archivos deben tener sus firmas comprueba cada vez que se cargan. Al instalar los paquetes VSPackage administrados en la GAC, use la herramienta regpkg **/assembly** conmutador para escribir entradas del registro que apunte al nombre seguro del ensamblado.

 Si instala los paquetes VSPackage administrados en una ubicación distinta de la GAC, siga los consejos anteriores dado para los VSPackages no administrados para elegir las jerarquías de directorio. Use la herramienta regpkg **/ codebase** conmutador para escribir entradas del registro que apunte a la ruta de acceso del ensamblado de VSPackage.

 Para obtener más información, consulte [registrar y anular el registro de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).

## <a name="satellite-dlls"></a>Archivos DLL satélite
 Por convención, VSPackage archivos DLL, que contienen los recursos para una configuración regional concreta, satélite se encuentran en los subdirectorios de la *VSPackage* directory. Los subdirectorios se corresponden con los valores de configuración regional (LCID) de identificador.

 El [administrar VSPackages](../../extensibility/managing-vspackages.md) artículo indica que las entradas del registro controlan dónde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] realmente busca un VSPackage satélite DLL. Sin embargo, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] intenta cargar un archivo DLL satélite en un subdirectorio con nombre para un valor LCID, en el orden siguiente:

1.  LCID de predeterminado (LCID de Visual Studio; por ejemplo, *\1033* para inglés)

2.  LCID predeterminado con el subidioma de forma predeterminada.

3.  LCID predeterminado del sistema.

4.  Sistema LCID predeterminado con el subidioma de forma predeterminada.

5.  EE. UU. Inglés (*. \1033* o *. \0x409*).


Si la DLL de VSPackage incluye los recursos y la **SatelliteDll\DllName** entrada del Registro apunta a ella, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] intenta cargarlos en el orden anterior.

## <a name="see-also"></a>Vea también
- [Elección entre VSPackages compartidos y con control de versiones](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Administrar los paquetes VSPackage](../../extensibility/managing-vspackages.md)
- [Administrar registro de paquete](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)