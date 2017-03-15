---
title: "IDebugProgramEx2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEx2::Attach"
helpviewer_keywords: 
  - "IDebugProgramEx2::Attach"
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgramEx2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Adjuntar una sesión a un programa.  
  
## Sintaxis  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### Parámetros  
 `pCallback`  
 \[in\]  Un objeto de [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que representa la función de devolución de llamada que el motor asociado de depuración envía eventos en.  
  
 `dwReason`  
 \[in\]  Un valor de enumeración de [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md) que describe el motivo de la operación de asociar.  
  
 `pSession`  
 \[in\]  Un valor que identifica la sesión que se está asociando el programa.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; si no devuelve un código de error.  Este método debe devolver `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` si el programa ya está asociado.  
  
## Comentarios  
 El puerto que contiene el programa puede utilizar el valor en `pSession` para determinar la sesión sólo intenta asociar el programa.  Por ejemplo, si un puerto solo permite a una sesión de depuración adjuntar a un proceso al mismo tiempo, el puerto puede determinar si se asocia a la misma sesión ya a otros programas en el proceso.  
  
> [!NOTE]
>  La interfaz última en `pSession` debe tratarlo solo como cookie, un valor que identifica de forma única el administrador de depuración de sesión asociado a este programa; ninguno de los métodos en la interfaz proporcionada funcionan.  
  
## Vea también  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)