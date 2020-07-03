---
title: 'IActiveScriptParse32:: AddScriptlet | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fcf11eb2-8e71-4cca-afda-a91791c243ff
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9ec8395f6c8f404a1d9010234da030c47594e087
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835750"
---
# <a name="iactivescriptparse32addscriptlet"></a>IActiveScriptParse32::AddScriptlet
Agrega un Scriptlet de código al script. Este método se utiliza en entornos en los que el estado persistente del script está entrelazado con el documento host y el host es responsable de restaurar el script, en lugar de hacerlo a través de una `IPersist*` interfaz. Los ejemplos principales son lenguajes de scripting de HTML que permiten que los scriptlets del código incrustado en el documento HTML se adjunten a eventos intrínsecos (por ejemplo, ONCLICK = "Button1. Text = ' exit '").  
  
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
 de Dirección de un nombre predeterminado que se va a asociar al Scriptlet. Si Scriptlet no contiene información de nomenclatura (como en el ejemplo de ONCLICK anterior), este nombre se usará para identificar el Scriptlet. Si este parámetro es `NULL` , el motor de scripting fabrica un nombre único, si es necesario.  
  
 `pstrCode`  
 de Dirección del texto de Scriptlet que se va a agregar. La interpretación de esta cadena depende del lenguaje de scripting.  
  
 `pstrItemName`  
 de Dirección de un búfer que contiene el nombre del elemento asociado a este Scriptlet. Este parámetro, además de `pstrSubItemName` , identifica el objeto para el que Scriptlet es un controlador de eventos.  
  
 `pstrSubItemName`  
 de Dirección de un búfer que contiene el nombre de un `subobject` del elemento con nombre al que está asociado este Scriptlet; este nombre debe encontrarse en la información de tipo del elemento con nombre. Este parámetro es NULL si Scriptlet se va a asociar al elemento con nombre en lugar de a `subitem` . Este parámetro, además de `pstrItemName` , identifica el objeto específico para el que Scriptlet es un controlador de eventos.  
  
 `pstrEventName`  
 de Dirección de un búfer que contiene el nombre del evento para el que el Scriptlet es un controlador de eventos.  
  
 `pstrDelimiter`  
 de Dirección del delimitador de fin de Scriptlet. Cuando el `pstrCode` parámetro se analiza desde un flujo de texto, el host normalmente usa un delimitador, como dos comillas simples (' '), para detectar el final del Scriptlet. Este parámetro especifica el delimitador utilizado por el host, lo que permite que el motor de scripting proporcione algún preprocesamiento primitivo condicional (por ejemplo, reemplazando una comilla simple ['] con dos comillas simples para su uso como delimitador). Exactamente cómo (y si) el motor de scripting hace uso de esta información depende del motor de scripting. Establezca este parámetro en NULL si el host no ha utilizado un delimitador para marcar el final del Scriptlet.  
  
 `dwSourceContextCookie`  
 de Valor definido por la aplicación que se usa para la depuración.  
  
 `ulStartingLineNumber`  
 de Valor basado en cero que especifica en qué línea comenzará el análisis.  
  
 `dwFlags`  
 de Marcas asociadas al Scriptlet. Puede ser una combinación de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|Indica que el texto del script debe ser visible (y, por lo tanto, puede ser invocable por nombre) como un método global en el espacio de nombres del script.|  
|SCRIPTTEXT_ISPERSISTENT|Indica que el código agregado durante esta llamada debe guardarse si se guarda el motor de scripting (por ejemplo, a través de una llamada a `IPersist*::Save` ) o si el motor de scripting se restablece por medio de una transición de vuelta al estado inicializado. Para obtener más información acerca de este estado, vea Estados del motor de scripts.|  
  
 `pbstrName` ,  
 enuncia Nombre real que se usa para identificar el Scriptlet. Esto va a ser en orden de preferencia: un nombre especificado explícitamente en el texto de Scriptlet, el nombre predeterminado proporcionado en `pstrDefaultName` o un nombre único sintetizado por el motor de scripting.  
  
 `pexcepinfo` ,  
 enuncia Dirección de una estructura que contiene información de la excepción. Esta estructura se debe rellenar si se devuelve DISP_E_EXCEPTION.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`DISP_E_EXCEPTION`|Se produjo una excepción en el análisis del Scriptlet. El `pexcepinfo` parámetro contiene información sobre la excepción.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_NOTIMPL`|Este método no se admite; el motor de scripting no admite la adición de scriptlets de receptores de eventos.|  
|`E_POINTER`|Se ha especificado un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting aún no se ha cargado o inicializado) y, por tanto, se ha producido un error.|  
|`OLESCRIPT_E_INVALIDNAME`|El nombre predeterminado proporcionado no es válido en este lenguaje de scripting.|  
|`OLESCRIPT_E_SYNTAX`|Se produjo un error de sintaxis no especificado en el Scriptlet.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)