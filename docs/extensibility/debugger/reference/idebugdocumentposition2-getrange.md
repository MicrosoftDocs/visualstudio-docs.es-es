---
title: IDebugDocumentPosition2::GetRange | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d4a80bebba1000c73af2d7e2cfd05e67fa44b1b7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109206"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Obtiene el intervalo para esta posición del documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pBegPosition`  
 [entrada, salida] A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estructura que se rellena con la posición inicial. Establezca este argumento en un valor null si no se necesita esta información.  
  
 `pEndPosition`  
 [entrada, salida] A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estructura que se rellena con la posición final. Establezca este argumento en un valor null si no se necesita esta información.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El intervalo especificado en una posición del documento para un punto de interrupción se utiliza por el motor de depuración (Alemania) para buscar una instrucción que realmente contribuye código con antelación. Por ejemplo, considere el siguiente código:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Línea 5 no contribuye ningún código para el programa que se está depurando. Si el depurador, que establece el punto de interrupción en la línea 5 desea que la DE buscar hacia delante una cierta cantidad de la primera línea que aporta código, el depurador debería especificar un intervalo que incluya las líneas de candidato adicional donde se puede colocar correctamente un punto de interrupción. La DE, a continuación, podría buscar hacia delante a través de las líneas hasta que encuentre una línea que podría aceptar un punto de interrupción.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)