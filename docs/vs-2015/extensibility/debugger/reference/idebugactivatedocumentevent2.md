---
title: IDebugActivateDocumentEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c2087cb8f1b9a4b89448f3bf07f869d16ed44dc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65673689"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

El motor DE depuración (DE) utiliza esta interfaz para solicitar un documento que se va a cargar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugActivateDocumentEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El DE implementa esta interfaz cuando necesita que se abra un archivo de código fuente. Esta interfaz la implementa solo los motores de depuración que funcionan con o forman parte de los intérpretes de script. La interfaz [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementarse en el mismo objeto que esta interfaz (el SDM usa [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para tener acceso a la `IDebugEvent2` interfaz).  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 Crea y envía este objeto DE evento cuando es necesario tener un archivo de código fuente abierto. El evento se envía mediante la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente se muestran los métodos de `IDebugActivateDocumentEvent2` .  
  
|Métodos|Descripción|  
|-------------|-----------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|Obtiene el documento que se va a activar.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|Obtiene el contexto del documento que describe la posición dentro del documento.|  
  
## <a name="remarks"></a>Observaciones  
 Un escenario típico en el que se usa esta interfaz es si se produce un error de análisis en el código de script de una página HTML, el script DE envía esta interfaz al SDM para que se pueda mostrar el documento con el error de análisis.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
