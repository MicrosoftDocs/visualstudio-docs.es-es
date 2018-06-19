---
title: IActiveScriptParse32::ParseScriptText | Documentos de Microsoft
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
ms.openlocfilehash: af1e3b6723b402263359719695aa1f57432c76e2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724825"
---
# <a name="iactivescriptparse32parsescripttext"></a>IActiveScriptParse32::ParseScriptText
Analiza el scriptlet de código determinado, agregar las declaraciones de espacio de nombres y evaluar el código según corresponda.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
|`pstrCode`|[in] Dirección del texto scriptlet para evaluar. La interpretación de esta cadena depende el lenguaje de scripting.|  
|`pstrItemName`|[in] Dirección del nombre del elemento que proporciona el contexto en el que se evaluará el scriptlet. Si este parámetro es NULL, el código se evalúa en el contexto global del motor de scripting.|  
|`punkContext`|[in] Dirección del objeto de contexto. Este objeto está reservado para su uso en un entorno de depuración, donde el depurador para representar un contexto de tiempo de ejecución activo pueden proporcionar un contexto de este tipo. Si este parámetro es NULL, el motor utiliza `pstrItemName` para identificar el contexto.|  
|`pstrDelimiter`|[in] Dirección del extremo de scriptlet delimitador. Cuando `pstrCode` se analiza desde una secuencia de texto, el host normalmente usa un delimitador, como dos comillas ("), para detectar el final de la scriptlet simples. Este parámetro especifica el delimitador que utiliza el host, lo que el motor de scripting proporcionar algunos condicional preprocesamiento primitivos (por ejemplo, reemplace una comilla simple ['] con dos comillas simples para su uso como un delimitador). Exactamente cómo (y si) el scripting hace motor depende del uso de esta información en el motor de scripting. Establezca este parámetro en `NULL` si el host no usó un delimitador para marcar el final de la scriptlet.|  
|`dwSourceContextCookie`|[in] Cookie que se usa para fines de depuración.|  
|`ulStartingLineNumber`|[in] Valor basado en cero que especifica la línea que el análisis se iniciará en.|  
|`dwFlags`|[in] Marcas asociadas con el scriptlet. Puede ser una combinación de estos valores:|  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|Si la diferencia entre una expresión de cálculo y una instrucción es importante, pero sintácticamente ambigua en el lenguaje de script, esta marca especifica que el scriptlet se interpreta como una expresión, en lugar de como una instrucción o una lista de instrucciones. De forma predeterminada, las instrucciones se supone que, a menos que se puede determinar la opción correcta de la sintaxis del texto scriptlet.|  
|SCRIPTTEXT_ISPERSISTENT|Indica que se debe guardar el código agregado durante esta llamada si se guarda el motor de scripting (por ejemplo, mediante una llamada a `IPersist*::Save`), o si se restablece el motor de scripting por medio de una transición al estado inicializado.|  
|SCRIPTTEXT_ISVISIBLE|Indica que el texto del script debe estar visible (y, por lo tanto, puede llamar por su nombre) como un método global en el espacio de nombres de la secuencia de comandos.|  
  
|||  
|-|-|  
|`pvarResult`|[out] Dirección de un búfer que recibe los resultados del procesamiento de scriptlet, o `NULL` si el llamador espera que ningún resultado (es decir, no se ha establecido el valor SCRIPTTEXT_ISEXPRESSION).|  
|`pexcepinfo`|[out] Dirección de una estructura que recibe información de excepción. Esta estructura se rellena si `IActiveScriptParse::ParseScriptText` devuelve DISP_E_EXCEPTION.|  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`DISP_E_EXCEPTION`|Se produjo una excepción en el procesamiento de la scriptlet. El `pexcepinfo` parámetro contiene información sobre la excepción.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
|`E_NOTIMPL`|No se admite este método. El motor de scripting no es compatible con la evaluación en tiempo de ejecución de expresiones o instrucciones.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting que se está en el estado sin inicializar o cerrado, o se estableció el marcador SCRIPTTEXT_ISEXPRESSION y es el motor de scripting en el estado de inicialización).|  
|`OLESCRIPT_E_SYNTAX`|Se produjo un error de sintaxis no especificado en el scriptlet.|  
  
## <a name="remarks"></a>Comentarios  
 Si el motor de scripting en el estado inicializado, ningún código realmente se evaluará durante esta llamada; en su lugar, este código está en cola y ejecutar cuando el motor de scripting se entra en (o a través de) el estado iniciado. Dado que no se permite la ejecución en el estado inicializado, es un error llamar a este método con la marca SCRIPTTEXT_ISEXPRESSION cuando se encuentra en el estado de inicialización.  
  
 El scriptlet puede ser una expresión, una lista de instrucciones o cualquier elemento permitido por el lenguaje de script. Por ejemplo, este método se utiliza en la evaluación del HTML \<SCRIPT > etiqueta, lo que permite que las instrucciones se puede ejecutar porque se está construyendo la página HTML en lugar de simplemente compilarlas en el estado de la secuencia de comandos.  
  
 El código que se pasa a este método debe ser una parte válida y completa del código. Por ejemplo, en VBScript no es válido para llamar a este método una vez con Sub Function(x) y, a continuación, una segunda vez con `End Sub`. El analizador no debe esperar a que la segunda llamada a completar la subrutina, pero en su lugar debe generar un error de análisis porque se ha iniciado pero no completado una declaración de la subrutina.  
  
 Para obtener más información acerca de los Estados de secuencia de comandos, vea la sección de Estados del motor de secuencia de comandos de [motores Windows Script](../../winscript/windows-script-engines.md).  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)