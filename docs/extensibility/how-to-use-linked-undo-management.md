---
title: "C&#243;mo: usar la administraci&#243;n de la acci&#243;n de deshacer vinculada | Microsoft Docs"
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
  - "editores [Visual Studio SDK] heredados - administración de la acción de deshacer vinculada"
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;mo: usar la administraci&#243;n de la acci&#243;n de deshacer vinculada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La fase de reversión vinculada ofrece al usuario simultáneamente para deshacer las mismas ediciones en varios archivos.  Por ejemplo, los cambios simultáneos de texto a través de los archivos de programa múltiples, como un archivo de encabezado y otro de Visual C\+\+, son una transacción vinculada de deshacer.  La capacidad vinculada de deshacer se compila en la implementación del entorno del administrador de deshacer, y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> permite manipular esta capacidad.  La fase de reversión vinculada es implementada por una unidad primaria de deshacer que puede vincular las pilas independientes de deshacer juntas que se tratarán como una sola unidad de deshacer.  El procedimiento para utilizar fase de reversión vinculada se describen en la sección siguiente.  
  
### para utilizar fase de reversión vinculada  
  
1.  Llame a `QueryService` en `SVsLinkedUndoManager` para obtener un puntero a `IVsLinkedUndoTransactionManager`.  
  
2.  Cree la unidad vinculada primario inicial de deshacer llamando a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>.  Esto establece el punto de partida para un conjunto de pilas de deshacer que se agruparán en pilas de fase de reversión vinculadas.  En el método de `OpenLinkedUndo` también necesitará especificar si desea deshacer vinculada para ser strict o no\-estricto.  el comportamiento vinculado No\-estricto de deshacer significa que los documentos con elementos relacionados vinculados de deshacer pueden cerrar y todavía que los otros elementos relacionados vinculados de deshacer en sus pilas.  El comportamiento de la fase de reversión vinculada estricta especifica que todas las pilas relacionadas de la fase de reversión vinculada tienen que revertirse conjuntamente o no hacerlo.  Agregue las pilas vinculadas subsiguientes de deshacer llamando al método de [IOleUndoManager:: Agregar](http://msdn.microsoft.com/library/windows/desktop/ms680135) .  
  
3.  Llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> para revertir todas las unidades de fase de reversión vinculadas como una.  
  
    > [!NOTE]
    >  Para implementar vinculados administración de deshacer en un editor, agregue la administración de deshacer.  Para obtener más información sobre cómo implementar la administración vinculada undo, vea [Cómo: Administración de deshacer de implementan](../extensibility/how-to-implement-undo-management.md).  
  
## Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [Cómo: implementar la administración de deshacer](../extensibility/how-to-implement-undo-management.md)