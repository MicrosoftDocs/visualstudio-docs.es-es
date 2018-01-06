---
title: Clase ContingentProperties - miembros internos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e1bd9c94b99b4881167d7ae434691ffd08666ced
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="contingentproperties-class---internal-members"></a>Clase ContingentProperties - miembros internos
Contiene propiedades adicionales para un <xref:System.Threading.Tasks.Task> objeto.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
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