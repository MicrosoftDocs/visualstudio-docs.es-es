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
ms.openlocfilehash: 1a83ce4cf47f8a1607e562dfdb69b5b7374de1a6
ms.sourcegitcommit: ca9375d1c48355f2e9f7bc1b2d3f0e94eb15db00
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "76022337"
---
# <a name="whats-new-in-msbuild-160"></a>Novedades de MSBuild 16.0

En este artículo se describen las características y propiedades actualizadas de MSBuild 16.0. Para ver las notas detalladas de la versión, consulte [MSBuild 16.0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

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
