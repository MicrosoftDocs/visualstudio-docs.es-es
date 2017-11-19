---
title: IProvideExpressionContexts::EnumExpressionContexts | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IProvideExpressionContexts.EnumExpressionContexts
apilocation: jscript.dll
helpviewer_keywords: IProvideExpressionContexts::EnumExpressionContexts
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c47619fface892e7e0d80141d7d4be53398a356e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iprovideexpressioncontextsenumexpressioncontexts"></a>IProvideExpressionContexts::EnumExpressionContexts
Devuelve un enumerador de contextos de expresión que se conoce por este componente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppedec`  
 [out] Enumerador de contextos de expresión que se conoce por este componente.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 El Administrador de depuración de procesos usa este método para buscar todos los contextos de expresión global asociados a un subproceso determinado.  
  
> [!NOTE]
>  Este método se llama desde el subproceso de interés. Es responsabilidad del implementador para identificar el subproceso actual y devuelve un enumerador correspondiente.  
  
## <a name="see-also"></a>Vea también  
 [IProvideExpressionContexts (Interfaz)](../../winscript/reference/iprovideexpressioncontexts-interface.md)