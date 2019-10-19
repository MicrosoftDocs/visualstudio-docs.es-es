---
title: 'IDispatchEx:: GetMemberName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetMemberName
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberName method
ms.assetid: 5e59b63c-b781-4b90-88fd-40603a379a2d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f68b0157e8e352b34885ae94d14026a51c4a6e97
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574106"
---
# <a name="idispatchexgetmembername"></a>IDispatchEx::GetMemberName
Recupera el nombre de un miembro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetMemberName(  
   DISPID id,  
   BSTR *pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `id`  
 Identifica el miembro. Utiliza `GetDispID` o `GetNextDispID` para obtener el identificador de envío.  
  
 `pbstrName`  
 Dirección de un `BSTR` que recibe el nombre del miembro. La aplicación que realiza la llamada es responsable de liberar este valor.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|||  
|-|-|  
|`S_OK`|Correcto.|  
|`DISP_E_UNKNOWNNAME`|No se conocía el nombre.|  
  
## <a name="example"></a>Ejemplo  
  
```cpp
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
 [IDispatchEx (interfaz](../../winscript/reference/idispatchex-interface.md) )    
 [IDispatchEx:: GetDispID](../../winscript/reference/idispatchex-getdispid.md)    
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)