---
title: "Interfaces (VSPackage del Control de origen) y servicios relacionados | Microsoft Docs"
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
  - "paquetes de control de código fuente, interfaces"
  - "interfaces de paquetes de control de código fuente"
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# Interfaces (VSPackage del Control de origen) y servicios relacionados
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Esta sección muestra todas las interfaces VSPackage\-relacionadas de control de código fuente en [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  El control de código fuente VSPackage implementa algunas de estas interfaces y utiliza otras para realizar tareas de control de código fuente.  
  
## interfaces implementadas por y para el control de código fuente VSPackages  
 Las interfaces siguientes se describen en [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], y el control de código fuente VSPackage implementa un subconjunto de ellas dependiendo del conjunto deseado de la característica.  algunas interfaces se marcan como sea necesario y se deben implementar por cada control de código fuente VSPackage.  
  
 para esas interfaces que un paquete no implemente, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona una implementación predeterminada.  Observe que la implementación predeterminada está diseñada para el caso cuando no se registra ningún VSPackage y no se controla ningún proyecto.  Un control de código fuente correctamente escrito VSPackage implementa todas las interfaces necesarias en lugar de dejándolo a la implementación predeterminada de esas interfaces.  
  
 Un control de código fuente VSPackage debe implementar un servicio privado que encapsula algunas o todas las interfaces de siguiente.  
  
 las interfaces son:  
  
-   requerido: La entidad correspondiente \(control de código fuente VSPackage, código auxiliar de control de código fuente, proyecto\) debe implementar la interfaz.  
  
-   recomendado: la entidad debe implementar esta interfaz; si no, la funcionalidad de control de código fuente puede estar limitado.  
  
-   opcional: la entidad puede implementar esta interfaz para proporcionar un conjunto más completo de características.  
  
|Interfaz|Propósito|Implementa por|¿Implementar?|  
|--------------|---------------|--------------------|-------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Los editores llaman a esta interfaz antes de modificar o de guardar un archivo.  El control de código fuente VSPackage puede desproteger el archivo o denegar la operación si se produce la desprotección.|control de código fuente VSPackage|Se recomienda|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Esta interfaz proporciona la funcionalidad básica de control de código fuente para los proyectos, como proyectos que registran y anular con control de código fuente y proporcionar compatibilidad con los glifos básicos de control de código fuente.|control de código fuente VSPackage|Obligatorio|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Esta interfaz se obtiene de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> mediante la función de <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> , o simplemente convertir el objeto que implementa `IVsHierarchy` a `IVsSccProject2`.  Se utiliza para obtener los archivos bajo control de código fuente en un proyecto o para informar al proyecto el estado o la ubicación actual del control de código fuente.|Proyecto|Obligatorio|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|El módulo de integración utiliza esta interfaz para establecer el paquete VSPackage activo actual.|control de código fuente VSPackage|Obligatorio|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Esta interfaz se basa en un modelo de pertenencia.  Cualquier VSPackage puede señalar que desea recibir eventos de documento y se aconsejado el shell en los eventos que están a punto de producirse.  Se implementa y administra [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], que a su vez pasa los eventos que implementan `IVsTrackProjectDocumentsEvents2` al Paquete.|Código auxiliar de control de código fuente|Obligatorio|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|Esta interfaz proporciona procesamiento por lotes, operaciones de lectura y escritura sincronizado, y un método avanzadas de `OnQueryAddFiles` .|Código auxiliar de control de código fuente|Obligatorio|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**Explorador de soluciones** y proyectos llaman a esta interfaz cuando los nuevos archivos se agregan a los proyectos, o cuando los archivos y carpetas cambian o eliminan de proyectos.  El control de código fuente VSPackage puede desproteger el archivo de proyecto o cancelar la operación.|control de código fuente VSPackage|Se recomienda|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**Explorador de soluciones** y proyectos llaman a esta interfaz en respuesta a las llamadas realizadas a los métodos de la interfaz IVstrackProjectDocuments3.  El control de código fuente VSPackage puede realizar operaciones por lotes, operaciones de lectura y escritura sincronizado, y trabajar con un método más avanzadas de `OnQueryAddFiles` .|control de código fuente VSPackage|Se recomienda|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|Esta interfaz proporciona compatibilidad de administración de matriculación para proyectos web.|control de código fuente VSPackage|Se recomienda|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|Esta interfaz se utiliza para recuperar la información sobre herramientas de los archivos controlados mediante código fuente en los proyectos.|control de código fuente VSPackage|Opcional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|Esta interfaz proporciona compatibilidad con la extensión de espacio de nombres.|control de código fuente VSPackage|Opcional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|El Paquete utiliza esta interfaz para integrar una extensión de espacio de nombres en los cuadros de diálogo de **Nuevo**, de **Abrir**, o de **Guardar** .  Por consiguiente, los proyectos se pueden agregar automáticamente al control de código fuente en creación, o agregar el control de código fuente cuando una operación de almacenamiento está vigente.|control de código fuente VSPackage|Opcional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|El Paquete utiliza esta interfaz para definir glifos adicionales como glifos de control de código fuente para los nodos de **Explorador de soluciones**.|control de código fuente VSPackage|Opcional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|El cuadro de diálogo de **Agregar** para proyectos web utiliza esta interfaz.  Proporciona métodos para buscar una ubicación de control de código fuente y abrir un proyecto web agregado en el repositorio de control de código fuente en esa ubicación.|control de código fuente VSPackage|Se recomienda|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|Esta interfaz proporciona compatibilidad para la carga asincrónica \(en segundo plano\) de proyectos de control de código fuente.|control de código fuente VSPackage|Opcional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|Esta interfaz permite proyectos de observar el progreso de carga asincrónica inicia <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>.|Proyecto|Opcional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|Esta interfaz permite que el IDE vea control de código fuente activo VSPackage.  Las consultas del IDE que el valor de los valores de control de código fuente que tienen un significado incluso cuando no haya ningún control de código fuente activo VSPackage registró.  Esta interfaz se implementa y controlada por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].|Código auxiliar de control de código fuente|Obligatorio|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|esta interfaz se utiliza en registrar el control de código fuente VSPackage.|Código auxiliar de control de código fuente|Obligatorio|  
|<xref:EnvDTE.SourceControl>|esta interfaz se utiliza en la automatización.  Como tal, expone sólo las funciones que se pueden ejecutar sin mostrar ninguna interfaz de usuario.|control de código fuente VSPackage|Opcional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|Esta interfaz se utiliza para guardar los valores de control de código fuente en el archivo de solución \(.sln\).  Los valores incluyen la ubicación de control de código fuente y el estado del control de origen marca.|control de código fuente VSPackage|Se recomienda|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|Esta interfaz se utiliza para guardar los valores de control de código fuente en el archivo de opciones de solución \(.suo\).  Esto puede incluir valores específicos del control de código fuente como la ubicación actual de la inscripción del usuario.|control de código fuente VSPackage|Se recomienda|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|Esta interfaz se utiliza para controlar eventos para realizar operaciones como archivos de proyecto de la protección antes de soluciones cerradas, o de obtener nuevos archivos de control de código fuente al abrir un proyecto.|control de código fuente VSPackage|Se recomienda|  
  
## Vea también  
 [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)