---
title: 'Iprovideexpressioncontexts (:: EnumExpressionContexts | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: f161c1591267af1398d5c04d00623381cfae2ad4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572387"
---
# <a name="iprovideexpressioncontextsenumexpressioncontexts"></a>IProvideExpressionContexts::EnumExpressionContexts
Devuelve un enumerador de los contextos de expresión que conoce este componente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppedec`  
 enuncia Enumerador de los contextos de expresión que conoce este componente.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 El administrador de depuración de proceso utiliza este método para buscar todos los contextos de expresión globales asociados a un subproceso determinado.  
  
> [!NOTE]
> Se llama a este método desde el subproceso de interés. Es el implementador quien debe identificar el subproceso actual y devolver un enumerador adecuado.  
  
## <a name="see-also"></a>Vea también  
 [IProvideExpressionContexts (Interfaz)](../../winscript/reference/iprovideexpressioncontexts-interface.md)