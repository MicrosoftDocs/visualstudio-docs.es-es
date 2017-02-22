---
title: "Modificadores de l&#237;nea de comandos devenv para el desarrollo de VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/Setup (modificador de línea de comandos)"
  - "modificador de línea de comandos/resetskippkgs"
  - "modificador de línea de comandos /noVSIP"
  - "modificador de línea de comandos /rootsuffix"
  - "modificadores de la línea de comandos"
  - "registro, SDK de Visual Studio"
  - "modificadores de línea de comandos"
  - "SDK de Visual Studio, los modificadores de línea de comandos"
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# Modificadores de l&#237;nea de comandos devenv para el desarrollo de VSPackage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permite a los desarrolladores automatizar las tareas desde la línea de comandos cuando se ejecuta devenv.exe, el archivo que se inicia el entorno de desarrollo integrado \(IDE\) de Visual Studio.  
  
 Las tareas incluyen:  
  
-   Implementación de aplicaciones en configuraciones prediseñadas desde fuera del IDE.  
  
-   Automáticamente compilar proyectos mediante programación la configuración de compilación o configuraciones de depuración.  
  
-   Cargando el IDE en configuraciones específicas, todo ello desde fuera del IDE. Además, puede personalizar el IDE al iniciarse.  
  
## Directrices para conmutadores  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] documentación describe los modificadores de línea de comandos de devenv de nivel de usuario. Para obtener más información, consulta [Modificadores de línea de comandos para Devenv](../ide/reference/devenv-command-line-switches.md). Devenv también admite modificadores de línea de comandos adicionales que son útiles con desarrollo VSPackage, implementación y depuración.  
  
|Modificador de línea de comandos|Descripción|  
|--------------------------------------|-----------------|  
|\/SafeMode|Inicia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en modo seguro, cargando únicamente el IDE predeterminado y los servicios. El modificador \/safemode evita que cargar cuando todos los VSPackages de otros fabricantes [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] inicia, garantizando así una ejecución estable.<br /><br /> Este modificador no toma ningún argumento.|  
|\/ resetskippkgs|Borra todos los omitir las opciones de carga que se han agregado los usuarios que desean evitar cargar VSPackages problemático, a continuación, inicia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. La presencia de una etiqueta SkipLoading deshabilita la carga de un VSPackage. Borrar la etiqueta rehabilita la carga de VSPackage.<br /><br /> Este modificador no toma ningún argumento.|  
|\/rootsuffix|Inicia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mediante el uso de una ubicación alternativa. El siguiente comando se ejecuta con el acceso directo creado por el [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] instalador:<br /><br /> Devenv \/RootSuffix exp<br /><br /> En este caso, exp identifica una ubicación con un sufijo determinado, por ejemplo 10.0Exp en lugar de 10.0. La instancia experimental permite depurar un VSPackage por separado de la instancia de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que utiliza para escribir código.<br /><br /> Este parámetro puede tomar cualquier cadena que identifica una ubicación que ha creado con VSRegEx.exe. Para obtener más información, consulta [La instancia Experimental](../extensibility/the-experimental-instance.md).|  
|\/Splash|Muestra el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] como de costumbre de pantalla de presentación y, a continuación, se muestra un cuadro de mensaje antes de mostrar el IDE principal. El cuadro de mensaje permite estudiar la pantalla de presentación, busque un icono de producto VSPackage, por ejemplo.<br /><br /> Este modificador no toma ningún argumento.|  
  
## Vea también  
 [Agregando modificadores de línea de comandos](../extensibility/adding-command-line-switches.md)   
 [Modificadores de línea de comandos para Devenv](../ide/reference/devenv-command-line-switches.md)