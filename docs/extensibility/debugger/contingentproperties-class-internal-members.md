---
title: 'ContingentProperties Class: miembros internos | Microsoft Docs'
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
ms.openlocfilehash: 8e3497b31e663967417544d8e87d40d860c2e4a8
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204419"
---
# <a name="contingentproperties-class---internal-members"></a>ContingentProperties class: miembros internos
Contiene propiedades adicionales para un <xref:System.Threading.Tasks.Task> objeto.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no se puede obtener acceso a estos miembros internos de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```csharp  
.class auto ansi nested assembly beforefieldinit ContingentProperties  
       extends System.Object  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="fields"></a>Campos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[m_children](../../extensibility/debugger/m-children-field.md)|La lista de tareas secundarias que están registrados en esta tarea.|  
  
## <a name="remarks"></a>Comentarios  
 .NET Framework inicializa los campos de esta clase solo cuando sean necesarios.  
  
## <a name="see-also"></a>Vea también  
 [Parámetros internos de extensiones paralelas para .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)