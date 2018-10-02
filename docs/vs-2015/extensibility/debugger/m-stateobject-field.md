---
title: m_stateObject (campo) | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d062d8a052ec89401d8b801ad329ed55ac86eb89
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578662"
---
# <a name="mstateobject-field"></a>m_stateObject (Campo)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [m_stateObject (campo)](https://docs.microsoft.com/visualstudio/extensibility/debugger/m-stateobject-field).  
  
Objeto que representa los datos que se va a usar la acción.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no se puede obtener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>Comentarios  
 Se trata de la `state` parámetro en el <xref:System.Threading.Tasks.Task.%23ctor%2A> constructor. También es el campo de respaldo para el <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> propiedad.  
  
## <a name="see-also"></a>Vea también  
 [Clase Task](../../extensibility/debugger/task-class-internal-members.md)

