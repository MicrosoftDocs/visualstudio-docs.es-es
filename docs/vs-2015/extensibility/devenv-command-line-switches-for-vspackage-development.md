---
title: Modificadores de la línea de comandos de devenv para el desarrollo de VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
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
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 97ce429a7140d7b95393c2dcb8b34491b3adfefa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185277"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Modificadores de la línea de comandos Devenv para el desarrollo de VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] permite a los desarrolladores automatizar las tareas desde la línea de comandos al ejecutar devenv.exe, el archivo que inicia el entorno de desarrollo integrado (IDE) de Visual Studio.  
  
 Las tareas incluyen:  
  
- Implementación de aplicaciones en configuraciones prediseñadas desde fuera del IDE.  
  
- Compilar proyectos automáticamente con valores de compilación predeterminados o configuraciones de depuración.  
  
- Cargar el IDE en configuraciones específicas, todo desde fuera del IDE. Además, puede personalizar el IDE al iniciarse.  
  
## <a name="guidelines-for-switches"></a>Directrices para modificadores  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en la documentación se describen los modificadores de línea de comandos de devenv de nivel de usuario. Para obtener más información, vea [modificadores de línea de comandos de devenv](../ide/reference/devenv-command-line-switches.md). Devenv también admite modificadores de línea de comandos adicionales que son útiles con el desarrollo, la implementación y la depuración de VSPackage.  
  
|Modificador de la línea de comandos|Descripción|  
|--------------------------|-----------------|  
|/SafeMode|Inicia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en modo seguro, cargando solo los servicios y el IDE predeterminados. El modificador/SafeMode impide que se carguen los VSPackages de terceros cuando [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se inicia, lo que garantiza una ejecución estable.<br /><br /> Este modificador no toma ningún argumento.|  
|/resetskippkgs|Borra todas las opciones de carga omitidas agregadas por los usuarios que quieren evitar cargar VSPackages problemáticos y, a continuación, comienza [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . La presencia de una etiqueta SkipLoading deshabilita la carga de un VSPackage. Al borrar la etiqueta, se vuelve a habilitar la carga del VSPackage.<br /><br /> Este modificador no toma ningún argumento.|  
|/rootsuffix|Comienza [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] con una ubicación alternativa. El siguiente comando lo ejecuta el acceso directo creado por el [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] instalador:<br /><br /> devenv/RootSuffix exp<br /><br /> En este caso, exp identifica una ubicación con un sufijo determinado, por ejemplo, 10.0 exp en lugar de 10,0. La instancia experimental le permite depurar un VSPackage por separado de la instancia de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que está usando para escribir código.<br /><br /> Este modificador puede tomar cualquier cadena que identifique una ubicación que haya creado mediante VSRegEx.exe. Para obtener más información, vea [la instancia experimental](../extensibility/the-experimental-instance.md).|  
|/splash|Muestra la [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pantalla de presentación como de costumbre y muestra un cuadro de mensaje antes de mostrar el IDE principal. El cuadro de mensaje le permite estudiar la pantalla de presentación, por ejemplo, para comprobar si hay un icono de producto de VSPackage.<br /><br /> Este modificador no toma ningún argumento.|  
  
## <a name="see-also"></a>Consulte también  
 [Agregar modificadores de la línea de comandos](../extensibility/adding-command-line-switches.md)   
 [Modificadores de línea de comandos de devenv](../ide/reference/devenv-command-line-switches.md)
