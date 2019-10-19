---
title: IActiveScriptParse32::P arseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33e454c-69d8-4cab-9150-d1e7fd04786d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: ec4e9539900ee39e99927bb9055a8c107f864653
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574898"
---
# <a name="iactivescriptparse32parsescripttext"></a>IActiveScriptParse32::P arseScriptText
Analiza el Scriptlet de código determinado, agregando declaraciones en el espacio de nombres y evaluando el código según corresponda.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT ParseScriptText(  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // cookie for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    VARIANT *pvarResult,             // address of buffer for results  
    EXCEPINFO *pexcepinfo            // address of buffer for error data  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|`pstrCode`|de Dirección del texto de Scriptlet que se va a evaluar. La interpretación de esta cadena depende del lenguaje de scripting.|  
|`pstrItemName`|de Dirección del nombre de elemento que proporciona el contexto en el que se va a evaluar el Scriptlet. Si este parámetro es NULL, el código se evalúa en el contexto global del motor de scripting.|  
|`punkContext`|de Dirección del objeto de contexto. Este objeto se reserva para su uso en un entorno de depuración, donde el depurador puede proporcionar un contexto de este tipo para representar un contexto de tiempo de ejecución activo. Si este parámetro es NULL, el motor utiliza `pstrItemName` para identificar el contexto.|  
|`pstrDelimiter`|de Dirección del delimitador de fin de Scriptlet. Cuando `pstrCode` se analiza desde un flujo de texto, el host normalmente usa un delimitador, como dos comillas simples (' '), para detectar el final del Scriptlet. Este parámetro especifica el delimitador utilizado por el host, lo que permite que el motor de scripting proporcione algún preprocesamiento primitivo condicional (por ejemplo, reemplazando una comilla simple ['] con dos comillas simples para su uso como delimitador). Exactamente cómo (y si) el motor de scripting hace uso de esta información depende del motor de scripting. Establezca este parámetro en `NULL` si el host no usó un delimitador para marcar el final del Scriptlet.|  
|`dwSourceContextCookie`|de Cookie que se usa para la depuración.|  
|`ulStartingLineNumber`|de Valor basado en cero que especifica en qué línea comenzará el análisis.|  
|`dwFlags`|de Marcas asociadas al Scriptlet. Puede ser una combinación de estos valores:|  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|Si la distinción entre una expresión de cálculo y una instrucción es importante, pero sintácticamente ambigua en el lenguaje de script, este marcador especifica que el Scriptlet debe interpretarse como una expresión, en lugar de como una instrucción o lista de instrucciones. De forma predeterminada, las instrucciones se suponen a menos que se pueda determinar la opción correcta a partir de la sintaxis del texto de Scriptlet.|  
|SCRIPTTEXT_ISPERSISTENT|Indica que el código agregado durante esta llamada debe guardarse si se guarda el motor de scripting (por ejemplo, a través de una llamada a `IPersist*::Save`) o si el motor de scripting se restablece por medio de una transición de vuelta al estado inicializado.|  
|SCRIPTTEXT_ISVISIBLE|Indica que el texto del script debe ser visible (y, por lo tanto, puede ser invocable por nombre) como un método global en el espacio de nombres del script.|  
  
|||  
|-|-|  
|`pvarResult`|enuncia Dirección de un búfer que recibe los resultados del procesamiento de Scriptlet o `NULL` si el llamador no espera ningún resultado (es decir, no se establece el valor SCRIPTTEXT_ISEXPRESSION).|  
|`pexcepinfo`|enuncia Dirección de una estructura que recibe información de excepción. Esta estructura se rellena si `IActiveScriptParse::ParseScriptText` devuelve DISP_E_EXCEPTION.|  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`DISP_E_EXCEPTION`|Se produjo una excepción en el procesamiento del Scriptlet. El parámetro `pexcepinfo` contiene información sobre la excepción.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se ha especificado un puntero no válido.|  
|`E_NOTIMPL`|No se admite este método. El motor de scripting no admite la evaluación en tiempo de ejecución de expresiones o instrucciones.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting está en estado no inicializado o cerrado, o bien se estableció la marca SCRIPTTEXT_ISEXPRESSION y el motor de scripting está en el estado inicializado).|  
|`OLESCRIPT_E_SYNTAX`|Se produjo un error de sintaxis no especificado en el Scriptlet.|  
  
## <a name="remarks"></a>Comentarios  
 Si el motor de scripting está en el estado inicializado, no se evaluará realmente ningún código durante esta llamada; en su lugar, ese código se pone en cola y se ejecuta cuando el motor de scripting pasa al estado Iniciado (o a través de él). Dado que la ejecución no se permite en el estado inicializado, es un error llamar a este método con la marca SCRIPTTEXT_ISEXPRESSION cuando se encuentra en estado inicializado.  
  
 Scriptlet puede ser una expresión, una lista de instrucciones o cualquier elemento permitido por el lenguaje de script. Por ejemplo, este método se usa en la evaluación de la etiqueta de > HTML \<SCRIPT, que permite que las instrucciones se ejecuten cuando se está construyendo la página HTML, en lugar de simplemente compilarlas en el estado del script.  
  
 El código que se pasa a este método debe ser una parte completa y válida del código. Por ejemplo, en VBScript no es válido llamar a este método una vez con sub function (x) y, a continuación, una segunda vez con `End Sub`. El analizador no debe esperar a la segunda llamada para completar la subrutina, sino que debe generar un error de análisis porque se inició una declaración de subrutina pero no se completó.  
  
 Para obtener más información sobre los Estados de script, consulte la sección Estados del motor de scripts de [Windows Script engines](../../winscript/windows-script-engines.md).  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)