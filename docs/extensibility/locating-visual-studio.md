---
title: Buscar Visual Studio | Microsoft Docs
description: Puede instalar varias instancias de la misma versión de Visual Studio. Obtenga información sobre cómo usar una API de consulta COM para buscar la instancia que desee.
ms.custom: SEO-VS-2020
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 175623723b8f7b59a644a439afd10246eab01c95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893599"
---
# <a name="locate-visual-studio"></a>Localización de Visual Studio

A partir de Visual Studio 2017, puede instalar varias instancias de la misma versión o incluso la edición. Esto resulta útil si desea obtener una vista previa de la nueva funcionalidad en el equipo de desarrollo principal mientras mantiene la instalación anterior. Debido a estos cambios, no hay una única variable de entorno o valor del registro que pueda usar para buscar una instancia. En su lugar, puede usar una [API de consulta com](/dotnet/api/microsoft.visualstudio.setup.configuration) para buscar instancias en función de los criterios relevantes para la extensión.

Se trata de una API rápida de solo lectura con paquetes NuGet disponibles para código nativo y administrado.

| Código | Paquete |
| ---- | --- |
| Nativa | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Administrados | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Puede buscar una sola instancia dada una ruta de acceso o el proceso actual, o enumerar todas las instancias. Consulte [nuestros ejemplos](https://github.com/Microsoft/vs-setup-samples) para obtener ejemplos completos de cómo encontrar Visual Studio.

## <a name="tools"></a>Herramientas

Para encontrar Visual Studio y otras herramientas en entornos de compilación, scripts de PowerShell, instaladores y más escenarios, hay una serie de herramientas de código abierto que puede usar directamente o redistribuir junto con sus propios scripts.

| Proyecto | Descripción |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Ejecutable nativo de un solo archivo para buscar instancias que cumplen criterios como la versión o la versión preliminar, el producto que se instala y las cargas de trabajo que se instalan. También admite la búsqueda de Visual Studio 2010 y versiones más recientes, aunque se devuelve menos información para Visual Studio 2017 y versiones más recientes. Vea la [wiki](https://github.com/Microsoft/vswhere/wiki) para obtener ejemplos. |
| [Cmdlets de VSSetup](https://github.com/Microsoft/vssetup.powershell) | Los cmdlets de PowerShell admiten 2,0 y versiones más recientes que devuelven información enriquecida como objetos que se pueden usar para buscar instancias en función de los mismos criterios que _vswhere_ y para detectar aún más propiedades sobre las instancias. Vea la [wiki](https://github.com/Microsoft/vssetup.powershell/wiki) para obtener ejemplos. |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Localiza _VSIXInstaller_ automáticamente y pasa la línea de comandos para instalar un archivo **. vsix* . Esta característica puede ser útil en los instaladores que no son compatibles directamente con las API de consulta. Vea la [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) para obtener ejemplos. |

## <a name="see-also"></a>Vea también

* [Cambios en el programa de instalación de Visual Studio 2017](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
* [Inicio de Visual Studio con DTE](launch-visual-studio-dte.md)