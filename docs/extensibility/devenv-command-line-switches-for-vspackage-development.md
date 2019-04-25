---
title: Modificadores de línea de comandos para devenv para el desarrollo de VSPackage | Microsoft Docs
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
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd95fe31949b51c7167337ad21c51251e84a19a7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705536"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Modificadores de línea de comandos para devenv para el desarrollo de VSPackage

Visual Studio permite a los desarrolladores a automatizar las tareas desde la línea de comandos al ejecutar `devenv.exe`, el archivo que se inicia el IDE de Visual Studio.

 Las tareas incluyen:

- Implementación de aplicaciones en las configuraciones prediseñadas desde fuera del IDE.

- Compilar proyectos mediante programación la configuración de generación o automáticamente configuraciones de depuración.

- Cargando el IDE en configuraciones específicas, todo ello desde fuera del IDE. También puede personalizar el IDE al iniciarse.

## <a name="guidelines-for-switches"></a>Directrices para los modificadores

Documentación de Visual Studio describe el nivel de usuario `devenv` modificadores de línea de comandos. Para obtener más información, consulte [modificadores de línea de comandos para Devenv](../ide/reference/devenv-command-line-switches.md). El `devenv` herramienta también admite modificadores de línea de comandos adicionales que son útiles con desarrollo VSPackage, implementación y depuración.

| Conmutador de línea de comandos | Descripción |
|---------------------| - |
| `/ResetSkipPkgs` | Borra todas las opciones de carga de omitir que se han agregado los usuarios que desea evitar cargar VSPackages problemáticos, a continuación, se inicia Visual Studio. La presencia de una etiqueta SkipLoading deshabilita la carga de un VSPackage. Al borrar la etiqueta rehabilita la carga del VSPackage.<br /><br /> Este modificador no toma ningún argumento. |
| `/RootSuffix` | Se inicia Visual Studio mediante el uso de una ubicación alternativa. El acceso directo creado por el instalador del SDK de Visual Studio, se ejecuta el comando siguiente:<br /><br /> `devenv /RootSuffix exp`<br /><br /> En este caso, `exp` identifica una ubicación con un sufijo determinado (por ejemplo, `10.0Exp` en lugar de `10.0`). La instancia experimental permite depurar un paquete VSPackage por separado de la instancia de Visual Studio que se usa para escribir código.<br /><br /> Este parámetro puede tomar cualquier cadena que identifica una ubicación que ha creado mediante el uso de VSRegEx.exe. Para obtener más información, consulte [la instancia Experimental](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Visual Studio se inicia en modo seguro, cargando solo el IDE predeterminado y los servicios. El `/SafeMode` modificador impide que todos los VSPackages de terceros se carga cuando se inicia Visual Studio, lo que garantiza una ejecución estable.<br /><br /> Este modificador no toma ningún argumento. |
| `/Setup` | Fuerza a Visual Studio para combinar los metadatos de recursos que describen los menús, barras de herramientas y los grupos de comandos de todos los VSPackages disponibles. Sólo se puede ejecutar este comando como administrador. <br /><br /> Este modificador no toma ningún argumento. El comando `devenv /Setup` suele ser el último paso del proceso de instalación. El uso de la `/Setup` conmutador no inicia el IDE.|
| `/Splash` | Cuadro a continuación, se muestra un mensaje antes de mostrar el IDE principal y de pantalla, como de costumbre, se muestra la presentación de Visual Studio. El cuadro de mensaje le estudiar la pantalla de presentación (por ejemplo, para que busque un icono de producto de VSPackage).<br /><br /> Este modificador no toma ningún argumento. |

## <a name="see-also"></a>Vea también

- [Agregar modificadores de línea de comandos](../extensibility/adding-command-line-switches.md)
- [Modificadores de línea de comandos para Devenv](../ide/reference/devenv-command-line-switches.md)