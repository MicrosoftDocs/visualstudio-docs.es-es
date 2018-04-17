---
title: IDebugComPlusSymbolProvider | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a1eab7e30715032500719ee371011a600d2e9552
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
Representa un proveedor de símbolos de COM + con métodos que son específicas de código administrado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Aunque hay una separación entre las interfaces que son útiles para un evaluador de expresiones (EE) y aquellos que están diseñados para ser usado por un motor de depuración (Alemania), los siguientes métodos pueden interesar probablemente Alemania sólo a los programadores: AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols y UpdateSymbols.  
  
## <a name="methods"></a>Métodos  
 Además de los métodos en el [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) interfaz, esta interfaz implementa los métodos siguientes:  
  
|Método|Descripción|  
|------------|-----------------|  
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Determina si se cargan los símbolos de depuración para el módulo especificado según el identificador de dominio de aplicación.|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Crea un tipo de tipo primitivo especificado.|  
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Asigna una posición del documento en el módulo especificado en una matriz de direcciones de depuración.|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Recupera información de tipo de la matriz especificada a partir de su dirección de depuración.|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Recupera el nombre del ensamblado dado su módulo y dominio de aplicación.|  
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Recupera las clases con el atributo especificado que se implementan en el lenguaje de programación determinado.|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Recupera las clases con el atributo especificado en un módulo determinado.|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Recupera el punto de entrada de la aplicación.|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Recupera la dirección dentro de una función que representa el desplazamiento de línea determinada.|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Recupera el diseño de las variables locales para un conjunto de métodos.|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Devuelve el nombre asociado con el token especificado de su objeto de metadatos determinado.|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Recupera los símbolos de depuración con el atributo primario indicado para el módulo especificado.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Recupera el lector de símbolos para su uso en código no administrado.|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Recupera a un tipo de símbolo determinado por su dirección de depuración.|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Determina si se elimina la función en la dirección de depuración especificado.|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Determina si la función en la dirección de depuración especificado se considera obsoleta.|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Determina si se oculta el código en la dirección de depurador especificado.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Carga los símbolos de depuración especificado en la memoria.|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Cargas depuración símbolos a partir de la secuencia de datos.|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Reemplaza los símbolos de depuración actual con los de la secuencia de datos especificada.|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Descarga los símbolos de depuración para el módulo especificado de la memoria.|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Actualiza los símbolos de depuración en la memoria con los que el flujo de datos especificado.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll