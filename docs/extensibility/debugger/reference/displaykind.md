---
title: "DisplayKind | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DisplayKind (enumeración)"
ms.assetid: 940968c5-6065-4bda-8ee6-c31597db4d71
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# DisplayKind
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Muestra los valores válidos que representan los tipos de información de tomar de un objeto de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) y de mostrar al usuario.  
  
## Sintaxis  
  
```cpp#  
enum enum_DisplayKind  
{  
   DisplayKind_Value = 0x1,  
   DisplayKind_Name = 0x2,  
   DisplayKind_Type = 0x3,  
};  
typedef DWORD DisplayKind;  
```  
  
```c#  
public enum enum_DisplayKind  
{  
   DisplayKind_Value = 0x1,  
   DisplayKind_Name = 0x2,  
   DisplayKind_Type = 0x3,  
};  
```  
  
#### Parámetros  
 DisplayKind\_Value  
 Valor del campo.  
  
 DisplayKind\_Name  
 Nombre del campo.  
  
 DisplayKind\_Type  
 tipo de campo.  
  
## Requisitos  
 encabezado: Ee.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)