---
title: Función JsStartDebugging | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsStartDebugging
helpviewer_keywords:
- JsStartDebugging function
ms.assetid: c48ba02d-6d47-466f-a970-02f087d525f3
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd9b7e3deb407d1a1e9d16db38e17c85ccc8c797
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569115"
---
# <a name="jsstartdebugging-function"></a>JsStartDebugging (Función)
Inicia la depuración en el contexto actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsStartDebugging();  
  
// Legacy mode signature  
STDAPI_(JsErrorCode)  JsStartDebugging(  
   _In_ IDebugApplication *debugApplication  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `debugApplication`  
 La aplicación de depuración que se va a usar para la depuración.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El host debe asegurarse de que `CoInitializeEx` se llama con `COINIT_MULTITHREADED` o `COINIT_APARTMENTTHREADED` al menos una vez antes de utilizar esta API  
  
 El parámetro `debugApplication` no es compatible con el modo de borde. Para más información sobre el uso de esta API en el modo de borde, vea [Compatibilidad con motores de borde o motores heredados](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)