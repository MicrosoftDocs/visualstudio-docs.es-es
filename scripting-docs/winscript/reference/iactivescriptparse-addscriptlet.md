---
title: IActiveScriptParse::AddScriptlet | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: e854ac71dc36263d805160f9336e049856076ce5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724655"
---
# <a name="iactivescriptparseaddscriptlet"></a>IActiveScriptParse::AddScriptlet
Agrega un Subscript de código a la secuencia de comandos. Este método se usa en entornos donde el estado persistente de la secuencia de comandos es entrelazado con el documento de host y el host es responsable de la restauración de la secuencia de comandos, en lugar de mediante un `IPersist*` interfaz. Los ejemplos principales son lenguajes de scripting de HTML que permiten scriptlets de código incrustado en el documento HTML que se adjuntará a eventos intrínsecos (por ejemplo, ONCLICK="button1.text='Exit'").  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
 [in] Dirección de un nombre predeterminado para asociar el scriptlet. Si el scriptlet no contiene información de asignación de nombres (como en el ejemplo ONCLICK anterior), este nombre se utilizará para identificar el scriptlet. Si este parámetro es `NULL`, el motor de scripting fabrica un nombre único, si es necesario.  
  
 `pstrCode`  
 [in] Dirección del texto scriptlet que se agregará. La interpretación de esta cadena depende el lenguaje de scripting.  
  
 `pstrItemName`  
 [in] Dirección de un búfer que contiene el nombre del elemento asociado a este scriptlet. Este parámetro, además de `pstrSubItemName`, identifica el objeto para el que el scriptlet es un controlador de eventos.  
  
 `pstrSubItemName`  
 [in] Dirección de un búfer que contiene el nombre de una `subobject` del elemento con nombre con el que está asociado este scriptlet; este nombre debe encontrarse en la información de tipo del elemento con nombre. Este parámetro es NULL si el scriptlet es que se asociará con el elemento con nombre en lugar de un `subitem`. Este parámetro, además de `pstrItemName`, identifica el objeto específico para el que el scriptlet es un controlador de eventos.  
  
 `pstrEventName`  
 [in] Dirección de un búfer que contiene el nombre del evento para el que el scriptlet es un controlador de eventos.  
  
 `pstrDelimiter`  
 [in] Dirección del extremo de scriptlet delimitador. Cuando el `pstrCode` parámetro se analiza desde una secuencia de texto, el host normalmente usa un delimitador, como dos comillas ("), para detectar el final de la scriptlet simples. Este parámetro especifica el delimitador que utiliza el host, lo que el motor de scripting proporcionar algunos condicional preprocesamiento primitivos (por ejemplo, reemplace una comilla simple ['] con dos comillas simples para su uso como un delimitador). Exactamente cómo (y si) el scripting hace motor depende del uso de esta información en el motor de scripting. Establezca este parámetro en NULL si el host no usó un delimitador para marcar el final de la scriptlet.  
  
 `dwSourceContextCookie`  
 [in] Valor definido por la aplicación que se usa para fines de depuración.  
  
 `ulStartingLineNumber`  
 [in] Valor basado en cero que especifica la línea que el análisis se iniciará en.  
  
 `dwFlags`  
 [in] Marcas asociadas con el scriptlet. Puede ser una combinación de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|Indica que el texto del script debe estar visible (y, por lo tanto, puede llamar por su nombre) como un método global en el espacio de nombres de la secuencia de comandos.|  
|SCRIPTTEXT_ISPERSISTENT|Indica que se debe guardar el código agregado durante esta llamada si se guarda el motor de scripting (por ejemplo, mediante una llamada a `IPersist*::Save`), o si se restablece el motor de scripting por medio de una transición al estado inicializado. Para obtener más información acerca de este estado, vea Estados de motor de secuencia de comandos.|  
  
 `pbstrName` ,  
 [out] Nombre real que se usa para identificar el scriptlet. Esto sirve para estar en orden de preferencia: un nombre se especifica explícitamente en el texto de scriptlet, el nombre predeterminado proporcionado en `pstrDefaultName`, o un nombre único sintetizada por el motor de scripting.  
  
 `pexcepinfo` ,  
 [out] Dirección de una estructura que contiene información de excepción. Esta estructura debe rellenarse si se devuelve DISP_E_EXCEPTION.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`DISP_E_EXCEPTION`|Se produjo una excepción en el análisis de la scriptlet. El `pexcepinfo` parámetro contiene información sobre la excepción.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_NOTIMPL`|Este método no se admite; el motor de scripting no admite la adición de scriptlets recibir eventos.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting se aún no ha cargado o inicializar) y, por tanto, no se pudo.|  
|`OLESCRIPT_E_INVALIDNAME`|El nombre predeterminado proporcionado no es válido en este lenguaje de scripting.|  
|`OLESCRIPT_E_SYNTAX`|Se produjo un error de sintaxis no especificado en el scriptlet.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)