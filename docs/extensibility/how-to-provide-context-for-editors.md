---
title: "C&#243;mo: proporcionar contexto para los editores | Microsoft Docs"
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
  - "editores [Visual Studio SDK] heredados - proporcionan contexto"
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;mo: proporcionar contexto para los editores
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para un editor, el contexto está activo sólo cuando el editor tiene el foco o tenía el foco antes de que se ha movido el foco a una ventana de herramientas. Puede proporcionar contexto para un editor haciendo lo siguiente:  
  
1.  Crear un contenedor de contextos.  
  
2.  Publicar el conjunto de contextos en el identificador del elemento de selección \(SEID\).  
  
3.  Mantener el contexto en el contenedor.  
  
 Estas tareas se tratan los procedimientos siguientes. Para obtener más información acerca de cómo proporcionar contexto, vea **programación eficaz** más adelante en este tema.  
  
### Para crear un contenedor de contexto de un editor o un diseñador  
  
1.  Llamar a `QueryService` en su <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> de interfaz para el <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> service.  
  
     Un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> interfaz es devuelto.  
  
2.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> método para crear un nuevo contenedor de contexto o subcontexto.  
  
     Un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> interfaz es devuelto.  
  
3.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> para agregar atributos, palabras clave de búsqueda o palabras clave F1 a la bolsa de contexto o subcontexto.  
  
4.  Si va a crear un contenedor de subcontexto, llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> método para vincular la bolsa subcontexto a la bolsa de contexto primario.  
  
5.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> para recibir una notificación cuando la **Ayuda dinámica** ventana que se va a actualizar.  
  
     Tener la **Ayuda dinámica** ventana llame a su editor cuando esté preparado para actualizar le ofrece la oportunidad de retrasar el cambio del contexto hasta que se produzca la actualización. Esto puede mejorar el rendimiento, ya que permite retrasar la ejecución algoritmos mucho tiempo hasta que el tiempo de inactividad del sistema está disponible.  
  
### Para publicar el conjunto de contextos en el SEID  
  
1.  Llamar a `QueryService` en el <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> servicio para devolver un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interfaz.  
  
2.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>, especificando un identificador de elemento \(`elementid` parámetro\) valor de SEID\_UserContext para indicar que está pasando el contexto en el nivel global.  
  
3.  Cuando se activa el editor o diseñador, los valores de sus <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> objeto se propagan a la selección global. Sólo se necesita completar este proceso una vez por sesión y, a continuación, almacene el puntero en el contexto global que se crea cuando llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>.  
  
### Para mantener el conjunto de contextos  
  
1.  Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> para asegurarse de que el **Ayuda dinámica** llamadas de la ventana del editor o diseñador antes de que actualice.  
  
     Para cada conjunto de contextos que se denomina <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> después de la bolsa de contexto se crea y se ha implementado <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>, las llamadas IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> notifique al proveedor de contexto que se actualizará el conjunto de contextos. Esta llamada puede utilizar para cambiar los atributos y palabras clave en la bolsa de contexto y en las bolsas de subcontexto antes la **Ayuda dinámica** se produce la actualización de la ventana.  
  
2.  Llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> en el conjunto de contextos para indicar que el editor o diseñador tiene el nuevo contexto.  
  
     Cuando el **Ayuda dinámica** ventana llamadas <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> para indicar que está actualizando, el editor o diseñador puede actualizar el contexto apropiado para el conjunto de contextos de principal y cualquier bolsas subcontexto en ese momento.  
  
    > [!NOTE]
    >  El `SetDirty` marca se establece automáticamente en `true` cada vez que se agrega o se quita de la bolsa de contexto de contexto. El **Ayuda dinámica** ventana sólo llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> en la bolsa de contexto si el `SetDirty` marca está establecida en `true`. Se restablece en `false` después de la actualización.  
  
3.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> para agregar contexto a la colección de contexto activo o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> para quitar el contexto.  
  
## Programación eficaz  
 Si está escribiendo su propio editor, debe completar los tres de los procedimientos de este tema para proporcionar contexto para el editor.  
  
> [!NOTE]
>  Para activar correctamente una ventana del editor o diseñador y asegurarse de que el enrutamiento de comandos se actualiza correctamente, se debe llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> en el componente para convertirla en la ventana de foco.  
  
 El SEID es una colección de propiedades que cambian en función de la selección. SEID información está disponible a través de la selección global. La selección global está conectada a los eventos desencadenados por el <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interfaz, y una lista de todo lo que ha seleccionado \(editor actual, la ventana de herramienta actual, jerarquía actual y así sucesivamente\).  
  
 Para diseñadores y editores, en el contexto en el que puede cambiar cada vez que el cursor se mueve dentro de una palabra no es eficaz para actualizar constantemente el conjunto de contextos. Para facilitar la actualización de más eficaz siempre que detecte el cursor dentro de la ventana de diseñador o editor, puede llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>. Esto permite mantener los cambios de contexto hasta que no hay tiempo de inactividad y servicio de contexto del IDE envía una notificación en el editor o diseñador que el **Ayuda dinámica** ventana se está actualizando. Este enfoque se utiliza en el procedimiento "para mantener el conjunto de contextos" en este tema.  
  
 Después de proporcionar contexto para las actividades en el editor o diseñador, debe proporcionar una palabra clave específica de F1 para permitir a los usuarios obtener ayuda sobre el editor o diseñador.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>