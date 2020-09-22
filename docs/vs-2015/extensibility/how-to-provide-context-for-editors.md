---
title: 'Cómo: proporcionar contexto a los editores | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 11a98599a9812cd00650d113170ff55c01ac44db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842683"
---
# <a name="how-to-provide-context-for-editors"></a>Cómo: Proporcionar el contexto para los editores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para un editor, el contexto solo está activo cuando el editor tiene el foco o tenía el foco inmediatamente antes de que se moviera el foco a una ventana de herramientas. Puede proporcionar el contexto para un editor haciendo lo siguiente:  
  
1. Cree un contenedor de contexto.  
  
2. Publique el contenedor de contextos en el identificador del elemento de selección (SEID).  
  
3. Mantener el contexto en el contenedor.  
  
   Estas tareas se describen en los procedimientos siguientes. Para obtener más información acerca de cómo proporcionar contexto, vea **programación sólida** más adelante en este tema.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Para crear un contenedor de contextos para un editor o un diseñador  
  
1. Llame a `QueryService` en la <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaz para el <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> servicio.  
  
     Se devuelve un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> interfaz.  
  
2. Llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> método para crear un nuevo contenedor de contexto o subcontexto.  
  
     Se devuelve un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> interfaz.  
  
3. Llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> método para agregar atributos, palabras clave de búsqueda o palabras clave de F1 al contenedor de contexto o subcontexto.  
  
4. Si va a crear un contenedor de subcontextos, llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> método para vincular el contenedor del subcontexto al contenedor de contextos primario.  
  
5. Llame <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> a para recibir una notificación cuando la ventana de **Ayuda dinámica** esté a punto de actualizarse.  
  
     Tener la ventana **Ayuda dinámica** que llama al editor cuando está listo para actualizar le ofrece la oportunidad de retrasar el cambio de contexto hasta que se produce la actualización. Esto puede mejorar el rendimiento porque le permite retrasar la ejecución de algoritmos que consumen mucho tiempo hasta que el tiempo de inactividad del sistema esté disponible.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>Para publicar el contenedor de contextos en el SEID  
  
1. Llame a `QueryService` en el <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> servicio para devolver un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interfaz.  
  
2. Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> , especificando un `elementid` valor de identificador de elemento (parámetro) de SEID_UserContext para indicar que está pasando el contexto al nivel global.  
  
3. Cuando el editor o el diseñador se activan, los valores de su <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> objeto se propagan a la selección global. Solo necesita completar este proceso una vez por sesión y, a continuación, almacenar el puntero en el contexto global creado cuando llamó a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> .  
  
### <a name="to-maintain-the-context-bag"></a>Para mantener el contenedor de contextos  
  
1. Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> para asegurarse de que la ventana de **Ayuda dinámica** llama al editor o al diseñador antes de que se actualice.  
  
     Para cada contenedor de contextos al que se ha llamado <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> después de crear el contenedor de contextos y se ha implementado <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate> , el IDE llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> a para notificar al proveedor de contexto que se va a actualizar el contenedor de contextos. Puede usar esta llamada para cambiar los atributos y las palabras clave en el contenedor de contextos, y en cualquier bolsas de subcontexto, antes de que se produzca la actualización de la ventana de **Ayuda dinámica** .  
  
2. Llame <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> a en el contenedor de contextos para indicar que el editor o el diseñador tienen un nuevo contexto.  
  
     Cuando la ventana **Ayuda dinámica** llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> a para indicar que se está actualizando, el editor o el diseñador pueden actualizar el contexto de forma adecuada tanto para el contenedor de contextos primario como para cualquier bolsa de subcontextos en ese momento.  
  
    > [!NOTE]
    > La `SetDirty` marca se establece automáticamente en `true` siempre que se agrega o se quita el contexto del contenedor de contextos. La ventana **Ayuda dinámica** solo llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> en el contenedor de contextos si la `SetDirty` marca está establecida en `true` . Se restablece en `false` después de la actualización.  
  
3. Llame <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> a para agregar contexto a la colección de contexto activa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> para quitar el contexto.  
  
## <a name="robust-programming"></a>Programación sólida  
 Si está escribiendo su propio editor, debe completar los tres procedimientos de este tema para proporcionar contexto para el editor.  
  
> [!NOTE]
> Para activar correctamente una ventana del editor o del diseñador y para asegurarse de que el enrutamiento del comando se ha actualizado correctamente, debe llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> en el componente para que sea la ventana de enfoque.  
  
 SEID es una colección de propiedades que cambian en función de la selección. La información de SEID está disponible a través de la selección global. La selección global se conecta a los eventos desencadenados por la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interfaz y tiene una lista de todo lo que se ha seleccionado (editor actual, ventana de herramientas actual, jerarquía actual, etc.).  
  
 En el caso de los editores y diseñadores, en los que el contexto puede cambiar cada vez que el cursor se mueve dentro de una palabra, no es eficaz actualizar constantemente el contenedor de contextos. Para que la actualización sea más eficaz cada vez que detecte el movimiento del cursor en la ventana del editor o del diseñador, puede llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> . Esto le permite mantener los cambios de contexto hasta que haya tiempo de inactividad y el servicio de contexto del IDE envíe una notificación al editor o diseñador que se está actualizando en la ventana **Ayuda dinámica** . Este enfoque se usa en el procedimiento "para mantener el contenedor de contextos" de este tema.  
  
 Después de proporcionar el contexto para las actividades dentro del editor o diseñador, debe proporcionar una palabra clave de F1 específica para permitir que los usuarios obtengan ayuda para el editor o el diseñador.  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>
