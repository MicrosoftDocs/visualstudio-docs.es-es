---
title: IDebugContainerField::EnumFields ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afc461d52f81afc2c2e7127a90313bea7b9dacf3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733221"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Crea un enumerador para los campos del contenedor.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumFields( 
   FIELD_KIND         dwKindFilter,
   FIELD_MODIFIERS    dwModifiersFilter,
   LPCOLESTR          pszNameFilter,
   NAME_MATCH         nameMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumFields(
   enum_ FIELD_KIND      dwKindFilter,
   enum_ FIELD_MODIFIERS dwModifiersFilter,
   string                pszNameFilter,
   NAME_MATCH            nameMatch,
   out IEnumDebugFields  ppEnum
);
```

## <a name="parameters"></a>Parámetros
`dwKindFilter`\
[en] Una combinación de [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) constantes que seleccionan los campos que se van a enumerar. Los tipos de campo pueden describir tipos de almacenamiento, como clase o primitivo, o información específica, como local, parámetro o puntero "this".

`dwModifiersFilter`\
[en] Una combinación de [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) constantes que seleccionan los campos que se van a enumerar. Los modificadores de campo pueden ser permisos de acceso, como público o privado, o información de almacenamiento, como virtual, estática o final.

`pszNameFilter`\
[en] El nombre del campo que se va a enumerar. Esto puede ser un valor nulo si se van a devolver todos los campos.

`nameMatch`\
[en] Un valor de la [enumeración NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) que controla si la búsqueda distingue mayúsculas de minúsculas o no.

`ppEnum`\
[fuera] Devuelve un [objeto IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de campos. Devuelve un valor nulo si no hay campos.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK o S_FALSE si no hay campos. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Los `dwKindFilter` `dwModifiersFilter`parámetros `pszNameFilter` , , y se pueden combinar, por ejemplo, para seleccionar todos los métodos virtuales públicos denominados "MyMethod".

## <a name="see-also"></a>Vea también
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
