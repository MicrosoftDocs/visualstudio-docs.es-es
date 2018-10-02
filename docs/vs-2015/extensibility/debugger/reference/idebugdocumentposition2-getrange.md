---
title: IDebugDocumentPosition2::GetRange | Documentos de Microsoft
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
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 654767613b48bc0c885da3af6a494661beddc5c4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566096"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugDocumentPosition2::GetRange](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumentposition2-getrange).  
  
Obtiene el intervalo de esta posición del documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 [in, out] Un [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estructura que se rellena con la posición inicial. Establezca este argumento en un valor null si no se necesita esta información.  
  
 `pEndPosition`  
 [in, out] Un [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estructura que se rellena con la posición final. Establezca este argumento en un valor null si no se necesita esta información.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El intervalo especificado en una posición de documento para un punto de interrupción se utiliza el motor de depuración (DE) para buscar directamente una instrucción que contribuye realmente el código. Por ejemplo, considere el siguiente código:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Línea 5 no contribuye con ningún código para el programa que se está depurando. Si desea que el depurador, que establece el punto de interrupción en la línea 5 la DE buscar hacia delante de una determinada cantidad de la primera línea que contribuye de código, el depurador especificaría un rango que incluya las líneas de candidato adicional donde se puede colocar correctamente un punto de interrupción. La DE, a continuación, podría buscar hacia delante a través de esas líneas hasta que encuentra una línea que pudiera aceptar un punto de interrupción.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)

