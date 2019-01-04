---
title: m_children (campo) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a5d924e0439be2f8ab615d18a61f1303994b8dde
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923697"
---
# <a name="mchildren-field"></a>m_children campo
La lista de tareas secundarias que están registrados en esta tarea.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en *mscorlib.dll*)  
  
 Dado que no se puede obtener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```csharp 
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Comentarios  
 Mientras se ejecuta la tarea, sólo el subproceso que ejecuta la tarea debe tener acceso a esta matriz.  
  
 Si la tarea se completa, otros subprocesos pueden tener acceso a este campo, siempre que no agrega nada a él o quitarle nada.  
  
## <a name="see-also"></a>Vea también  
 [Clase ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)