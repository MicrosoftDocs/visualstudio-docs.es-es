---
title: 'Ivariantchangetype (:: ChangeType | Microsoft Docs'
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
ms.openlocfilehash: 406d5d8486b3016f0105b7bd8bf231db0e1e9613
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571785"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Toma un valor Variant y crea una nueva variante con un tipo especificado.  
  
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
 [in, out] Variante que contiene el valor representado por `pvarSrc`, pero con el tipo especificado por `vtNew`.  
  
 `pvarSrc`  
 de Valor Variant que se va a cambiar a un nuevo tipo.  
  
 `lcid`  
 de Contexto de la configuración regional que se va a usar al convertir los argumentos en cadenas o desde ellas.  
  
 `vtNew`  
 de Especifica el tipo de `pvarDst` que se va a convertir en.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Los argumentos `pvarDst` y `pvarSrc` pueden ser iguales, en cuyo caso se sobrescribe el valor original. Este método pasa `pvarDst` a la función de `VariantClear` y, por consiguiente, `pvarDst` debe inicializarse en un valor válido.  
  
## <a name="see-also"></a>Vea también  
 [IVariantChangeType (Interfaz)](../../winscript/reference/ivariantchangetype-interface.md)