---
title: "Actualizar proyectos | Microsoft Docs"
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
  - "actualizar VSPackages"
  - "actualizar aplicaciones, estrategias"
  - "VSPackages, compatibilidad con la actualización"
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Actualizar proyectos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Los cambios en el modelo de proyecto desde una versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el próximo pueden requieren que los proyectos y las soluciones se actualizan para que puedan ejecutarse en la versión más reciente.  [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] proporciona interfaces que se pueden utilizar para implementar la compatibilidad de actualización en dispone de proyectos.  
  
## Estrategias de actualización  
 Para admitir una actualización, la aplicación del sistema del proyecto debe definir e implementar una estrategia de actualización.  Para determinar la estrategia, puede elegir ofrecer en paralelo la copia de seguridad, la copia de seguridad de copia, o ambas \(de SxS\).  
  
-   La copia de seguridad de SxS significa que un proyecto copia solo los archivos que necesita actualizar en contexto, agregando un sufijo eficaz de nombre de archivo, por ejemplo, “.old”.  
  
-   La copia de seguridad de copia significa que un proyecto copia todos los elementos a la versión de la ubicación de la copia de seguridad.  Los archivos correspondientes en la ubicación original del proyecto se actualizan.  
  
## cómo funciona la actualización  
 Cuando una solución creada en una versión anterior de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se abre en una versión más reciente, el IDE comprueba el archivo de solución para determinar si es necesario actualizar.  Si se requiere la actualización, **Asistente para actualización** automáticamente se inicia para recorrer el usuario con el proceso de actualización.  
  
 Cuando una solución necesita actualizar, notifica las consultas cada generador de proyectos para su estrategia de actualización.  La estrategia determina si el generador de proyectos admite la copia de seguridad de copia o la copia de seguridad de SxS.  La información se envía a **Asistente para actualización**, que obtiene la información necesaria para la copia de seguridad y muestra las opciones aplicables al usuario.  
  
### Soluciones de varios proyectos  
 Si una solución contiene varios proyectos y difieren las estrategias de actualización, por ejemplo cuando el proyecto de c\+\+. que sólo admite la copia de seguridad de SxS y un proyecto web que solo la copia de seguridad de copia admiten, generadores de proyecto debe negociar la estrategia de actualización.  
  
 Las consultas de la solución cada generador de proyectos para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>.  Llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> para ver si los archivos de proyecto globales deben actualizar y determinar las estrategias compatibles de actualización.  **Asistente para actualización** se invoca.  
  
 Después de que el usuario ha completado el asistente, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> se llama en cada generador de proyectos para realizar la actualización real.  Para facilitar la copia de seguridad, los métodos de IVsProjectUpgradeViaFactory proporcionan el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> para registrar los detalles del proceso de actualización.  Este servicio no se puede almacenar en memoria caché.  
  
 Después de actualizar todos los archivos globales pertinentes, cada generador de proyectos puede decidir crear instancias de un proyecto.  La ejecución del proyecto debe admitir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  El método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> se llama para actualizar todos los elementos de proyecto pertinentes.  
  
> [!NOTE]
>  El método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> no proporciona el servicio de SVsUpgradeLogger.  Este servicio se puede obtener llamando a <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.  
  
## Procedimientos recomendados  
 Utilice el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> para comprobar si se puede editar un archivo antes de editarlo, y puede guardar antes de guardarlo.  Esto ayudará la copia de seguridad y las implementaciones de actualización controlan los archivos de proyecto en control de código fuente, archivos con permisos suficientes, etc.  
  
 Utilice el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> durante todas las fases de copia de seguridad y de actualización para proporcionar información sobre el éxito o el error del proceso de actualización.  
  
 Para obtener más información sobre la seguridad y actualización de proyectos, vea los comentarios de IVsProjectUpgrade en vsshell2.idl.  
  
## Vea también  
 [Proyectos](../../extensibility/internals/projects.md)   
 [Actualizar proyectos personalizados](../../misc/upgrading-custom-projects.md)   
 [Actualización de elementos de proyecto](../../misc/upgrading-project-items.md)