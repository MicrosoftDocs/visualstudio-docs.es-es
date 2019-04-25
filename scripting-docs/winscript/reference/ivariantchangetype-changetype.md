---
title: IVariantChangeType::ChangeType | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IVariantChangeType.ChangeType
apilocation:
- scrobj.dll
helpviewer_keywords:
- IVariantChangeType::ChangeType
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81ed0a8502e9b0cfc53725621d477d34ee5010ea
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158586"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Toma un valor de tipo variant y crea una nueva variante con un tipo especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pvarDst`  
 [in, out] Una variante que contiene el valor representado por `pvarSrc`, pero con el tipo especificado por `vtNew`.  
  
 `pvarSrc`  
 [in] Un valor para cambiar a un nuevo tipo de variante.  
  
 `lcid`  
 [in] El contexto de la configuración regional que se usará al convertir los argumentos a o desde cadenas.  
  
 `vtNew`  
 [in] Especifica el tipo para `pvarDst` para convertirse en.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 El `pvarDst` y `pvarSrc` argumentos pueden ser iguales, en cuyo caso el valor original se sobrescribe. Este método pasa `pvarDst` a la `VariantClear` función y por consiguiente `pvarDst` debe inicializarse en un valor válido.  
  
## <a name="see-also"></a>Vea también  
 [IVariantChangeType (Interfaz)](../../winscript/reference/ivariantchangetype-interface.md)