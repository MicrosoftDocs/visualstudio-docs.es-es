---
title: IDebugActivateDocumentEvent2 | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bc9a93df7b99fb14f990633fdae58003ac7c04fa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578327"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugActivateDocumentEvent2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugactivatedocumentevent2).  
  
El motor de depuración (DE) usa esta interfaz para solicitar un documento que se va a cargar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugActivateDocumentEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 La DE implementa esta interfaz cuando es necesario abrir un archivo de origen. Esta interfaz se implementa únicamente por los motores de depuración que funcionan con o forman parte de los intérpretes de secuencia de comandos. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz debe implementarse en el mismo objeto que esta interfaz (usa el SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para tener acceso a la `IDebugEvent2` interfaz).  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 La DE crea y envía este objeto de evento cuando es necesario tener un archivo de código fuente abierto. El evento se envía mediante la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada proporcionada por el SDM cuando adjunta al programa que se está depurando.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugActivateDocumentEvent2`.  
  
|Métodos|Descripción|  
|-------------|-----------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|Obtiene el documento que se va a activar.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|Obtiene el contexto del documento que describe la posición dentro del documento.|  
  
## <a name="remarks"></a>Comentarios  
 Un escenario típico en el que se usa esta interfaz es que si se produce un error de análisis de código de script en una página HTML, la secuencia de comandos DE envía esta interfaz para el SDM, por lo que se pueda mostrar el documento con el error de análisis.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

