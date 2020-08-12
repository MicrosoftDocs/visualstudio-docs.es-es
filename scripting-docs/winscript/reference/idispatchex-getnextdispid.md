---
title: 'IDispatchEx:: GetNextDispID | Microsoft Docs'
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
ms.openlocfilehash: 8811e828a6701769badf45ca7c37f9c53529150f
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144434"
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID

Enumera los miembros del objeto.

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
Determina el conjunto de elementos que se va a enumerar. Puede ser una combinación de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|fdexEnumDefault|Solicita que el objeto Enumere los elementos predeterminados. El objeto puede enumerar cualquier conjunto de elementos.|
|fdexEnumAll|Solicita que el objeto Enumere todos los elementos. El objeto puede enumerar cualquier conjunto de elementos.|

`id`\
Identifica el miembro actual. GetNextDispID recupera el elemento de la enumeración después de este. Usa GetDispID o una llamada anterior a GetNextDispID para obtener este identificador. Utiliza el valor DISPID_STARTENUM para obtener el primer identificador del primer elemento.

`pid`\
Dirección de una variable de DISPID que recibe el identificador del siguiente elemento de la enumeración.

Si un miembro es eliminado por `DeleteMemberByName` o `DeleteMemberByDispID` , `DISPID` debe seguir siendo válido para `GetNextDispID` .

## <a name="return-value"></a>Valor devuelto

Devuelve uno de los valores siguientes:

|Value|Significado|
|-|-|
|`S_OK`|Correcto.|
|`S_FALSE`|La enumeración se realiza.|

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

## <a name="see-also"></a>Consulte también

- [IDispatchEx (Interfaz)](../../winscript/reference/idispatchex-interface.md)
- [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)
- [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)
- [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)