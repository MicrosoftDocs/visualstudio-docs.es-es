---
title: "Detalles de configuraci&#243;n de Control de c&#243;digo fuente | Microsoft Docs"
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
  - "control de código fuente [Visual Studio SDK], detalles de configuración"
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Detalles de configuraci&#243;n de Control de c&#243;digo fuente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Para implementar el control de código fuente, es necesario configurar correctamente el sistema o el editor de proyecto hacer lo siguiente:  
  
-   Solicite el permiso a la transición al estado cambiado  
  
-   Solicitar permiso para guardar un archivo  
  
-   Solicite permiso para agregar, quitar, o cambiar de nombre los archivos del proyecto  
  
## Permiso de la solicitud en la transición al estado cambiado  
 Un proyecto o un editor debe solicitar permiso a la transición al estado \(modificada\) cambia llamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>.  Cada editor que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> debe llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> y recibir aprobación para cambiar el documento del entorno antes de devolver `True` para `M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)`.  Un proyecto es esencialmente editor para un archivo de proyecto y, en consecuencia, tiene la misma responsabilidad de implementar en la cambiar\-provincia que realiza para el archivo de proyecto como un editor de texto hace para los archivos.  El entorno controla el estado cambia de la solución, pero debe controlar el estado cambia de cualquier objeto las referencias de la solución pero no almacena, como un archivo de proyecto o sus elementos.  Normalmente si el proyecto o el editor es responsable de administrar la persistencia para un elemento, entonces es responsable de implementar el seguimiento de la cambiar\-provincia.  
  
 En respuesta a la llamada de `IVsQueryEditQuerySave2::QueryEditFiles` , el entorno puede hacer lo siguiente:  
  
-   Rechazar la llamada para cambiar, en cuyo caso el editor o el proyecto debe permanecer en estado \(limpia\) sin cambios.  
  
-   Indica que los datos de documento deben volver.  Para un proyecto, el entorno se recargará los datos para el proyecto.  Un editor debe cargar los datos desde el disco con su implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> .  En cualquier caso, el contexto del proyecto o el editor puede cambiar cuando se vuelve a cargar los datos.  
  
 Es una tarea compleja y difícil refinar las llamadas apropiadas de `IVsQueryEditQuerySave2::QueryEditFiles` sobre una base de código existente.  Como resultado, estas llamadas deben integrar durante la creación del proyecto o del editor.  
  
## Permiso de solicitud a Guardar un archivo  
 Antes de un proyecto o un editor guardar un archivo, debe llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>.  Para los archivos de proyecto, estas llamadas automáticamente son completadas por la solución, que sabe cuándo guardar un archivo de proyecto.  Los editores son responsables de crear estas llamadas a menos que la implementación del editor de `IVsPersistDocData2` utilice el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>de la función auxiliar.  Si el editor implementa `IVsPersistDocData2` de esta manera, la llamada a `IVsQueryEditQuerySave2::QuerySaveFile` o a `IVsQueryEditQuerySave2::QuerySaveFiles` se hace automáticamente.  
  
> [!NOTE]
>  haga siempre estas llamadas de forma preventiva\-que es, en un momento en que el editor puede recibir una cancelación.  
  
## El solicitar permiso para agregar, quitar, o los archivos de La en el proyecto  
 Antes de que un proyecto puede agregar, cambiar el nombre, o quitar un archivo o directorio, debe llamar al método adecuado de `IVsTrackProjectDocuments2::OnQuery*` para solicitar permiso del entorno.  Si se concede el permiso, el proyecto debe completar la operación y después llamar al método adecuado de `IVsTrackProjectDocuments2::OnAfter*` para notificar al entorno que la operación se completa.  El proyecto debe llamar a los métodos de la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> para todos los archivos \(por ejemplo, archivos especiales\) y no sólo los archivos principales.  Las llamadas de archivo son obligatorias, pero las llamadas del directorio son opcionales.  Si el proyecto tiene información de directorio, deberá llamar a los métodos adecuados de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> , pero si no tiene esta información, el entorno infiere la información del directorio.  
  
 El proyecto no debe llamar a los métodos de `IVsTrackProjectDocuments2` en el proyecto abierto o cerrar.  Los agentes de escucha que desean esta información en el inicio pueden esperar el evento de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> y iterarlo en la solución para buscar la información que necesitan.  Al cerrar, esta información no es necesaria.  `IVsTrackProjectDocuments2` se proporciona de <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.  
  
 Para cada agregue, cambie, y quita la acción, hay un método de `OnQuery*` y un método de `OnAfter*` .  Llame al método de `OnQuery*` que solicita permiso para agregar, cambiar de nombre, o quitar el archivo o directorio.  Llame al método de `OnAfter*` después del archivo o se ha agregado el directorio, o cuyo quitado y el estado del proyecto refleja al nuevo estado.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [Compatibilidad con Control de código fuente](../../extensibility/internals/supporting-source-control.md)