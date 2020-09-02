---
title: 'Clase ContingentProperties: miembros internos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f6778aef90361a7751ccd744fcf93822f8f97db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62414651"
---
# <a name="contingentproperties-class---internal-members"></a>ContingentProperties (Clase): miembros internos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Contiene propiedades adicionales para un <xref:System.Threading.Tasks.Task> objeto.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no puede tener acceso a estos miembros internos desde el .NET Framework, se proporciona la siguiente sintaxis en el lenguaje intermedio común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.class auto ansi nested assembly beforefieldinit ContingentProperties  
       extends System.Object  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="fields"></a>Campos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[m_children](../../extensibility/debugger/m-children-field.md)|La lista de tareas secundarias que se registran con esta tarea.|  
  
## <a name="remarks"></a>Comentarios  
 El .NET Framework inicializa los campos de esta clase solo cuando son necesarios.  
  
## <a name="see-also"></a>Consulte también  
 [Datos internos de extensiones paralelas para .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
