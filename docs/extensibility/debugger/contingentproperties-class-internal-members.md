---
title: "Clase ContingentProperties - miembros internos | Microsoft Docs"
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
  - "Clase ContingentProperties [motores de depuración de .NET Framework]"
  - "motores de depuración, ContingentProperties (clase) [.NET Framework]"
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Clase ContingentProperties - miembros internos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Contiene propiedades adicionales para un <xref:System.Threading.Tasks.Task> objeto.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib \(en mscorlib.dll\)  
  
 No se puede tener acceso a estos miembros internos de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común \(CIL\).  
  
## Sintaxis  
  
```  
.class auto ansi nested assembly beforefieldinit ContingentProperties  
       extends System.Object  
```  
  
## Miembros  
  
### Campos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[m\_children](../../extensibility/debugger/m-children-field.md)|La lista de tareas secundarias que están registrados en esta tarea.|  
  
## Comentarios  
 .NET Framework inicializa los campos de esta clase solo cuando sean necesarios.  
  
## Vea también  
 [Información interna de extensiones paralelas para .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)