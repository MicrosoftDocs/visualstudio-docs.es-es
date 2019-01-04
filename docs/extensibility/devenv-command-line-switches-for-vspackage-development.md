---
title: Modificadores de línea de comandos para devenv para el desarrollo de VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- /setup command line switch
- /resetskippkgs command line switch
- /noVSIP command line switch
- /rootsuffix command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e4333f7e0c892771ffb9b4643f4814cf3352a8f1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820298"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Modificadores de línea de comandos para devenv para el desarrollo de VSPackage
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permite a los desarrolladores a automatizar las tareas desde la línea de comandos al ejecutar *devenv.exe*, el archivo que se inicia el entorno de desarrollo integrado (IDE) de Visual Studio.  

 Las tareas incluyen:  

-   Implementación de aplicaciones en las configuraciones prediseñadas desde fuera del IDE.  

-   Compilar proyectos mediante programación la configuración de generación o automáticamente configuraciones de depuración.  

-   Cargando el IDE en configuraciones específicas, todo ello desde fuera del IDE. Además, puede personalizar el IDE al iniciarse.  

## <a name="guidelines-for-switches"></a>Directrices para los modificadores  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] documentación describe los modificadores de línea de comandos para devenv de nivel de usuario. Para obtener más información, consulte [modificadores de línea de comandos para Devenv](../ide/reference/devenv-command-line-switches.md). Devenv también admite modificadores de línea de comandos adicionales que son útiles con desarrollo VSPackage, implementación y depuración.  


| Conmutador de línea de comandos | Descripción |
|---------------------| - |
| /SafeMode | Inicia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en modo seguro, cargando solo el IDE predeterminado y los servicios. El modificador /safemode impide que todos los VSPackages de terceros se cargue cuando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se inicia, lo que garantiza una ejecución estable.<br /><br /> Este modificador no toma ningún argumento. |
| / resetskippkgs | Borra todo omitir las opciones de carga que se han agregado los usuarios que deseen evitar cargar VSPackages problemáticos, a continuación, inicia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. La presencia de una etiqueta SkipLoading deshabilita la carga de un VSPackage. Al borrar la etiqueta rehabilita la carga del VSPackage.<br /><br /> Este modificador no toma ningún argumento. |
| /rootsuffix | Se inicia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mediante el uso de una ubicación alternativa. El siguiente comando se ejecuta el acceso directo creado por el [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] instalador:<br /><br /> Devenv /RootSuffix exp<br /><br /> En este caso, exp identifica una ubicación con un sufijo determinado, por ejemplo 10.0Exp en lugar de a 10.0. Permite depurar un paquete VSPackage por separado de la instancia de la instancia experimental [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que está usando para escribir código.<br /><br /> Este parámetro puede tomar cualquier cadena que identifica una ubicación que ha creado mediante el uso de VSRegEx.exe. Para obtener más información, consulte [la instancia Experimental](../extensibility/the-experimental-instance.md). |
| /Splash | Muestra el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] como de costumbre en pantalla de presentación y, a continuación, se muestra un cuadro de mensaje antes de mostrar el IDE principal. El cuadro de mensaje le estudiar la pantalla de presentación, para que busque un icono de producto de VSPackage, por ejemplo.<br /><br /> Este modificador no toma ningún argumento. |

## <a name="see-also"></a>Vea también  
 [Agregar modificadores de línea de comandos](../extensibility/adding-command-line-switches.md)   
 [Modificadores de línea de comandos para Devenv](../ide/reference/devenv-command-line-switches.md)