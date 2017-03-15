---
title: "Aplicaciones auxiliares SDK para la depuraci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "dbgmetric.lib"
  - "registro, SDK de depuración"
  - "SDK de depuración, ubicaciones del registro"
  - "dbgmetric.h"
  - "métricas [SDK de depuración]"
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# Aplicaciones auxiliares SDK para la depuraci&#243;n
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Estas funciones y declaraciones son funciones globales auxiliares para implementar los motores de depuración, los evaluadores de expresión, y proveedores de símbolo en C\+\+.  
  
> [!NOTE]
>  No hay versiones administradas de estas funciones y declaraciones en este tiempo.  
  
## Información general  
 Para que los motores de depuración, los evaluadores de expresión, y los proveedores de símbolo son utilizados por Visual Studio, deben registrarse.  Esto se hace estableciendo subclaves del Registro y entradas, si no se conoce como “métricas de valor”. Las funciones globales siguientes están diseñadas para facilitar el proceso de actualizar estas métricas.  Vea la sección en ubicaciones del registro para averiguar el diseño de cada subclave del Registro que se actualizará por estas funciones.  
  
## funciones métricas generales  
 Estas funciones generales utilizadas por los motores de depuración.  Las funciones especializadas para los evaluadores de expresión y los proveedores de símbolo se detallan más adelante.  
  
### método de GetMetric  
 Recupera un valor métrica del registro.  
  
```cpp#  
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
|pszMachine|\[in\]  El nombre de un equipo remoto cuyo registro se escribirá \(`NULL` significa posiblemente el equipo local\).|  
|pszType|\[in\]  Uno de los tipos métrica.|  
|guidSection|\[in\]  GUID de un motor, un evaluador, una excepción, un etc. concretos.  Especifica una subsección bajo un tipo métrica para un elemento específico.|  
|pszMetric|\[in\]  La métrica que se obtendrá.  Esto corresponde a un nombre de valor concreto.|  
|pdwValue|\[in\]  La ubicación de almacenamiento del valor de la.  Hay varios tipos de GetMetric que pueden devolver DWORD \(como en este ejemplo\), BSTR, GUID, o una matriz de GUID.|  
|pszAltRoot|\[in\]  Una raíz alternativa de registro a utilizar.  Establezca en `NULL` para utilizar el valor predeterminado.|  
  
### método de SetMetric  
 Establece el valor métrica especificado en el registro.  
  
```cpp#  
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
|pszType|\[in\]  Uno de los tipos métrica.|  
|guidSection|\[in\]  GUID de un motor, un evaluador, una excepción, un etc. concretos.  Especifica una subsección bajo un tipo métrica para un elemento específico.|  
|pszMetric|\[in\]  La métrica que se obtendrá.  Esto corresponde a un nombre de valor concreto.|  
|dwValue|\[in\]  La ubicación de almacenamiento del valor de la métrica.  Hay varios tipos de SetMetric que pueden almacenar DWORD \(en este ejemplo\), BSTR, GUID, o una matriz de GUID.|  
|fUserSpecific|\[in\]  TRUE si la métrica es específico y si se escribe en el subárbol de usuario en lugar del subárbol del equipo local.|  
|pszAltRoot|\[in\]  Una raíz alternativa de registro a utilizar.  Establezca en `NULL` para utilizar el valor predeterminado.|  
  
### método de RemoveMetric  
 Quita la métrica especificada del registro.  
  
```cpp#  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|pszType|\[in\]  Uno de los tipos métrica.|  
|guidSection|\[in\]  GUID de un motor, un evaluador, una excepción, un etc. concretos.  Especifica una subsección bajo un tipo métrica para un elemento específico.|  
|pszMetric|\[in\]  La métrica que se quitará.  Esto corresponde a un nombre de valor concreto.|  
|pszAltRoot|\[in\]  Una raíz alternativa de registro a utilizar.  Establezca en `NULL` para utilizar el valor predeterminado.|  
  
### método de EnumMetricSections  
 Muestra las secciones diferentes métricas en el registro.  
  
```cpp#  
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
|pszMachine|\[in\]  El nombre de un equipo remoto cuyo registro se escribirá \(`NULL` significa posiblemente el equipo local\).|  
|pszType|\[in\]  Uno de los tipos métrica.|  
|rgguidSections|\[in, out\]  Matriz reservado de GUID que se va a realizar.|  
|pdwSize|\[in\]  El número máximo de GUID que se puede almacenar en la matriz de `rgguidSections` .|  
|pszAltRoot|\[in\]  Una raíz alternativa de registro a utilizar.  Establezca en `NULL` para utilizar el valor predeterminado.|  
  
## Funciones del evaluador de expresiones  
  
|Función|Descripción|  
|-------------|-----------------|  
|GetEEMetric|Recupera un valor métrica del registro.|  
|SetEEMetric|Establece el valor métrica especificado en el registro.|  
|RemoveEEMetric|Quita la métrica especificada del registro.|  
|GetEEMetricFile|Obtiene un nombre de archivo de la especificada y lo carga, devolviendo el contenido del archivo como cadena.|  
  
## Funciones de excepción  
  
|Función|Descripción|  
|-------------|-----------------|  
|GetExceptionMetric|Recupera un valor métrica del registro.|  
|SetExceptionMetric|Establece el valor métrica especificado en el registro.|  
|RemoveExceptionMetric|Quita la métrica especificada del registro.|  
|RemoveAllExceptionMetrics|Quita todas las métricas de excepciones del registro.|  
  
## Funciones del proveedor del token  
  
|Función|Descripción|  
|-------------|-----------------|  
|GetSPMetric|Recupera un valor métrica del registro.|  
|SetSPMetric|Establece el valor métrica especificado en el registro.|  
|RemoveSPMetric|Quita la métrica especificada del registro.|  
  
## funciones de enumeración  
  
|Función|Descripción|  
|-------------|-----------------|  
|EnumMetricSections|Enumera todas las métricas para un tipo métrica especificado.|  
|EnumDebugEngine|Enumera los motores registrados de depuración.|  
|EnumEEs|Enumera los evaluadores registrados de la expresión.|  
|EnumExceptionMetrics|Enumera todas las medidas de la excepción.|  
  
## definiciones métricas  
 Estas definiciones se pueden utilizar para los nombres métrica predefinidos.  Los nombres corresponden a diferentes claves del Registro y nombres de valores y son todos definido como cadenas de caracteres anchos: por ejemplo, `extern LPCWSTR metrictypeEngine`.  
  
|Tipos métrica predefinidos|descripción: La clave base para….|  
|--------------------------------|---------------------------------------|  
|metrictypeEngine|Todos depuración métricas del motor.|  
|más metrictypePortSupplier|Todas las métricas de proveedor de puerto.|  
|metrictypeException|Todas las medidas de la excepción.|  
|metricttypeEEExtension|Todas las extensiones del evaluador de expresiones.|  
  
|Propiedades del motor de depuración|Descripción|  
|-----------------------------------------|-----------------|  
|metricAddressBP|Establece en cero para indicar la compatibilidad para los puntos de interrupción de dirección.|  
|metricAlwaysLoadLocal|Establece en cero para cargar siempre el motor de depuración localmente.|  
|metricLoadInDebuggeeSession|NOT UTILIZADO|  
|metricLoadedByDebuggee|Establece en cero para indicar que el motor de depuración se cargará siempre o por el programa que se depura.|  
|metricAttach|Establece en cero para indicar la compatibilidad de los datos adjuntos a los programas existentes.|  
|metricCallStackBP|Establece en cero para indicar la compatibilidad para los puntos de interrupción de la pila de llamadas.|  
|metricConditionalBP|Establece en cero para indicar la compatibilidad para el valor de puntos de interrupción condicionales.|  
|metricDataBP|Establece en cero para indicar la compatibilidad para el valor de puntos de interrupción en los cambios de los datos.|  
|metricDisassembly|Establece en cero para indicar la compatibilidad para la generación de una lista de desensamblado.|  
|el metricDumpWriting|Establece en cero para indicar la compatibilidad para la escritura de volcado de memoria \(el volcar de memoria en un dispositivo de salida\).|  
|metricENC|Establece en cero para indicar la compatibilidad para editar y continuar. **Note:**  Un motor de depuración nunca debe establecerla o debe establecerse siempre en 0.|  
|metricExceptions|Establece en cero para indicar la compatibilidad para las excepciones.|  
|metricFunctionBP|Establece en cero para indicar la compatibilidad para los puntos de interrupción denominados \(puntos de interrupción importantes cuando se llama a un nombre de función\).|  
|metricHitCountBP|Establece en cero para indicar la compatibilidad para el valor “de los puntos de interrupción del punto de la posición” \(puntos de interrupción que se desencadenan sólo una vez alcanzado algunas veces\).|  
|metricJITDebug|Establece en cero para indicar la compatibilidad para la depuración Just\-In\-Time \(se inicia el depurador cuando se produce una excepción en un proceso en ejecución\).|  
|metricMemory|NOT UTILIZADO|  
|más metricPortSupplier|Establezca esta opción en el CLSID del proveedor de puerto si se implementa una.|  
|metricRegisters|NOT UTILIZADO|  
|metricSetNextStatement|Establezca en cero para indicar la compatibilidad para establecer la siguiente instrucción \(que omite la ejecución de instrucciones intermedias\).|  
|metricSuspendThread|Establece en cero para indicar la compatibilidad para suspender la ejecución de subprocesos.|  
|metricWarnIfNoSymbols|Establece en cero para indicar que el usuario debe ser una notificación si no hay símbolos.|  
|metricProgramProvider|Establezca esta opción en el CLSID del proveedor del programa.|  
|metricAlwaysLoadProgramProviderLocal|Establezca esta opción en cero para indicar que el proveedor de programa se debe cargar siempre localmente.|  
|metricEngineCanWatchProcess|Establezca esta opción en cero para indicar que el motor de depuración observará para procesar eventos en lugar del proveedor del programa.|  
|el metricRemoteDebugging|Establezca esta opción en cero para indicar la compatibilidad para la depuración remota.|  
|metricEncUseNativeBuilder|Establezca esta opción en cero para indicar que la edición y el administrador de Continuar deben utilizar el encbuild.dll del motor de depuración para compilar para editar y continuar. **Note:**  Un motor de depuración nunca debe establecerla o debe establecerse siempre en 0.|  
|metricLoadUnderWOW64|Establezca esta opción en cero para indicar que el motor de depuración se debe cargar en el proceso depurado bajo el WOW al depurar un proceso de 64 bits; si no, el motor de depuración se cargará en el proceso de Visual Studio \(que ejecuta bajo WOW64\).|  
|metricLoadProgramProviderUnderWOW64|Establezca esta opción en cero para indicar que el proveedor de programa se debe cargar en el proceso depurado al depurar un proceso de 64 bits bajo el WOW; si no, se cargará en el proceso de Visual Studio.|  
|metricStopOnExceptionCrossingManagedBoundary|Establezca esta opción en cero para indicar que el proceso debe detener si se provoca una excepción no controlada a través de límites administrados\/código no administrado.|  
|metricAutoSelectPriority|Establezca esta opción en una prioridad para la selección automática del motor de depuración \(valores superiores igual prioridad\).|  
|metricAutoSelectIncompatibleList|Clave del Registro que contiene entradas que especifican GUID para que los motores de depuración se omiten en la selección automática.  Estas entradas son un número \(0, 1, 2, etc.\) con un GUID expresado como una cadena.|  
|metricIncompatibleList|Clave del Registro que contiene entradas que especifican GUID para los motores de depuración que son incompatibles con este motor de depuración.|  
|metricDisableJITOptimization|Establezca esta opción en cero para indicar que las optimizaciones just\-in\-time \(para código administrado\) se deben deshabilitar durante la depuración.|  
  
|Propiedades del evaluador de expresiones|Descripción|  
|----------------------------------------------|-----------------|  
|metricEngine|Esto mantiene el número de motores de depuración que admitan el evaluador especificado de la expresión.|  
|metricPreloadModules|Establezca esta opción en cero para indicar que los módulos debe cargar cuando se inicia un evaluador de expresiones en un programa.|  
|metricThisObjectName|Establezca esta opción en “este” nombre de objeto.|  
  
|Propiedades de la extensión del evaluador de expresiones|Descripción|  
|--------------------------------------------------------------|-----------------|  
|metricExtensionDll|Nombre de la DLL que admite esta extensión.|  
|metricExtensionRegistersSupported|lista de registros admitidos.|  
|metricExtensionRegistersEntryPoint|punto de entrada para los registros de acceso.|  
|metricExtensionTypesSupported|lista de tipos admitidos.|  
|metricExtensionTypesEntryPoint|punto de entrada para los tipos de acceso.|  
  
|Propiedades del proveedor de puerto|Descripción|  
|-----------------------------------------|-----------------|  
|metricPortPickerCLSID|El CLSID del selector de puerto \(un cuadro de diálogo que el usuario puede utilizar los puertos seleccionar y agregar puertos necesarios para depurar\).|  
|metricDisallowUserEnteredPorts|Distinto de cero si los puertos introducidos no se pueden agregar al proveedor de puerto \(esto crea readonly del cuadro de diálogo puerto\-recogedor esencialmente\).|  
|metricPidBase|El identificador de proceso base utilizado por el proveedor de puerto al asignar los identificadores de proceso.|  
  
|Tipos predefinidos de almacén de SP|Descripción|  
|-----------------------------------------|-----------------|  
|storetypeFile|los símbolos se almacenan en un archivo independiente.|  
|storetypeMetadata|los símbolos se almacenan como metadatos en un ensamblado.|  
  
|Propiedades diferentes|Descripción|  
|----------------------------|-----------------|  
|metricShowNonUserCode|Establezca esta opción en cero para mostrar el código de no usuario.|  
|el metricJustMyCodeStepping|Establezca esta opción en cero para indicar que el recorrido sólo puede aparecer en el código de usuario.|  
|metricCLSID|El CLSID para un objeto de un tipo métrica concreto.|  
|metricName|Nombre descriptivo de un objeto de un tipo métrica concreto.|  
|metricLanguage|Nombre del idioma.|  
  
## Ubicaciones del registro  
 Las métricas se leen de y se escriben en el registro, específicamente en la subclave de `VisualStudio` .  
  
> [!NOTE]
>  La mayoría de las veces, métricas se escribe en la clave HKEY\_LOCAL\_MACHINE.  Sin embargo, HKEY\_CURRENT\_USER se a veces la clave de destino.  Dbgmetric.lib controla las dos claves.  Al obtener una medida, busca HKEY\_CURRENT\_USER primero, entonces HKEY\_LOCAL\_MACHINE.  Cuando se establece una medida, un parámetro especifica que clave de nivel superior a utilizar.  
  
 *\[clave del Registro\]*\\  
  
 `Software`\\  
  
 `Microsoft`\\  
  
 `VisualStudio`\\  
  
 *\[raíz de la versión\]*\\  
  
 *\[raíz métricas\]*\\  
  
 *\[tipo métrica\]*\\  
  
 *\[métrica\] \= \[valor métrica\]*  
  
 *\[métrica\] \= \[valor métrica\]*  
  
 *\[métrica\] \= \[valor métrica\]*  
  
|marcador de posición|Descripción|  
|--------------------------|-----------------|  
|*\[clave del Registro\]*|`HKEY_CURRENT_USER` o `HKEY_LOCAL_MACHINE`.|  
|*\[raíz de la versión\]*|la versión de Visual Studio \(por ejemplo, `7.0`, `7.1`, o `8.0`\).  Sin embargo, esta raíz se puede modificar utilizando el modificador**\/rootsuffix** a **devenv.exe**.  Para VSIP, este modificador es normalmente Exp, por lo que la raíz de la versión sería, por ejemplo, 8.0Exp.|  
|*\[raíz métricas\]*|Éste es `AD7Metrics` o `AD7Metrics(Debug)`, dependiendo de si la versión de depuración de dbgmetric.lib se utiliza. **Note:**  Si dbgmetric.lib se utiliza, esta convención de nomenclatura debe ser adherida si tiene diferencias entre depurar y las versiones de lanzamiento que deben reflejar en el registro.|  
|*\[tipo métrica\]*|El tipo de medida que se escriba: `Engine`, `ExpressionEvaluator`, `SymbolProvider`, etc.  Éstos son todos definido como en dbgmetric.h como, donde es el nombre de tipo específico.|  
|*\[métrica\]*|El nombre de una entrada para asignar un valor para establecer la métrica.  La organización real de métricas depende del tipo métrica.|  
|*\[valor métrica\]*|El valor asignado al métrica.  El tipo que el valor debe tener \(cadena, número, etc.\) depende de la.|  
  
> [!NOTE]
>  Todo el GUID se almacena en el formato de `{GUID}`.  Por ejemplo, `{123D150B-FA18-461C-B218-45B3E4589F9B}`.  
  
### Los motores de depuración  
 Lo siguiente es la organización de las métricas de los motores de depuración en el registro.  `Engine` es el nombre de tipo métrica para un motor de depuración y corresponde a *\[tipo métrica\]* en el subárbol anterior del registro.  
  
 `Engine`\\  
  
 *\[guid de motor\]*\\  
  
 `CLSID` \= *\[guid de la clase\]*  
  
 *\[métrica\] \= \[valor métrica\]*  
  
 *\[métrica\] \= \[valor métrica\]*  
  
 *\[métrica\] \= \[valor métrica\]*  
  
 `PortSupplier`\\  
  
 `0` \= *\[guid de proveedor de puerto\]*  
  
 `1` \= *\[guid de proveedor de puerto\]*  
  
|marcador de posición|Descripción|  
|--------------------------|-----------------|  
|*\[guid de motor\]*|GUID del motor de depuración.|  
|*\[guid de la clase\]*|GUID de la clase que implementa este motor de depuración.|  
|*\[guid de proveedor de puerto\]*|GUID del proveedor de puerto, si existe.  Muchos motores de depuración utilizan el proveedor de puerto y por consiguiente no especifique su propio proveedor.  en este caso, la subclave `PortSupplier` estará ausente.|  
  
### Proveedores de puerto  
 A continuación se muestra la disposición de las métricas de proveedor de puerto en el registro.  `PortSupplier` es el nombre de tipo métrica para un proveedor de puerto y corresponde a *\[tipo métrica\]*.  
  
 `PortSupplier`\\  
  
 *\[guid de proveedor de puerto\]*\\  
  
 `CLSID` \= *\[guid de la clase\]*  
  
 *\[métrica\] \= \[valor métrica\]*  
  
 *\[métrica\] \= \[valor métrica\]*  
  
|marcador de posición|Descripción|  
|--------------------------|-----------------|  
|*\[guid de proveedor de puerto\]*|GUID del proveedor de puerto|  
|*\[guid de la clase\]*|GUID de la clase que implementa este proveedor de puerto|  
  
### Proveedores de símbolos  
 A continuación se muestra la disposición de las métricas de proveedor de símbolo en el registro.  `SymbolProvider` es el nombre de tipo métrica para el proveedor del token y corresponde a *\[tipo métrica\]*.  
  
 `SymbolProvider`\\  
  
 *\[guid del proveedor del token\]*\\  
  
 `file`\\  
  
 `CLSID` \= *\[guid de la clase\]*  
  
 *\[métrica\] \= \[valor métrica\]*  
  
 *\[métrica\] \= \[valor métrica\]*  
  
 `metadata`\\  
  
 `CLSID` \= *\[guid de la clase\]*  
  
 *\[métrica\] \= \[valor métrica\]*  
  
 *\[métrica\] \= \[valor métrica\]*  
  
|marcador de posición|Descripción|  
|--------------------------|-----------------|  
|*\[guid del proveedor del token\]*|GUID del proveedor del token|  
|*\[guid de la clase\]*|GUID de la clase que implementa este proveedor de símbolo|  
  
### Evaluadores de expresión  
 Lo siguiente es la organización de las métricas del evaluador de expresiones en el registro.  `ExpressionEvaluator` es el nombre de tipo métrica para el evaluador de expresiones y corresponde a *\[tipo métrica\]*.  
  
> [!NOTE]
>  El tipo métrica para `ExpressionEvaluator` no está definido en dbgmetric.h, como se supone que todos los cambios métrica para los evaluadores de expresión pasará con funciones métricas de evaluador adecuado de la expresión \(el diseño de la subclave de `ExpressionEvaluator` es algo más complicado, por lo que oculta los detalles dentro de dbgmetric.lib\).  
  
 `ExpressionEvaluator`\\  
  
 *\[guid del lenguaje\]*\\  
  
 *\[guid de proveedor\]*\\  
  
 `CLSID` \= *\[guid de la clase\]*  
  
 *\[métrica\] \= \[valor métrica\]*  
  
 *\[métrica\] \= \[valor métrica\]*  
  
 `Engine`\\  
  
 `0` \= *\[guid del motor de depuración\]*  
  
 `1` \= *\[guid del motor de depuración\]*  
  
|marcador de posición|Descripción|  
|--------------------------|-----------------|  
|*\[guid del lenguaje\]*|GUID de un lenguaje|  
|*\[guid de proveedor\]*|GUID de un proveedor|  
|*\[guid de la clase\]*|GUID de la clase que implementa este evaluador de expresiones|  
|*\[guid del motor de depuración\]*|GUID de un motor de depuración con el que el evaluador de expresiones funciona|  
  
### Extensiones del evaluador de expresiones  
 Lo siguiente es la organización de las métricas de la extensión del evaluador de expresiones en el registro.  `EEExtensions` es el nombre de tipo métrica para las extensiones del evaluador de expresiones y corresponde a *\[tipo métrica\]*.  
  
 `EEExtensions`\\  
  
 *\[guid de extensión\]*\\  
  
 *\[métrica\] \= \[valor métrica\]*  
  
 *\[métrica\] \= \[valor métrica\]*  
  
|marcador de posición|Descripción|  
|--------------------------|-----------------|  
|*\[guid de extensión\]*|GUID de una extensión del evaluador de expresiones|  
  
### Excepciones  
 Lo siguiente es la organización de las métricas de las excepciones en el registro.  `Exception` es el nombre de tipo métrica para las excepciones y corresponde a *\[tipo métrica\]*.  
  
 `Exception`\\  
  
 *\[guid del motor de depuración\]*\\  
  
 *\[tipos de excepción\]*\\  
  
 *\[excepción\]*\\  
  
 *\[métrica\] \= \[valor métrica\]*  
  
 *\[métrica\] \= \[valor métrica\]*  
  
 *\[excepción\]*\\  
  
 *\[métrica\] \= \[valor métrica\]*  
  
 *\[métrica\] \= \[valor métrica\]*  
  
|marcador de posición|Descripción|  
|--------------------------|-----------------|  
|*\[guid del motor de depuración\]*|GUID de un motor de depuración que admite las excepciones.|  
|*\[tipos de excepción\]*|Un título general para la subclave que identifica la clase de excepciones que pueden ser controlado.  Los nombres comunes son **C\+\+ Exceptions**, **Win32 Exceptions**, **Common Language Runtime Exceptions**, y **Native Run\-Time Checks**.  Estos nombres también se utilizan para identificar una clase determinada de excepción al usuario.|  
|*\[excepción\]*|un nombre para una excepción: por ejemplo, **\_com\_error** o **Control\-Break**.  Estos nombres también se utilizan para identificar una excepción determinada al usuario.|  
  
## Requisitos  
 Estos archivos se encuentran en el directorio de instalación de [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] SDK \(de forma predeterminada, *\[\] unidad*\\Program Files\\Microsoft Visual Studio 2010 SDK \\\).  
  
 encabezado: incluye \\ dbgmetric.h  
  
 biblioteca: bibliotecas \\ ad2de.lib, bibliotecas \\ dbgmetric.lib  
  
## Vea también  
 [Referencia de API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)