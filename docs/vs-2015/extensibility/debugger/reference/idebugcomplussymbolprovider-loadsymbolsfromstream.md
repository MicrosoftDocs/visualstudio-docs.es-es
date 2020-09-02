---
title: 'IDebugComPlusSymbolProvider:: LoadSymbolsFromStream | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::LoadSymbolsFromStream
- LoadSymbolsFromStream
ms.assetid: 1de272f0-24f4-4548-8b70-a205cddd4727
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 50ff4d2ca585b243cf5b040e355a94ecb3a0576d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176759"
---
# <a name="idebugcomplussymbolproviderloadsymbolsfromstream"></a>IDebugComPlusSymbolProvider::LoadSymbolsFromStream
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Carga los símbolos de depuración dados el flujo de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT LoadSymbolsFromStream(  
   ULONG32   ulAppDomainID,  
   GUID      guidModule,  
   ULONGLONG baseAddress,  
   IUnknown* pUnkMetadataImport,  
   IStream*  pStream  
);  
```  
  
```csharp  
int LoadSymbolsFromStream(  
   uint    ulAppDomainID,  
   Guid    guidModule,  
   ulong   baseAddress,  
   object  pUnkMetadataImport,  
   IStream pStream  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ulAppDomainID`  
 de Identificador del dominio de aplicación.  
  
 `guidModule`  
 de Identificador único del módulo.  
  
 `baseAddress`  
 de Dirección de memoria base.  
  
 `pUnkMetadataImport`  
 de Objeto que contiene los metadatos de símbolos.  
  
 `pStream`  
 de Flujo de datos que contiene los símbolos.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo implementar este método para un objeto **CDebugSymbolProvider** que expone la interfaz [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) . El método llama al método [LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md) .  
  
```cpp#  
HRESULT CDebugSymbolProvider::LoadSymbolsFromStream(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    ULONGLONG baseOffset,  
    IUnknown* pUnkMetadataImport,  
    IStream* pStream  
)  
{  
    return LoadSymbolsFromStreamWithCorModule (ulAppDomainID, guidModule, baseOffset, pUnkMetadataImport, NULL, pStream);  
}  
```  
  
## <a name="see-also"></a>Consulte también  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
