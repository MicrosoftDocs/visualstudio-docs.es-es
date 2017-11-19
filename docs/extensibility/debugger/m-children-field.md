---
title: m_children campo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9e6c7db4e05873ca0272da4eb551418d466ddc03
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="mchildren-field"></a>m_children campo
La lista de tareas secundarias que están registrados con esta tarea.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no se puede obtener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Comentarios  
 Mientras se ejecuta la tarea, sólo el subproceso que ejecuta la tarea debe tener acceso a esta matriz.  
  
 Si la tarea se completa, otros subprocesos pueden tener acceso a este campo siempre y cuando no se agrega nada a ella ni quitar cualquier elemento de la misma.  
  
## <a name="see-also"></a>Vea también  
 [Clase ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)