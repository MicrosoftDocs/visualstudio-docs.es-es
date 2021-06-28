---
title: Buscar Visual Studio | Microsoft Docs
description: Puede instalar varias instancias de la misma versión de Visual Studio. Aprenda a usar una API de consulta COM para buscar la instancia que desee.
ms.custom: SEO-VS-2020
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
author: leslierichardson95
ms.author: lerich
ms.workload:
- vssdk
ms.openlocfilehash: cd0fcd294983d6a6567676f06703b4bd1dd376c4
ms.sourcegitcommit: b4cc3dee59421f7089112becf128a369acadaf61
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2021
ms.locfileid: "112990511"
---
# <a name="locate-visual-studio"></a>Localización de Visual Studio

A partir Visual Studio 2017, puede instalar varias instancias de la misma versión o incluso edición. Esto resulta útil cuando desea obtener una vista previa de la nueva funcionalidad en la máquina de desarrollo principal mientras mantiene la instalación anterior. Debido a estos cambios, no hay ninguna variable de entorno única o valor del Registro que pueda usar para buscar una instancia. En su lugar, puede usar una [API de consulta COM](/dotnet/api/microsoft.visualstudio.setup.configuration) para buscar instancias basadas en criterios pertinentes para la extensión.

Se trata de una API rápida y de solo lectura con paquetes NuGet disponibles para código nativo y administrado.

| Código | Paquete |
| ---- | --- |
| Nativa | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Administrado | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Puede buscar una sola instancia dada una ruta de acceso o el proceso actual, o enumerar todas las instancias. Consulte [nuestros ejemplos](https://github.com/Microsoft/vs-setup-samples) para obtener ejemplos completos de cómo buscar Visual Studio.

## <a name="tools"></a>Herramientas

Para encontrar Visual Studio y otras herramientas en entornos de compilación, scripts de PowerShell, instaladores y otros escenarios, hay una serie de herramientas de código abierto que puede usar directamente o redistribuir junto con sus propios scripts.

| Proyecto | Descripción |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Ejecutable nativo de un solo archivo para buscar instancias que cumplan criterios como la versión o la versión previa, qué producto está instalado y qué cargas de trabajo están instaladas. También admite la búsqueda Visual Studio 2010 y versiones más recientes, aunque se devuelve menos información para Visual Studio 2017 y versiones posteriores. Consulte la [wiki para](https://github.com/Microsoft/vswhere/wiki) obtener ejemplos. |
| [Cmdlets de VSSetup](https://github.com/Microsoft/vssetup.powershell) | Los cmdlets de PowerShell admiten la versión 2.0 y versiones posteriores que  devuelven información enriquecte como objetos que se pueden usar para buscar instancias basadas en los mismos criterios que en otros lugares y para detectar aún más propiedades sobre las instancias. Consulte la [wiki para](https://github.com/Microsoft/vssetup.powershell/wiki) obtener ejemplos. |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Busca automáticamente _VSIXInstaller_ y pasa la línea de comandos a través de para instalar un archivo **.vsix.* Esta característica puede ser útil en instaladores que no tienen compatibilidad directa con las API de consulta. Consulte la [wiki para](https://github.com/Microsoft/vsixbootstrapper/wiki) obtener ejemplos. |

## <a name="see-also"></a>Consulta también

* [Cambios en la Visual Studio de 2017](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
* [Inicio de Visual Studio con DTE](launch-visual-studio-dte.md)
