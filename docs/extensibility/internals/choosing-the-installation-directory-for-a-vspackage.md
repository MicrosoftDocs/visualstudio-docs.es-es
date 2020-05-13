---
title: Elegir el directorio de instalación para un VSPackage ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8391cbdd3a857ea4ebaf3a36655520935f1a128
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709764"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>Elija el directorio de instalación de un VSPackage
Un VSPackage y sus archivos auxiliares deben estar en el sistema de archivos de un usuario. La ubicación depende de si el VSPackage está administrado o no, el esquema de control de versiones en paralelo y la elección del usuario.

## <a name="unmanaged-vspackages"></a>VSPackages no administrados
 Un VSPackage no administrado es un servidor COM que se puede instalar en cualquier ubicación. Su información de registro debe reflejar con precisión su ubicación. La interfaz de usuario (UI) del instalador debe `ProgramFilesFolder` proporcionar una ubicación predeterminada como subdirectorio del valor de la propiedad de Windows Installer. Por ejemplo:

*&lt;ProgramFilesFolder&gt;\\&lt;&gt;\\&lt;MyCompany MyVSPackageProduct&gt;?V1.0\\*

 Se debe permitir al usuario cambiar el directorio predeterminado para dar cabida a los usuarios que mantienen una pequeña partición de arranque y prefieren instalar aplicaciones y herramientas en otro volumen.

 Si el esquema en paralelo usa un VSPackage versionado, puede usar subdirectorios para almacenar diferentes versiones. Por ejemplo:

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2002\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2003\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2005\\*

## <a name="managed-vspackages"></a>VSPackages administrado
 VSPackages administrados también se pueden instalar en cualquier ubicación. Sin embargo, debe considerar instalarlos siempre en la caché global de ensamblados (GAC) para reducir los tiempos de carga del ensamblado. Dado que los VSPackages administrados siempre son ensamblados con nombre seguro, instalarlos en la GAC significa que su comprobación de firma de nombre seguro toma solo en el momento de la instalación. Los ensamblados con nombre seguro instalados en otra parte del sistema de archivos deben tener sus firmas verificadas cada vez que se cargan. Al instalar VSPackages administrados en la GAC, use el modificador **/assembly** de la herramienta regpkg para escribir entradas del Registro que apunten al nombre seguro del ensamblado.

 Si instala VSPackages administrados en una ubicación distinta de la GAC, siga el consejo anterior dado para VSPackages no administrados para elegir jerarquías de directorios. Use el modificador **/codebase** de la herramienta regpkg para escribir entradas del Registro que apunten a la ruta de acceso del ensamblado VSPackage.

 Para obtener más información, vea Registrar y anular el registro de [VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).

## <a name="satellite-dlls"></a>archivos DLL satélite
 Por convención, los archivos DLL satélite de VSPackage, que contienen recursos para una configuración regional determinada, se encuentran en subdirectorios del directorio *VSPackage.* Los subdirectorios corresponden a valores de ID de configuración regional (LCID).

 El [administrar VSPackages](../../extensibility/managing-vspackages.md) artículo indica que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] las entradas del registro controlan donde realmente busca el archivo DLL satélite de un VSPackage. Sin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] embargo, intenta cargar un archivo DLL satélite en un subdirectorio denominado para un valor LCID, en el siguiente orden:

1. LCID predeterminado (Visual Studio LCID; por ejemplo, *1033* euros para inglés)

2. LCID predeterminado con el subidioma predeterminado.

3. LCID predeterminado del sistema.

4. LCID predeterminado del sistema con el subidioma predeterminado.

5. Inglés de los EE. UU. (*.-1033* o *.-0x409*).

Si el archivo DLL de VSPackage incluye recursos y la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entrada del Registro **SatelliteDll-DllName** apunta a él, intenta cargarlos en el orden anterior.

## <a name="see-also"></a>Vea también
- [Elija entre VSPackages compartidos y versionados](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Administración de VSPackages](../../extensibility/managing-vspackages.md)
- [Administrar el registro de paquetes](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
