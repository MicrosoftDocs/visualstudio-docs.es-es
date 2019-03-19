---
title: IActiveScriptParse::AddScriptlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_AddScriptlet
ms.assetid: 824929f4-4dd3-473a-92d9-0b96acea2f14
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee5d76060789118e9051c2d8dcc5fc570617f6a8
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151276"
---
# <a name="iactivescriptparseaddscriptlet"></a>IActiveScriptParse::AddScriptlet
Agrega un scriptlet de código a la secuencia de comandos. Este método se usa en entornos donde el estado persistente del script es imbricado con el documento de host y el host es responsable de restaurar la secuencia de comandos, en lugar de mediante un `IPersist*` interfaz. Los principales ejemplos son lenguajes de scripting de HTML que permiten scriptlets de código incrustado en el documento HTML que se adjuntará a eventos intrínsecos (por ejemplo, ONCLICK="button1.text='Exit'").  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT AddScriptlet(  
    LPCOLESTR pstrDefaultName,       // address of default name of scriptlet  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    LPCOLESTR pstrSubItemName,       // address of subitem name  
    LPCOLESTR pstrEventName,         // address of event name  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    BSTR *pbstrName,                 // address of actual name of scriptlet  
    EXCEPINFO *pexcepinfo            // address of exception information  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstrDefaultName`  
 [in] Dirección de un nombre predeterminado para asociar el scriptlet. Si el scriptlet no contiene información de nombres (como se muestra en el ejemplo anterior de ONCLICK), este nombre se usará para identificar el scriptlet. Si este parámetro es `NULL`, el motor de scripting fabrica un nombre único, si es necesario.  
  
 `pstrCode`  
 [in] Dirección del texto de scriptlet a agregar. La interpretación de esta cadena depende del lenguaje de scripting.  
  
 `pstrItemName`  
 [in] Dirección de un búfer que contiene el nombre del elemento asociado a este scriptlet. Este parámetro, además de `pstrSubItemName`, identifica el objeto para el que el scriptlet es un controlador de eventos.  
  
 `pstrSubItemName`  
 [in] Dirección de un búfer que contiene el nombre de un `subobject` del elemento con nombre que está asociado este scriptlet; este nombre debe encontrarse en la información de tipo del elemento con nombre. Este parámetro es NULL si el scriptlet está asociarse con el elemento con nombre en lugar de un `subitem`. Este parámetro, además de `pstrItemName`, identifica el objeto específico para el que el scriptlet es un controlador de eventos.  
  
 `pstrEventName`  
 [in] Dirección de un búfer que contiene el nombre del evento para el que el scriptlet es un controlador de eventos.  
  
 `pstrDelimiter`  
 [in] Dirección del delimitador final de scriptlet. Cuando el `pstrCode` parámetro se analiza desde una secuencia de texto, el host normalmente utiliza un delimitador, como dos comillas ("), para detectar el final de scriptlet. Este parámetro especifica el delimitador que utiliza el host, lo que permite el motor de scripting proporcione algún preprocesamiento primitivo condicional (por ejemplo, que reemplaza una comilla sencilla ['] con dos comillas simples para su uso como un delimitador). Exactamente cómo (y si) el motor de scripting hace uso de esta información depende del motor de scripting. Establezca este parámetro en NULL si el host no utilizó un delimitador para marcar el final de scriptlet.  
  
 `dwSourceContextCookie`  
 [in] Valor definido por la aplicación que se usa con fines de depuración.  
  
 `ulStartingLineNumber`  
 [in] Valor de base cero que especifica en qué línea empezará el análisis en.  
  
 `dwFlags`  
 [in] Marcas asociadas al scriptlet. Puede ser una combinación de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|Indica que el texto del script debería estar visible (y, por lo tanto, invocable por nombre) como método global en el espacio de nombres de la secuencia de comandos.|  
|INDICADOR SCRIPTTEXT_ISPERSISTENT|Indica que se debe guardar el código agregado durante esta llamada si se guarda el motor de scripting (por ejemplo, mediante una llamada a `IPersist*::Save`), o si el motor de scripting se restablece por medio de una transición al estado inicializado. Para obtener más información acerca de este estado, vea Estados del motor de secuencia de comandos.|  
  
 `pbstrName` ,  
 [out] Nombre real que se usa para identificar el scriptlet. Esto es para estar en orden de preferencia: en el texto de scriptlet especifica explícitamente un nombre, el nombre predeterminado proporcionado en `pstrDefaultName`, o un nombre único sintetizados por el motor de scripting.  
  
 `pexcepinfo` ,  
 [out] Dirección de una estructura que contiene información de excepción. Esta estructura debe rellenarse si se devuelve DISP_E_EXCEPTION.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`DISP_E_EXCEPTION`|Se produjo una excepción en el análisis del scriptlet. El `pexcepinfo` parámetro contiene información sobre la excepción.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_NOTIMPL`|Este método no se admite; el motor de scripting no admite la adición de scriptlets de recepción de eventos.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting no se ha cargado o inicializado) y, por tanto, no se pudo.|  
|`OLESCRIPT_E_INVALIDNAME`|El nombre predeterminado proporcionado no es válido en este lenguaje de scripting.|  
|`OLESCRIPT_E_SYNTAX`|Se produjo un error de sintaxis no especificado en el scriptlet.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)