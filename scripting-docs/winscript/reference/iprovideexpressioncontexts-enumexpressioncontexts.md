---
title: IProvideExpressionContexts::EnumExpressionContexts | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProvideExpressionContexts.EnumExpressionContexts
apilocation:
- jscript.dll
helpviewer_keywords:
- IProvideExpressionContexts::EnumExpressionContexts
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dd18408235a5621354531a2fd228ff44a19d6a1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088717"
---
# <a name="iprovideexpressioncontextsenumexpressioncontexts"></a>IProvideExpressionContexts::EnumExpressionContexts
Devuelve un enumerador de contextos de expresión que se conoce por este componente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppedec`  
 [out] Un enumerador de los contextos de expresión conocido por este componente.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 El Administrador de depuración del proceso, usa este método para buscar todos los contextos de expresión global asociados a un subproceso determinado.  
  
> [!NOTE]
>  Este método se llama desde dentro del subproceso de interés. Es responsabilidad del implementador para identificar el subproceso actual y devuelve un enumerador correspondiente.  
  
## <a name="see-also"></a>Vea también  
 [IProvideExpressionContexts (Interfaz)](../../winscript/reference/iprovideexpressioncontexts-interface.md)