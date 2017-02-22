---
title: "IDebugProcess3 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3"
helpviewer_keywords: 
  - "Interfaz IDebugProcess3"
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa un proceso en ejecución y sus lectores.  Esta interfaz existe como reemplazo a varios métodos de la interfaz de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .  Proporciona control sobre todos los programas en el proceso.  
  
> [!NOTE]
>  Los métodos de[Continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md), de [Ejecutar](../../../extensibility/debugger/reference/idebugprogram2-execute.md), y de [Paso](../../../extensibility/debugger/reference/idebugprogram2-step.md) están desusadas y deben ser utilizados ya no.  Utilice los métodos correspondientes de la interfaz de `IDebugProcess3` en su lugar.  
  
## Sintaxis  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## Notas para los implementadores  
 Esta interfaz se implementa por un proveedor de puerto para administrar programas como grupo.  Cuando los programas se administran como grupo, puede controlar su ejecución y establecer un lenguaje para un evaluador de expresiones.  Esta interfaz se debe implementar el proveedor de puerto.  
  
## Notas para los llamadores  
 Esta interfaz es denominada principalmente por el administrador de depuración de la sesión \(SDM\) para interactuar con un grupo de software identificados en este proceso.  
  
 Llame a [QueryInterface](/visual-cpp/atl/queryinterface) en una interfaz de [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) para obtener esta interfaz.  
  
## métodos en el orden de Vtable  
 Además de los métodos heredados de [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` implementa los siguientes métodos.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Continúa la ejecución de o el recorrido a través de un proceso.|  
|[Ejecutar](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Inicia la ejecución de un proceso.|  
|[Paso](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Pasos hacia delante una instrucción o instrucciones en el proceso.|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Obtiene el motivo que el proceso se inicia para depurar.|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Establece el lenguaje de hospedaje de modo que el motor de depuración pueda cargar el evaluador adecuado de la expresión.|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Recupera el idioma establecido actualmente para este proceso.|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Deshabilita editar y continuar \(ENC\) para este proceso.<br /><br /> Un proveedor de puerto no implementa este método \(siempre debe devolver `E_NOTIMPL`\).|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Obtiene el estado de ENC para este proceso.<br /><br /> Un proveedor de puerto no implementa este método \(siempre debe devolver `E_NOTIMPL`\).|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Recupera una matriz de identificadores únicos para los motores disponibles de depuración.|  
  
## Requisitos  
 encabezado: Msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)