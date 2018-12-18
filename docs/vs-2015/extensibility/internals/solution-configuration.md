---
title: Configuración de soluciones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 53d8e3d33a81e20d553e6a5c97eb6e6f33339079
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801614"
---
# <a name="solution-configuration"></a>Configuración de soluciones
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Configuraciones de soluciones almacenan propiedades de nivel de solución. Estos dirigen el comportamiento de la **iniciar** clave (F5) y **compilar** comandos. De forma predeterminada, estos comandos compilación e iniciar la configuración de depuración. Ambos comandos se ejecutan en el contexto de una configuración de soluciones. Esto significa que el usuario puede esperar F5 para iniciar y se configura independientemente de la solución activa a través de la configuración de compilación. El entorno está diseñado para optimizar para soluciones en lugar de los proyectos en cuanto a la generación y ejecución.  
  
 La barra de herramientas estándar de Visual Studio contiene un botón de inicio y una lista desplegable a la derecha del botón Inicio de la configuración de soluciones. Esta lista permite a los usuarios elegir la configuración que se iniciarán cuando se presiona F5, crear sus propias configuraciones de soluciones o editar una configuración existente.  
  
> [!NOTE]
>  No hay ninguna interfaz de extensibilidad para crear o editar las configuraciones de soluciones. Debe usar `DTE.SolutionBuilder`. Sin embargo, hay una API de extensibilidad para administrar la compilación de la solución. Para obtener más información, consulta <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.  
  
 Le mostramos cómo puede implementar las configuraciones de soluciones compatibles con el tipo de proyecto:  
  
- Proyecto  
  
   Muestra los nombres de los proyectos que se encuentran en la solución actual.  
  
- Configuración  
  
   Para proporcionar la lista de configuraciones compatibles con el tipo de proyecto y aparece en las páginas de propiedades, implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>.  
  
   La columna configuración muestra el nombre de la configuración del proyecto para compilar en esta configuración de soluciones y enumera todas las configuraciones de proyecto al hacer clic en el botón de flecha. El entorno llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> método para rellenar esta lista. Si el <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> método indica que nuevo el proyecto admite la edición de la configuración, o las selecciones de edición también se muestran bajo el encabezado de la configuración. Cada una de estas selecciones iniciar cuadros de diálogo que llamar a métodos de la `IVsCfgProvider2` interfaz para modificar la configuración del proyecto.  
  
   Si un proyecto no es compatible con configuraciones, la columna configuración muestra ninguno y está deshabilitada.  
  
- Plataforma  
  
   Muestra la plataforma de compilaciones para la configuración del proyecto seleccionado y todas las plataformas disponibles para el proyecto muestra al hacer clic en el botón de flecha. El entorno llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> método para rellenar esta lista. Si el <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> método indica que nuevo el proyecto admite la edición de la plataforma, o las selecciones de edición también se muestran bajo el encabezado de la plataforma. Cada una de estas selecciones iniciar cuadros de diálogo que llaman a `IVsCfgProvider2` métodos para editar plataformas disponibles del proyecto.  
  
   Si un proyecto no es compatible con plataformas, la columna de la plataforma para ese proyecto muestra ninguno y está deshabilitada.  
  
- Compilar  
  
   Especifica si el proyecto se compila la configuración de la solución actual. Los proyectos no seleccionados no se compilan cuando se invocan los comandos de compilación de nivel de la solución a pesar de todas las dependencias de proyecto que contienen. Proyectos seleccionados no se generarán todavía se incluyen en la depuración, ejecución, empaquetado e implementación de la solución.  
  
- Implementar  
  
   Especifica si el proyecto se implementará cuando se usan los comandos de inicio o implementar con la configuración de compilación de la solución seleccionada. La casilla de verificación para este campo estará disponible si el proyecto admite la implementación mediante la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfaz en su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> objeto.  
  
  Una vez que se agrega una nueva configuración de soluciones, el usuario puede seleccionar en el cuadro de lista desplegable de configuración de soluciones en la barra de herramientas estándar para generar o se comienza a esa configuración.  
  
## <a name="see-also"></a>Vea también  
 [Administración de las opciones de configuración](../../extensibility/internals/managing-configuration-options.md)   
 [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)   
 [Objeto de configuración del proyecto](../../extensibility/internals/project-configuration-object.md)

