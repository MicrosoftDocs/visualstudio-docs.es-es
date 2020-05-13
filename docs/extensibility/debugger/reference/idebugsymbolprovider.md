---
title: IDebugSymbolProvider ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11e180288a9312d9af5a3d3b1bd63d8f2266f581
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719172"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Esta interfaz representa un proveedor de símbolos que proporciona símbolos y tipos, devolviéndolos como campos.

## <a name="syntax"></a>Sintaxis

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
Un proveedor de símbolos debe implementar esta interfaz para proporcionar información de símbolos y tipos a un evaluador de expresiones.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
Esta interfaz se obtiene mediante `CoCreateInstance` la función de COM (para proveedores de símbolos no administrados) o cargando el ensamblado de código administrado adecuado y creando una instancia del proveedor de símbolos en función de la información que se encuentra en ese ensamblado. El motor de depuración crea una instancia del proveedor de símbolos para que funcione en coordinación con el evaluador de expresiones. Consulte el ejemplo para obtener un enfoque para crear instancias de esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
En la tabla siguiente `IDebugSymbolProvider`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|`Initialize`|En desuso. No debe usarse.|
|`Uninitialize`|En desuso. No debe usarse.|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Obtiene el campo que contiene la dirección de depuración.|
|`GetField`|En desuso. No debe usarse.|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Asigna una posición de documento en una matriz de direcciones de depuración.|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Asigna un contexto de documento en una matriz de direcciones de depuración.|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Asigna una dirección de depuración a un contexto de documento.|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Obtiene el lenguaje utilizado para compilar el código en la dirección de depuración.|
|`GetGlobalContainer`|En desuso. No debe usarse.|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Obtiene el campo que representa un nombre de método completo.|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Obtiene el tipo de campo de clase que representa un nombre de clase completo.|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Crea un enumerador para espacios de nombres asociados a la dirección de depuración.|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Asigna un nombre de símbolo a un tipo de símbolo.|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Obtiene la dirección de depuración que sigue a una dirección de depuración determinada en un método.|

## <a name="remarks"></a>Observaciones
Esta interfaz asocia las posiciones del documento en los direccionamientos del debug y viceversa.

## <a name="requirements"></a>Requisitos
Encabezado: sh.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Ejemplo
En este ejemplo se muestra cómo crear instancias del proveedor de símbolos, dado su GUID (un motor de depuración debe conocer este valor).

```cpp
// A debug engine uses its own symbol provider and would know the GUID
// of that provider.
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugSymbolProvider *pProvider = NULL;
    if (pSymbolProviderGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetSPMetric(*pSymbolProviderGuid,
                      storetypeFile,
                      metricCLSID,
                      &clsidProvider,
                      strRegistrationRoot);
        if (IsEqualGUID(clsidProvider,GUID_NULL)) {
            // No file type provider, try metadata provider.
            ::GetSPMetric(*pSymbolProviderGuid,
                          ::storetypeMetadata,
                          metricCLSID,
                          &clsidProvider,
                          strRegistrationRoot);
        }
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugSymbolProvider> spSymbolProvider;
            spSymbolProvider.CoCreateInstance(clsidProvider);
            if (spSymbolProvider != NULL) {
                pProvider = spSymbolProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>Vea también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
