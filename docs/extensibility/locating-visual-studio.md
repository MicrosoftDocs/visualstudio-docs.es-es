---
title: "Ubicación de Visual Studio | Documentos de Microsoft"
ms.custom: 
ms.date: 08/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5623ea382266fdbcd59bbe57b71522a7a1f4a31e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="locating-visual-studio"></a>Ubicación de Visual Studio

A partir de 2017 de Visual Studio, puede instalar varias instancias de la misma versión o edición incluso. Esto resulta útil cuando desea obtener una vista previa de la nueva funcionalidad en el equipo de desarrollo principal conservando la instalación anterior. Debido a estos cambios, no hay ningún valor de registro o la variable de entorno único que se puede utilizar para buscar una instancia. En su lugar, puede usar un [consulta COM API](https://msdn.microsoft.com/library/microsoft.visualstudio.setup.configuration.aspx) para encontrar instancias basándose en criterios relacionados con la extensión.

Se trata de una API rápida y de solo lectura con paquetes de NuGet disponibles para código nativo y administrado.

| Código | Package |
| ---- | --- |
| Nativo | https://NuGet.org/Packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Administrado | https://NuGet.org/Packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Puede encontrar una sola instancia tiene una ruta de acceso o el proceso actual o enumerar todas las instancias. Vea [nuestros ejemplos](https://github.com/Microsoft/vs-setup-samples) para obtener ejemplos completos de cómo encontrar Visual Studio.

## <a name="tools"></a>Herramientas

Para encontrar Visual Studio y otras herramientas en entornos de compilación, las secuencias de comandos de PowerShell, instaladores y más escenarios, tenemos una variedad de herramientas de código abierto, puede usar directamente o redistribuir junto con sus propios scripts.

| Proyecto | Descripción |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Solo archivo ejecutable nativo para localizar instancias que cumplen criterios como la versión o una versión preliminar, qué producto está instalado y se instalan las cargas de trabajo. También admite la búsqueda de Visual Studio 2010 y versiones más recientes, aunque menos información se devuelve para Visual Studio de 2017 y versiones más recientes. Consulte la [wiki](https://github.com/Microsoft/vswhere/wiki) para obtener ejemplos. |
| [Cmdlets de VSSetup](https://github.com/Microsoft/vssetup.powershell) | Admitidas los cmdlets de PowerShell 2.0 y versiones más recientes que devuelven información detallada como objetos que puede usar para buscar instancias en función de los mismos criterios como _vswhere_ y detectar propiedades incluso más acerca de las instancias. Consulte la [wiki](https://github.com/Microsoft/vssetup.powershell/wiki) para obtener ejemplos. |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Busca automáticamente _VSIXInstaller_ y pasa a través de la línea de comandos para instalar un _.vsix_ archivo. Esto puede ser útil en los instaladores que no tienen una compatibilidad directa para la API de consulta. Consulte la [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) para obtener ejemplos. |

## <a name="see-also"></a>Vea también

* [Cambios en el programa de instalación Visual Studio de 2017](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup)
