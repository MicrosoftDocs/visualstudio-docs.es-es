---
title: Aplicaciones auxiliares SDK para depurar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9c5d24c8a3a2bb81c87b2cc405a6885b8f23374
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="sdk-helpers-for-debugging"></a>Aplicaciones auxiliares SDK para la depuración
Estas funciones y declaraciones son funciones auxiliares globales para la implementación de motores de depuración, los evaluadores de expresión y los proveedores de símbolos en C++.  
  
> [!NOTE]
>  No hay ningún versiones administradas de estas funciones y declaraciones en este momento.  
  
## <a name="overview"></a>Información general  
 En orden para motores de depuración, los evaluadores de expresión y los proveedores de símbolo que va a usar Visual Studio, se deben registrar. Esto se hace estableciendo subclaves y entradas, también conocidas como "establecer la métrica". Las siguientes funciones globales están diseñadas para facilitar el proceso de actualización de estas métricas. Vea la sección sobre ubicaciones del registro para averiguar el diseño de cada subclave del registro que se actualiza mediante estas funciones.  
  
## <a name="general-metric-functions"></a>Funciones de métrica general  
 Se trata de funciones generales usadas por motores de depuración. Especializado funciones para evaluadores de expresión y proveedores de símbolos se detallan más adelante.  
  
### <a name="getmetric-method"></a>GetMetric (método)  
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
|pszMachine|[in] Nombre de una máquina remota posiblemente cuyo registro se va a escribir (`NULL` significa el equipo local).|  
|pszType|[in] Uno de los tipos de métrica.|  
|guidSection|[in] GUID de un motor específico, evaluador, excepción, etcetera. Esta propiedad especifica una subsección en un tipo de métrica para un elemento específico.|  
|pszMetric|[in] La métrica que se va a obtener. Esto corresponde a un nombre de valor específico.|  
|pdwValue|[in] La ubicación de almacenamiento del valor de la métrica. Hay varias versiones de GetMetric que puede devolver un valor de DWORD (como en este ejemplo), una cadena BSTR, un GUID o una matriz de GUID.|  
|pszAltRoot|[in] Una raíz del registro alternativo a usar. Establecido en `NULL` para utilizar el valor predeterminado.|  
  
### <a name="setmetric-method"></a>SetMetric (método)  
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
|pszType|[in] Uno de los tipos de métrica.|  
|guidSection|[in] GUID de un motor específico, evaluador, excepción, etcetera. Esta propiedad especifica una subsección en un tipo de métrica para un elemento específico.|  
|pszMetric|[in] La métrica que se va a obtener. Esto corresponde a un nombre de valor específico.|  
|dwValue|[in] La ubicación de almacenamiento del valor de la métrica. Hay varias versiones de SetMetric que puede almacenar un valor de DWORD (en este ejemplo), una cadena BSTR, un GUID o una matriz de GUID.|  
|fUserSpecific|[in] Es TRUE si la métrica es específica del usuario y se debe escribir en el subárbol del usuario en lugar de la sección de la máquina local.|  
|pszAltRoot|[in] Una raíz del registro alternativo a usar. Establecido en `NULL` para utilizar el valor predeterminado.|  
  
### <a name="removemetric-method"></a>RemoveMetric (método)  
 Elimina la métrica especificada del registro.  
  
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
|pszType|[in] Uno de los tipos de métrica.|  
|guidSection|[in] GUID de un motor específico, evaluador, excepción, etcetera. Esta propiedad especifica una subsección en un tipo de métrica para un elemento específico.|  
|pszMetric|[in] La métrica que se va a quitar. Esto corresponde a un nombre de valor específico.|  
|pszAltRoot|[in] Una raíz del registro alternativo a usar. Establecido en `NULL` para utilizar el valor predeterminado.|  
  
### <a name="enummetricsections-method"></a>EnumMetricSections (método)  
 Enumera las distintas secciones de métricas en el registro.  
  
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
|pszMachine|[in] Nombre de una máquina remota posiblemente cuyo registro se va a escribir (`NULL` significa el equipo local).|  
|pszType|[in] Uno de los tipos de métrica.|  
|rgguidSections|[entrada, salida] Preasignado matriz de GUID que se va a rellenar.|  
|pdwSize|[in] El número máximo de GUID que se pueden almacenar en la `rgguidSections` matriz.|  
|pszAltRoot|[in] Una raíz del registro alternativo a usar. Establecido en `NULL` para utilizar el valor predeterminado.|  
  
## <a name="expression-evaluator-functions"></a>Funciones del evaluador de expresiones  
  
|Función|Descripción|  
|--------------|-----------------|  
|GetEEMetric|Recupera un valor de métrica del registro.|  
|SetEEMetric|Establece el valor de métrica especificado en el registro.|  
|RemoveEEMetric|Elimina la métrica especificada del registro.|  
|GetEEMetricFile|Obtiene un nombre de archivo de la métrica especificada y lo carga, devolver el contenido del archivo como una cadena.|  
  
## <a name="exception-functions"></a>Funciones de excepciones  
  
|Función|Descripción|  
|--------------|-----------------|  
|GetExceptionMetric|Recupera un valor de métrica del registro.|  
|SetExceptionMetric|Establece el valor de métrica especificado en el registro.|  
|RemoveExceptionMetric|Elimina la métrica especificada del registro.|  
|RemoveAllExceptionMetrics|Elimina todas las métricas de excepción del registro.|  
  
## <a name="symbol-provider-functions"></a>Funciones del proveedor de símbolos  
  
|Función|Descripción|  
|--------------|-----------------|  
|GetSPMetric|Recupera un valor de métrica del registro.|  
|SetSPMetric|Establece el valor de métrica especificado en el registro.|  
|RemoveSPMetric|Elimina la métrica especificada del registro.|  
  
## <a name="enumeration-functions"></a>Funciones de enumeración  
  
|Función|Descripción|  
|--------------|-----------------|  
|EnumMetricSections|Enumera todas las métricas para un tipo de métrica especificada.|  
|EnumDebugEngine|Enumera los motores de depuración registrados.|  
|EnumEEs|Enumera los evaluadores de expresión registrados.|  
|EnumExceptionMetrics|Enumera todas las métricas de excepción.|  
  
## <a name="metric-definitions"></a>Definiciones de métrica  
 Estas definiciones se pueden utilizar para los nombres de métrica predefinidos. Los nombres corresponden a las diversas claves de registro y nombres de los valores y se definen como cadenas de caracteres anchos todos: por ejemplo, `extern LPCWSTR metrictypeEngine`.  
  
|Tipos predefinidos de métricos|Descripción: La clave base para...|  
|-----------------------------|---------------------------------------|  
|metrictypeEngine|Todas las métricas de motor de depuración.|  
|metrictypePortSupplier|Todas las métricas de proveedor de puerto.|  
|metrictypeException|Todas las métricas de excepción.|  
|metricttypeEEExtension|Todas las extensiones de evaluador de expresiones.|  
  
|Propiedades del motor de depuración|Descripción|  
|-----------------------------|-----------------|  
|metricAddressBP|Establézcalo es distinto de cero para indicar la compatibilidad para puntos de interrupción de dirección.|  
|metricAlwaysLoadLocal|Establézcalo es distinto de cero con el fin de cargar siempre el motor de depuración localmente.|  
|metricLoadInDebuggeeSession|NO USADO|  
|metricLoadedByDebuggee|Establézcalo es distinto de cero para indicar que el motor de depuración siempre se cargará con o por el programa que se está depurando.|  
|metricAttach|Establézcalo es distinto de cero para indicar la compatibilidad para datos adjuntos a los programas existentes.|  
|metricCallStackBP|Establézcalo es distinto de cero para indicar la compatibilidad con los puntos de interrupción de la pila de llamadas.|  
|metricConditionalBP|Establézcalo es distinto de cero para indicar la compatibilidad para la configuración de puntos de interrupción condicionales.|  
|metricDataBP|Establézcalo es distinto de cero para indicar la compatibilidad para la configuración de puntos de interrupción en cambios en los datos.|  
|metricDisassembly|Establecer a es distinto de cero para indicar la compatibilidad para la producción de una lista de desensamblado.|  
|metricDumpWriting|Establézcalo es distinto de cero para indicar la compatibilidad para escribir (el volcado de memoria para un dispositivo de salida) de volcado de memoria.|  
|metricENC|Establecer a es distinto de cero para indicar la compatibilidad para editar y continuar. **Nota:** un motor de depuración personalizadas nunca debe establecer esto o siempre debe establecer en 0.|  
|metricExceptions|Establézcalo es distinto de cero para indicar la compatibilidad para las excepciones.|  
|metricFunctionBP|Establézcalo es distinto de cero para indicar la compatibilidad para puntos de interrupción con nombre (puntos de interrupción que interrumpir cuando se llama a un nombre de función determinado).|  
|metricHitCountBP|Establézcalo es distinto de cero para indicar la compatibilidad para la configuración de puntos de interrupción "punto de aciertos" (los puntos de interrupción que se desencadenan después de que se va a alcance a un número determinado de veces).|  
|metricJITDebug|Establecer a es distinto de cero para indicar la compatibilidad para la depuración de just-in-time (el depurador se inicia cuando se produce una excepción en un proceso en ejecución).|  
|metricMemory|NO USADO|  
|metricPortSupplier|Establezca el CLSID del proveedor del puerto si hay una está implementada.|  
|metricRegisters|NO USADO|  
|metricSetNextStatement|Establézcalo es distinto de cero para indicar la compatibilidad para establecer la siguiente instrucción (que omite la ejecución de instrucciones intermedias).|  
|metricSuspendThread|Establézcalo es distinto de cero para indicar la compatibilidad para suspender la ejecución del subproceso.|  
|metricWarnIfNoSymbols|Establézcalo es distinto de cero para indicar que se debe notificar al usuario si no hay ningún símbolo.|  
|metricProgramProvider|Establezca esta opción en el CLSID del proveedor de programa.|  
|metricAlwaysLoadProgramProviderLocal|Establezca esta propiedad a es distinto de cero para indicar que el proveedor de programa siempre se debe cargar localmente.|  
|metricEngineCanWatchProcess|Establezca este parámetro es distinto de cero para indicar que el motor de depuración inspeccionará para procesar los eventos en lugar del proveedor de programa.|  
|metricRemoteDebugging|Establezca este parámetro es distinto de cero para indicar la compatibilidad para la depuración remota.|  
|metricEncUseNativeBuilder|Establezca esta propiedad a es distinto de cero para indicar que la editar y continuar con el administrador deben usar encbuild.dll del motor de depuración al compilar para editar y continuar. **Nota:** un motor de depuración personalizadas nunca debe establecer esto o siempre debe establecer en 0.|  
|metricLoadUnderWOW64|Establezca esta propiedad en es distinto de cero para indicar que el motor de depuración se debe cargar en el proceso depurado en WOW cuando se depura un proceso de 64 bits; en caso contrario, el motor de depuración se cargará en el proceso de Visual Studio (que se ejecuta bajo WOW64).|  
|metricLoadProgramProviderUnderWOW64|Establezca esta propiedad en es distinto de cero para indicar que el proveedor de programa se debe cargar en el proceso de depuración al depurar un proceso de 64 bits en WOW; en caso contrario, se cargarán en el proceso de Visual Studio.|  
|metricStopOnExceptionCrossingManagedBoundary|Establezca este parámetro es distinto de cero para indicar que el proceso debe detenerse si se produce una excepción no controlada en los límites del código administrado y no administrado.|  
|metricAutoSelectPriority|Establezca una prioridad para la selección automática del motor de depuración (valores es igual a mayor prioridad).|  
|metricAutoSelectIncompatibleList|Clave del registro que contiene entradas que especifican los GUID para los motores de depuración que se pasará por alto en la selección automática. Estas entradas son un número (0, 1, 2 y así sucesivamente) con un GUID expresado como una cadena.|  
|metricIncompatibleList|Clave del registro que contiene entradas que especifican los GUID para los motores de depuración que no son compatibles con este motor de depuración.|  
|metricDisableJITOptimization|Establezca este parámetro es distinto de cero para indicar que se deben deshabilitar las optimizaciones de just-in-time (para código administrado) durante la depuración.|  
  
|Propiedades del evaluador de expresiones|Descripción|  
|-------------------------------------|-----------------|  
|metricEngine|Esto contiene el número de motores de depuración que admiten el evaluador de expresiones especificado.|  
|metricPreloadModules|Establezca este parámetro es distinto de cero para indicar que se deben cargar previamente módulos para cuando se inicia un evaluador de expresiones en un programa.|  
|metricThisObjectName|Establezca esta opción en el nombre del objeto "this".|  
  
|Propiedades de extensión del evaluador de expresiones|Descripción|  
|-----------------------------------------------|-----------------|  
|metricExtensionDll|Nombre de la dll que es compatible con esta extensión.|  
|metricExtensionRegistersSupported|Lista de registros que se admiten.|  
|metricExtensionRegistersEntryPoint|Punto de entrada para el acceso a los registros.|  
|metricExtensionTypesSupported|Lista de tipos compatibles.|  
|metricExtensionTypesEntryPoint|Punto de entrada para tener acceso a los tipos.|  
  
|Propiedades de puerto de proveedor|Descripción|  
|------------------------------|-----------------|  
|metricPortPickerCLSID|Identificador CLSID del selector de puerto (un cuadro de diálogo, el usuario puede usar para seleccionar los puertos y agregar puertos que debe utilizar para la depuración).|  
|metricDisallowUserEnteredPorts|Es distinto de cero si no se pueden agregar los puertos escrito por el usuario para el proveedor del puerto (Esto hace que el cuadro de diálogo Selector de puerto esencialmente de solo lectura).|  
|metricPidBase|El identificador del proceso base utilizado por el proveedor de puerto al asignar identificadores de proceso.|  
  
|Los tipos de almacén de SP predefinidos|Descripción|  
|-------------------------------|-----------------|  
|storetypeFile|Los símbolos se almacenan en un archivo independiente.|  
|storetypeMetadata|Los símbolos se almacenan como metadatos en un ensamblado.|  
  
|Propiedades de varios|Descripción|  
|------------------------------|-----------------|  
|metricShowNonUserCode|Establezca este parámetro es distinto de cero para mostrar código no es de usuario.|  
|metricJustMyCodeStepping|Establezca este parámetro es distinto de cero para indicar que la ejecución paso a paso pueden producirse solo en el código de usuario.|  
|metricCLSID|CLSID de un objeto de un tipo específico de métrica.|  
|metricName|Nombre descriptivo de un objeto de un tipo específico de métrica.|  
|metricLanguage|Nombre del idioma.|  
  
## <a name="registry-locations"></a>Ubicaciones del registro  
 Las métricas se leen y escritas en el registro, específicamente en el `VisualStudio` subclave.  
  
> [!NOTE]
>  La mayoría de los casos, las métricas se escribirá en la clave HKEY_LOCAL_MACHINE. Sin embargo, en ocasiones HKEY_CURRENT_USER será la clave de destino. Dbgmetric.lib controla las dos claves. Al obtener una métrica, busca HKEY_CURRENT_USER primero, a continuación, en HKEY_LOCAL_MACHINE. Cuando se está estableciendo una métrica, un parámetro especifica qué clave de nivel superior que se usará.  
  
 *[clave del registro]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[raíz versión]*\  
  
 *[raíz métrica]*\  
  
 *[tipo de métrica]*\  
  
 *[metric] = [valor de métrica]*  
  
 *[metric] = [valor de métrica]*  
  
 *[metric] = [valor de métrica]*  
  
|Marcador de posición|Descripción|  
|-----------------|-----------------|  
|*[clave del registro]*|`HKEY_CURRENT_USER` o `HKEY_LOCAL_MACHINE`.|  
|*[raíz versión]*|La versión de Visual Studio (por ejemplo, `7.0`, `7.1`, o `8.0`). Sin embargo, esta raíz también se puede modificar con el **/rootsuffix** cambie a **devenv.exe**. Para VSIP, este modificador es normalmente **Exp**, por lo que podría ser la raíz de la versión, por ejemplo, 8.0Exp.|  
|*[raíz métrica]*|Esto es `AD7Metrics` o `AD7Metrics(Debug)`, dependiendo de si se utiliza la versión de depuración de dbgmetric.lib. **Nota:** si no se utiliza dbgmetric.lib, esta convención de nomenclatura debe cumplir si tiene las diferencias entre debug y release versiones que deben reflejarse en el registro.|  
|*[tipo de métrica]*|El tipo de métrica se escriban: `Engine`, `ExpressionEvaluator`, `SymbolProvider`, etcetera. Éstos se definen como en dbgmetric.h como `metricTypeXXXX`, donde `XXXX` es el nombre de tipo específico.|  
|*[metric]*|El nombre de una entrada que se asignará un valor con el fin de establecer la métrica. En función de la organización real de las métricas en el tipo de métrica.|  
|*[valor de métrica]*|El valor asignado a la métrica. El tipo que del valor debe tener (cadena), números, etc. depende de la métrica.|  
  
> [!NOTE]
>  Todos los GUID se almacenan en el formato de `{GUID}`. Por ejemplo: `{123D150B-FA18-461C-B218-45B3E4589F9B}`.  
  
### <a name="debug-engines"></a>Motores de depuración  
 La siguiente es la organización de las métricas de motores de depuración en el registro. `Engine`es el nombre de tipo de métrica de un motor de depuración y corresponde a *[tipo de métrica]* en el subárbol del registro anterior.  
  
 `Engine`\  
  
 *[motor guid]*\  
  
 `CLSID` = *[guid de clase]*  
  
 *[metric] = [valor de métrica]*  
  
 *[metric] = [valor de métrica]*  
  
 *[metric] = [valor de métrica]*  
  
 `PortSupplier`\  
  
 `0` = *[guid de proveedor de puerto]*  
  
 `1` = *[guid de proveedor de puerto]*  
  
|Marcador de posición|Descripción|  
|-----------------|-----------------|  
|*[motor guid]*|El GUID del motor de depuración.|  
|*[guid de clase]*|El GUID de la clase que implementa este motor de depuración.|  
|*[guid de proveedor de puerto]*|El GUID del proveedor del puerto, si lo hay. Muchos motores de depuración utiliza el proveedor del puerto predeterminado y, por tanto, no especifican su propio proveedor. En este caso, la subclave `PortSupplier` estará ausente.|  
  
### <a name="port-suppliers"></a>Proveedores de puertos  
 La siguiente es la organización de las métricas del proveedor de puerto en el registro. `PortSupplier`es el nombre de tipo de métrica para un proveedor del puerto y se corresponde con *[tipo de métrica]*.  
  
 `PortSupplier`\  
  
 *[guid de proveedor de puerto]*\  
  
 `CLSID` = *[guid de clase]*  
  
 *[metric] = [valor de métrica]*  
  
 *[metric] = [valor de métrica]*  
  
|Marcador de posición|Descripción|  
|-----------------|-----------------|  
|*[guid de proveedor de puerto]*|El GUID del proveedor del puerto|  
|*[guid de clase]*|El GUID de la clase que implementa este proveedor de puerto|  
  
### <a name="symbol-providers"></a>Proveedores de símbolos  
 La siguiente es la organización de las métricas del proveedor de símbolos en el registro. `SymbolProvider`es el nombre de tipo de métrica para el proveedor de símbolos y corresponde a *[tipo de métrica]*.  
  
 `SymbolProvider`\  
  
 *[guid de proveedor de símbolos]*\  
  
 `file`\  
  
 `CLSID` = *[guid de clase]*  
  
 *[metric] = [valor de métrica]*  
  
 *[metric] = [valor de métrica]*  
  
 `metadata`\  
  
 `CLSID` = *[guid de clase]*  
  
 *[metric] = [valor de métrica]*  
  
 *[metric] = [valor de métrica]*  
  
|Marcador de posición|Descripción|  
|-----------------|-----------------|  
|*[guid de proveedor de símbolos]*|El GUID del proveedor de símbolos|  
|*[guid de clase]*|El GUID de la clase que implementa este proveedor de símbolos|  
  
### <a name="expression-evaluators"></a>Evaluadores de expresión  
 La siguiente es la organización de las métricas del evaluador de expresiones en el registro. `ExpressionEvaluator`es el nombre de tipo de métrica para el evaluador de expresiones y corresponde a *[tipo de métrica]*.  
  
> [!NOTE]
>  El tipo de métrica para `ExpressionEvaluator` no está definido en dbgmetric.h, ya que se supone que todos los cambios de métrica para evaluadores de expresión pasará a través de las funciones de métrica de evaluador de expresión adecuada (el diseño de la `ExpressionEvaluator` subclave es en cierto modo complicado, por lo que los detalles están ocultos en dbgmetric.lib).  
  
 `ExpressionEvaluator`\  
  
 *[guid de lenguaje]*\  
  
 *[guid de proveedor]*\  
  
 `CLSID` = *[guid de clase]*  
  
 *[metric] = [valor de métrica]*  
  
 *[metric] = [valor de métrica]*  
  
 `Engine`\  
  
 `0` = *[guid de motor de depuración]*  
  
 `1` = *[guid de motor de depuración]*  
  
|Marcador de posición|Descripción|  
|-----------------|-----------------|  
|*[guid de lenguaje]*|El GUID de un idioma|  
|*[guid de proveedor]*|El GUID de un proveedor|  
|*[guid de clase]*|El GUID de la clase que implementa este evaluador de expresiones|  
|*[guid de motor de depuración]*|El GUID de un motor de depuración que funciona este evaluador de expresiones con|  
  
### <a name="expression-evaluator-extensions"></a>Extensiones del evaluador de expresiones  
 La siguiente es la organización de las métricas de extensión del evaluador de expresiones en el registro. `EEExtensions`es el nombre de tipo de métrica para la expresión de extensiones de evaluador y corresponde a *[tipo de métrica]*.  
  
 `EEExtensions`\  
  
 *[guid de extensión]*\  
  
 *[metric] = [valor de métrica]*  
  
 *[metric] = [valor de métrica]*  
  
|Marcador de posición|Descripción|  
|-----------------|-----------------|  
|*[guid de extensión]*|El GUID de una extensión de evaluador de expresiones|  
  
### <a name="exceptions"></a>Excepciones  
 La siguiente es la organización de las métricas de excepciones en el registro. `Exception`es el nombre de tipo de métrica para las excepciones y corresponde a *[tipo de métrica]*.  
  
 `Exception`\  
  
 *[guid de motor de depuración]*\  
  
 *[tipos de excepción]*\  
  
 *[excepción]*\  
  
 *[metric] = [valor de métrica]*  
  
 *[metric] = [valor de métrica]*  
  
 *[excepción]*\  
  
 *[metric] = [valor de métrica]*  
  
 *[metric] = [valor de métrica]*  
  
|Marcador de posición|Descripción|  
|-----------------|-----------------|  
|*[guid de motor de depuración]*|El GUID de un motor de depuración que admite excepciones.|  
|*[tipos de excepción]*|Un título general para la subclave identifica la clase de excepciones que se pueden administrar. Nombres típicos son **las excepciones de C++**, **excepciones Win32**, **excepciones de Common Language Runtime**, y **comprobaciones en tiempo de ejecución nativas**. Estos nombres también se usan para identificar una clase determinada de excepción para el usuario.|  
|*[excepción]*|Un nombre para una excepción: por ejemplo, **_com_error** o **interrupción de Control**. Estos nombres también se usan para identificar una excepción determinada al usuario.|  
  
## <a name="requirements"></a>Requisitos  
 Estos archivos se encuentran en el [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] directorio de instalación de SDK (de forma predeterminada, *[unidad]*\Program SDK de Visual Studio 2010\\).  
  
 Encabezado: includes\dbgmetric.h  
  
 Biblioteca: libs\ad2de.lib, libs\dbgmetric.lib  
  
## <a name="see-also"></a>Vea también  
 [Referencia de API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)