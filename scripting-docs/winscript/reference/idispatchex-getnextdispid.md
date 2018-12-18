---
title: IDispatchEx::GetNextDispID | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNextDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNextDispID method
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ece7bde3230da370c8434cef7f780a92604df34c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728525"
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID
Enumera a los miembros del objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetNextDispID(  
   DWORD grfdex,  
   DISPID id,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `grfdex`  
 Determina qué conjunto de elementos se van a enumerar. Esto puede ser una combinación de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|fdexEnumDefault|Solicitudes que el objeto enumera los elementos de forma predeterminada. El objeto puede enumerar todos los conjuntos de elementos.|  
|fdexEnumAll|Solicitudes que el objeto enumera todos los elementos. El objeto puede enumerar todos los conjuntos de elementos.|  
  
 `id`  
 Identifica al miembro actual. GetNextDispID recupera el elemento de la enumeración después de éste. Usa GetDispID o una llamada anterior a GetNextDispID para obtener este identificador. Utiliza el valor DISPID_STARTENUM para obtener el primer identificador del primer elemento.  
  
 `pid`  
 Dirección de una variable DISPID que recibe el identificador del siguiente elemento de la enumeración.  
  
 Si se elimina un miembro por `DeleteMemberByName` o `DeleteMemberByDispID`, `DISPID` necesite siguen siendo válidas para `GetNextDispID`.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|||  
|-|-|  
|`S_OK`|Correcto.|  
|`S_FALSE`|Se realiza la enumeración.|  
  
## <a name="example"></a>Ejemplo  
  
```  
HRESULT hr;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
  
   // Assign to pdex  
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
   while (hr == NOERROR)  
   {  
      hr = pdex->GetMemberName(dispid, &bstrName);  
      if (!wcscmp(bstrName, OLESTR("Bar")))  
      {  
         SysFreeString(bstrName);  
         return TRUE;  
      }  
      SysFreeString(bstrName);  
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);  
   }  
```  
  
## <a name="see-also"></a>Vea también  
 [IDispatchEx (interfaz)](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](#lrfidispatchexgetnextdispid)   
 [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)   
 [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)