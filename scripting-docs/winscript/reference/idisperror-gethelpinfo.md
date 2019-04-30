---
title: IDispError::GetHelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHelpInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHelpInfo
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa831ff511ea507e03ca858b93383ff38ead9039
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446908"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
Devuelve la ruta de acceso del archivo de ayuda y el identificador de contexto del tema que explica el error, si es posible.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrFileName`  
 [out] Cadena que contiene la ruta de acceso completa del archivo de ayuda. Si no hay ningún archivo de ayuda o se produce un error, el valor devuelto es NULL.  
  
 `pdwContext`  
 [out] El identificador de contexto de ayuda para el error. Si no hay ningún archivo de ayuda (si `pbstrFileName` es NULL), este parámetro no tiene ningún significado.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|Se ha producido un error específico del proveedor.|  
|`E_INVALIDARG`|`pbstrFileName` o `pdwContext` era NULL.|  
|`E_OUTOFMEMORY`|El proveedor no pudo asignar suficiente memoria en el que se va a devolver la ruta de acceso del archivo de ayuda.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve la ruta de acceso del archivo de ayuda y el identificador de contexto del tema que explica el error, si es posible.  
  
> [!NOTE]
> Este método no se implementa.  
  
## <a name="see-also"></a>Vea también  
 [IDispError (Interfaz)](../../winscript/reference/idisperror-interface.md)