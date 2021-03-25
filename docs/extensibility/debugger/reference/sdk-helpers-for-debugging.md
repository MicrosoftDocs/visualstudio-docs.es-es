---
title: Aplicaciones auxiliares de SDK para la depuración | Microsoft Docs
description: Obtenga información sobre las funciones y declaraciones que son funciones auxiliares globales para implementar motores de depuración, evaluadores de expresiones y proveedores de símbolos en C++.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4f5a34513130ea112393ffbb4935093bcea6e797
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061542"
---
# <a name="sdk-helpers-for-debugging"></a>Asistentes de SDK para la depuración
Estas funciones y declaraciones son funciones auxiliares globales para implementar motores de depuración, evaluadores de expresiones y proveedores de símbolos en C++.

> [!NOTE]
> En este momento no hay versiones administradas de estas funciones y declaraciones.

## <a name="overview"></a>Información general
 Para que Visual Studio use los motores de depuración, los evaluadores de expresiones y los proveedores de símbolos, se deben registrar. Esto se hace mediante la configuración de las subclaves del registro y las entradas, también conocidas como "establecer métricas". Las siguientes funciones globales están diseñadas para facilitar el proceso de actualización de estas métricas. Vea la sección sobre ubicaciones del registro para averiguar el diseño de cada subclave del registro que se actualiza mediante estas funciones.

## <a name="general-metric-functions"></a>Funciones de métricas generales
 Se trata de funciones generales utilizadas por los motores de depuración. Las funciones especializadas para los evaluadores de expresiones y los proveedores de símbolos se detallan más adelante.

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
|pszMachine|de Nombre de un equipo posiblemente remoto cuyo registro se escribirá (es `NULL` decir, equipo local).|
|pszType|de Uno de los tipos de métricas.|
|guidSection|de GUID de un motor específico, evaluador, excepción, etc. Esto especifica una subsección bajo un tipo de métrica para un elemento específico.|
|pszMetric|de Métrica que se va a obtener. Esto corresponde a un nombre de valor específico.|
|pdwValue|de Ubicación de almacenamiento del valor de la métrica. Hay varias versiones de GetMetric que pueden devolver un valor DWORD (como en este ejemplo), un BSTR, un GUID o una matriz de GUID.|
|pszAltRoot|de Raíz del registro alternativa que se va a usar. Establezca en `NULL` para usar el valor predeterminado.|

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
|pszType|de Uno de los tipos de métricas.|
|guidSection|de GUID de un motor específico, evaluador, excepción, etc. Esto especifica una subsección bajo un tipo de métrica para un elemento específico.|
|pszMetric|de Métrica que se va a obtener. Esto corresponde a un nombre de valor específico.|
|dwValue|de Ubicación de almacenamiento del valor de la métrica. Hay varias versiones de SetMetric que pueden almacenar un valor DWORD (en este ejemplo), un BSTR, un GUID o una matriz de GUID.|
|fUserSpecific|de TRUE si la métrica es específica del usuario y si se debe escribir en el subárbol del usuario en lugar de en el subárbol del equipo local.|
|pszAltRoot|de Raíz del registro alternativa que se va a usar. Establezca en `NULL` para usar el valor predeterminado.|

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
|pszType|de Uno de los tipos de métricas.|
|guidSection|de GUID de un motor específico, evaluador, excepción, etc. Esto especifica una subsección bajo un tipo de métrica para un elemento específico.|
|pszMetric|de Métrica que se va a quitar. Esto corresponde a un nombre de valor específico.|
|pszAltRoot|de Raíz del registro alternativa que se va a usar. Establezca en `NULL` para usar el valor predeterminado.|

### <a name="enummetricsections-method"></a>Método EnumMetricSections
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
|pszMachine|de Nombre de un equipo posiblemente remoto cuyo registro se escribirá (es `NULL` decir, equipo local).|
|pszType|de Uno de los tipos de métricas.|
|rgguidSections|[in, out] Matriz de GUID preasignada que se va a rellenar.|
|pdwSize|de Número máximo de GUID que se pueden almacenar en la `rgguidSections` matriz.|
|pszAltRoot|de Raíz del registro alternativa que se va a usar. Establezca en `NULL` para usar el valor predeterminado.|

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

## <a name="symbol-provider-functions"></a>Funciones de proveedor de símbolos

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
|EnumEEs|Enumera los evaluadores de expresiones registrados.|
|EnumExceptionMetrics|Enumera todas las métricas de excepción.|

## <a name="metric-definitions"></a>Definiciones de métricas
 Estas definiciones se pueden usar para nombres de métricas predefinidos. Los nombres corresponden a varias claves del registro y nombres de valor y se definen como cadenas de caracteres anchos: por ejemplo, `extern LPCWSTR metrictypeEngine` .

|Tipos de métricas predefinidos|Descripción: la clave base para....|
|-----------------------------|---------------------------------------|
|metrictypeEngine|Todas las métricas del motor de depuración.|
|metrictypePortSupplier|Todas las métricas de los proveedores de puertos.|
|metrictypeException|Todas las métricas de excepciones.|
|metricttypeEEExtension|Todas las extensiones del evaluador de expresiones.|

|Propiedades del motor de depuración|Descripción|
|-----------------------------|-----------------|
|metricAddressBP|Se establece en un valor distinto de cero para indicar la compatibilidad con puntos de interrupción de direcciones.|
|metricAlwaysLoadLocal|Se establece en un valor distinto de cero para cargar siempre el motor de depuración localmente.|
|metricLoadInDebuggeeSession|NO SE USA|
|metricLoadedByDebuggee|Se establece en un valor distinto de cero para indicar que el motor de depuración siempre se cargará con o por el programa que se está depurando.|
|metricAttach|Se establece en un valor distinto de cero para indicar la compatibilidad con datos adjuntos a programas existentes.|
|metricCallStackBP|Se establece en un valor distinto de cero para indicar la compatibilidad con los puntos de interrupción de la pila de llamadas.|
|metricConditionalBP|Se establece en un valor distinto de cero para indicar la compatibilidad con la configuración de puntos de interrupción condicionales.|
|metricDataBP|Se establece en un valor distinto de cero para indicar la compatibilidad con la configuración de puntos de interrupción en los cambios en los datos.|
|metricDisassembly|Se establece en un valor distinto de cero para indicar la compatibilidad con la producción de una lista desensamblado.|
|metricDumpWriting|Se establece en un valor distinto de cero para indicar la compatibilidad con la escritura de volcado (el volcado de memoria en un dispositivo de salida).|
|metricENC|Se establece en un valor distinto de cero para indicar la compatibilidad con editar y continuar. **Nota:**  Un motor de depuración personalizado nunca debe establecerlo o debe establecerlo en 0.|
|metricExceptions|Se establece en un valor distinto de cero para indicar la compatibilidad con las excepciones.|
|metricFunctionBP|Se establece en un valor distinto de cero para indicar la compatibilidad con puntos de interrupción con nombre (puntos de interrupción que se interrumpen cuando se llama a un determinado nombre de función).|
|metricHitCountBP|Se establece en un valor distinto de cero para indicar la compatibilidad con la configuración de los puntos de interrupción de "punto de acierto" (puntos de interrupción que solo se desencadenan después de alcanzar un número determinado de veces).|
|metricJITDebug|Se establece en un valor distinto de cero para indicar la compatibilidad con la depuración Just-in-Time (el depurador se inicia cuando se produce una excepción en un proceso en ejecución).|
|metricMemory|NO SE USA|
|metricPortSupplier|Establézcalo en el CLSID del proveedor del puerto si se implementa uno.|
|metricRegisters|NO SE USA|
|metricSetNextStatement|Se establece en un valor distinto de cero para indicar la compatibilidad con la configuración de la siguiente instrucción (que omite la ejecución de instrucciones intermedias).|
|metricSuspendThread|Se establece en un valor distinto de cero para indicar la compatibilidad para suspender la ejecución de subprocesos.|
|metricWarnIfNoSymbols|Se establece en un valor distinto de cero para indicar que se debe notificar al usuario si no hay símbolos.|
|metricProgramProvider|Establézcalo en el CLSID del proveedor de programas.|
|metricAlwaysLoadProgramProviderLocal|Establézcalo en distinto de cero para indicar que el proveedor de programas siempre debe cargarse localmente.|
|metricEngineCanWatchProcess|Establezca este valor en un valor distinto de cero para indicar que el motor de depuración inspeccionará los eventos de proceso en lugar del proveedor de programas.|
|metricRemoteDebugging|Establezca este valor en un valor distinto de cero para indicar la compatibilidad con la depuración remota.|
|metricEncUseNativeBuilder|Establézcalo en distinto de cero para indicar que el administrador de edición y continuación debe utilizar el encbuild.dll del motor de depuración para compilar para editar y continuar. **Nota:**  Un motor de depuración personalizado nunca debe establecerlo o debe establecerlo en 0.|
|metricLoadUnderWOW64|Establezca este valor en un valor distinto de cero para indicar que el motor de depuración debe cargarse en el proceso de depuración bajo WOW al depurar un proceso de 64 bits; de lo contrario, el motor de depuración se cargará en el proceso de Visual Studio (que se ejecuta bajo WOW64).|
|metricLoadProgramProviderUnderWOW64|Establezca este valor en un valor distinto de cero para indicar que el proveedor de programas debe cargarse en el proceso de depuración al depurar un proceso de 64 bits en WOW. de lo contrario, se cargará en el proceso de Visual Studio.|
|metricStopOnExceptionCrossingManagedBoundary|Establézcalo en distinto de cero para indicar que el proceso debe detenerse si se produce una excepción no controlada a través de los límites de código administrado o no administrado.|
|metricAutoSelectPriority|Establezca esta opción en prioridad para la selección automática del motor de depuración (los valores superiores son iguales a la prioridad más alta).|
|metricAutoSelectIncompatibleList|Clave del registro que contiene entradas que especifican los GUID de los motores de depuración que se van a omitir en la selección automática. Estas entradas son un número (0, 1, 2, etc.) con un GUID expresado como una cadena.|
|metricIncompatibleList|Clave del registro que contiene entradas que especifican los GUID de los motores de depuración que no son compatibles con este motor de depuración.|
|metricDisableJITOptimization|Establezca este valor en un valor distinto de cero para indicar que las optimizaciones Just-in-Time (para código administrado) deben deshabilitarse durante la depuración.|

|Propiedades del evaluador de expresiones|Descripción|
|-------------------------------------|-----------------|
|metricEngine|Contiene el número de motores de depuración que admiten el evaluador de expresiones especificado.|
|metricPreloadModules|Establezca este valor en un valor distinto de cero para indicar que los módulos se deben cargar previamente cuando se inicia un evaluador de expresiones en un programa.|
|metricThisObjectName|Establézcalo en el nombre de objeto "this".|

|Propiedades de la extensión del evaluador de expresiones|Descripción|
| - |-----------------|
|metricExtensionDll|Nombre del archivo DLL que admite esta extensión.|
|metricExtensionRegistersSupported|Lista de registros admitidos.|
|metricExtensionRegistersEntryPoint|Punto de entrada para acceder a los registros.|
|metricExtensionTypesSupported|Lista de tipos admitidos.|
|metricExtensionTypesEntryPoint|Punto de entrada para obtener acceso a los tipos.|

|Propiedades del proveedor del puerto|Descripción|
|------------------------------|-----------------|
|metricPortPickerCLSID|CLSID del selector de puertos (un cuadro de diálogo que el usuario puede usar para seleccionar puertos y agregar puertos para su depuración).|
|metricDisallowUserEnteredPorts|Distinto de cero si los puertos especificados por el usuario no se pueden agregar al proveedor del puerto (esto hace que el cuadro de diálogo del selector de Puerto sea esencialmente de solo lectura).|
|metricPidBase|IDENTIFICADOR de proceso base utilizado por el proveedor del puerto al asignar los ID. de proceso.|

|Tipos de almacén de SP predefinidos|Descripción|
|-------------------------------|-----------------|
|storetypeFile|Los símbolos se almacenan en un archivo independiente.|
|storetypeMetadata|Los símbolos se almacenan como metadatos en un ensamblado.|

|Propiedades varias|Descripción|
|------------------------------|-----------------|
|metricShowNonUserCode|Establézcalo en distinto de cero para mostrar el código que no es de usuario.|
|metricJustMyCodeStepping|Establezca este valor en un valor distinto de cero para indicar que la ejecución paso a paso solo puede producirse en el código de usuario.|
|metricCLSID|CLSID de un objeto de un tipo de métrica específico.|
|metricName|Nombre descriptivo de un objeto de un tipo de métrica específico.|
|metricLanguage|Nombre del idioma.|

## <a name="registry-locations"></a>Ubicaciones del registro
 Las métricas se leen y se escriben en el registro, específicamente en la `VisualStudio` subclave.

> [!NOTE]
> La mayoría de las veces, las métricas se escribirán en la clave de HKEY_LOCAL_MACHINE. Sin embargo, a veces HKEY_CURRENT_USER será la clave de destino. Dbgmetric. lib controla ambas claves. Al obtener una métrica, busca primero HKEY_CURRENT_USER y, a continuación, HKEY_LOCAL_MACHINE. Cuando se establece una métrica, un parámetro especifica la clave de nivel superior que se va a usar.

 *[clave del registro]*\

 `Software`\

 `Microsoft`\

 `VisualStudio`\

 *[raíz de la versión]*\

 *[raíz métrica]*\

 *[tipo de métrica]*\

 *[Metric] = [valor de métrica]*

 *[Metric] = [valor de métrica]*

 *[Metric] = [valor de métrica]*

|Marcador de posición|Descripción|
|-----------------|-----------------|
|*[clave del registro]*|`HKEY_CURRENT_USER` o `HKEY_LOCAL_MACHINE`.|
|*[raíz de la versión]*|La versión de Visual Studio (por ejemplo, `7.0` , `7.1` o `8.0` ). Sin embargo, esta raíz también se puede modificar mediante el modificador **/rootsuffix** para **devenv.exe**. En el caso de VSIP, este modificador suele ser **exp**, por lo que la raíz de la versión sería, por ejemplo, 8.0 exp.|
|*[raíz métrica]*|Es `AD7Metrics` o `AD7Metrics(Debug)` , dependiendo de si se usa la versión de depuración de dbgmetric. lib. **Nota:**  Tanto si se usa dbgmetric. lib como si no, se debe cumplir esta Convención de nomenclatura si tiene diferencias entre las versiones de depuración y de lanzamiento que se deben reflejar en el registro.|
|*[tipo de métrica]*|Tipo de métrica que se va a escribir: `Engine` , `ExpressionEvaluator` , `SymbolProvider` , etc. Todos se definen como en dbgmetric. h como `metricTypeXXXX` , donde `XXXX` es el nombre de tipo específico.|
|*métrica*|El nombre de una entrada a la que se va a asignar un valor para establecer la métrica. La organización real de las métricas depende del tipo de métrica.|
|*[valor de métrica]*|Valor asignado a la métrica. El tipo que debe tener (cadena, número, etc.) depende de la métrica.|

> [!NOTE]
> Todos los GUID se almacenan en el formato de `{GUID}` . Por ejemplo, `{123D150B-FA18-461C-B218-45B3E4589F9B}`.

### <a name="debug-engines"></a>Motores de depuración
 A continuación se encuentra la organización de las métricas de los motores de depuración en el registro. `Engine` es el nombre de tipo de métrica para un motor de depuración y corresponde a *[tipo de métrica]* en el subárbol del registro anterior.

 `Engine`\

 *[GUID del motor]*\

 `CLSID` = *[GUID de clase]*

 *[Metric] = [valor de métrica]*

 *[Metric] = [valor de métrica]*

 *[Metric] = [valor de métrica]*

 `PortSupplier`\

 `0` = *[GUID del proveedor del puerto]*

 `1` = *[GUID del proveedor del puerto]*

|Marcador de posición|Descripción|
|-----------------|-----------------|
|*[GUID del motor]*|GUID del motor de depuración.|
|*[GUID de clase]*|GUID de la clase que implementa este motor de depuración.|
|*[GUID del proveedor del puerto]*|GUID del proveedor del puerto, si existe. Muchos motores de depuración usan el proveedor de puerto predeterminado y, por lo tanto, no especifican su propio proveedor. En este caso, la subclave estará `PortSupplier` ausente.|

### <a name="port-suppliers"></a>Proveedores de puertos
 A continuación se facilita la organización de las métricas de los proveedores de puertos en el registro. `PortSupplier` es el nombre de tipo de métrica para un proveedor de puerto y se corresponde con *[tipo de métrica]*.

 `PortSupplier`\

 *[GUID del proveedor del puerto]*\

 `CLSID` = *[GUID de clase]*

 *[Metric] = [valor de métrica]*

 *[Metric] = [valor de métrica]*

|Marcador de posición|Descripción|
|-----------------|-----------------|
|*[GUID del proveedor del puerto]*|GUID del proveedor del puerto.|
|*[GUID de clase]*|GUID de la clase que implementa este proveedor de puerto.|

### <a name="symbol-providers"></a>Proveedores de símbolos
 A continuación se facilita la organización de las métricas de los proveedores de símbolos en el registro. `SymbolProvider` es el nombre del tipo de métrica del proveedor de símbolos y corresponde a *[tipo de métrica]*.

 `SymbolProvider`\

 *[GUID del proveedor de símbolos]*\

 `file`\

 `CLSID` = *[GUID de clase]*

 *[Metric] = [valor de métrica]*

 *[Metric] = [valor de métrica]*

 `metadata`\

 `CLSID` = *[GUID de clase]*

 *[Metric] = [valor de métrica]*

 *[Metric] = [valor de métrica]*

|Marcador de posición|Descripción|
|-----------------|-----------------|
|*[GUID del proveedor de símbolos]*|GUID del proveedor de símbolos|
|*[GUID de clase]*|GUID de la clase que implementa este proveedor de símbolos|

### <a name="expression-evaluators"></a>Evaluadores de expresiones
 A continuación se encuentra la organización de las métricas del evaluador de expresiones en el registro. `ExpressionEvaluator` es el nombre de tipo de métrica del evaluador de expresiones y corresponde a *[tipo de métrica]*.

> [!NOTE]
> El tipo de métrica para `ExpressionEvaluator` no está definido en dbgmetric. h, ya que se supone que todos los cambios de métricas para los evaluadores de expresiones van a través de las funciones de métrica del evaluador de expresiones adecuadas (el diseño de la `ExpressionEvaluator` subclave es algo complicado, por lo que los detalles están ocultos dentro de dbgmetric. lib).

 `ExpressionEvaluator`\

 *[GUID de idioma]*\

 *[GUID del proveedor]*\

 `CLSID` = *[GUID de clase]*

 *[Metric] = [valor de métrica]*

 *[Metric] = [valor de métrica]*

 `Engine`\

 `0` = *[GUID del motor de depuración]*

 `1` = *[GUID del motor de depuración]*

|Marcador de posición|Descripción|
|-----------------|-----------------|
|*[GUID de idioma]*|El GUID de un idioma.|
|*[GUID del proveedor]*|El GUID de un proveedor|
|*[GUID de clase]*|GUID de la clase que implementa este evaluador de expresiones.|
|*[GUID del motor de depuración]*|GUID de un motor de depuración con el que funciona este evaluador de expresiones|

### <a name="expression-evaluator-extensions"></a>Extensiones del evaluador de expresiones
 A continuación se encuentra la organización de las métricas de la extensión evaluador de expresiones en el registro. `EEExtensions` es el nombre del tipo de métrica para las extensiones del evaluador de expresiones y corresponde a *[tipo de métrica]*.

 `EEExtensions`\

 *[GUID de extensión]*\

 *[Metric] = [valor de métrica]*

 *[Metric] = [valor de métrica]*

|Marcador de posición|Descripción|
|-----------------|-----------------|
|*[GUID de extensión]*|GUID de una extensión del evaluador de expresiones.|

### <a name="exceptions"></a>Excepciones
 A continuación se encuentra la organización de las métricas de las excepciones en el registro. `Exception` es el nombre del tipo de métrica de las excepciones y corresponde a *[tipo de métrica]*.

 `Exception`\

 *[GUID del motor de depuración]*\

 *[tipos de excepción]*\

 *excepcional*\

 *[Metric] = [valor de métrica]*

 *[Metric] = [valor de métrica]*

 *excepcional*\

 *[Metric] = [valor de métrica]*

 *[Metric] = [valor de métrica]*

|Marcador de posición|Descripción|
|-----------------|-----------------|
|*[GUID del motor de depuración]*|GUID de un motor de depuración que admite excepciones.|
|*[tipos de excepción]*|Título general de la subclave que identifica la clase de excepciones que se puede controlar. Los nombres típicos son las **excepciones de C++**, las **excepciones de Win32**, las excepciones de **Common Language Runtime** y las **comprobaciones de Run-Time nativas**. Estos nombres también se usan para identificar una clase de excepción determinada para el usuario.|
|*excepcional*|Un nombre para una excepción: por ejemplo, **_com_error** o **el salto de control**. Estos nombres también se usan para identificar una excepción determinada para el usuario.|

## <a name="requirements"></a>Requisitos
 Estos archivos se encuentran en el [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] Directorio de instalación del SDK (de forma predeterminada, *[unidad]* \Archivos de programa\microsoft Visual Studio 2010 SDK \\ ).

 Encabezado: includes\dbgmetric.h

 Biblioteca: libs\ad2de.lib, libs\dbgmetric.lib

## <a name="see-also"></a>Consulte también
- [Referencia de API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
