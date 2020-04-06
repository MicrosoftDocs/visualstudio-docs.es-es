---
title: Conmutadores de línea de comandos de Devenv para el desarrollo de VSPackage Microsoft Docs
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
ms.openlocfilehash: ad3a5125a730b9230959bbf9342b4c0a4823c4d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712192"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Modificadores de línea de comandos Devenv para el desarrollo de VSPackage

Visual Studio permite a los desarrolladores automatizar `devenv.exe`tareas desde la línea de comandos al ejecutar , el archivo que inicia el IDE de Visual Studio.

 Las tareas incluyen:

- Implementación de aplicaciones en configuraciones prediseñadas desde fuera del IDE.

- Creación automática de proyectos mediante configuraciones de compilación predefinidas o configuraciones de depuración.

- Cargar el IDE en configuraciones específicas, todo desde fuera del IDE. También puede personalizar el IDE al iniciarse.

## <a name="guidelines-for-switches"></a>Directrices para interruptores

La documentación de Visual Studio `devenv` describe los modificadores de línea de comandos de nivel de usuario. Para obtener más información, consulte [Conmutadores de línea de comandos de Devenv](../ide/reference/devenv-command-line-switches.md). La `devenv` herramienta también admite modificadores de línea de comandos adicionales que son útiles con el desarrollo, la implementación y la depuración de VSPackage.

| Interruptor de línea de comandos | Descripción |
|---------------------| - |
| `/ResetSkipPkgs` | Borra todas las opciones de carga de omisión que han agregado los usuarios que desean evitar cargar VSPackages problemáticos y, a continuación, inicia Visual Studio. La presencia de un SkipLoading etiqueta deshabilita la carga de un VSPackage. Borrar la etiqueta vuelve a habilitar la carga del VSPackage.<br /><br /> Este modificador no toma ningún argumento. |
| `/RootSuffix` | Inicia Visual Studio mediante una ubicación alternativa. El siguiente comando se ejecuta mediante el acceso directo creado por el instalador del SDK de Visual Studio:<br /><br /> `devenv /RootSuffix exp`<br /><br /> En este `exp` caso, identifica una ubicación con un `10.0Exp` sufijo `10.0`determinado (por ejemplo, en lugar de ). La instancia experimental permite depurar un VSPackage por separado de la instancia de Visual Studio que está utilizando para escribir código.<br /><br /> Este modificador puede tomar cualquier cadena que identifique una ubicación que haya creado mediante VSRegEx.exe. Para obtener más información, consulte [La instancia experimental](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Inicia Visual Studio en modo seguro, cargando solo el IDE y los servicios predeterminados. El `/SafeMode` modificador impide que todos los VSPackages de terceros se carguen cuando se inicia Visual Studio, lo que garantiza una ejecución estable.<br /><br /> Este modificador no toma ningún argumento. |
| `/Setup` | Obliga a Visual Studio a combinar metadatos de recursos que describen menús, barras de herramientas y grupos de comandos de todos los VSPackages disponibles. Solo puede ejecutar este comando como administrador. <br /><br /> Este modificador no toma ningún argumento. El comando `devenv /Setup` suele ser el último paso del proceso de instalación. El uso `/Setup` del modificador no inicia el IDE.|
| `/Splash` | Muestra la pantalla de presentación de Visual Studio, como de costumbre y, a continuación, muestra un cuadro de mensaje antes de mostrar el IDE principal. El cuadro de mensaje le permite estudiar la pantalla de presentación (por ejemplo, para comprobar si hay un icono de producto de VSPackage).<br /><br /> Este modificador no toma ningún argumento. |

## <a name="see-also"></a>Vea también

- [Agregar modificadores de línea de comandos](../extensibility/adding-command-line-switches.md)
- [Modificadores de línea de comandos para Devenv](../ide/reference/devenv-command-line-switches.md)
