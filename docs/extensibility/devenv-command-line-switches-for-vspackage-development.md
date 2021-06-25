---
title: Modificadores de Command-Line de desarrollo de VSPackage | Microsoft Docs
description: Obtenga información sobre cómo los desarrolladores pueden automatizar las tareas desde la línea de comandos al ejecutar devenv.exe, el archivo que inicia el IDE Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /Setup command line switch
- /ResetSkipPkgs command line switch
- /RootSuffix command line switch
- /SafeMode command line switch
- /Splash command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4ea08b4714a79e09fce5933b67997a032532481f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904248"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Modificadores de línea de comandos Devenv para el desarrollo de VSPackage

Visual Studio permite a los desarrolladores automatizar tareas desde la línea de comandos al ejecutar , el archivo que `devenv.exe` inicia Visual Studio IDE.

 Las tareas incluyen:

- Implementación de aplicaciones en configuraciones prediseñadas desde fuera del IDE.

- Compilar proyectos automáticamente mediante configuraciones de compilación preestablecidas o configuraciones de depuración.

- Cargar el IDE en configuraciones específicas, todo desde fuera del IDE. También puede personalizar el IDE al iniciarse.

## <a name="guidelines-for-switches"></a>Directrices para conmutadores

Visual Studio documentación describe los modificadores de línea de comandos `devenv` de nivel de usuario. Para obtener más información, vea [Modificadores de línea de comandos de Devenv.](../ide/reference/devenv-command-line-switches.md) La `devenv` herramienta también admite modificadores de línea de comandos adicionales que son útiles con el desarrollo, la implementación y la depuración de VSPackage.

| Modificador de línea de comandos | Descripción |
|---------------------| - |
| `/ResetSkipPkgs` | Borra todas las opciones de skip loading que han agregado los usuarios que desean evitar la carga de VSPackages problemáticos y, a continuación, Visual Studio. La presencia de una etiqueta SkipLoading deshabilita la carga de un VSPackage. Al borrar la etiqueta, se vuelve a habilitar la carga del VSPackage.<br /><br /> Este modificador no toma ningún argumento. |
| `/RootSuffix` | Inicia Visual Studio mediante una ubicación alternativa. El siguiente comando se ejecuta mediante el acceso directo creado por el instalador Visual Studio SDK:<br /><br /> `devenv /RootSuffix exp`<br /><br /> En este caso, `exp` identifica una ubicación con un sufijo determinado (por ejemplo, en lugar de `10.0Exp` `10.0` ). La instancia experimental permite depurar un VSPackage independientemente de la instancia de Visual Studio que se usa para escribir código.<br /><br /> Este modificador puede tomar cualquier cadena que identifique una ubicación que haya creado mediante VSRegEx.exe. Para obtener más información, vea [La instancia experimental](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Inicia Visual Studio en modo seguro, cargando solo el IDE y los servicios predeterminados. El modificador impide que todos los VSPackages de terceros se carguen Visual Studio inicio, lo que `/SafeMode` garantiza una ejecución estable.<br /><br /> Este modificador no toma ningún argumento. |
| `/Setup` | Fuerza Visual Studio a combinar metadatos de recursos que describen menús, barras de herramientas y grupos de comandos de todos los VSPackages disponibles. Solo puede ejecutar este comando como administrador. <br /><br /> Este modificador no toma ningún argumento. El comando `devenv /Setup` suele ser el último paso del proceso de instalación. El uso del `/Setup` modificador no inicia el IDE.|
| `/Splash` | Muestra la Visual Studio de presentación, como de costumbre, y, a continuación, muestra un cuadro de mensaje antes de mostrar el IDE principal. El cuadro de mensaje le permite estudiar la pantalla de presentación (por ejemplo, para comprobar si hay un icono de producto de VSPackage).<br /><br /> Este modificador no toma ningún argumento. |

## <a name="see-also"></a>Consulta también

- [Adición de modificadores de línea de comandos](../extensibility/adding-command-line-switches.md)
- [Modificadores de línea de comandos para Devenv](../ide/reference/devenv-command-line-switches.md)
