---
title: Novedades de MSBuild 16.0 | Microsoft Docs
description: Obtenga información sobre las características y propiedades modificadas y actualizadas para MSBuild 16.0 y el vínculo a las notas de la versión.
ms.custom: SEO-VS-2020
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: a4e0079fa301d751962a945a0bf8348ffd3c359d
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047790"
---
# <a name="whats-new-in-msbuild-160"></a>Novedades de MSBuild 16.0

En este artículo se describen las características y propiedades actualizadas de MSBuild 16.0. Para ver las notas detalladas de la versión, consulte [MSBuild 16.0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Ruta de acceso cambiada

 MSBuild está instalado en la carpeta *\Current* de cada versión de Visual Studio, y los archivos ejecutables están en la subcarpeta *\Bin*. Por ejemplo, la ruta de acceso para *MSBuild. exe* instalado con Visual Studio 2019 Community es *C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe*. También puede usar el siguiente módulo de PowerShell para buscar MSBuild: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Propiedades cambiadas

 Las siguientes propiedades de MSBuild se han actualizado debido al nuevo número de versión.

- `MSBuildToolsVersion` para esta versión de las herramientas es "Current". La versión del ensamblado es la misma que en Visual Studio 2017, que es 15.1.0.0.

- `VisualStudioVersion` para esta versión de las herramientas es "16.0"

## <a name="updates"></a>Actualizaciones

MSBuild (y Visual Studio) ahora tiene como destino .NET Framework 4.7.2. Si quiere usar las nuevas características de API de MSBuild, también debe actualizar el ensamblado, pero el código existente seguirá funcionando.

## <a name="see-also"></a>Vea también

- [MSBuild](../msbuild/msbuild.md)
