---
title: IDebugSymbolProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8485497f9a5f0c6a04090755e6848bf8ed916ab3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909563"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Esta interfaz representa un proveedor de símbolos que proporciona símbolos y tipos y los devuelve como campos.

## <a name="syntax"></a>Sintaxis

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
Un proveedor de símbolos debe implementar esta interfaz para proporcionar información de símbolos y tipos a un evaluador de expresiones.

## <a name="notes-for-callers"></a>Notas para llamadores
Esta interfaz se obtiene utilizando la función de COM `CoCreateInstance` (para los proveedores de símbolos no administrados) o cargando el ensamblado de código administrado adecuado y creando una instancia del proveedor de símbolos basándose en la información que se encuentra en ese ensamblado. El motor de depuración crea una instancia del proveedor de símbolos para trabajar en coordinación con el evaluador de expresiones. Vea el ejemplo de un enfoque para crear una instancia de esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
En la tabla siguiente se muestran los métodos de `IDebugSymbolProvider` .

|Método|Descripción|
|------------|-----------------|
|`Initialize`|Desusado. No utilizar.|
|`Uninitialize`|Desusado. No utilizar.|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Obtiene el campo que contiene la dirección de depuración.|
|`GetField`|Desusado. No utilizar.|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Asigna una posición de documento en una matriz de direcciones de depuración.|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Asigna un contexto de documento en una matriz de direcciones de depuración.|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Asigna una dirección de depuración en un contexto de documento.|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Obtiene el lenguaje usado para compilar el código en la dirección de depuración.|
|`GetGlobalContainer`|Desusado. No utilizar.|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Obtiene el campo que representa un nombre de método completo.|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Obtiene el tipo de campo de clase que representa un nombre de clase completo.|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Crea un enumerador para los espacios de nombres asociados a la dirección de depuración.|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Asigna un nombre de símbolo a un tipo de símbolo.|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Obtiene la dirección de depuración que sigue a una dirección de depuración determinada en un método.|

## <a name="remarks"></a>Notas
Esta interfaz asigna posiciones de documento en direcciones de depuración y viceversa.

## <a name="requirements"></a>Requisitos
Encabezado: SH. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Ejemplo
En este ejemplo se muestra cómo crear una instancia del proveedor de símbolos, dado su GUID (un motor de depuración debe conocer este valor).

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
