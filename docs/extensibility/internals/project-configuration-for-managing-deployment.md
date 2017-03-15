---
title: "Configuraci&#243;n del proyecto para administrar la implementaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuraciones de proyecto, la administración de implementación"
  - "proyectos [Visual Studio SDK], configuración de administración de implementación"
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Configuraci&#243;n del proyecto para administrar la implementaci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La implementación es el acto físicamente de mover los elementos de salida de un proceso de compilación en la ubicación esperada para la depuración y la instalación.  Por ejemplo, una aplicación web se puede compilar en un equipo local y después colocar en el servidor.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] admite dos maneras que los proyectos se pueden incluir en la implementación:  
  
-   Como el asunto del proceso de implementación.  
  
-   Como administrador del proceso de implementación.  
  
 Antes de que las soluciones puedan implementar, debe agregar primero un proyecto de implementación para configurar opciones de implementación.  Si no existe el proyecto de implementación ya, se le preguntará si desea crear uno al seleccionar **Implementar solución** del menú o haga clic con el botón secundario de **Generar** la solución.  Haga clic en **Sí** abre el cuadro de diálogo de **Agregar nuevo proyecto** con el proyecto de **Asistente para implementación remota** seleccionado.  
  
 El equipo remoto implementan el asistente le indica el tipo de aplicación \(Windows o Web\), los grupos de salida del proyecto a inclusión, los archivos adicionales que desea incluir, y el equipo remoto desea implementar en.  La última página del asistente muestra un resumen de las opciones seleccionadas.  
  
 Los proyectos que están el asunto de la producción del proceso de implementación generan los elementos que se deben mover un entorno alternativo.  Estos elementos de salida se describen como parámetros para la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> , cuyo propósito principal si de permitir proyectos de agrupar salidas.  Para obtener más información sobre la implementación de `IVsProjectCfg2`, vea [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md).  
  
 Los proyectos de implementación, que administra el proceso de implementación, permiten el comando deploy y responden a este comando está seleccionado.  Los proyectos de implementación implementan la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> para realizar la implementación y realizar llamadas a la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> para señalar implemente los eventos de estado.  
  
 Las configuraciones se pueden especificar las dependencias que afectan a las operaciones de compilación o de implementación.  Compile o implemente las dependencias son los proyectos que se van a compilar o implementar antes o después de que se compilar o implementar la configuración propios.  Compile las dependencias entre proyectos se describen con la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> y implementan dependencias con la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> .  Para obtener más información, vea [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md).  
  
## Vea también  
 [Administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md)   
 [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)   
 [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md)