---
title: Modificadores de línea de comandos de devenv para el desarrollo de VSPackage | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: b6ad615048255452fc5642f8680b586d69587db5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134392"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Modificadores de línea de comandos de devenv para el desarrollo de VSPackage
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permite a los desarrolladores automatizar las tareas desde la línea de comandos cuando se ejecuta devenv.exe, el archivo que se inicia el entorno de desarrollo integrado (IDE) de Visual Studio.  
  
 Las tareas incluyen:  
  
-   Implementar aplicaciones en configuraciones prediseñadas desde fuera del IDE.  
  
-   Compilar proyectos mediante programación la configuración de compilación o automáticamente configuraciones de depuración.  
  
-   Cargando el IDE en configuraciones específicas, todo ello desde fuera del IDE. Además, puede personalizar el IDE al inicio.  
  
## <a name="guidelines-for-switches"></a>Directrices para conmutadores  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] documentación describe los modificadores de línea de comandos para devenv de nivel de usuario. Para obtener más información, consulte [Devenv Command Line Switches](../ide/reference/devenv-command-line-switches.md). Devenv también admite modificadores de línea de comandos adicionales que son útiles con el desarrollo VSPackage, implementación y depuración.  
  
|Modificador de línea de comandos|Descripción|  
|--------------------------|-----------------|  
|/SafeMode|Inicia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en modo seguro, cargando únicamente el IDE predeterminado y los servicios. El conmutador /safemode impide que cargue cuando todos los VSPackages de otros fabricantes [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] inicia, lo que garantiza una ejecución estable.<br /><br /> Este modificador no toma ningún argumento.|  
|/ resetskippkgs|Borra todos los omitir las opciones de carga que se han agregado los usuarios que desean evitar al cargar VSPackages problemáticos, a continuación, inicia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. La presencia de una etiqueta SkipLoading deshabilita la carga de un VSPackage. Borrar la etiqueta rehabilita la carga de VSPackage.<br /><br /> Este modificador no toma ningún argumento.|  
|/rootsuffix|Inicia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mediante el uso de una ubicación alternativa. El siguiente comando se ejecuta mediante el acceso directo creado por el [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] instalador:<br /><br /> Devenv /RootSuffix exp<br /><br /> En este caso, exp identifica una ubicación con un sufijo determinado, por ejemplo 10.0Exp en lugar de 10.0. La instancia experimental permite depurar un paquete VSPackage por separado de la instancia de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que usa para escribir código.<br /><br /> Este parámetro puede tomar cualquier cadena que identifica una ubicación que ha creado con VSRegEx.exe. Para obtener más información, consulte [la instancia Experimental](../extensibility/the-experimental-instance.md).|  
|/Splash|Muestra el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] como de costumbre en pantalla de presentación y, a continuación, se muestra un cuadro de mensaje antes de mostrar el IDE principal. El cuadro de mensaje permite estudiar la pantalla de presentación, para comprobar si un icono de producto de VSPackage, por ejemplo.<br /><br /> Este modificador no toma ningún argumento.|  
  
## <a name="see-also"></a>Vea también  
 [Adición de modificadores de línea de comandos](../extensibility/adding-command-line-switches.md)   
 [Modificadores de línea de comandos para Devenv](../ide/reference/devenv-command-line-switches.md)