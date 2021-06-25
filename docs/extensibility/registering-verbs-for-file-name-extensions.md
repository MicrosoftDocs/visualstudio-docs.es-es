---
title: Registro de verbos para extensiones de nombre de archivo | Microsoft Docs
description: Obtenga información sobre cómo registrar un verbo asociado a un identificador de programación para una extensión de nombre de archivo mediante una clave de Shell.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c223dea7e265d8d040d502c99ded09380e89690f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901232"
---
# <a name="register-verbs-for-file-name-extensions"></a>Registro de verbos para extensiones de nombre de archivo
La asociación de una extensión de nombre de archivo con una aplicación suele tener una acción preferida que se produce cuando un usuario hace doble clic en un archivo. Esta acción preferida está vinculada a un verbo, por ejemplo abierto, que corresponde a la acción.

 Puede registrar verbos asociados a un identificador de programación (ProgID) para una extensión mediante la clave de shell que se encuentra en **HKEY_CLASSES_ROOT \{ progid}\shell**. Para obtener más información, vea [Tipos de archivo](/windows/desktop/shell/fa-file-types).

## <a name="register-standard-verbs"></a>Registro de verbos estándar
 El sistema operativo reconoce los siguientes verbos estándar:

- Abrir

- Editar

- Reproducir

- Impresión

- Vista previa

  Siempre que sea posible, registre un verbo estándar. La opción más común es el verbo Abrir. Use el verbo Editar solo si hay una diferencia clara entre abrir el archivo y editarlo. Por ejemplo, al abrir *.htm* archivo se muestra en el explorador, mientras que al editar un archivo *.htm* se inicia un editor HTML. Los verbos estándar se localizan con la configuración regional del sistema operativo.

> [!NOTE]
> Al registrar verbos estándar, no establezca el valor predeterminado para la tecla Open. El valor predeterminado contiene la cadena de presentación en el menú. El sistema operativo proporciona esta cadena para verbos estándar.

 Los archivos de proyecto se deben registrar para iniciar una nueva instancia de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cuando un usuario abre el archivo. En el ejemplo siguiente se muestra un registro de verbo estándar para un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] proyecto.

```
[HKEY_CLASSES_ROOT\.csproj]
@="VisualStudio.csproj.8.0"

[HKEY_CLASSES_ROOT\.csproj\OpenWithList]
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]
@=""

[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]
"VisualStudio.csproj.8.0"=""

[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]
@="C# Project file"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""
```

 Para abrir un archivo en una instancia existente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , registre una clave DDEEXEC. En el ejemplo siguiente se muestra un registro de verbo estándar para un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] *archivo .cs.*

```
[HKEY_CLASSES_ROOT\.cs]
@="VisualStudio.cs.8.0"

[HKEY_CLASSES_ROOT\.cs\OpenWithList]
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]
@=""

[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]
"VisualStudio.cs.8.0"=""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]
@="C# Source file"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]
@="Open(\"%1\")"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]
@="VisualStudio.8.0"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]
@="system"
```

## <a name="set-the-default-verb"></a>Establecer el verbo predeterminado
 El verbo predeterminado es la acción que se ejecuta cuando un usuario hace doble clic en un archivo en Explorador de Windows. El verbo predeterminado es el verbo especificado como valor predeterminado para el HKEY_CLASSES_ROOT **\\ *clave progid*\Shell.** Si no se especifica ningún valor, el verbo predeterminado es el primer verbo especificado en la HKEY_CLASSES_ROOT **\\ *progid*\Shell** key list.

> [!NOTE]
> Si planea cambiar el verbo predeterminado de una extensión en una implementación en paralelo, tenga en cuenta el impacto en la instalación y eliminación. Durante la instalación, se sobrescribe el valor predeterminado original.

## <a name="see-also"></a>Consulta también
- [Administración de asociaciones de archivos en paralelo](../extensibility/managing-side-by-side-file-associations.md)
