---
title: "Cómo: proporcionar un contexto para editores | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d9b89c4e45f8268df55386d321816325fb50174c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-provide-context-for-editors"></a>Cómo: proporcionar un contexto para los editores
Para un editor, el contexto está activo sólo cuando el editor tiene el foco o tenía foco inmediatamente antes de que se ha movido el foco a una ventana de herramientas. Puede proporcionar el contexto para un editor haciendo lo siguiente:  
  
1.  Crear un conjunto de contextos.  
  
2.  Publicar la bolsa de contexto en el identificador de elemento de selección (SEID).  
  
3.  Mantener el contexto en el contenedor.  
  
 Estas tareas están cubiertas por los procedimientos siguientes. Para obtener más información acerca de cómo proporcionar contexto, vea **programación sólida** más adelante en este tema.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Para crear un conjunto de contextos de un editor o un diseñador  
  
1.  Llame a `QueryService` en su <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaz para el <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> service.  
  
     Un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> se devuelve la interfaz.  
  
2.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> método para crear un nuevo contenedor de contexto o subcontexto.  
  
     Un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> se devuelve la interfaz.  
  
3.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> método para agregar atributos, palabras clave de búsqueda o palabras clave de F1 para el contenedor de contexto o subcontexto.  
  
4.  Si va a crear un contenedor de subcontexto, llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> método para vincular la bolsa subcontexto a la bolsa de contexto del elemento primario.  
  
5.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> para recibir una notificación cuando la **Ayuda dinámica** ventana que se va a actualizar.  
  
     Tener la **Ayuda dinámica** ventana llamar a su editor cuando esté preparado para actualizar tendrá la oportunidad para retrasar cambiar el contexto de hasta que se produzca la actualización. Esto puede mejorar el rendimiento, ya que permite retrasar la ejecución de algoritmos que consumen muchos recursos hasta que el tiempo de inactividad del sistema está disponible.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>Para publicar el conjunto de contextos en lo SEID  
  
1.  Llame a `QueryService` en el <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> servicio para devolver un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interfaz.  
  
2.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>, especificando un identificador de elemento (`elementid` parámetro) valor de SEID_UserContext para indicar que está pasando el contexto en el nivel global.  
  
3.  Cuando se activa el editor o diseñador, los valores de sus <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> objeto se propagan a la selección global. Solo se necesita completar este proceso una vez por sesión y, a continuación, almacene el puntero en el contexto global que se crean cuando llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>.  
  
### <a name="to-maintain-the-context-bag"></a>Para mantener el conjunto de contextos  
  
1.  Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> para asegurarse de que el **Ayuda dinámica** llamadas de la ventana del editor o diseñador antes de que actualice.  
  
     Para cada conjunto de contextos que se denomina <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> después de la bolsa de contexto se crea y se ha implementado <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>, las llamadas IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> notifique al proveedor de contexto que se actualizará el conjunto de contextos. Puede usar esta llamada para cambiar los atributos y palabras clave en el conjunto de contextos y en los contenedores de subcontexto antes el **Ayuda dinámica** Windows update se produce.  
  
2.  Llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> en el conjunto de contextos para indicar que el editor o diseñador tiene nuevo contexto.  
  
     Cuando el **Ayuda dinámica** ventana llamadas <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> para indicar que está actualizando, el editor o diseñador puede actualizar el contexto apropiado para el conjunto de contextos de principal y cualquier bolsas subcontexto en ese momento.  
  
    > [!NOTE]
    >  El `SetDirty` marca se establece automáticamente en `true` cada vez que se agrega o se quita de la bolsa de contexto de contexto. El **Ayuda dinámica** ventana solo llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> en el conjunto de contextos si la `SetDirty` marca se establece en `true`. Se restablece a `false` después de la actualización.  
  
3.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> para agregar contexto a la colección de contexto activo o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> para quitar el contexto.  
  
## <a name="robust-programming"></a>Programación sólida  
 Si está escribiendo su propio editor, debe completar los tres de los procedimientos de este tema para proporcionar un contexto para el editor.  
  
> [!NOTE]
>  Para activar una ventana del editor o diseñador de correctamente y para asegurarse de que el enrutamiento de comandos se ha actualizado correctamente, debe llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> en el componente para convertirla en la ventana de foco.  
  
 El SEID es una colección de propiedades que cambian en función de la selección. SEID información está disponible a través de la selección global. La selección global está conectada a los eventos desencadenados por el <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interfaz, y una lista de todos los elementos que ha seleccionado (editor actual, ventana de herramientas actual, la jerarquía actual y así sucesivamente).  
  
 Para los editores y diseñadores, en contexto que se puede cambiar cada vez que el cursor se mueve dentro de una palabra, no es eficaz para actualizar el conjunto de contextos de constantemente. Para facilitar la actualización más eficaz cualquier momento para detectar el cursor dentro del editor o la ventana del diseñador, se puede llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>. Esto le permite mantener los cambios de contexto hasta que no hay tiempo de inactividad y servicio de contexto del IDE envía notificación para el editor o diseñador que la **Ayuda dinámica** ventana se está actualizando. Este enfoque se usa en el procedimiento "para mantener el conjunto de contextos" en este tema.  
  
 Después de proporcionar contexto para las actividades dentro de un editor o diseñador, debe proporcionar una palabra clave de F1 específica para permitir a los usuarios obtener ayuda sobre el editor o diseñador.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>