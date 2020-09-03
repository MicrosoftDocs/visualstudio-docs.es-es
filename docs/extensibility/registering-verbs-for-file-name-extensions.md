---
title: Registrando verbos para las extensiones de nombre de archivo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac2854f1799075cc14d9beb557335be5228be21d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701530"
---
# <a name="register-verbs-for-file-name-extensions"></a>Registrar verbos para las extensiones de nombre de archivo
La Asociación de una extensión de nombre de archivo con una aplicación generalmente tiene una acción preferida que se produce cuando un usuario hace doble clic en un archivo. Esta acción preferida está vinculada a un verbo, como Open, que corresponde a la acción.

 Puede registrar verbos que están asociados a un identificador de programación (ProgID) para una extensión mediante la clave de Shell ubicada en **HKEY_CLASSES_ROOT \{ ProgID} \Shell**. Para obtener más información, vea [tipos de archivo](/windows/desktop/shell/fa-file-types).

## <a name="register-standard-verbs"></a>Registrar verbos estándar
 El sistema operativo reconoce los siguientes verbos estándar:

- Abrir

- Editar

- Reproducir

- Impresión

- Vista previa

  Siempre que sea posible, registre un verbo estándar. La opción más común es el verbo abierto. Utilice el verbo Edit solo si hay una diferencia clara entre abrir el archivo y editar el archivo. Por ejemplo, al abrir un archivo *. htm* , se muestra en el explorador, mientras que al editar un archivo *. htm* se inicia un editor HTML. Los verbos estándar se localizan con la configuración regional del sistema operativo.

> [!NOTE]
> Al registrar verbos estándar, no establezca el valor predeterminado de la clave abierta. El valor predeterminado contiene la cadena de presentación en el menú. El sistema operativo proporciona esta cadena para los verbos estándar.

 Los archivos de proyecto se deben registrar para iniciar una nueva instancia de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cuando un usuario abre el archivo. En el ejemplo siguiente se muestra un registro de verbo estándar para un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] proyecto de.

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

 Para abrir un archivo en una instancia existente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , registre una clave DDEEXEC. En el ejemplo siguiente se muestra un registro de verbo estándar para un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] archivo *. CS* .

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
 El verbo predeterminado es la acción que se ejecuta cuando un usuario hace doble clic en un archivo en el explorador de Windows. El verbo predeterminado es el verbo especificado como valor predeterminado para la clave **HKEY_CLASSES_ROOT \\ *ProgID*\Shell** . Si no se especifica ningún valor, el verbo predeterminado es el primer verbo especificado en la lista de claves de **HKEY_CLASSES_ROOT \\ *ProgID*\Shell** .

> [!NOTE]
> Si tiene previsto cambiar el verbo predeterminado de una extensión en una implementación en paralelo, tenga en cuenta el impacto en la instalación y la eliminación. Durante la instalación, se sobrescribe el valor predeterminado original.

## <a name="see-also"></a>Vea también
- [Administrar asociaciones de archivos en paralelo](../extensibility/managing-side-by-side-file-associations.md)
