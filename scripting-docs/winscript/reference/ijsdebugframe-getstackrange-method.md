---
title: 'Ijsdebugframe:: GetStackRange (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetStackRange
apilocation:
- jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cce4d4542f4f76657475636ad6d8e430e1909181
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727875"
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange (Método)
Devuelve el intervalo de direcciones absolutas del marco de pila de JavaScript lógico.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pStart`  
 [out] Abajo mayoría puntero de pila del marco.  
  
 `pEnd`  
 [out] Superior puntero Apilador mayoría del marco.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Este método es útil para unir seguimientos de pila intercalados recopilados a partir de varios tiempos de ejecución. El inicio, punteros de pila final pueden abarcar varios marcos de pila de máquina física (para los marcos de tiempo de ejecución de JavaScript interpretados). Inicio > Finalizar a medida que crece la pila de alto a bajo dirección.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugFrame (Interfaz)](../../winscript/reference/ijsdebugframe-interface.md)