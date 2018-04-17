---
title: Clase ContingentProperties - miembros internos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b44bec34394df6f976416a827d7eb5d67cb99f6a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="contingentproperties-class---internal-members"></a>Clase ContingentProperties - miembros internos
Contiene propiedades adicionales para un <xref:System.Threading.Tasks.Task> objeto.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no se puede obtener acceso a estos miembros internos de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.class auto ansi nested assembly beforefieldinit ContingentProperties  
       extends System.Object  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="fields"></a>Campos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[m_children](../../extensibility/debugger/m-children-field.md)|La lista de tareas secundarias que están registrados con esta tarea.|  
  
## <a name="remarks"></a>Comentarios  
 .NET Framework inicializa los campos de esta clase solo cuando sean necesarias.  
  
## <a name="see-also"></a>Vea también  
 [Datos internos de extensiones paralelas para .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)