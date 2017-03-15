---
title: "IDebugProgramEngines2::EnumPossibleEngines | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEngines2::EnumPossibleEngines"
helpviewer_keywords: 
  - "IDebugProgramEngines2::EnumPossibleEngines"
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramEngines2::EnumPossibleEngines
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Devuelve el GUID para todos los motores \(DE\) posibles de depuración que pueden depurar este programa.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```c#  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### Parámetros  
 `celtBuffer`  
 \[in\]  El número de GUID a devolver.  Esto también especifica el tamaño máximo de la matriz de `rgguidEngines` .  
  
 `rgguidEngines`  
 \[in, out\]  Una matriz de GUID que se va a realizar.  
  
 `pceltEngines`  
 \[out\]  Devuelve el número real de GUID que se devuelve.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  Devuelve \[C\+\+\] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` o \[C\#\] 0x8007007A si el búfer no es suficientemente grande.  
  
## Comentarios  
 Para determinar cuántos motores hay, llaman a este método una vez con el parámetro de `celtBuffer` establecido en 0 y el parámetro de `rgguidEngines` establecido en un valor nulo.  Esto devuelve `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` \(0x8007007A para C\#\), y el parámetro de `pceltEngines` devuelve el tamaño necesario del búfer.  
  
## Vea también  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)