---
title: Novedades de MSBuild 15 | Microsoft Docs
ms.date: 03/01/2017
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2017'
ms.openlocfilehash: 2503040e074a62422d4c7c904f5ad3a2bd84d6c1
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631034"
---
# <a name="whats-new-in-msbuild-15"></a>Novedades de MSBuild 15

MSBuild ahora está disponible como parte del [SDK de .NET Core](https://www.microsoft.com/net/download/core) y puede compilar proyectos de .NET Core en Windows, Mac OS y Linux.

## <a name="changed-path"></a>Ruta de acceso cambiada

 MSBuild ahora se instala en una carpeta bajo cada versión de Visual Studio. Por ejemplo, *C:\Archivos de programa (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild*. También puede utilizar el siguiente módulo de PowerShell para localizar MSBuild: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

 MSBuild ya no se instala en la memoria caché global de ensamblados. Para hacer referencia a MSBuild mediante programación, use paquetes NuGet. Para más información, consulte [Actualización de una aplicación existente a MSBuild 15.0](../msbuild/updating-an-existing-application.md).

## <a name="changed-properties"></a>Propiedades cambiadas

 Las siguientes propiedades de MSBuild se han actualizado debido al nuevo número de versión.

- `MSBuildToolsVersion` para esta versión de las herramientas es 15.0. La versión de ensamblado es 15.1.0.0.

- `MSBuildToolsPath` ya no tiene una ubicación fija. De forma predeterminada, se encuentra en la carpeta *MSBuild\15.0\Bin* relativa a la ubicación de instalación de Visual Studio, pero la ubicación de instalación de Visual Studio se puede cambiar en el momento de la instalación.

- Los valores `ToolsVersion` ya no se establecen en el registro.

- Las propiedades `SDK35ToolsPath` y `SDK40ToolsPath` apuntan al .NET Framework SDK que se incluye con esta versión de Visual Studio (por ejemplo, 10.0A para la versión 4.X de las herramientas).

## <a name="updates"></a>Actualizaciones

- El [elemento Project](../msbuild/project-element-msbuild.md) tiene un nuevo atributo `SDK`. También el atributo `Xmlns` es opcional ahora. Para obtener más información sobre el atributo `SDK`, vea [Cómo: Usar SDK de proyecto de MSBuild](../msbuild/how-to-use-project-sdk.md), [Paquetes, metapaquetes y marcos de trabajo](/dotnet/core/packages) y [Adiciones al formato csproj para .NET Core](/dotnet/core/tools/csproj).
- El [elemento Item](../msbuild/item-element-msbuild.md) tiene un nuevo atributo `Update`. Además, la restricción en el atributo `Remove` se ha eliminado.
- *Directory.Build.props* es un archivo definido por el usuario que proporciona personalizaciones a los proyectos de un directorio. Este archivo se importa automáticamente desde *Microsoft.Common.props*, a menos que la propiedad `ImportDirectoryBuildTargets` esté establecida en **false**. *Directory.Build.targets* lo importa *Microsoft.Common.targets*.
- Los metadatos con un nombre que no entre en conflicto con la lista actual de atributos pueden expresarse opcionalmente como un atributo. Para más información, consulte [Elemento Item](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Nuevas funciones de propiedad

- `EnsureTrailingSlash` agrega una barra diagonal final a una ruta de acceso si no existe una.
- `NormalizePath` combina elementos de ruta de acceso y garantiza que la cadena de salida tiene los caracteres separadores de directorio correctos para el sistema operativo actual.
- `NormalizeDirectory` combina elementos de ruta de acceso, garantiza una barra diagonal inicial y asegura que la cadena de salida tiene los caracteres separadores de directorio correctos para el sistema operativo actual.
- `GetPathOfFileAbove` devuelve la ruta de acceso del archivo inmediatamente anterior a este. Es funcionalmente equivalente a llamar a `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`.

## <a name="see-also"></a>Vea también

- [MSBuild](../msbuild/msbuild.md)
