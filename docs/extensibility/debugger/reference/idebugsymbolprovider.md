---
title: IDebugSymbolProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98bd86cd219ec2604816e290f75e02d1f9530a53
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457629"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Esta interfaz representa un proveedor de símbolos que proporciona los símbolos y tipos, devolverlos como campos.

## <a name="syntax"></a>Sintaxis

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
Un proveedor de símbolos debe implementar esta interfaz para proporcionar símbolos y escriba la información a un evaluador de expresiones.

## <a name="notes-for-callers"></a>Notas para los llamadores
Esta interfaz se obtiene mediante el uso de COM `CoCreateInstance` función (por proveedores de símbolos no administrado) o cargando adecuado administrados ensamblado de código y crear instancias del proveedor de símbolos según la información encontrada en ese ensamblado. El motor de depuración crea el proveedor de símbolos para que funcione en coordinación con el evaluador de expresiones. Vea el ejemplo de un enfoque para crear una instancia de esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
La tabla siguiente muestran los métodos de `IDebugSymbolProvider`.

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
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Obtiene el campo que representa el nombre completo del método.|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Obtiene el tipo de campo de clase que representa el nombre completo de clase.|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Crea un enumerador para los espacios de nombres asociado a la dirección de depuración.|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Asigna un nombre de símbolo a un tipo de símbolo.|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Obtiene la dirección de depuración que sigue a una dirección de depuración especificado en un método.|

## <a name="remarks"></a>Comentarios
Esta interfaz asigna las posiciones de documento en las direcciones de depuración y viceversa.

## <a name="requirements"></a>Requisitos
Encabezado: sh.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

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
