---
title: Aplicaciones auxiliares de SDK para depurar | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6655b96ed51cd7cce5e94ce96cedf97517f1872a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53942416"
---
# <a name="sdk-helpers-for-debugging"></a>Asistentes de SDK para la depuración
Estas funciones y declaraciones son funciones auxiliares globales para implementar motores de depuración, los evaluadores de expresión y los proveedores de símbolos en C++.  
  
> [!NOTE]
>  Existen versiones administradas de estas funciones y declaraciones en este momento.  
  
## <a name="overview"></a>Información general  
 En orden para motores de depuración, los evaluadores de expresión y los proveedores de símbolo que va a usar Visual Studio, debe estar registrados. Esto se realiza mediante el establecimiento de subclaves del registro y las entradas, también conocidas como "establecer la métrica". Las funciones globales siguientes están diseñadas para facilitar el proceso de actualización de estas métricas. Consulte la sección sobre las ubicaciones del registro para averiguar el diseño de cada subclave del registro que se actualiza mediante estas funciones.  
  
## <a name="general-metric-functions"></a>Funciones de métrica generales  
 Estas son funciones generales usadas por los motores de depuración. Funciones especializadas en evaluadores de expresión y proveedores de símbolos se detallan más adelante.  
  
### <a name="getmetric-method"></a>Método GetMetric  
 Recupera un valor de métrica del registro.  
  
```cpp  
HRESULT GetMetric(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD * pdwValue,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|pszMachine|[in] Nombre de un equipo remoto, posiblemente, cuyo registro se escribirá (`NULL` significa que el equipo local).|  
|pszType|[in] Uno de los tipos de métricas.|  
|guidSection|[in] GUID de un motor concreto, del evaluador de expresiones, excepción, etcetera. Especifica una subsección en un tipo de métrica para un elemento específico.|  
|pszMetric|[in] La métrica que se va a obtener. Esto corresponde a un nombre de valor específico.|  
|pdwValue|[in] La ubicación de almacenamiento del valor de la métrica. Existen varios modelos de GetMetric que puede devolver un valor de DWORD (como en este ejemplo), una cadena BSTR, un GUID o una matriz de GUID.|  
|pszAltRoot|[in] Una raíz del registro alternativo a usar. Establecido en `NULL` para usar el valor predeterminado.|  
  
### <a name="setmetric-method"></a>Método SetMetric  
 Establece el valor de métrica especificado en el registro.  
  
```cpp  
HRESULT SetMetric(  
         LPCWSTR pszType,  
         REFGUID guidSection,  
         LPCWSTR pszMetric,  
   const DWORD   dwValue,  
         bool    fUserSpecific,  
         LPCWSTR pszAltRoot  
);  
```  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|pszType|[in] Uno de los tipos de métricas.|  
|guidSection|[in] GUID de un motor concreto, del evaluador de expresiones, excepción, etcetera. Especifica una subsección en un tipo de métrica para un elemento específico.|  
|pszMetric|[in] La métrica que se va a obtener. Esto corresponde a un nombre de valor específico.|  
|dwValue|[in] La ubicación de almacenamiento del valor de la métrica. Existen varios modelos de SetMetric que puede almacenar un valor de DWORD (en este ejemplo), una cadena BSTR, un GUID o una matriz de GUID.|  
|fUserSpecific|[in] TRUE si la métrica es específica del usuario y si debe escribirse en el subárbol del usuario en lugar de subárbol local machine.|  
|pszAltRoot|[in] Una raíz del registro alternativo a usar. Establecido en `NULL` para usar el valor predeterminado.|  
  
### <a name="removemetric-method"></a>Método RemoveMetric  
 Quita la métrica especificada del registro.  
  
```cpp  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|pszType|[in] Uno de los tipos de métricas.|  
|guidSection|[in] GUID de un motor concreto, del evaluador de expresiones, excepción, etcetera. Especifica una subsección en un tipo de métrica para un elemento específico.|  
|pszMetric|[in] La métrica que se va a quitar. Esto corresponde a un nombre de valor específico.|  
|pszAltRoot|[in] Una raíz del registro alternativo a usar. Establecido en `NULL` para usar el valor predeterminado.|  
  
### <a name="enummetricsections-method"></a>Método EnumMetricSections  
 Enumera las distintas secciones de métrica en el registro.  
  
```cpp  
HRESULT EnumMetricSections(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   GUID *  rgguidSections,  
   DWORD * pdwSize,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|pszMachine|[in] Nombre de un equipo remoto, posiblemente, cuyo registro se escribirá (`NULL` significa que el equipo local).|  
|pszType|[in] Uno de los tipos de métricas.|  
|rgguidSections|[in, out] Preasignado matriz de GUID que se va a rellenar.|  
|pdwSize|[in] El número máximo de GUID que se pueden almacenar en el `rgguidSections` matriz.|  
|pszAltRoot|[in] Una raíz del registro alternativo a usar. Establecido en `NULL` para usar el valor predeterminado.|  
  
## <a name="expression-evaluator-functions"></a>Funciones del evaluador de expresiones  
  
|Función|Descripción|  
|--------------|-----------------|  
|GetEEMetric|Recupera un valor de métrica del registro.|  
|SetEEMetric|Establece el valor de métrica especificado en el registro.|  
|RemoveEEMetric|Quita la métrica especificada del registro.|  
|GetEEMetricFile|Obtiene un nombre de archivo de la métrica especificada y lo carga, devolver el contenido del archivo como una cadena.|  
  
## <a name="exception-functions"></a>Funciones de excepción  
  
|Función|Descripción|  
|--------------|-----------------|  
|GetExceptionMetric|Recupera un valor de métrica del registro.|  
|SetExceptionMetric|Establece el valor de métrica especificado en el registro.|  
|RemoveExceptionMetric|Quita la métrica especificada del registro.|  
|RemoveAllExceptionMetrics|Quita todas las métricas de la excepción del registro.|  
  
## <a name="symbol-provider-functions"></a>Funciones del proveedor de símbolos  
  
|Función|Descripción|  
|--------------|-----------------|  
|GetSPMetric|Recupera un valor de métrica del registro.|  
|SetSPMetric|Establece el valor de métrica especificado en el registro.|  
|RemoveSPMetric|Quita la métrica especificada del registro.|  
  
## <a name="enumeration-functions"></a>Funciones de enumeración  
  
|Función|Descripción|  
|--------------|-----------------|  
|EnumMetricSections|Enumera todas las métricas para un tipo de métrica especificado.|  
|EnumDebugEngine|Enumera los motores de depuración registrados.|  
|EnumEEs|Enumera los evaluadores de expresión registrados.|  
|EnumExceptionMetrics|Enumera todas las métricas de la excepción.|  
  
## <a name="metric-definitions"></a>Definiciones de métricas  
 Estas definiciones se pueden usar para los nombres de métrica predefinidos. Los nombres se corresponden con diversas claves del registro y nombres de valor y se definen como cadenas de caracteres anchos todos: por ejemplo, `extern LPCWSTR metrictypeEngine`.  
  
|Tipos predefinidos de métrica|Descripción: La clave base para...|  
|-----------------------------|---------------------------------------|  
|metrictypeEngine|Todas las métricas de motor de depuración.|  
|metrictypePortSupplier|Todas las métricas del proveedor de puerto.|  
|metrictypeException|Todas las métricas de excepción.|  
|metricttypeEEExtension|Todas las extensiones del evaluador de expresión.|  
  
|Propiedades del motor de depuración|Descripción|  
|-----------------------------|-----------------|  
|metricAddressBP|Establezca en distinto de cero para indicar la compatibilidad con los puntos de interrupción de dirección.|  
|metricAlwaysLoadLocal|Establezca en distinto de cero con el fin de cargar siempre el motor de depuración local.|  
|metricLoadInDebuggeeSession|NO SE UTILIZA|  
|metricLoadedByDebuggee|Establezca en distinto de cero para indicar que el motor de depuración siempre se cargará con o por el programa que se está depurando.|  
|metricAttach|Establezca en distinto de cero para indicar la compatibilidad con datos adjuntos a los programas existentes.|  
|metricCallStackBP|Establezca en distinto de cero para indicar la compatibilidad con los puntos de interrupción de la pila de llamadas.|  
|metricConditionalBP|Establezca en distinto de cero para indicar la compatibilidad con la configuración de puntos de interrupción condicionales.|  
|metricDataBP|Establezca en distinto de cero para indicar la compatibilidad con la configuración de puntos de interrupción en los cambios en los datos.|  
|metricDisassembly|Establezca a distinto de cero para indicar la compatibilidad para la producción de una lista de desensamblado.|  
|metricDumpWriting|Establezca en distinto de cero para indicar la compatibilidad para escribir (el volcado de memoria para un dispositivo de salida) de volcado de memoria.|  
|metricENC|Establezca a distinto de cero para indicar la compatibilidad para editar y continuar. **Nota:**  Un motor de depuración nunca debe establecer esto o siempre debe establecer en 0.|  
|metricExceptions|Establezca en distinto de cero para indicar la compatibilidad para las excepciones.|  
|metricFunctionBP|Establezca en distinto de cero para indicar la compatibilidad con los puntos de interrupción con nombre (los puntos de interrupción que se interrumpan cuando se llama a un nombre de función determinado).|  
|metricHitCountBP|Establezca en distinto de cero para indicar la compatibilidad con la configuración de puntos de interrupción "de aciertos de punto" (puntos de interrupción que se desencadenan después de que se vea afectado a un número determinado de veces).|  
|metricJITDebug|Establezca a distinto de cero para indicar la compatibilidad para la depuración de just-in-time (el depurador se inicia cuando se produce una excepción en un proceso en ejecución).|  
|metricMemory|NO SE UTILIZA|  
|metricPortSupplier|Establezca esta opción en el CLSID del proveedor del puerto si uno está implementado.|  
|metricRegisters|NO SE UTILIZA|  
|metricSetNextStatement|Establezca en distinto de cero para indicar la compatibilidad para establecer la instrucción siguiente (que omite la ejecución de instrucciones intermedias).|  
|metricSuspendThread|Establezca en distinto de cero para indicar la compatibilidad para suspender la ejecución del subproceso.|  
|metricWarnIfNoSymbols|Establezca en distinto de cero para indicar que se debe notificar al usuario si no hay ningún símbolo.|  
|metricProgramProvider|Establezca esta opción en el CLSID del proveedor del programa.|  
|metricAlwaysLoadProgramProviderLocal|Establezca esta opción a distinto de cero para indicar que el proveedor del programa siempre se debe cargar localmente.|  
|metricEngineCanWatchProcess|Establezca esta opción en distinto de cero para indicar que el motor de depuración inspeccionará para procesar eventos en lugar del proveedor del programa.|  
|metricRemoteDebugging|Establezca esta opción en distinto de cero para indicar la compatibilidad para la depuración remota.|  
|metricEncUseNativeBuilder|Establezca esta opción a distinto de cero para indicar que el editar y continuar con el administrador deben usar encbuild.dll del motor de depuración para crear aplicaciones para editar y continuar. **Nota:**  Un motor de depuración nunca debe establecer esto o siempre debe establecer en 0.|  
|metricLoadUnderWOW64|Establezca esta opción en distinto de cero para indicar que el motor de depuración se debe cargar en el proceso depurado bajo WOW cuando se depura un proceso de 64 bits; en caso contrario, el motor de depuración se cargarán en el proceso de Visual Studio (que se ejecuta bajo WOW64).|  
|metricLoadProgramProviderUnderWOW64|Establezca esta opción en distinto de cero para indicar que el proveedor del programa debe cargarse en el proceso depurado al depurar un proceso de 64 bits en WOW; en caso contrario, se cargarán en el proceso de Visual Studio.|  
|metricStopOnExceptionCrossingManagedBoundary|Establezca esta opción en distinto de cero para indicar que el proceso debe detenerse si se produce una excepción no controlada en los límites de código administrado y no administrado.|  
|metricAutoSelectPriority|Establezca esta opción en una prioridad para la selección automática del motor de depuración (valores igual a mayor prioridad).|  
|metricAutoSelectIncompatibleList|Clave de registro que contiene entradas que especifican los GUID de motores de depuración se pasará por alto en la selección automática. Estas entradas son un número (0, 1, 2 y así sucesivamente) con un GUID que se expresa como una cadena.|  
|metricIncompatibleList|Clave de registro que contiene entradas que especifican los GUID para los motores de depuración que no son compatibles con el motor de depuración.|  
|metricDisableJITOptimization|Establezca esta opción en distinto de cero para indicar que se deben deshabilitar las optimizaciones de just-in-time (para código administrado) durante la depuración.|  
  
|Propiedades de la expresión del evaluador de expresiones|Descripción|  
|-------------------------------------|-----------------|  
|metricEngine|Esto contiene el número de motores de depuración que admiten el evaluador de expresiones especificado.|  
|metricPreloadModules|Establezca esta opción en distinto de cero para indicar que se deben cargar previamente a los módulos cuando se inicia un evaluador de expresiones en un programa.|  
|metricThisObjectName|Establezca esta opción en el nombre del objeto "this".|  
  
|Propiedades de extensión del evaluador de expresiones|Descripción|  
| - |-----------------|  
|metricExtensionDll|Nombre del archivo dll que es compatible con esta extensión.|  
|metricExtensionRegistersSupported|Lista de registros que se admiten.|  
|metricExtensionRegistersEntryPoint|Punto de entrada para tener acceso a registros.|  
|metricExtensionTypesSupported|Lista de tipos admitidos.|  
|metricExtensionTypesEntryPoint|Punto de entrada para el acceso a los tipos.|  
  
|Propiedades de puerto de proveedor|Descripción|  
|------------------------------|-----------------|  
|metricPortPickerCLSID|El CLSID del selector de puerto (un cuadro de diálogo, el usuario puede utilizar para seleccionar los puertos y agregar los puertos que se utilizará para depuración).|  
|metricDisallowUserEnteredPorts|Distinto de cero si no se puede agregar los puertos escrito por el usuario para el proveedor del puerto (Esto hace que el cuadro de diálogo Selector de puerto básicamente de sólo lectura).|  
|metricPidBase|El identificador de proceso base utilizado por el proveedor del puerto al asignar identificadores de proceso.|  
  
|Tipos de Store SP predefinidos|Descripción|  
|-------------------------------|-----------------|  
|storetypeFile|Los símbolos se almacenan en un archivo independiente.|  
|storetypeMetadata|Los símbolos se almacenan como metadatos en un ensamblado.|  
  
|Propiedades varias|Descripción|  
|------------------------------|-----------------|  
|metricShowNonUserCode|Establezca esta opción en distinto de cero para mostrar el código no es de usuario.|  
|metricJustMyCodeStepping|Establezca esta opción en distinto de cero para indicar que la ejecución paso a paso pueden producirse solo en el código de usuario.|  
|metricCLSID|CLSID de un objeto de un tipo específico de métrica.|  
|MetricName|Nombre descriptivo para un objeto de un tipo específico de métrica.|  
|metricLanguage|Nombre del idioma.|  
  
## <a name="registry-locations"></a>Ubicaciones del registro  
 Las métricas se leen y escritas en el registro, concretamente, en el `VisualStudio` subclave.  
  
> [!NOTE]
>  La mayoría de los casos, las métricas se escribirán en la clave HKEY_LOCAL_MACHINE. Sin embargo, a veces HKEY_CURRENT_USER será la clave de destino. Dbgmetric.lib controla ambas claves. Al obtener una métrica, lo busca en HKEY_CURRENT_USER primero y, después, en HKEY_LOCAL_MACHINE. Cuando se está estableciendo una métrica, un parámetro especifica qué clave de nivel superior que se usará.  
  
 *[clave del registro]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[raíz de la versión]*\  
  
 *[raíz métrica]*\  
  
 *[tipo de métrica]*\  
  
 *[metric] = [valor métrico]*  
  
 *[metric] = [valor métrico]*  
  
 *[metric] = [valor métrico]*  
  
|Marcador de posición|Descripción|  
|-----------------|-----------------|  
|*[clave del registro]*|`HKEY_CURRENT_USER` o `HKEY_LOCAL_MACHINE`.|  
|*[raíz de la versión]*|La versión de Visual Studio (por ejemplo, `7.0`, `7.1`, o `8.0`). Sin embargo, esta raíz también se puede modificar mediante la **/rootsuffix** cambie a **devenv.exe**. VSIP, este modificador es normalmente **Exp**, por lo que podría ser la raíz de la versión, por ejemplo, 8.0Exp.|  
|*[raíz métrica]*|Puede ser `AD7Metrics` o `AD7Metrics(Debug)`, dependiendo de si se usa la versión de depuración de dbgmetric.lib. **Nota:**  Si se utiliza dbgmetric.lib, esta convención de nomenclatura debe cumplir si dispone de las diferencias entre depuración y lanzamiento de versiones que deben reflejarse en el registro.|  
|*[tipo de métrica]*|El tipo de métrica se escriban: `Engine`, `ExpressionEvaluator`, `SymbolProvider`, etcetera. Todas ellas se definen como en dbgmetric.h como `metricTypeXXXX`, donde `XXXX` es el nombre de tipo específico.|  
|*[metric]*|El nombre de una entrada que se asignará un valor con el fin de establecer la métrica. La organización de las métricas depende del tipo de métrica.|  
|*[valor de métrica]*|El valor asignado a la métrica. El tipo que el valor debe tener (cadena), números, etc. depende de la métrica.|  
  
> [!NOTE]
>  Todos los GUID se almacenan en el formato de `{GUID}`. Por ejemplo: `{123D150B-FA18-461C-B218-45B3E4589F9B}`.  
  
### <a name="debug-engines"></a>Motores de depuración  
 La siguiente es la organización de las métricas de los motores de depuración en el registro. `Engine` es el nombre de tipo de métrica para un motor de depuración y corresponde a *[tipo de métrica]* en el subárbol del registro anterior.  
  
 `Engine`\  
  
 *[guid de motor]*\  
  
 `CLSID` = *[guid de clase]*  
  
 *[metric] = [valor métrico]*  
  
 *[metric] = [valor métrico]*  
  
 *[metric] = [valor métrico]*  
  
 `PortSupplier`\  
  
 `0` = *[guid de proveedor de puerto]*  
  
 `1` = *[guid de proveedor de puerto]*  
  
|Marcador de posición|Descripción|  
|-----------------|-----------------|  
|*[guid de motor]*|El GUID del motor de depuración.|  
|*[guid de clase]*|El GUID de la clase que implementa el motor de depuración.|  
|*[guid de proveedor de puerto]*|El GUID del proveedor del puerto, si existe. Muchos motores de depuración utiliza el proveedor del puerto predeterminado y, por tanto, no especifican su propio proveedor. En este caso, la subclave `PortSupplier` estará ausente.|  
  
### <a name="port-suppliers"></a>Proveedores de puertos  
 La siguiente es la organización de las métricas del proveedor de puerto en el registro. `PortSupplier` es el nombre de tipo de métrica para un proveedor de puerto y corresponde a *[tipo de métrica]*.  
  
 `PortSupplier`\  
  
 *[guid de proveedor de puerto]*\  
  
 `CLSID` = *[guid de clase]*  
  
 *[metric] = [valor métrico]*  
  
 *[metric] = [valor métrico]*  
  
|Marcador de posición|Descripción|  
|-----------------|-----------------|  
|*[guid de proveedor de puerto]*|El GUID del proveedor del puerto|  
|*[guid de clase]*|El GUID de la clase que implementa este proveedor de puerto|  
  
### <a name="symbol-providers"></a>Proveedores de símbolos  
 La siguiente es la organización de las métricas del proveedor de símbolos en el registro. `SymbolProvider` es el nombre de tipo de métrica para el proveedor de símbolos y corresponde a *[tipo de métrica]*.  
  
 `SymbolProvider`\  
  
 *[símbolo guid de proveedor]*\  
  
 `file`\  
  
 `CLSID` = *[guid de clase]*  
  
 *[metric] = [valor métrico]*  
  
 *[metric] = [valor métrico]*  
  
 `metadata`\  
  
 `CLSID` = *[guid de clase]*  
  
 *[metric] = [valor métrico]*  
  
 *[metric] = [valor métrico]*  
  
|Marcador de posición|Descripción|  
|-----------------|-----------------|  
|*[símbolo guid de proveedor]*|El GUID del proveedor de símbolos|  
|*[guid de clase]*|El GUID de la clase que implementa este proveedor de símbolos|  
  
### <a name="expression-evaluators"></a>Evaluadores de expresión  
 La siguiente es la organización de las métricas de evaluador de expresión en el registro. `ExpressionEvaluator` es el nombre de tipo de métrica para el evaluador de expresiones y corresponde a *[tipo de métrica]*.  
  
> [!NOTE]
>  El tipo de métrica para `ExpressionEvaluator` no está definido en dbgmetric.h, ya que se supone que todos los cambios de métrica para evaluadores de expresión pasará a través de las funciones de métrica de evaluador de expresión adecuada (el diseño de la `ExpressionEvaluator` subclave es ligeramente complicado, por lo que los detalles están ocultos en dbgmetric.lib).  
  
 `ExpressionEvaluator`\  
  
 *[guid de lenguaje]*\  
  
 *[guid de proveedor]*\  
  
 `CLSID` = *[guid de clase]*  
  
 *[metric] = [valor métrico]*  
  
 *[metric] = [valor métrico]*  
  
 `Engine`\  
  
 `0` = *[guid de motor de depuración]*  
  
 `1` = *[guid de motor de depuración]*  
  
|Marcador de posición|Descripción|  
|-----------------|-----------------|  
|*[guid de lenguaje]*|El GUID de un idioma|  
|*[guid de proveedor]*|El GUID de un proveedor|  
|*[guid de clase]*|El GUID de la clase que implementa este evaluador de expresiones|  
|*[guid de motor de depuración]*|El GUID de un motor de depuración que trabaja este evaluador de expresiones|  
  
### <a name="expression-evaluator-extensions"></a>Extensiones del evaluador de expresiones  
 La siguiente es la organización de las métricas de extensión de evaluador de expresión en el registro. `EEExtensions` es el nombre de tipo de métrica para la expresión de extensiones del evaluador de expresiones y corresponde a *[tipo de métrica]*.  
  
 `EEExtensions`\  
  
 *[guid de la extensión]*\  
  
 *[metric] = [valor métrico]*  
  
 *[metric] = [valor métrico]*  
  
|Marcador de posición|Descripción|  
|-----------------|-----------------|  
|*[guid de la extensión]*|El GUID de una extensión de evaluador de expresiones|  
  
### <a name="exceptions"></a>Excepciones  
 La siguiente es la organización de las métricas de excepciones en el registro. `Exception` es el nombre de tipo de métrica para las excepciones y corresponde a *[tipo de métrica]*.  
  
 `Exception`\  
  
 *[guid de motor de depuración]*\  
  
 *[tipos de excepción]*\  
  
 *[excepción]*\  
  
 *[metric] = [valor métrico]*  
  
 *[metric] = [valor métrico]*  
  
 *[excepción]*\  
  
 *[metric] = [valor métrico]*  
  
 *[metric] = [valor métrico]*  
  
|Marcador de posición|Descripción|  
|-----------------|-----------------|  
|*[guid de motor de depuración]*|El GUID del motor de depuración es compatible con las excepciones.|  
|*[tipos de excepción]*|Un título general para la subclave que identifica la clase de excepciones que se pueden administrar. Los nombres típicos son **las excepciones de C++**, **las excepciones Win32**, **excepciones de Common Language Runtime**, y **comprobaciones nativas en tiempo de ejecución**. Estos nombres también se usan para identificar una clase determinada de excepción para el usuario.|  
|*[excepción]*|Un nombre para una excepción: por ejemplo, **_com_error** o **CTRL+INTERR**. Estos nombres también se usan para identificar una excepción determinada para el usuario.|  
  
## <a name="requirements"></a>Requisitos  
 Estos archivos se encuentran en el [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] directorio de instalación del SDK (de forma predeterminada, *[unidad]* \Program Files\Microsoft SDK de Visual Studio 2010\\).  
  
 Encabezado: includes\dbgmetric.h  
  
 Biblioteca: libs\ad2de.lib, libs\dbgmetric.lib  
  
## <a name="see-also"></a>Vea también  
 [Referencia de API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)