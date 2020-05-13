---
title: IDebugComPlusSymbolProvider ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 482ea1b2fb2eb7ddad46bd99694e4599e9fd9bbe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733475"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
Representa un proveedor de símbolos COM+ con métodos específicos para el código administrado.

## <a name="syntax"></a>Sintaxis

```
IDebugComPlusSymbolProvider : IDebugSymbolProvider
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Aunque no hay separación entre las interfaces que son útiles para un evaluador de expresiones (EE) y las que están diseñadas para ser utilizadas por un motor de depuración (DE), los métodos siguientes probablemente interesarán a los desarrolladores DE solamente: AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols y UpdateSymbols.

## <a name="methods"></a>Métodos
 Además de los métodos de la [interfaz IDebugSymbolProvider,](../../../extensibility/debugger/reference/idebugsymbolprovider.md) esta interfaz implementa los métodos siguientes:

|Método|Descripción|
|------------|-----------------|
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Determina si los símbolos de depuración se cargan para el módulo especificado dado el identificador de dominio de aplicación.|
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Crea un tipo a partir del tipo primitivo especificado.|
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Asigna una posición de documento en el módulo especificado a una matriz de direcciones de depuración.|
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Recupera información de tipo sobre la matriz especificada dada su dirección de depuración.|
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Recupera el nombre del ensamblado dado su módulo y dominio de aplicación.|
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Recupera las clases con el atributo especificado que se implementan en el lenguaje de programación especificado.|
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Recupera las clases con el atributo especificado en un módulo determinado.|
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Recupera el punto de entrada de la aplicación.|
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Recupera la dirección dentro de una función que representa el desplazamiento de línea especificado.|
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Recupera el diseño de variables locales para un conjunto de métodos.|
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Devuelve el nombre asociado al token especificado dado su objeto de metadatos.|
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Recupera los símbolos de depuración con el atributo primario especificado para el módulo especificado.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Recupera el lector de símbolos que va a usar el código no administrado.|
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Recupera a un tipo de símbolo dada su dirección de depuración.|
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Determina si se elimina la función en la dirección de depuración especificada.|
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Determina si la función en la dirección de depuración especificada se considera obsoleta.|
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Determina si el código en la dirección del depurador especificada está oculto.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Carga los símbolos de depuración especificados en la memoria.|
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Carga símbolos de depuración dado el flujo de datos.|
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Reemplaza los símbolos de depuración actuales por los de la secuencia de datos especificada.|
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Descarga los símbolos de depuración para el módulo especificado desde la memoria.|
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Actualiza los símbolos de depuración en memoria con los de la secuencia de datos especificada.|

## <a name="requirements"></a>Requisitos
 Encabezado: Sh.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
