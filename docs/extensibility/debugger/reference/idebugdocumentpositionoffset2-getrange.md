---
title: IDebugDocumentPositionOffset2::GetRange | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 60d7ee73be7ccd421c7f5e0b4861e9cd935fbdb0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Recupera el intervalo de la posición del documento actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetRange(  
   DWORD* pdwBegOffset,  
   DWORD* pdwEndOffset  
);  
```  
  
```csharp  
public int GetRange(  
   ref uint pdwBegOffset,  
   ref uint pdwEndOffset  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdwBegOffset`  
 [entrada, salida] Desplazamiento de la posición inicial del intervalo. Establezca este parámetro en un valor null si no se necesita esta información.  
  
 `pdwEndOffset`  
 [entrada, salida] Desplazamiento de la posición final del intervalo. Establezca este parámetro en un valor null si no se necesita esta información.  
  
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
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)