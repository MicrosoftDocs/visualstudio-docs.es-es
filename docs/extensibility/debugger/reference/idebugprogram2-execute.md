---
title: "IDebugProgram2::Execute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Execute"
helpviewer_keywords: 
  - "IDebugProgram2::Execute"
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProgram2::Execute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Sigue ejecutando este programa de un estado detenido.  Borre cualquier estado anterior de la ejecución \(como un paso\), y el inicio del programa que se ejecuta de nuevo.  
  
> [!NOTE]
>  Este método es obsoleto.  Utilice el método [Ejecutar](../../../extensibility/debugger/reference/idebugprocess3-execute.md) en su lugar.  
  
## Sintaxis  
  
```cpp#  
HRESULT Execute(  
   void  
);  
```  
  
```c#  
int Execute();  
```  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Cuando el usuario inicia la ejecución de un estado detenido en el subproceso de algún otro programa, este método se llama este programa.  Este método también se llama cuando el usuario selecciona el comando de **Iniciar** de menú de **Depurar** en el IDE.  La implementación de este método puede ser tan simple como llamando al método de [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) en el subproceso actual en el programa.  
  
> [!WARNING]
>  No envíe un evento que detiene o un evento \(sincrónico\) inmediato a [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras controla esta llamada; si no el depurador puede no responder.  
  
## Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)