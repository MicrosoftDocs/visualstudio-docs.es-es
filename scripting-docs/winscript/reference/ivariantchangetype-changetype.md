---
title: IVariantChangeType::ChangeType | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 0a02b8a3991ff6d20370cd4a2ea4cd87aa9a1226
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086585"
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