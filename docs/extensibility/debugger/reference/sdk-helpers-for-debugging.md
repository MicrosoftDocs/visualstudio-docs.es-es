---
title: Ayudantes del SDK para la depuración de SDK Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9edb7c508fdea6736a71c0f70c0d2ff305d4a399
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713649"
---
# <a name="sdk-helpers-for-debugging"></a>Asistentes de SDK para la depuración
Estas funciones y declaraciones son funciones auxiliares globales para implementar motores de depuración, evaluadores de expresiones y proveedores de símbolos en C++.

> [!NOTE]
> No hay versiones administradas de estas funciones y declaraciones en este momento.

## <a name="overview"></a>Información general
 Para que Visual Studio use los motores de depuración, los evaluadores de expresiones y los proveedores de símbolos, deben estar registrados. Esto se hace estableciendo subclaves y entradas del Registro, también conocidas como "establecer métricas." Las siguientes funciones globales están diseñadas para facilitar el proceso de actualización de estas métricas. Consulte la sección Ubicaciones del Registro para averiguar el diseño de cada subclave del Registro que se actualiza mediante estas funciones.

## <a name="general-metric-functions"></a>Funciones métricas generales
 Estas son funciones generales utilizadas por los motores de depuración. Las funciones especializadas para evaluadores de expresiones y proveedores de símbolos se detallan más adelante.

### <a name="getmetric-method"></a>GetMetric Método
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
|pszMachine|[en] Nombre de una máquina posiblemente remota`NULL` cuyo registro se escribirá (significa máquina local).|
|pszType|[en] Uno de los tipos de métricas.|
|guidSection|[en] GUID de un motor, evaluador, excepción, etc. específicos. Esto especifica una subsección en un tipo de métrica para un elemento específico.|
|pszMetric|[en] La métrica que se va a obtener. Esto corresponde a un nombre de valor específico.|
|pdwValue|[en] La ubicación de almacenamiento del valor de la métrica. Hay varios sabores de GetMetric que pueden devolver un DWORD (como en este ejemplo), un BSTR, un GUID o una matriz de GUID.|
|pszAltRoot|[en] Una raíz de registro alternativa para usar. `NULL` Establézalo para usar el valor predeterminado.|

### <a name="setmetric-method"></a>SetMetric Método
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
|pszType|[en] Uno de los tipos de métricas.|
|guidSection|[en] GUID de un motor, evaluador, excepción, etc. específicos. Esto especifica una subsección en un tipo de métrica para un elemento específico.|
|pszMetric|[en] La métrica que se va a obtener. Esto corresponde a un nombre de valor específico.|
|dwValue|[en] La ubicación de almacenamiento del valor en la métrica. Hay varios sabores de SetMetric que pueden almacenar un DWORD (en este ejemplo), un BSTR, un GUID o una matriz de GUID.|
|fUserSpecific|[en] TRUESi la métrica es específica del usuario y si se debe escribir en el subárbol del usuario en lugar del subárbol del equipo local.|
|pszAltRoot|[en] Una raíz de registro alternativa para usar. `NULL` Establézalo para usar el valor predeterminado.|

### <a name="removemetric-method"></a>RemoveMetric Método
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
|pszType|[en] Uno de los tipos de métricas.|
|guidSection|[en] GUID de un motor, evaluador, excepción, etc. específicos. Esto especifica una subsección en un tipo de métrica para un elemento específico.|
|pszMetric|[en] La métrica que se va a quitar. Esto corresponde a un nombre de valor específico.|
|pszAltRoot|[en] Una raíz de registro alternativa para usar. `NULL` Establézalo para usar el valor predeterminado.|

### <a name="enummetricsections-method"></a>Método EnumMetricSections
 Enumera las distintas secciones de métricas del registro.

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
|pszMachine|[en] Nombre de una máquina posiblemente remota`NULL` cuyo registro se escribirá (significa máquina local).|
|pszType|[en] Uno de los tipos de métricas.|
|rgguidSections|[adentro, fuera] Matriz preasignada de GUID que se van a rellenar.|
|pdwSize|[en] El número máximo de GUID que se `rgguidSections` pueden almacenar en la matriz.|
|pszAltRoot|[en] Una raíz de registro alternativa para usar. `NULL` Establézalo para usar el valor predeterminado.|

## <a name="expression-evaluator-functions"></a>Funciones del evaluador de expresiones

|Función|Descripción|
|--------------|-----------------|
|GetEEMetric|Recupera un valor de métrica del registro.|
|SetEEMetric|Establece el valor de métrica especificado en el registro.|
|RemoveEEMetric|Quita la métrica especificada del registro.|
|GetEEMetricFile|Obtiene un nombre de archivo de la métrica especificada y lo carga, devolviendo el contenido del archivo como una cadena.|

## <a name="exception-functions"></a>Funciones de excepción

|Función|Descripción|
|--------------|-----------------|
|GetExceptionMetric|Recupera un valor de métrica del registro.|
|SetExceptionMetric|Establece el valor de métrica especificado en el registro.|
|RemoveExceptionMetric|Quita la métrica especificada del registro.|
|RemoveAllExceptionMetrics|Quita todas las métricas de excepción del registro.|

## <a name="symbol-provider-functions"></a>Funciones del proveedor de símbolos

|Función|Descripción|
|--------------|-----------------|
|GetSPMetric|Recupera un valor de métrica del registro.|
|SetSPMetric|Establece el valor de métrica especificado en el registro.|
|RemoveSPMetric|Quita la métrica especificada del registro.|

## <a name="enumeration-functions"></a>Funciones de enumeración

|Función|Descripción|
|--------------|-----------------|
|EnumMetricSections|Enumera todas las métricas de un tipo de métrica especificado.|
|EnumDebugEngine|Enumera los motores de depuración registrados.|
|EnumEEs|Enumera los evaluadores de expresiones registradas.|
|EnumExceptionMetrics|Enumera todas las métricas de excepción.|

## <a name="metric-definitions"></a>Definiciones de métricas
 Estas definiciones se pueden utilizar para nombres de métricas predefinidos. Los nombres corresponden a varias claves del Registro y nombres de `extern LPCWSTR metrictypeEngine`valor y se definen como cadenas de caracteres anchos: por ejemplo, .

|Tipos de métricas predefinidos|Descripción: La clave base para....|
|-----------------------------|---------------------------------------|
|metrictypeEngine|Todas las métricas del motor de depuración.|
|metrictypePortSupplier|Todas las métricas del proveedor de puertos.|
|metrictypeException|Todas las métricas de excepción.|
|metricttypeEEExtension|Todas las extensiones del evaluador de expresiones.|

|Propiedades del motor de depuración|Descripción|
|-----------------------------|-----------------|
|metricAddressBP|Establézcalo en distinto de cero para indicar la compatibilidad con los puntos de interrupción de direcciones.|
|metricAlwaysLoadLocal|Fije al distinto cero para cargar siempre el motor del debug localmente.|
|metricLoadInDebuggeeSession|NO UTILIZADO|
|metricLoadedByDebuggee|Se establece en distinto de cero para indicar que el motor de depuración siempre se cargará con o por el programa que se está depurando.|
|metricAttach|Establézcalo en distinto de cero para indicar la compatibilidad con los datos adjuntos a programas existentes.|
|metricCallStackBP|Establezca en distinto de cero para indicar la compatibilidad con los puntos de interrupción de la pila de llamadas.|
|metricConditionalBP|Establézcalo en distinto de cero para indicar la compatibilidad con la configuración de puntos de interrupción condicionales.|
|metricDataBP|Establézcalo en distinto de cero para indicar la compatibilidad con la configuración de puntos de interrupción en los cambios en los datos.|
|metricDesassembly|Establézcalo en distinto de cero para indicar la compatibilidad con la producción de una lista de desensamblados.|
|metricDumpWriting|Establézcalo en distinto de cero para indicar la compatibilidad con la escritura de volcado (el volcado de memoria en un dispositivo de salida).|
|metricENC|Establézcalo en distinto de cero para indicar la compatibilidad con Editar y continuar. **Nota:**  Un motor de depuración personalizado nunca debe establecer esto o siempre debe establecerlo en 0.|
|metricExceptions|Establézcalo en distinto de cero para indicar la compatibilidad con excepciones.|
|metricFunctionBP|Se establece en distinto de cero para indicar la compatibilidad con puntos de interrupción con nombre (puntos de interrupción que se interrumpen cuando se llama a un determinado nombre de función).|
|metricHitCountBP|Establézcalo en distinto de cero para indicar la compatibilidad con la configuración de puntos de interrupción de "punto de impacto" (puntos de interrupción que se activan solo después de alcanzarun cierto número de veces).|
|metricJITDebug|Se establece en distinto de cero para indicar la compatibilidad con la depuración Just-In-Time (el depurador se inicia cuando se produce una excepción en un proceso en ejecución).|
|metricMemory|NO UTILIZADO|
|metricPortSupplier|Establezca esto en el CLSID del proveedor de puertos si se implementa uno.|
|metricRegisters|NO UTILIZADO|
|metricSetNextStatement|Se establece en distinto de cero para indicar la compatibilidad con la configuración de la siguiente instrucción (que omite la ejecución de instrucciones intermedias).|
|metricSuspendThread|Establézcalo en distinto de cero para indicar la compatibilidad con la suspensión de la ejecución de subprocesos.|
|metricWarnIfNoSymbols|Establézcalo en distinto de cero para indicar que se debe notificar al usuario si no hay símbolos.|
|metricProgramProvider|Establezca esta configuración en el CLSID del proveedor del programa.|
|metricAlwaysLoadProgramProviderLocal|Establezca esta configuración en distinto de cero para indicar que el proveedor del programa siempre debe cargarse localmente.|
|metricEngineCanWatchProcess|Establezca esta opción en distinto de cero para indicar que el motor de depuración buscará eventos de proceso en lugar del proveedor de programa.|
|metricRemoteDebugging|Establezca esta configuración en distinto de cero para indicar la compatibilidad con la depuración remota.|
|metricEncUseNativeBuilder|Establezca este en distinto de cero para indicar que el Administrador de edición y continuación debe usar encbuild.dll del motor de depuración para compilar para Editar y continuar. **Nota:**  Un motor de depuración personalizado nunca debe establecer esto o siempre debe establecerlo en 0.|
|metricLoadUnderWOW64|Establezca esto en distinto de cero para indicar que el motor de depuración se debe cargar en el proceso de depuración bajo WOW al depurar un proceso de 64 bits; de lo contrario, el motor de depuración se cargará en el proceso de Visual Studio (que se ejecuta en WOW64).|
|metricLoadProgramProviderUnderWOW64|Establezca esto en distinto de cero para indicar que el proveedor de programa debe cargarse en el proceso de depuración al depurar un proceso de 64 bits en WOW; de lo contrario, se cargará en el proceso de Visual Studio.|
|metricStopOnExceptionCrossingManagedBoundary|Establezca este en distinto de cero para indicar que el proceso debe detenerse si se produce una excepción no controlada a través de los límites de código administrado o no administrado.|
|metricAutoSelectPriority|Establezca esto en una prioridad para la selección automática del motor de depuración (los valores más altos son iguales a la prioridad más alta).|
|metricAutoSelectIncompatibleList|Clave del Registro que contiene entradas que especifican GUID para los motores de depuración que se omitirán en la selección automática. Estas entradas son un número (0, 1, 2, etc.) con un GUID expresado como una cadena.|
|metricIncompatibleList|Clave del Registro que contiene entradas que especifican GUID para motores de depuración incompatibles con este motor de depuración.|
|metricDisableJITOptimization|Establezca esta configuración en distinto de cero para indicar que las optimizaciones Just-In-Time (para código administrado) deben deshabilitarse durante la depuración.|

|Propiedades del evaluador de expresiones|Descripción|
|-------------------------------------|-----------------|
|metricEngine|Esto contiene el número de motores de depuración que admiten el evaluador de expresiones especificado.|
|metricPreloadModules|Establezca esta configuración en distinto de cero para indicar que los módulos deben precargarse cuando se inicia un evaluador de expresiones en un programa.|
|metricThisObjectName|Establezca esta configuración en el nombre del objeto "this".|

|Propiedades de extensión del evaluador de expresiones|Descripción|
| - |-----------------|
|metricExtensionDll|Nombre del archivo dll que abre esta extensión.|
|metricExtensionRegistersSupported|Lista de registros admitidos.|
|metricExtensionRegistersEntryPoint|Punto de entrada para acceder a los registros.|
|metricExtensionTypesSupported|Lista de tipos admitidos.|
|metricExtensionTypesEntryPoint|Punto de entrada para acceder a tipos.|

|Propiedades del proveedor de puertos|Descripción|
|------------------------------|-----------------|
|metricPortPickerCLSID|El CLSID del selector de puertos (un cuadro de diálogo que el usuario puede usar para seleccionar puertos y agregar puertos para usar los de depuración).|
|metricDisallowUserEnteredPorts|Distinto de cero si los puertos introducidos por el usuario no se pueden agregar al proveedor de puertos (esto hace que el cuadro de diálogo del selector de puertos sea esencialmente de solo lectura).|
|metricPidBase|El ID de proceso base utilizado por el proveedor de puertos al asignar identificadores de proceso.|

|Tipos de almacén de SP predefinidos|Descripción|
|-------------------------------|-----------------|
|storetypeFile|Los símbolos se almacenan en un archivo independiente.|
|storetypeMetadata|Los símbolos se almacenan como metadatos en un ensamblado.|

|Propiedades diversas|Descripción|
|------------------------------|-----------------|
|metricShowNonUserCode|Establezca esta configuración en distinto de cero para mostrar código que no sea de usuario.|
|metricJustMyCodeStepping|Establezca esta opción en distinto de cero para indicar que el paso solo puede producirse en el código de usuario.|
|metricCLSID|CLSID para un objeto de un tipo de métrica específico.|
|metricName|Nombre fácil de usar para un objeto de un tipo de métrica específico.|
|metricLanguage|Nombre del idioma.|

## <a name="registry-locations"></a>Ubicaciones del Registro
 Las métricas se leen y escriben en `VisualStudio` el registro, específicamente en la subclave.

> [!NOTE]
> La mayoría de las veces, las métricas se escribirán en la clave de HKEY_LOCAL_MACHINE. Sin embargo, a veces HKEY_CURRENT_USER será la clave de destino. Dbgmetric.lib controla ambas claves. Al obtener una métrica, primero HKEY_CURRENT_USER busca y, a continuación, HKEY_LOCAL_MACHINE. Cuando se establece una métrica, un parámetro especifica qué clave de nivel superior se va a utilizar.

 *[clave de registro]*\

 `Software`\

 `Microsoft`\

 `VisualStudio`\

 *[raíz de versión]*\

 *[raíz métrica]*\

 *[tipo métrico]*\

 *[métrica] á [valor métrico]*

 *[métrica] á [valor métrico]*

 *[métrica] á [valor métrico]*

|Marcador de posición|Descripción|
|-----------------|-----------------|
|*[clave de registro]*|`HKEY_CURRENT_USER` o `HKEY_LOCAL_MACHINE`.|
|*[raíz de versión]*|La versión de Visual `7.0`Studio `7.1`(por ejemplo, , , o `8.0`). Sin embargo, esta raíz también se puede modificar mediante el modificador **/rootsuffix** a **devenv.exe**. Para VSIP, este modificador suele ser **Exp**, por lo que la raíz de la versión sería, por ejemplo, 8.0Exp.|
|*[raíz métrica]*|Esto es `AD7Metrics` `AD7Metrics(Debug)`o , dependiendo de si se utiliza la versión de depuración de dbgmetric.lib. **Nota:**  Si se utiliza o no dbgmetric.lib, esta convención de nomenclatura debe cumplirse si tiene diferencias entre las versiones de depuración y versión que deben reflejarse en el registro.|
|*[tipo métrico]*|El tipo de métrica `Engine`que `ExpressionEvaluator` `SymbolProvider`se va a escribir: , , , etc. Todos ellos se definen como `metricTypeXXXX`en `XXXX` dbgmetric.h como , donde está el nombre de tipo específico.|
|*[métrica]*|El nombre de una entrada que se asignará un valor para fijar la métrica. La organización real de las métricas depende del tipo de métrica.|
|*[valor métrico]*|El valor asignado a la métrica. El tipo que debe tener el valor (cadena, número, etc.) depende de la métrica.|

> [!NOTE]
> Todos los GUID se almacenan `{GUID}`en el formato de . Por ejemplo, `{123D150B-FA18-461C-B218-45B3E4589F9B}`.

### <a name="debug-engines"></a>Motores de depuración
 A continuación se muestra la organización de las métricas de motores de depuración en el registro. `Engine`es el nombre de tipo de métrica para un motor de depuración y corresponde a *[tipo de métrica]* en el subárbol del registro anterior.

 `Engine`\

 *[guía del motor]*\

 `CLSID` = *[guía de clase]*

 *[métrica] á [valor métrico]*

 *[métrica] á [valor métrico]*

 *[métrica] á [valor métrico]*

 `PortSupplier`\

 `0` = *[guía del proveedor del puerto]*

 `1` = *[guía del proveedor del puerto]*

|Marcador de posición|Descripción|
|-----------------|-----------------|
|*[guía del motor]*|Guid del motor de depuración.|
|*[guía de clase]*|GUID de la clase que implementa este motor de depuración.|
|*[guía del proveedor del puerto]*|El GUID del proveedor de puertos, si existe. Muchos motores de depuración utilizan el proveedor de puerto predeterminado y, por lo tanto, no especifican su propio proveedor. En este caso, `PortSupplier` la subclave estará ausente.|

### <a name="port-suppliers"></a>Proveedores de puertos
 A continuación se muestra la organización de las métricas del proveedor de puertos en el registro. `PortSupplier`es el nombre de tipo de métrica para un proveedor de puertos y corresponde a *[tipo de métrica].*

 `PortSupplier`\

 *[guía del proveedor del puerto]*\

 `CLSID` = *[guía de clase]*

 *[métrica] á [valor métrico]*

 *[métrica] á [valor métrico]*

|Marcador de posición|Descripción|
|-----------------|-----------------|
|*[guía del proveedor del puerto]*|El GUID del proveedor portuario|
|*[guía de clase]*|El GUID de la clase que implementa este proveedor de puertos|

### <a name="symbol-providers"></a>Proveedores de símbolos
 A continuación se muestra la organización de las métricas del proveedor de símbolos en el registro. `SymbolProvider`es el nombre de tipo de métrica para el proveedor de símbolos y corresponde a *[tipo de métrica].*

 `SymbolProvider`\

 *[guid del proveedor de símbolos]*\

 `file`\

 `CLSID` = *[guía de clase]*

 *[métrica] á [valor métrico]*

 *[métrica] á [valor métrico]*

 `metadata`\

 `CLSID` = *[guía de clase]*

 *[métrica] á [valor métrico]*

 *[métrica] á [valor métrico]*

|Marcador de posición|Descripción|
|-----------------|-----------------|
|*[guid del proveedor de símbolos]*|El GUID del proveedor de símbolos|
|*[guía de clase]*|GUID de la clase que implementa este proveedor de símbolos|

### <a name="expression-evaluators"></a>Evaluadores de expresiones
 A continuación se muestra la organización de las métricas del evaluador de expresiones en el registro. `ExpressionEvaluator`es el nombre de tipo de métrica para el evaluador de expresiones y corresponde a *[tipo de métrica].*

> [!NOTE]
> El tipo `ExpressionEvaluator` de métrica para no está definido en dbgmetric.h, ya que se supone que todos los cambios `ExpressionEvaluator` de métricas para los evaluadores de expresiones pasarán por las funciones de métricas del evaluador de expresiones adecuadas (el diseño de la subclave es algo complicado, por lo que los detalles se ocultan dentro de dbgmetric.lib).

 `ExpressionEvaluator`\

 *[guía del idioma]*\

 *[guía del proveedor]*\

 `CLSID` = *[guía de clase]*

 *[métrica] á [valor métrico]*

 *[métrica] á [valor métrico]*

 `Engine`\

 `0` = *[guid del motor de depuración]*

 `1` = *[guid del motor de depuración]*

|Marcador de posición|Descripción|
|-----------------|-----------------|
|*[guía del idioma]*|El GUID de un idioma|
|*[guía del proveedor]*|El GUID de un proveedor|
|*[guía de clase]*|Guid de la clase que implementa este evaluador de expresiones|
|*[guid del motor de depuración]*|El GUID de un motor de depuración con el que trabaja este evaluador de expresiones|

### <a name="expression-evaluator-extensions"></a>Extensiones del evaluador de expresiones
 A continuación se muestra la organización de las métricas de extensión del evaluador de expresiones en el registro. `EEExtensions`es el nombre de tipo de métrica para las extensiones del evaluador de expresiones y corresponde a *[tipo de métrica].*

 `EEExtensions`\

 *[guid de extensión]*\

 *[métrica] á [valor métrico]*

 *[métrica] á [valor métrico]*

|Marcador de posición|Descripción|
|-----------------|-----------------|
|*[guid de extensión]*|El GUID de una extensión del evaluador de expresiones|

### <a name="exceptions"></a>Excepciones
 A continuación se muestra la organización de las métricas de excepciones en el registro. `Exception`es el nombre de tipo de métrica para las excepciones y corresponde a *[tipo de métrica].*

 `Exception`\

 *[guid del motor de depuración]*\

 *[tipos de excepción]*\

 *[excepción]*\

 *[métrica] á [valor métrico]*

 *[métrica] á [valor métrico]*

 *[excepción]*\

 *[métrica] á [valor métrico]*

 *[métrica] á [valor métrico]*

|Marcador de posición|Descripción|
|-----------------|-----------------|
|*[guid del motor de depuración]*|GUID de un motor de depuración que admite excepciones.|
|*[tipos de excepción]*|Un título general para la subclave que identifica la clase de excepciones que se pueden controlar. Los nombres típicos son **C++ Exceptions**, **Win32 Exceptions**, **Common Language Runtime Exceptions**y **Native Run-Time Checks**. Estos nombres también se utilizan para identificar una clase determinada de excepción para el usuario.|
|*[excepción]*|Un nombre para una excepción: por ejemplo, **_com_error** o **Control-Break**. Estos nombres también se utilizan para identificar una excepción determinada al usuario.|

## <a name="requirements"></a>Requisitos
 Estos archivos se [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] encuentran en el directorio de instalación del SDK (de forma predeterminada, *[unidad]*.\\

 Encabezado: includes-dbgmetric.h

 Biblioteca: libs-ad2de.lib, libs-dbgmetric.lib

## <a name="see-also"></a>Vea también
- [Referencia de API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
