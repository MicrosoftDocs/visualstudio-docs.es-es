---
title: IDispError::GetSource | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetSource
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetSource
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 629ecb8427539069bb9e235e733140331875288c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091824"
---
# <a name="idisperrorgetsource"></a>IDispError::GetSource
Devuelve el identificador de programación dependiente del idioma para la clase o aplicación que generó el error.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrSource`  
 [out] Cadena que contiene un identificador de programación, en el formulario `progname.objectname`.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método se utiliza para determinar la clase o la aplicación donde se produjo la excepción. El identificador de programación puede devolverse en el idioma especificado por el identificador de configuración regional (LCID) suministrado en el momento de invocación.  
  
> [!NOTE]
>  Este método no se implementa.  
  
## <a name="see-also"></a>Vea también  
 [IDispError (Interfaz)](../../winscript/reference/idisperror-interface.md)