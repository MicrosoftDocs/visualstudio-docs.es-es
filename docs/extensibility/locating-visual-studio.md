---
title: Localización de Visual Studio | Microsoft Docs
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c13146d0d48dc176417040bcb756bf8069ad3c3e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62907309"
---
# <a name="locate-visual-studio"></a>Busque Visual Studio

A partir de Visual Studio 2017, puede instalar varias instancias de la misma versión o edición incluso. Esto resulta útil cuando desea obtener una vista previa de la nueva funcionalidad en el equipo de desarrollo principal manteniendo la instalación anterior. Debido a estos cambios, no hay ningún valor de variable o del registro de entorno solo que se puede utilizar para buscar una instancia. En su lugar, puede usar un [consulta COM API](https://msdn.microsoft.com/library/microsoft.visualstudio.setup.configuration.aspx) para buscar instancias en función de criterios relacionados con la extensión.

Esto es una API rápida y de solo lectura con paquetes de NuGet disponibles para código nativo y administrado.

| Código | Paquete |
| ---- | --- |
| Nativo | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Administrado | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Puede buscar una sola instancia dada una ruta de acceso o el proceso actual, o enumerar todas las instancias. Consulte [nuestros ejemplos](https://github.com/Microsoft/vs-setup-samples) para obtener ejemplos completos de cómo encontrar Visual Studio.

## <a name="tools"></a>Herramientas

Para encontrar Visual Studio y otras herramientas en entornos de compilación, las secuencias de comandos de PowerShell, instaladores y más escenarios, hay una serie de herramientas de código abierto que puede usar directamente o redistribuir junto con sus propios scripts.

| Proyecto | Descripción |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Solo archivo ejecutable nativo para buscar instancias que cumplen criterios de lanzamiento o versión preliminar, qué producto está instalado y qué cargas de trabajo están instalados. También admite la búsqueda de Visual Studio 2010 y versiones más recientes, aunque menos información se devuelve para Visual Studio 2017 y versiones más recientes. Consulte la [wiki](https://github.com/Microsoft/vswhere/wiki) para obtener ejemplos. |
| [Cmdlets de VSSetup](https://github.com/Microsoft/vssetup.powershell) | Admitidas los cmdlets de PowerShell 2.0 y versiones más recientes que devuelven información completa como objetos que puede usar para buscar instancias en función de los mismos criterios que _vswhere_ y para detectar las propiedades incluso más acerca de las instancias. Consulte la [wiki](https://github.com/Microsoft/vssetup.powershell/wiki) para obtener ejemplos. |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Busca automáticamente _VSIXInstaller_ y pasa a través de la línea de comandos para instalar un **.vsix* archivo. Esta característica puede ser útil en los instaladores que no tienen compatibilidad directa para la API de consulta. Consulte la [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) para obtener ejemplos. |

## <a name="see-also"></a>Vea también

* [Cambios realizados en el programa de instalación de Visual Studio 2017](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
