---
title: IDispatchEx::GetNextDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 4d964a8744f1f0a28704dd0a1d5e0fd2e67aab1c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62997342"
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID

Enumera a los miembros del objeto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetNextDispID(
   DWORD grfdex,
   DISPID id,
   DISPID *pid
);
```

## <a name="parameters"></a>Parámetros

`grfdex`\
Determina qué conjunto de elementos se van a enumerar. Esto puede ser una combinación de los siguientes valores:

|Valor|Significado|
|-----------|-------------|
|fdexEnumDefault|Solicita que el objeto enumera los elementos de forma predeterminada. El objeto se puede enumerar cualquier conjunto de elementos.|
|fdexEnumAll|Solicita que el objeto enumera todos los elementos. El objeto se puede enumerar cualquier conjunto de elementos.|

`id`\
Identifica al miembro actual. GetNextDispID recupera el elemento de la enumeración después de este. Para obtener este identificador se utiliza GetDispID o una llamada anterior a GetNextDispID. Usa el valor DISPID_STARTENUM para obtener el primer identificador del primer elemento.

`pid`\
Dirección de una variable de identificador de envío que recibe el identificador del elemento siguiente en la enumeración.

Si se elimina un miembro por `DeleteMemberByName` o `DeleteMemberByDispID`, el `DISPID` deba sigan siendo válidos `GetNextDispID`.

## <a name="return-value"></a>Valor devuelto

Devuelve uno de los siguientes valores:

|||
|-|-|
|`S_OK`|Correcto.|
|`S_FALSE`|Se realiza la enumeración.|

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

- [IDispatchEx (Interfaz)](../../winscript/reference/idispatchex-interface.md)
- [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)
- [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)
- [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)