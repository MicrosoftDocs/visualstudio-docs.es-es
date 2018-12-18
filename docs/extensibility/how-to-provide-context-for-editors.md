---
title: 'Cómo: proporcionar el contexto para los editores | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 848778506bdea1b7bf61b6a94a1fb14908a7b930
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908959"
---
# <a name="how-to-provide-context-for-editors"></a>Cómo: proporcionar el contexto para los editores
Para un editor, el contexto está activo sólo cuando el editor tiene el foco o tenía el foco antes de que el foco se ha movido a una ventana de herramientas. Puede proporcionar contexto para un editor, realice las siguientes tareas:  
  
1. Crear un contenedor de contextos.  
  
2. Publicar el contenedor de contexto en el identificador de elemento de selección (SEID).  
  
3. Mantener el contexto en el contenedor.  
  
   Estas tareas están cubiertas por los procedimientos siguientes. Para obtener más información acerca de cómo proporcionar el contexto, vea **programación sólida** más adelante en este artículo.  
  
## <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Para crear un contenedor de contexto de un editor o un diseñador  
  
1.  Llame a `QueryService` en su <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaz para el <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> service.  
  
     Un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> se devuelve la interfaz.  
  
2.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> método para crear un nuevo contenedor de contextos o subcontextos.  
  
     Un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> se devuelve la interfaz.  
  
3.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> método para agregar atributos, las palabras clave de búsqueda, o **F1** palabras clave al contenedor de contextos o subcontextos.  
  
4.  Si va a crear un contenedor de subcontextos, llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> método para vincular el contenedor del subcontexto en el contenedor de contextos primario.  
  
5.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> para recibir una notificación cuando la **Ayuda dinámica** ventana está a punto de actualización.  
  
     Tener la **Ayuda dinámica** ventana llamar a su editor cuando esté preparado para actualizar le ofrece la oportunidad de retrasar el cambio del contexto hasta que se produzca la actualización. Esto puede mejorar el rendimiento porque permite retrasar la ejecución de algoritmos que requieren mucho tiempo hasta que el tiempo de inactividad del sistema está disponible.  
  
## <a name="to-publish-the-context-bag-to-the-seid"></a>Para publicar el contenedor de contexto en el SEID  
  
1.  Llame a `QueryService` en el <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> service que devuelva un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interfaz.  
  
2.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>, especificando un identificador de elemento (`elementid` parámetro) valor de SEID_UserContext para indicar que va a pasar contexto a nivel global.  
  
3.  Cuando esté activo el editor o diseñador, los valores de sus <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> objeto se propagan a la selección global. Solo se necesita completar este proceso una vez por sesión y, a continuación, almacene el puntero en el contexto global creado cuando llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>.  
  
## <a name="to-maintain-the-context-bag"></a>Para mantener el contenedor de contexto  
  
1.  Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> para asegurarse de que el **Ayuda dinámica** llamadas de la ventana del editor o diseñador antes de las actualizaciones.  
  
     Para cada contenedor de contexto que se denomina <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> después de que el contenedor de contexto se crea y se ha implementado <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>, las llamadas IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> notifique al proveedor de contexto que se actualizará el contenedor de contexto. Puede usar esta llamada para cambiar los atributos y palabras clave en el contenedor de contexto y en los contenedores de subcontextos antes el **Ayuda dinámica** se produce la actualización de la ventana.  
  
2.  Llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> en el contenedor de contexto para indicar que el editor o diseñador tiene el nuevo contexto.  
  
     Cuando el **Ayuda dinámica** ventana llamadas <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> para indicar que se está actualizando, el diseñador o editor puede actualizar el contexto apropiado para el contenedor de contextos primario y los contenedores de subcontextos en ese momento.  
  
    > [!NOTE]
    >  El `SetDirty` marca se establece automáticamente en `true` cada vez que se agrega o se quita del contenedor de contextos contexto. El **Ayuda dinámica** solo llama la ventana <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> en el contenedor de contexto si el `SetDirty` marca se establece en `true`. Se restablece en `false` después de la actualización.  
  
3.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> para agregar contexto a la colección de contexto activo o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> para quitar el contexto.  
  
## <a name="robust-programming"></a>Programación sólida  
 Si está escribiendo su propio editor, a continuación, debe completar tres de los procedimientos descritos en este artículo para proporcionar contexto para el editor.  
  
> [!NOTE]
>  Para activar correctamente una ventana del editor o diseñador y asegurarse de que el enrutamiento de comandos se ha actualizado correctamente, debe llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> en el componente para convertirla en la ventana de foco.  
  
 El SEID es una colección de propiedades que cambian en función de la selección. SEID información está disponible a través de la selección global. La selección global está conectada a los eventos desencadenados por el <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interfaz, y una lista de todo lo que ha seleccionado (editor actual, ventana de herramientas actual, la jerarquía actual y así sucesivamente).  
  
 Para los editores y diseñadores, en cuyo contexto se puede cambiar cada vez que el cursor se mueve dentro de una palabra, no es eficaz para actualizar constantemente el contenedor de contexto. Para facilitar la actualización de más eficaz siempre que detecte el cursor mover dentro del editor o la ventana del diseñador, puede llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>. Esto le permite mantener los cambios de contexto hasta que no hay tiempo de inactividad y servicio del contexto del IDE envía notificaciones para el diseñador o editor que la **Ayuda dinámica** ventana se está actualizando. Este enfoque se usa en el **para mantener el contenedor de contexto** procedimiento en este artículo.  
  
 Después de proporcionar contexto para las actividades dentro de un editor o diseñador, debe proporcionar un determinado **F1** palabra clave para permitir que los usuarios obtener ayuda sobre el editor o diseñador en sí mismo.  
  
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