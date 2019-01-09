---
title: 'Iactivescriptparse:: Parsescripttext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_ParseScriptText
ms.assetid: 2d237d6c-cc65-415b-8808-72791304a136
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d88258a1bd16dba1de8d6ffa282f0f8ba409e2d
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088977"
---
# <a name="iactivescriptparseparsescripttext"></a>IActiveScriptParse::ParseScriptText
Analiza el scriptlet de código dado, agregando declaraciones al espacio de nombres y evaluando código según corresponda.  
  
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
|`pstrCode`|[in] Dirección del texto de scriptlet a evaluar. La interpretación de esta cadena depende del lenguaje de scripting.|  
|`pstrItemName`|[in] Dirección del nombre del elemento que proporciona el contexto en el que se puede evaluar el scriptlet. Si este parámetro es NULL, el código se evalúa en el contexto global del motor de scripting.|  
|`punkContext`|[in] Dirección del objeto de contexto. Este objeto está reservado para su uso en un entorno de depuración, donde el depurador para representar un contexto de tiempo de ejecución activo puede proporcionar un contexto de este tipo. Si este parámetro es NULL, el motor utiliza `pstrItemName` para identificar el contexto.|  
|`pstrDelimiter`|[in] Dirección del delimitador final de scriptlet. Cuando `pstrCode` se analiza desde una secuencia de texto, el host normalmente utiliza un delimitador, como dos comillas ("), para detectar el final de scriptlet. Este parámetro especifica el delimitador que utiliza el host, lo que permite el motor de scripting proporcione algún preprocesamiento primitivo condicional (por ejemplo, que reemplaza una comilla sencilla ['] con dos comillas simples para su uso como un delimitador). Exactamente cómo (y si) el motor de scripting hace uso de esta información depende del motor de scripting. Establezca este parámetro en `NULL` si el host no utilizó un delimitador para marcar el final de scriptlet.|  
|`dwSourceContextCookie`|[in] Cookie utilizada para fines de depuración.|  
|`ulStartingLineNumber`|[in] Valor de base cero que especifica en qué línea empezará el análisis en.|  
|`dwFlags`|[in] Marcas asociadas al scriptlet. Puede ser una combinación de estos valores:|  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|Si la diferencia entre una expresión computacional y una instrucción es importante pero sintácticamente ambigua en el lenguaje de script, este marcador especifica que es el scriptlet debe interpretarse como una expresión, en lugar de una instrucción o una lista de instrucciones. De forma predeterminada, las instrucciones se asumen a menos que se puede determinar la elección correcta de la sintaxis del texto de scriptlet.|  
|INDICADOR SCRIPTTEXT_ISPERSISTENT|Indica que se debe guardar el código agregado durante esta llamada si se guarda el motor de scripting (por ejemplo, mediante una llamada a `IPersist*::Save`), o si el motor de scripting se restablece por medio de una transición al estado inicializado.|  
|SCRIPTTEXT_ISVISIBLE|Indica que el texto del script debería estar visible (y, por lo tanto, invocable por nombre) como método global en el espacio de nombres de la secuencia de comandos.|  
  
|||  
|-|-|  
|`pvarResult`|[out] Dirección de un búfer que recibe los resultados del procesamiento del scriptlet o `NULL` si el llamador no espera ningún resultado (es decir, no se establece el valor SCRIPTTEXT_ISEXPRESSION).|  
|`pexcepinfo`|[out] Dirección de una estructura que recibe información de excepción. Esta estructura se rellena si `IActiveScriptParse::ParseScriptText` devuelve DISP_E_EXCEPTION.|  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`DISP_E_EXCEPTION`|Se produjo una excepción en el procesamiento del scriptlet. El `pexcepinfo` parámetro contiene información sobre la excepción.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
|`E_NOTIMPL`|No se admite este método. El motor de scripting no admite evaluación en tiempo de ejecución de expresiones o instrucciones.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting está en estado no inicializado o cerrado, o se ha establecido la marca SCRIPTTEXT_ISEXPRESSION y el motor de scripting está en estado inicializado).|  
|`OLESCRIPT_E_SYNTAX`|Se produjo un error de sintaxis no especificado en el scriptlet.|  
  
## <a name="remarks"></a>Comentarios  
 Si el motor de scripting está en estado inicializado, realmente no se evaluará ningún código durante esta llamada; en su lugar, dicho código está en cola y se ejecuta cuando se envía el motor de scripting (o pasa) al estado iniciado. Dado que no se permite la ejecución en el estado inicializado, es un error llamar a este método con el indicador SCRIPTTEXT_ISEXPRESSION cuando está en estado inicializado.  
  
 El scriptlet puede ser una expresión, una lista de instrucciones o cualquier elemento permitido por el lenguaje de script. Por ejemplo, este método se utiliza en la evaluación del código HTML \<SCRIPT > etiqueta, que permite que las instrucciones se puede ejecutar porque se está construyendo la página HTML en lugar de simplemente compilarlas en el estado de la secuencia de comandos.  
  
 El código que se pasa a este método debe ser una parte válida y completa del código. Por ejemplo, en VBScript es válido llamar a este método una vez con Sub Function (x) y, a continuación, una segunda vez con `End Sub`. El analizador no debe esperar a que la segunda llamada completar la subrutina, pero en su lugar debe generar un error de análisis porque se inició pero no ha completado una declaración de subrutina.  
  
 Para obtener más información acerca de los Estados de secuencia de comandos, vea la sección de Estados del motor de secuencia de comandos de [motores de scripts de Windows](../../winscript/windows-script-engines.md).  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)