---
title: 'IDebugContainerField:: EnumFields | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
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
de Combinación de constantes de [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) que seleccionan los campos que se van a enumerar. Los tipos de campo pueden describir los tipos de almacenamiento, como clase o primitivo, o información específica, como la configuración local, el parámetro o el puntero "this".

`dwModifiersFilter`\
de Combinación de constantes de [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) que seleccionan los campos que se van a enumerar. Los modificadores de campo pueden ser permisos de acceso, como público o privado, o información de almacenamiento, como virtual, static o final.

`pszNameFilter`\
de Nombre del campo que se va a enumerar. Puede ser un valor NULL si se van a devolver todos los campos.

`nameMatch`\
de Un valor de la enumeración [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) que controla si la búsqueda distingue entre mayúsculas y minúsculas o no.

`ppEnum`\
enuncia Devuelve un objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de campos. Devuelve un valor NULL si no hay ningún campo.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, Devuelve S_OK o S_FALSE si no hay ningún campo. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Los `dwKindFilter` `dwModifiersFilter` parámetros, y `pszNameFilter` se pueden combinar, por ejemplo, para seleccionar todos los métodos virtuales públicos denominados "MyMethod".

## <a name="see-also"></a>Vea también
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
