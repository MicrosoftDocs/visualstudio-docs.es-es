---
title: API de MSBuild | Microsoft Docs
description: Obtenga información sobre la superficie de API pública que proporciona MSBuild para que el programa pueda realizar compilaciones e inspeccionar proyectos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b376f1cb1d6b473c0ea37bb33f6ae2b60789fa24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919300"
---
# <a name="use-the-msbuild-api"></a>Usar la API de MSBuild

MSBuild proporciona una superficie de API pública para que el programa pueda realizar compilaciones e inspeccionar proyectos. Las versiones recientes de las API MSBuild se pueden encontrar en los paquetes NuGet siguientes:

| Nombre del paquete | Descripción |
| ------------ | ----------- |
| [Microsoft.Build](https://www.nuget.org/packages/Microsoft.Build) | Contiene el ensamblado Microsoft.Build que se usa para crear, editar y evaluar proyectos de MSBuild.|
| [Microsoft.Build.Framework](https://www.nuget.org/packages/Microsoft.Build.Framework)| Contiene el ensamblado de marco de MSBuild común que usan otros ensamblados de MSBuild. |
| [Microsoft.Build.Runtime](https://www.nuget.org/packages/Microsoft.Build.Runtime) | Proporciona una copia ejecutable completa de MSBuild. Haga referencia a este paquete solo si la aplicación necesita cargar proyectos o ejecutar compilaciones en proceso sin requerir la instalación de MSBuild. La evaluación correcta de los proyectos con este paquete requiere la agregación de componentes adicionales (como los compiladores) en un directorio de aplicación. |
| [Microsoft.Build.Tasks.Core](https://www.nuget.org/packages/Microsoft.Build.Tasks.Core) | Contiene el ensamblado Microsoft.Build.Tasks que implementa las tareas de MSBuild que se usan habitualmente. |
| [Microsoft.Build.Utilities.Core](https://www.nuget.org/packages/Microsoft.Build.Utilities.Core) | Contiene el ensamblado Microsoft.Build.Utilities que se usa para implementar tareas de MSBuild personalizadas. |

Además, NuGet también hospeda un ensamblado heredado, [Microsoft.Build.Engine](https://www.nuget.org/packages/Microsoft.Build.Engine), que está en desuso.

Hay varias versiones diferentes de la API MSBuild y, para las versiones 15 y 16, hay dos formatos distintos de los ensamblados en los paquetes NuGet, uno compilado con .NET Framework y otro con .NET Core, que es un subconjunto de la superficie de las API de .NET Framework.  La versión de .NET Core de MSBuild se usa al invocar el comando `dotnet` y al utilizar MSBuild en sistemas Mac y Linux.

La documentación de la API MSBuild se puede encontrar mediante el [explorador de API de .NET](/dotnet/api), o bien si se examinan los espacios de nombres de la lista siguiente.

::: moniker range="vs-2017"
| Espacio de nombres | Se aplica a | Descripción |
|-----------| -----------| ----------- |
| [Microsoft.Build.Construction](/dotnet/api/Microsoft.Build.Construction?view=msbuild-15&preserve-view=true) | Todas |  Contiene tipos que el modelo de objetos de MSBuild usa para construir raíces del proyecto con valores no evaluados. Cada raíz del proyecto se corresponde a un archivo de proyecto o de destinos. |
| [Microsoft.Build.Definition](/dotnet/api/Microsoft.Build.Definition?view=msbuild-15&preserve-view=true) | Todas | Contiene la clase `ProjectOptions`, que admite la construcción de proyectos. |
| [Microsoft.Build.Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-15&preserve-view=true) | Todas | Contiene tipos que el modelo de objetos de MSBuild usa para evaluar proyectos. Cada proyecto está asociado a una o más raíces del proyecto. |
| [Microsoft.Build.Evaluation.Context](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-15&preserve-view=true) | Todas | Contiene la clase `EvaluationContext`, que se usa para almacenar el estado de la evaluación entre llamadas. |
| [Microsoft.Build.Exceptions](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-15&preserve-view=true) | Todas | Contiene los tipos de excepción que se pueden iniciar durante el proceso de compilación. |
| [Microsoft.Build.Execution](/dotnet/api/Microsoft.Build.Execution?view=msbuild-15&preserve-view=true) | Todas | Contiene tipos que el modelo de objetos de MSBuild usa para compilar proyectos. |
| [Microsoft.Build.Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-15&preserve-view=true) | Todas | Contiene los tipos que definen la forma en que las tareas y los registradores interactúan con el motor de MSBuild.|
| [Microsoft.Build.Framework.Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-15&preserve-view=true) | Todas | Contiene los tipos que admiten la generación de perfiles de rendimiento. |
| [Microsoft.Build.Framework.XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-15&preserve-view=true) | Solo para .NET Framework | Contiene clases que se usan para representar tipos XAML analizados desde archivos, reglas y otros orígenes. |
| [Microsoft.Build.Globbing](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-15&preserve-view=true) | Todas | Contiene clases que admiten el procesamiento de caracteres comodín. |
| [Microsoft.Build.Globbing.Extensions](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-15&preserve-view=true) | Todas | Contiene tipos que admiten extensiones para el procesamiento de caracteres comodín. |
| [Microsoft.Build.Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-15&preserve-view=true) | Todas | Contiene tipos que admiten el modificador `-graph` de MSBuild. |
| [Microsoft.Build.Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-15&preserve-view=true) | Todas | Contiene los tipos que se usan para registrar el progreso de una compilación. |
| [Microsoft.Build.ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-15&preserve-view=true) | Todas | Contiene tipos que admiten la comunicación remota en MSBuild. |
| [Microsoft.Build.Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-15&preserve-view=true) | Todas | Contiene la implementación de todas las tareas que se distribuyen con MSBuild. |
| [Microsoft.Build.Tasks.Deployment.Bootstrapper](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-15&preserve-view=true) | Solo para .NET Framework | Contiene clases que MSBuild usa de forma interna. |
| [Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-15&preserve-view=true) | Solo para .NET Framework | Contiene clases que usa MSBuild.|
| [Microsoft.Build.Tasks.Hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-15&preserve-view=true) | Todas | Contiene clases que MSBuild usa de forma interna. |
| [Microsoft.Build.Tasks.Xaml](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-15&preserve-view=true) | Solo para .NET Framework | Contiene clases relacionadas con las tareas de compilación de XAML. |
| [Microsoft.Build.Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-15&preserve-view=true) | Todas | Contiene clases auxiliares que puede usar para crear registradores y tareas de MSBuild propios.|
:::moniker-end
:::moniker range=">=vs-2019"
| Espacio de nombres | Se aplica a | Descripción |
|-----------| -----------| ----------- |
| [Microsoft.Build.Construction](/dotnet/api/Microsoft.Build.Construction?view=msbuild-16&preserve-view=true) | Todas |  Contiene tipos que el modelo de objetos de MSBuild usa para construir raíces del proyecto con valores no evaluados. Cada raíz del proyecto se corresponde a un archivo de proyecto o de destinos. |
| [Microsoft.Build.Definition](/dotnet/api/Microsoft.Build.Definition?view=msbuild-16&preserve-view=true) | Todas | Contiene la clase `ProjectOptions`, que admite la construcción de proyectos. |
| [Microsoft.Build.Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-16&preserve-view=true) | Todas | Contiene tipos que el modelo de objetos de MSBuild usa para evaluar proyectos. Cada proyecto está asociado a una o más raíces del proyecto. |
| [Microsoft.Build.Evaluation.Context](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-16&preserve-view=true) | Todas | Contiene la clase `EvaluationContext`, que se usa para almacenar el estado de la evaluación entre llamadas. |
| [Microsoft.Build.Exceptions](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-16&preserve-view=true) | Todas | Contiene los tipos de excepción que se pueden iniciar durante el proceso de compilación. |
| [Microsoft.Build.Execution](/dotnet/api/Microsoft.Build.Execution?view=msbuild-16&preserve-view=true) | Todas | Contiene tipos que el modelo de objetos de MSBuild usa para compilar proyectos. |
| [Microsoft.Build.Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-16&preserve-view=true) | Todas | Contiene los tipos que definen la forma en que las tareas y los registradores interactúan con el motor de MSBuild.|
| [Microsoft.Build.Framework.Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-16&preserve-view=true) | Todas | Contiene los tipos que admiten la generación de perfiles de rendimiento. |
| [Microsoft.Build.Framework.XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-16&preserve-view=true) | Solo para .NET Framework | Contiene clases que se usan para representar tipos XAML analizados desde archivos, reglas y otros orígenes. |
| [Microsoft.Build.Globbing](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-16&preserve-view=true) | Todas | Contiene clases que admiten el procesamiento de caracteres comodín. |
| [Microsoft.Build.Globbing.Extensions](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-16&preserve-view=true) | Todas | Contiene tipos que admiten extensiones para el procesamiento de caracteres comodín. |
| [Microsoft.Build.Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-16&preserve-view=true) | Todas | Contiene tipos que admiten el modificador `-graph` de MSBuild. |
| [Microsoft.Build.Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-16&preserve-view=true) | Todas | Contiene los tipos que se usan para registrar el progreso de una compilación. |
| [Microsoft.Build.ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-16&preserve-view=true) | Todas | Contiene tipos que admiten la comunicación remota en MSBuild. |
| [Microsoft.Build.Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-16&preserve-view=true) | Todas | Contiene la implementación de todas las tareas que se distribuyen con MSBuild. |
| [Microsoft.Build.Tasks.Deployment.Bootstrapper](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-16&preserve-view=true) | Solo para .NET Framework | Contiene clases que MSBuild usa de forma interna. |
| [Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-16&preserve-view=true) | Solo para .NET Framework | Contiene clases que usa MSBuild.|
| [Microsoft.Build.Tasks.Hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-16&preserve-view=true) | Todas | Contiene clases que MSBuild usa de forma interna. |
| [Microsoft.Build.Tasks.Xaml](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-16&preserve-view=true) | Solo para .NET Framework | Contiene clases relacionadas con las tareas de compilación de XAML. |
| [Microsoft.Build.Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-16&preserve-view=true) | Todas | Contiene clases auxiliares que puede usar para crear registradores y tareas de MSBuild propios.|
:::moniker-end

En la tabla anterior, Todas en la columna Se aplica a significa que los tipos del espacio de nombres están disponibles en las versiones para .NET Framework y .NET Core de la API MSBuild.
