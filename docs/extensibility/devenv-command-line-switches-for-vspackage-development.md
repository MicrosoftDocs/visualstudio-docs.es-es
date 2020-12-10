---
title: Modificadores de Command-Line devenv para el desarrollo de VSPackage | Microsoft Docs
description: Obtenga información sobre cómo los desarrolladores pueden automatizar las tareas desde la línea de comandos al ejecutar devenv.exe, el archivo que inicia el IDE de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: conceptual
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6e2784066c98f8fac696306e455e7cf26b65907
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996154"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Modificadores de línea de comandos Devenv para el desarrollo de VSPackage

Visual Studio permite a los desarrolladores automatizar las tareas desde la línea de comandos al ejecutarse `devenv.exe` , el archivo que inicia el IDE de Visual Studio.

 Las tareas incluyen:

- Implementación de aplicaciones en configuraciones prediseñadas desde fuera del IDE.

- Compilar proyectos automáticamente con valores de compilación predeterminados o configuraciones de depuración.

- Cargar el IDE en configuraciones específicas, todo desde fuera del IDE. También puede personalizar el IDE al iniciarse.

## <a name="guidelines-for-switches"></a>Directrices para modificadores

La documentación de Visual Studio describe los modificadores de línea de comandos de nivel de usuario `devenv` . Para obtener más información, vea [modificadores de la línea de comandos de devenv](../ide/reference/devenv-command-line-switches.md). La `devenv` herramienta también admite modificadores de línea de comandos adicionales que son útiles con el desarrollo, la implementación y la depuración de VSPackage.

| Modificador de la línea de comandos | Descripción |
|---------------------| - |
| `/ResetSkipPkgs` | Borra todas las opciones de carga omitidas agregadas por los usuarios que quieren evitar cargar VSPackages problemáticos y, a continuación, inicia Visual Studio. La presencia de una etiqueta SkipLoading deshabilita la carga de un VSPackage. Al borrar la etiqueta, se vuelve a habilitar la carga del VSPackage.<br /><br /> Este modificador no toma ningún argumento. |
| `/RootSuffix` | Inicia Visual Studio mediante una ubicación alternativa. El siguiente comando lo ejecuta el acceso directo creado por el instalador del SDK de Visual Studio:<br /><br /> `devenv /RootSuffix exp`<br /><br /> En este caso, `exp` identifica una ubicación con un sufijo determinado (por ejemplo, `10.0Exp` en lugar de `10.0` ). La instancia experimental le permite depurar un VSPackage por separado de la instancia de Visual Studio que está usando para escribir código.<br /><br /> Este modificador puede tomar cualquier cadena que identifique una ubicación que haya creado mediante VSRegEx.exe. Para obtener más información, vea [la instancia experimental](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Inicia Visual Studio en modo seguro, cargando solo los servicios y el IDE predeterminados. El `/SafeMode` modificador impide que se carguen los VSPackages de terceros cuando se inicia Visual Studio, lo que garantiza una ejecución estable.<br /><br /> Este modificador no toma ningún argumento. |
| `/Setup` | Fuerza a Visual Studio a combinar los metadatos de recursos que describen los menús, las barras de herramientas y los grupos de comandos de todos los VSPackages disponibles. Este comando solo se puede ejecutar como administrador. <br /><br /> Este modificador no toma ningún argumento. El comando `devenv /Setup` suele ser el último paso del proceso de instalación. El uso del `/Setup` modificador no inicia el IDE.|
| `/Splash` | Muestra la pantalla de presentación de Visual Studio, como de costumbre, y muestra un cuadro de mensaje antes de mostrar el IDE principal. El cuadro de mensaje le permite estudiar la pantalla de presentación (por ejemplo, para comprobar si hay un icono de producto de VSPackage).<br /><br /> Este modificador no toma ningún argumento. |

## <a name="see-also"></a>Consulte también

- [Agregar modificadores de la línea de comandos](../extensibility/adding-command-line-switches.md)
- [Modificadores de línea de comandos para Devenv](../ide/reference/devenv-command-line-switches.md)
