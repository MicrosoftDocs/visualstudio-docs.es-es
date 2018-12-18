---
title: m_children (campo) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f044c2dae278a0656f1f9e4c41a3940d87658a64
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731041"
---
# <a name="mchildren-field"></a>m_children (Campo)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La lista de tareas secundarias que están registrados en esta tarea.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no se puede obtener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Comentarios  
 Mientras se ejecuta la tarea, sólo el subproceso que ejecuta la tarea debe tener acceso a esta matriz.  
  
 Si la tarea se completa, otros subprocesos pueden tener acceso a este campo siempre no agrega nada a ella ni quitar nada de ella.  
  
## <a name="see-also"></a>Vea también  
 [Clase ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)

