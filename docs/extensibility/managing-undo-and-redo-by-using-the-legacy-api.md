---
title: "Administraci&#243;n de deshacer y rehacer mediante la API heredada | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - deshacer administración"
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Administraci&#243;n de deshacer y rehacer mediante la API heredada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Editores deben admitir las operaciones de deshacer que permiten a los usuarios revertir sus cambios recientes cuando modifica el código. Mayoría de los editores implementada en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] pueden tener soporte deshacer proporciona automáticamente el entorno de desarrollo integrado \(IDE\).  
  
## En esta sección  
 [Cómo: implementar la administración de deshacer](../extensibility/how-to-implement-undo-management.md)  
 Proporciona la capacidad de deshacer para los editores con una o varias vistas.  
  
 [Cómo: borrar la pila de deshacer](../extensibility/how-to-clear-the-undo-stack.md)  
 Describe cómo borrar una pila de deshacer.  
  
 [Cómo: usar la administración de la acción de deshacer vinculada](../extensibility/how-to-use-linked-undo-management.md)  
 Incorpora la administración de la acción de deshacer vinculada en el editor.  
  
## Referencia  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Proporciona administración de deshacer para un editor que admite varias vistas.  
  
## Secciones relacionadas