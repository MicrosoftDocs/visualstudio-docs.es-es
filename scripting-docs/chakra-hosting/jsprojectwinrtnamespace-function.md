---
title: Función JsProjectWinRTNamespace | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 8a23c154-df4b-4ce3-9fef-f41f90acdb87
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04ecff41550219cdda5ea5d57f34fc440865bc99
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568475"
---
# <a name="jsprojectwinrtnamespace-function"></a>Función JsProjectWinRTNamespace
Proyecte un espacio de nombres de WinRT.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode)  
   JsProjectWinRTNamespace(  
   _In_z_ const wchar_t *namespaceName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `namespaceName`  
 El espacio de nombres de WinRT que se va a proyectar.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
 Esta API solo es compatible en modo perimetral.  
  
> [!NOTE]
>  WinRT era el nombre de la plataforma antes de Plataforma universal de Windows (UWP).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)