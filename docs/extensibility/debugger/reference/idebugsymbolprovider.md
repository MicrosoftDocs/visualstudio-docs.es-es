---
title: "IDebugSymbolProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider"
helpviewer_keywords: 
  - "Interfaz IDebugSymbolProvider"
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugSymbolProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa un proveedor de símbolos que proporciona símbolos y tipos, devolviéndolos como campos.  
  
## Sintaxis  
  
```  
IDebugSymbolProvider : IUnknown  
```  
  
## Notas para los implementadores  
 Un proveedor de token debe implementar esta interfaz para proporcionar símbolo y la información de tipos a un evaluador de expresiones.  
  
## Notas para los llamadores  
 Esta interfaz es obtenida mediante la función de `CoCreateInstance` COM \(para los proveedores no administrada de símbolos\) o cargar el ensamblado adecuado de código administrado y creando instancias del proveedor del token basado en la encontrada en ese ensamblado.  El motor de depuración crea instancias del proveedor del token para trabajar en coordinación con el evaluador de expresiones.  Vea el ejemplo para un enfoque para crear instancias de esta interfaz.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugSymbolProvider`.  
  
|Método|Descripción|  
|------------|-----------------|  
|`Initialize`|Obsoleto.  No utilizar.|  
|`Uninitialize`|Obsoleto.  No utilizar.|  
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Obtiene el campo que contiene la dirección de depuración.|  
|`GetField`|Obsoleto.  No utilizar.|  
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Asigna una posición del documento en una matriz de direcciones de depuración.|  
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Asigna un contexto del documento en una matriz de direcciones de depuración.|  
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Asigna una dirección de depuración en un contexto del documento.|  
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Obtiene el idioma utilizado para compilar el código en la dirección de depuración.|  
|`GetGlobalContainer`|Obsoleto.  No utilizar.|  
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Obtiene el campo que representa un nombre completo del método.|  
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Obtiene el tipo de campo de clase que representa un nombre de clase completo.|  
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Crea un enumerador para los espacios de nombres asociado con la dirección de la depuración.|  
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Asigna un nombre de símbolo a un tipo de token.|  
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Obtiene la dirección de depuración que sigue a una dirección determinada de depuración en un método.|  
  
## Comentarios  
 Esta interfaz asigna las posiciones del documento en direcciones de depuración y viceversa.  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Ejemplo  
 Este ejemplo muestra cómo crear instancias del proveedor de símbolos, dado su GUID \(un motor de depuración debe conocer este valor\).  
  
```cpp#  
// A debug engine uses its own symbol provider and would know the GUID  
// of that provider.  
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)  
{  
    // This is typically defined globally.  For this example, it is  
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
  
## Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)