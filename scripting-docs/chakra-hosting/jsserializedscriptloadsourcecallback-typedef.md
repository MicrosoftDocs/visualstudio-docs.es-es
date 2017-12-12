---
title: "Definición de tipo JsSerializedScriptLoadSourceCallback | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9406c488-76ac-49e5-b305-39751f3412ea
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ff3bc206cf3779023a13166f30e8f4f719e7ebe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsserializedscriptloadsourcecallback-typedef"></a>JsSerializedScriptLoadSourceCallback (typedef)
El tiempo de ejecución llama a esta typedef para cargar el código fuente del script serializado.     El llamador debe mantener el búfer de script válido hasta la `JsSerializedScriptUnloadCallback`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef bool (CALLBACK * JsSerializedScriptLoadSourceCallback)(  
  _In_ JsSourceContextsourceContext,  
  _Outptr_result_z_ const wchar_t** scriptBuffer  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `sourceContext`  
 El contexto que se pasa a `JsParseSerializedScriptWithCallback` o `JsRunSerializedScriptWithCallback`.  
  
 `scriptBuffer`  
 El script que se devuelve.  
  
## <a name="remarks"></a>Comentarios  
  
> [!WARNING]
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)