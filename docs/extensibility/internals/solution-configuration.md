---
title: "Configuraci&#243;n de soluciones | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuraciones de soluciones"
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Configuraci&#243;n de soluciones
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Configuraciones de soluciones almacenan propiedades de nivel de solución. Indican el comportamiento de la **Start** clave \(F5\) y **Build** comandos. De forma predeterminada, estos comandos compilación e iniciar la configuración de depuración. Ambos comandos se ejecutan en el contexto de una configuración de soluciones. Esto significa que el usuario puede esperar F5 para iniciar y cualquier la solución activa se configura a través de la configuración de compilación. El entorno está diseñado para optimizar para soluciones en lugar de proyectos en cuanto a la generación y ejecución.  
  
 La barra de herramientas estándar de Visual Studio contiene un botón de inicio y una lista desplegable a la derecha del botón Inicio de la configuración de soluciones. Esta lista permite a los usuarios elegir la configuración que se inicie cuando se presiona F5, crear sus propias configuraciones de soluciones o editar una configuración existente.  
  
> [!NOTE]
>  No hay ninguna interfaz de extensibilidad para crear o editar las configuraciones de soluciones. Debe usar `DTE.SolutionBuilder`. Sin embargo, hay una API de extensibilidad para administrar la compilación de la solución. Para obtener más información, consulta <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.  
  
 Le mostramos cómo puede implementar las configuraciones de soluciones compatibles con el tipo de proyecto:  
  
-   Proyecto  
  
     Muestra los nombres de los proyectos de la solución actual.  
  
-   Configuración  
  
     Para proporcionar la lista de configuraciones compatibles con el tipo de proyecto y aparece en las páginas de propiedades, implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>.  
  
     La columna de configuración muestra el nombre de la configuración del proyecto para compilar en esta configuración de soluciones y enumera todas las configuraciones de proyecto al hacer clic en el botón de flecha. El entorno llama el <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> método para rellenar esta lista. Si el <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> método indica que nuevo el proyecto admite la edición de la configuración, o editar selecciones aparecen bajo el encabezado de la configuración. Cada una de estas selecciones iniciar cuadros de diálogo que llaman a métodos de la `IVsCfgProvider2` interfaz para modificar las configuraciones del proyecto.  
  
     Si un proyecto no admite las configuraciones, la columna configuración muestra ninguno y está deshabilitada.  
  
-   Plataforma  
  
     Muestra la plataforma que se genera para la configuración del proyecto seleccionado y enumera todas las plataformas disponibles para el proyecto al hacer clic en el botón de flecha. El entorno llama el <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> método para rellenar esta lista. Si el <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> método indica que nuevo proyecto admite la edición de plataforma, o editar selecciones aparecen bajo el encabezado de la plataforma. Cada una de estas selecciones iniciar cuadros de diálogo que llaman a `IVsCfgProvider2` métodos para editar las plataformas disponibles del proyecto.  
  
     Si un proyecto no es compatible con plataformas, la columna de la plataforma para el proyecto muestra ninguno y está deshabilitada.  
  
-   Compilar  
  
     Especifica si se compila el proyecto de la configuración de la solución actual. Proyectos no seleccionados no se generan cuando se invocan los comandos de compilación de nivel de la solución a pesar de las dependencias de proyecto que contienen. Proyectos seleccionados no se generarán todavía se incluyen en la depuración, ejecución, empaquetado e implementación de la solución.  
  
-   Implementar  
  
     Especifica si se permite o no se implementará el proyecto cuando se utilizan los comandos de inicio o implementar con la configuración de compilación de soluciones seleccionada. La casilla de verificación de este campo estará disponible si el proyecto admite la implementación mediante la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfaz en su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> objeto.  
  
 Una vez que se agrega una nueva configuración de soluciones, el usuario puede seleccionar en el cuadro de lista desplegable Configuración de soluciones en la barra de herramientas estándar para crear o iniciar esa configuración.  
  
## Vea también  
 [Administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md)   
 [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)   
 [Objeto de configuración de proyecto](../../extensibility/internals/project-configuration-object.md)