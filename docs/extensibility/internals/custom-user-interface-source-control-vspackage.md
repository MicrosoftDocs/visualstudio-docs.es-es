---
title: "Interfaz de usuario personalizada (VSPackage del Control de c&#243;digo fuente) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interfaz de usuario, los paquetes de control de código fuente"
  - "paquetes de control de código fuente, interfaz de usuario"
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# Interfaz de usuario personalizada (VSPackage del Control de c&#243;digo fuente)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un VSPackage declara sus elementos de menú y a sus estados predeterminados en el archivo de la tabla de comandos de Visual Studio \(.vsct\).  El entorno de desarrollo integrado de \(IDE\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] muestra los elementos de menú en sus estados predeterminados hasta que el Paquete se carga.  Posteriormente, el método de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> se denomina para habilitar o los elementos de menú deshabilitados.  
  
 Un Paquete puede establecer una clave del Registro para que el Paquete se puede cargar automáticamente dependiendo de un contexto de interfaz de \(UI\) usuario de comandos, aunque un control de origen VSPackage debe cargar normalmente a petición en lugar de limitarse a cambiar a la interfaz de usuario un contexto determinado.  Para obtener más información sobre la clave del Registro de AutoLoadPackages, vea [Administración de VSPackages](../../extensibility/managing-vspackages.md).  
  
## interfaz de usuario de VSPackage  
 Un paquete de control de código fuente se implementa como un VSPackage y no utiliza ninguna interfaz de usuario de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Cada control de origen VSPackage debe especificar sus propios elementos de interfaz de usuario como elementos de menú, grupos de menús, ventanas de herramientas, barras de herramientas, y cualquier interfaz de usuario necesaria para establecer opciones específicas del control de código fuente VSPackage.  Estos elementos de la interfaz de usuario se pueden habilitar dinámicamente.  Elementos estáticos de la interfaz de usuario se define en un archivo de .vsct y se muestran si el Paquete se carga o no.  Los elementos dinámicos de la interfaz de usuario son visibles en función de un contexto de la interfaz de usuario del detalle, como <xref:EnvDTE.Constants.vsContextNoSolution>, o como resultado de una llamada al método de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> .  La visibilidad de los elementos dinámicos de la interfaz de usuario cumple la estrategia de carga retrasada de VSPackages.  
  
## Restricciones de interfaz de usuario en el Control de origen VSPackages  
 Dado que el control de código fuente VSPackage no se puede quitar del IDE después de que se carga, el Paquete debe poder entrar en un estado inactivo.  Cuando un VSPackage recibe la notificación de que ya no esté activa, el paquete VSPackage deshabilita la interfaz de usuario y omite cualquier interacción externa del IDE.  La implementación del Paquete del método de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> debe ocultar comandos cuando el Paquete no está activa.  
  
 cada control de código fuente VSPackage debe implementar la interfaz de `IVsSccProvider` .  Dos métodos en la interfaz, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, se deben implementar por el paquete VSPackage.  
  
 El control de código fuente VSPackage haya suscrito a diferente IDE eventos, implementados por <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>, etc.  Además, el Paquete puede haber implementado interfaces de devolución de llamada registro\-habilitadas, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>.  Éstos deben omitirse cuando están inactivos.  
  
 La lista siguiente se muestran las interfaces afectadas por el estado activo de un control de código fuente VSPackage:  
  
-   El proyecto de pista documenta eventos.  
  
-   eventos de la solución.  
  
-   Interfaces de persistencia de la solución.  Cuando están inactivos, los paquetes no deben escribir en archivos .sln y .suo.  
  
-   Extensores de la propiedad.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> necesario y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, y también ninguna interfaces opcional asociado al control de código fuente, no se llama cuando el control de código fuente VSPackage está inactivo.  
  
 Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se inicia el IDE, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] establece el contexto de la interfaz de usuario de comandos al identificador de identificación predeterminada actual de VSPackage de control de código fuente  Esto hace que la interfaz de usuario estática del control de código fuente activo VSPackage aparezcan en el IDE realmente cargar el Paquete.  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pausa para que el paquete VSPackage registrado con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> antes de que haga cualquier llamada a VSPackage.  
  
 La tabla siguiente se describen los detalles concretos sobre cómo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE oculta diferentes elementos de la interfaz de usuario.  
  
|elemento de la interfaz de usuario|Descripción|  
|----------------------------------------|-----------------|  
|Menús y barras de herramientas|El paquete del control de origen debe establecer los estados iniciales de visibilidad del menú y la barra de herramientas en el identificador del paquete de control de código fuente en la sección de [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) del archivo de .vsct.  Esto permite a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el IDE para establecer el estado de los elementos de menú correctamente sin cargar el paquete VSPackage y llamar a una implementación del método de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> .|  
|ventanas de herramientas|El control de código fuente VSPackage oculta cualquier ventana de herramientas que posee cuando se crea inactivo.|  
|Páginas opciones VSPackage\-específicas de control de código fuente|La clave del Registro HKLM \\SOFTWARE\\Microsoft\\VisualStudio\\X.Y\\ToolsOptionsPages\\VisibilityCmdUIContexts lets a VSPackage establece los contextos en los que requiere sus páginas de opciones mostrar.  Una entrada de Registro bajo esta clave tendría que estar creada mediante el identificador de servicio \(SID\) del servicio de control de código fuente y de asignarle un valor DWORD de 1.  Siempre que un evento de interfaz de usuario aparece en un contexto el control de código fuente VSPackage se registra con, el Paquete se llamará si está activa.|  
  
## Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [Administración de VSPackages](../../extensibility/managing-vspackages.md)