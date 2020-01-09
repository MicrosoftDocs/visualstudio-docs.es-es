---
title: Novedades de MSBuild 16.0 | Microsoft Docs
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 3e6ecfc1c08f30eb0232f230d955967d95bc32ee
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566974"
---
# <a name="whats-new-in-msbuild-160"></a>Novedades de MSBuild 16.0

En este artículo se describen las características y propiedades actualizadas de MSBuild 16.0. Para ver las notas detalladas de la versión (solo versión de borrador), consulte [MSBuild 16.0](https://gist.github.com/rainersigwald/009627466f03964d0028e16fda633d9c).

## <a name="changed-path"></a>Ruta de acceso cambiada

 MSBuild está instalado en la carpeta *\Current* de cada versión de Visual Studio. Por ejemplo, *C:\Archivos de programa (x86)\Microsoft Visual Studio\Current\Enterprise\MSBuild*. También puede utilizar el siguiente módulo de PowerShell para localizar MSBuild: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Propiedades cambiadas

 Las siguientes propiedades de MSBuild se han actualizado debido al nuevo número de versión.

- `MSBuildToolsVersion` para esta versión de las herramientas es "Current". La versión del ensamblado es la misma que en Visual Studio 2017, que es 15.1.0.0.

- `VisualStudioVersion` para esta versión de las herramientas es "16.0"

## <a name="updates"></a>Actualizaciones

MSBuild (y Visual Studio) ahora tiene como destino .NET Framework 4.7.2. Si quiere usar las nuevas características de API de MSBuild, también debe actualizar el ensamblado, pero el código existente seguirá funcionando.

## <a name="see-also"></a>Vea también
- [MSBuild](../msbuild/msbuild.md)
