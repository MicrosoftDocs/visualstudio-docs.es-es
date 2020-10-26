---
title: Registro de cambios (Visual Studio Tools para Unity, Windows) | Microsoft Docs
description: Vea el registro de cambios de Visual Studio Tools para Unity, Windows. Vea los cambios de la versión 1.0.0.0 a la 4.7.0.0 y más allá.
ms.custom: ''
ms.date: 7/30/2020
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: f745cca14202c87386dc276b00e89fb70b399404
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039443"
---
# <a name="change-log-visual-studio-tools-for-unity-windows"></a>Registro de cambios (Visual Studio Tools para Unity, Windows)

Registro de cambios de Visual Studio Tools para Unity.

## <a name="4710"></a>4.7.1.0
Publicado el 5 de agosto de 2020

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad con los espacios de nombres a las plantillas predeterminadas.
  
  - API de mensajes de Unity actualizada a 2019.4.

  - Se ha agregado el supresor [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md) para `CA1823`. Los campos privados con los atributos `SerializeField` o `SerializeReference` no deben marcarse como sin usar (FxCop).
  
  - Se ha agregado el supresor [`USP0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0014.md) para `CA1822`. Los mensajes de Unity no deben marcarse como candidatos para el modificador `static` (FxCop).

  - Se ha agregado el supresor [`USP0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0015.md) para `CA1801`. Los parámetros sin utilizar no se deben quitar de los mensajes de Unity (FxCop).
  
  - Se ha agregado compatibilidad de MenuItem con el supresor [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md).  

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se han corregido los supresores [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) y [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) que no funcionaban con paréntesis adicionales o con argumentos de método.
  
  - Se ha corregido la actualización obligatoria de la base de datos de recursos incluso cuando la actualización automática estaba deshabilitada en la configuración de Unity.

## <a name="4700"></a>4.7.0.0
Publicado el 23 de junio de 2020

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad para conservar carpetas de soluciones mientras Unity regenera la solución y proyectos.

  - Se ha agregado el diagnóstico [`UNT0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0015.md). Detecte una signatura del método incorrecta con el atributo `InitializeOnLoadMethod` o `RuntimeInitializeOnLoadMethod`.

  - Se ha agregado el diagnóstico [`UNT0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0016.md). El uso de `Invoke`, `InvokeRepeating`, `StartCoroutine` o `StopCoroutine` con un literal de cadena como primer argumento no posee seguridad de tipos.

  - Se ha agregado el diagnóstico [`UNT0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0017.md). La invocación `SetPixels` es lenta.

  - Se ha agregado compatibilidad con el comentario de bloque y la sangría de archivos de sombreador.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - No restablezca la selección al filtrar mensajes en el asistente de mensajes de Unity.
  
  - Use siempre el explorador predeterminado al abrir la documentación de API para Unity.
  
  - Se han corregido los supresores [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md), [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) y [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) con las siguientes reglas: suprima `IDE0044` (solo lectura), `IDE0051` (sin usar), `CS0649` (nunca se asignó) en todos los campos decorados con el atributo SerializeField. Suprima `CS0649` (nunca se asignó) en los campos públicos de todos los tipos que amplían `Unity.Object`.

  - Se ha corregido la comprobación de los parámetros de tipo genérico para el diagnóstico [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md).

- **Evaluación:**

  - Se ha corregido la comparación de igualdad con enumeraciones.

## <a name="4610"></a>4.6.1.0
Fecha de publicación: 19 de mayo de 2020

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se advierte si no se puede crear el servidor de mensajería en el lado de Unity.
  
  - Los analizadores se ejecutan correctamente durante la compilación ligera.
  
  - Se ha corregido un problema que provocaba que una clase MonoBehaviour creada a partir de UPE no coincidiese con el nombre del archivo.

## <a name="4600"></a>4.6.0.0
Fecha de publicación: 14 de abril de 2020

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad con CodeLens (scripts y mensajes de Unity).
  
  - Se ha agregado el diagnóstico [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0012.md). Detecte y ajuste las llamadas a las corrutinas en `StartCoroutine()`.

  - Se ha agregado el diagnóstico [`UNT0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0013.md). Detecte y quite el atributo `SerializeField` no válido o redundante.

  - Se ha agregado el diagnóstico [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md). Detecte llamadas a `GetComponent()` con tipos no basados en componentes ni en interfaces.
  
  - Se ha agregado el supresor [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) para `IDE0051`. No marque los métodos con el atributo `ContextMenu` o a los que un campo con el atributo `ContextMenuItem` haga referencia como no utilizados.

  - Se ha agregado el supresor [`USP0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0010.md) para `IDE0051`. No marque los campos con el atributo `ContextMenuItem` como no utilizados.
  
  - Se ha agregado el supresor [`USP0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0011.md) para `IDE0044`. No haga que los campos con el atributo `ContextMenuItem` sean de solo lectura.
  
  - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md), [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) y [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) funcionan ahora con los atributos `SerializeReference` y `SerializeField`.
  
### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Envíe solo comandos de inicio/parada a Unity cuando el editor pueda comunicarse.
  
  - Se ha corregido la documentación sobre QuickInfo con mensajes heredados.
  
  - Se ha corregido el ámbito de mensaje del mensaje `CreateInspectorGUI`.

  - No informe [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md) sobre los métodos con modificadores polimórficos.

- **Evaluación:**

  - Se ha corregido el control de instrucciones Using con alias.

## <a name="4510"></a>4.5.1.0

Fecha de publicación: 16 de marzo de 2020

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado el supresor [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md) para `IDE0051`. Los métodos privados usados con Invoke, InvokeRepeating, StartCoroutine o StopCoroutine no se deben marcar como sin usar.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido la documentación sobre OnDrawGizmos/OnDrawGizmosSelected.

- **Evaluación:**

  - Se ha corregido la inspección del argumento lambda.

## <a name="4501"></a>4.5.0.1

Fecha de publicación: 19 de febrero de 2020

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido la comprobación de diagnósticos [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) para la signatura de mensaje incorrecta. Al inspeccionar tipos con varios niveles de herencia, este diagnóstico podría producir un error con el mensaje siguiente: `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added`.

## <a name="4500"></a>4.5.0.0

Fecha de publicación: 22 de enero de 2020

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad con archivos HLSL.
  
  - Se ha agregado el supresor [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) para `IDE0051`. Los campos privados con el atributo `SerializeField` no deben marcarse como sin usar.
  
  - Se ha agregado el supresor [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) para `CS0649`. Los campos con el atributo `SerializeField` no deben marcarse como sin asignar.  

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido la generación de proyectos (el destino de `GenerateTargetFrameworkMonikerAttribute` no siempre se encontraba correctamente).

## <a name="4420"></a>4.4.2.0

Fecha de publicación: 3 de diciembre de 2019

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Diagnósticos corregidos con interfaces definidas por el usuario.

  - Información sobre herramientas rápida corregida con expresiones con formato incorrecto.

## <a name="4410"></a>4.4.1.0

Fecha de publicación: 6 de noviembre de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad con los procesos en segundo plano de Unity. (El depurador puede conectarse automáticamente al proceso principal en lugar de a un proceso secundario).
  
  - Se ha agregado una información sobre herramientas rápida para mensajes de Unity que muestran la documentación asociada.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido el analizador de comparación de etiquetas [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0002.md) con expresiones avanzadas binarias y de invocación.

### <a name="deprecated-features"></a>Características en desuso

- **Integración:**

  - A partir de ahora, Visual Studio Tools para Unity solo admitirá Visual Studio 2017+.

## <a name="4400"></a>4.4.0.0

Fecha de publicación: 15 de octubre de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado el supresor [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) para `IDE0060` (parámetro sin usar) para todos los mensajes de Unity.
  
  - Se ha agregado una información sobre herramientas rápida para los campos etiquetados con `TooltipAttribute`. (Esto funcionará para un descriptor de acceso get sencillo mediante este campo también).

## <a name="4330"></a>4.3.3.0

Fecha de publicación: 23 de septiembre de 2019

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se han corregido los informes de errores y advertencias de las compilaciones ligeras.

## <a name="4320"></a>4.3.2.0

Fecha de publicación: 16 de septiembre de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Hemos aumentado el reconocimiento que tiene Visual Studio para los proyectos de Unity mediante la adición de nuevos diagnósticos específicos para Unity. También hemos hecho que el entorno de desarrollo integrado sea más inteligente suprimiendo los diagnósticos generales de C# que no se aplican a los proyectos de Unity. Por ejemplo, el IDE no mostrará una corrección rápida para cambiar una variable del inspector a `readonly`, lo que le impediría modificar la variable en el editor de Unity.
    - [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md): El tiempo de ejecución llama a los mensajes de Unity aunque estén vacíos; no los declare para evitar el procesamiento innecesario por parte del tiempo de ejecución de Unity.
    - [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0002.md): La comparación de etiquetas con la igualdad de cadenas es más lenta que el método CompareTag integrado.
    - [`UNT0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0003.md): Se prefiere el uso de la forma genérica de GetComponent para la seguridad de tipos.
    - [`UNT0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0004.md): El mensaje de actualización depende de la velocidad de fotogramas y debe usar Time.deltaTime en lugar de Time.fixedDeltaTime.
    - [`UNT0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0005.md): El mensaje de FixedUpdate no depende de la velocidad de fotogramas y debe usar Time.fixedDeltaTime en lugar de Time.deltaTime.
    - [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md): se ha detectado una firma de método incorrecta para este mensaje de Unity.
    - [`UNT0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0007.md): Unity invalida el operador de comparación NULL para objetos de Unity que es incompatible con el uso combinado de NULL.
    - [`UNT0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0008.md): Unity invalida el operador de comparación NULL para objetos de Unity que es incompatible con la propagación de tipo NULL.
    - [`UNT0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0009.md): Al aplicar el atributo InitializeOnLoad a una clase, debe proporcionar un constructor estático. El atributo InitializeOnLoad garantiza que se le llamará cuando se inicie el editor.
    - [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md): El componente MonoBehaviours solo debe crearse con AddComponent(). MonoBehaviour es un componente y debe adjuntarse a un elemento GameObject.
    - [`UNT0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0011.md): El componente ScriptableObject solo debe crearse con CreateInstance(). ScriptableObject debe crearse mediante el motor de Unity para controlar los métodos de mensajes de Unity.
    - [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) para `IDE0029`: los objetos de Unity no deben usar la fusión nula.
    - [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) para `IDE0031`: los objetos de Unity no deben usar la propagación nula.
    - [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) para `IDE0051`: los mensajes de Unity se invocan mediante el tiempo de ejecución de Unity.
    - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) para `IDE0044`: los campos con un atributo SerializeField no deben ser de solo lectura.

## <a name="4310"></a>4.3.1.0

Fecha de publicación: 4 de septiembre de 2019

### <a name="new-features"></a>Características nuevas

- **Evaluación:**

  - Se ha agregado compatibilidad para mejorar la presentación de tipos, es decir, `List<object>` en lugar de `List'1[[System.Object, <corlib...>]]`.

  - Se ha agregado compatibilidad con el acceso a miembros de puntero, es decir, `p->data->member`.

  - Se ha agregado compatibilidad con las conversiones implícitas en inicializadores de matriz, es decir, `new byte [] {1,2,3,4}`.

## <a name="4300"></a>4.3.0.0

Fecha de publicación: 13 de agosto de 2019

### <a name="new-features"></a>Características nuevas

- **Depurador:**

  - Se ha agregado compatibilidad con el protocolo MDS 2.51.

- **Integración:**

  - Se ha mejorado la ventana para asociar a una instancia de Unity con características de ordenación, búsqueda y actualización. El PID ahora se muestra incluso para los reproductores locales (para lo que se consultan los sockets de escucha del sistema, a fin de recuperar el proceso al que pertenece).

  - Se ha agregado compatibilidad con archivos asmdef.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido el control de los mensajes con formato incorrecto al comunicarse con reproductores de Unity.

- **Evaluación:**

  - Se ha corregido el control de los espacios de nombres en las expresiones.

  - Se ha corregido la inspección con los tipos IntPtr.
  
  - Se han corregido los problemas de ejecución paso a paso con excepciones.

  - Se ha corregido la evaluación de los pseudoidentificadores (como $exception).

  - Se ha evitado el bloqueo al desreferenciar direcciones no válidas.  

  - Se ha corregido el problema con los dominios de aplicación descargados.

## <a name="4201"></a>4.2.0.1

Publicado el 24 de julio de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - se ha agregado una nueva opción para crear cualquier tipo de archivo desde el explorador de proyectos de Unity.
  
  - Mejora del almacenamiento en caché de diagnóstico al usar compilaciones rápidas para proyectos de Unity.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - se ha corregido un problema en el que la extensión de archivo no se controlaba mediante ningún editor conocido.

  - Se ha corregido la compatibilidad con extensiones personalizadas en el explorador de proyectos de Unity.

  - Se ha corregido el guardado de la configuración fuera del cuadro de diálogo principal.

  - Se ha quitado la dependencia heredada de Microsoft.VisualStudio.MPF.

## <a name="4110"></a>4.1.1.0

Publicada el 24 de mayo de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha actualizado la API MonoBehaviour a 2019.1.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido la notificación de advertencias y errores que se genera cuando está habilitada la compilación ligera.

  - Se ha corregido el rendimiento de la compilación ligera.

## <a name="4100"></a>4.1.0.0

Publicada el 21 de mayo de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad con la nueva API de lote para volver a cargar los proyectos más rápido.

  - Se ha deshabilitado la compilación completa para los proyectos de Unity, en favor del uso de los errores y advertencias de IntelliSense. De hecho, Unity crea una solución de Visual Studio con proyectos de biblioteca de clases que representan lo que Unity hace internamente. Dicho esto, el resultado de la compilación en Visual Studio nunca se utiliza o selecciona por Unity, ya que su canal de compilación está cerrado. La compilación en Visual Studio solo está consumiendo recursos para nada. Si necesita una compilación completa porque tiene herramientas o una configuración que depende de ella, puede deshabilitar esta optimización (Herramientas/Opciones/Herramientas para Unity/Deshabilitar la compilación completa de proyectos).

  - El Explorador de proyectos de Unity se muestra automáticamente cuando se carga un proyecto de Unity. Este explorador se acoplará junto al Explorador de soluciones.

  - Se ha actualizado el mecanismo de extracción de nombres del proyecto con Unity 2019.x.

  - Se ha agregado compatibilidad para paquetes de Unity en el Explorador de proyectos de Unity. Solo son visibles los paquetes a los que se hace referencia (mediante manifest.json en la carpeta `Packages`) y los paquetes locales (insertados en la carpeta `Packages`).

- **Project Generation:**

  - Conservar las propiedades externas al procesar el archivo de solución.

- **Evaluación:**

  - Se ha agregado compatibilidad para nombres calificados con el alias (solo el espacio de nombres global por ahora). Así pues, el evaluador de expresiones acepta ahora tipos con el formato global::namespace.type.

  - Se ha agregado compatibilidad con el formato `pointer[index]`, que es semánticamente idéntico al formato `*(pointer+index)` de desreferencia de puntero.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se han corregido problemas de dependencia con Microsoft.VisualStudio.MPF.

  - Se ha corregido la asociación del reproductor UWP, sin ningún proyecto cargado.

  - Se ha corregido la actualización automática de la base de datos de activos cuando Visual Studio aún no estaba asociado.

  - Se han corregido problemas de tema con etiquetas y casillas de verificación.

- **Depurador:**

  - Se ha corregido la ejecución paso a paso con constructores estáticos.

## <a name="4005"></a>4.0.0.5

Publicada el 27 de febrero de 2019

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido la detección de la versión de Visual Studio con el paquete de instalación.

  - Se han quitado los ensamblados sin utilizar del paquete de instalación.

## <a name="4004"></a>4.0.0.4

Publicada el 13 de febrero de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad para detectar correctamente procesos de Unity durante la instalación y permitir que el motor de instalación administre mejor los bloqueos de archivo.

  - Se ha actualizado la API `ScriptableObject`.

## <a name="4003"></a>4.0.0.3

Publicada el 31 de enero de 2019

### <a name="new-features"></a>Características nuevas

- **Project Generation:**

  - Los campos públicos y serializados ya no generarán advertencias. Hemos suprimido automáticamente las advertencias del compilador `CS0649` y `IDE0051` en los proyectos de Unity que crearon estos mensajes.

- **Integración:**

  - Ha mejorado la experiencia del usuario para mostrar las instancias del reproductor y el editor de Unity (ahora se puede cambiar el tamaño de las ventanas, se pueden usar márgenes uniformes y se puede mostrar un control de ajuste de tamaño). Se ha agregado información del identificador del proceso para editores de Unity.

  - Se ha actualizado la API `MonoBehaviour`.

- **Evaluación:**

  - Se ha agregado compatibilidad con las funciones locales.

  - Se ha agregado compatibilidad con las pseudovariables (identificadores de excepción y objetos).

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido un problema con los temas y las imágenes de moniker.

  - Solo se escribe en la Ventana de salida durante la depuración, cuando se realiza la actualización automática de la base de datos de recursos.

  - Se han corregido los retrasos de la UI con el filtrado del asistente MonoBehaviour.

- **Depurador:**

  - Se ha corregido la lectura de atributos personalizados de los argumentos con nombre al usar versiones de protocolo anteriores.

## <a name="4002"></a>4.0.0.2

Publicada el 23 de enero de 2019

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido la generación de la compilación experimental.

  - Se ha corregido el control de eventos de archivos de proyecto para minimizar la presión del subproceso de la interfaz de usuario.

  - Se ha corregido el proveedor de finalización con cambios de texto por lotes.

- **Depurador:**

  - Se ha corregido la presentación de mensajes de depuración de usuario en el depurador asociado.

## <a name="4001"></a>4.0.0.1

Publicada el 10 de diciembre de 2018

### <a name="new-features"></a>Características nuevas

- **Evaluación:**

  - Se ha reemplazado NRefactory a favor de Roslyn para la evaluación de expresiones.

  - Se ha agregado compatibilidad con los punteros: desreferencia, conversión y aritmética de puntero (tanto Unity 2018.2+ y el nuevo tiempo de ejecución son necesarios para esto).

  - Se ha agregado compatibilidad con la vista del puntero de matrices (como en C++). Adopte una expresión de puntero y, a continuación, anexe una coma y el número de elementos que desea ver.

  - Se ha agregado compatibilidad con las construcciones asincrónicas.

- **Integración:**

  - Se ha agregado compatibilidad con la actualización automática de la base de datos de recursos de Unity al guardarla. Esta característica está habilitada de forma predeterminada y desencadenará una recompilación en el lado de Unity al guardar un script en Visual Studio. Puede deshabilitar esta característica en la base de datos de recursos ubicada en Tools\Options\Tools for Unity\Refresh al guardarla.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido la activación del puente cuando Visual Studio no está seleccionado como el editor externo preferido.

  - Se ha corregido la evaluación de expresiones con expresiones con un formato incorrecto o no admitidas.

## <a name="4000"></a>4.0.0.0

Publicada el 4 de diciembre de 2018

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad con Visual Studio 2019 (debe tener al menos Unity 2018.3 para poder usar Visual Studio 2019 como editor de scripts externos).

  - Se ha adoptado el catálogo y el servicio de imágenes de Visual Studio, con compatibilidad total con los temas, las imágenes de píxeles perfectos y el escalado de HDPI.

### <a name="deprecated-features"></a>Características en desuso

- **Integración:**

  - A partir de ahora, Visual Studio Tools para Unity solo admitirá Unity 5.2 + (con la integración de Visual Studio incorporada en Unity).

  - A partir de ahora, Visual Studio Tools para Unity solo admitirá Visual Studio 2015 +.

  - Se han quitado la barra de estado, la lista de errores y el servicio de lenguaje heredado.

  - Se ha quitado el asistente de Monobehaviour rápido (en favor de la compatibilidad con IntelliSense dedicada).

## <a name="3903"></a>3.9.0.3

Publicado el 28 de noviembre de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se han corregido problemas de IntelliSense y de recarga de proyectos al agregar o quitar scripts localizados en el primer proyecto.

## <a name="3902"></a>3.9.0.2

Publicado el 19 de noviembre de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Depurador:**

  - Se ha corregido un interbloqueo en la biblioteca usada para comunicarse con el motor de depuración de Unity, que hacía que Visual Studio o Unity se congelara, especialmente al ejecutar 'Asociar a Unity' o reiniciar el juego.

## <a name="3901"></a>3.9.0.1

Publicado el 15 de noviembre de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido la activación de los complementos de Unity cuando se seleccionaba otro editor predeterminado.

## <a name="3900"></a>3.9.0.0

Publicado el 13 de noviembre de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Project Generation:**

  - Se revirtió la solución a un error de rendimiento de Unity que se ha corregido en Unity.

## <a name="3807"></a>3.8.0.7

Publicado el 20 de septiembre de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Depurador:**

  - (Trasladado de la versión 3.9.0.2) Se ha corregido un interbloqueo en la biblioteca usada para comunicarse con el motor de depuración de Unity, que hacía que Visual Studio o Unity se congelara, especialmente al ejecutar "Asociar a Unity" o reiniciar el juego.

## <a name="3806"></a>3.8.0.6

Publicado el 27 de agosto de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido la recarga de proyectos y soluciones.

## <a name="3805"></a>3.8.0.5

Publicado el 20 de agosto de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido la eliminación de suscripciones de supervisión de proyectos.

## <a name="3804"></a>3.8.0.4

Publicado el 14 de agosto de 2018

### <a name="new-features"></a>Características nuevas

- **Evaluación:**

  - Se agregó compatibilidad para los valores de puntero.

  - Se agregó compatibilidad para métodos genéricos.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se cambió la recarga inteligente con varios proyectos.

## <a name="3803"></a>3.8.0.3

Publicado el 24 de julio de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Project Generation:**

  - (Trasladado de la versión 3.9.0.0) Se ha revertido la solución alternativa para un error de rendimiento de Unity que se había corregido en Unity.

## <a name="3802"></a>3.8.0.2

Publicado el 7 de julio de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Project Generation:**

  - Solución alternativa temporal de un error de rendimiento de Unity: MonoIslands en caché al generar proyectos.

## <a name="3801"></a>3.8.0.1

Publicado el 26 de junio de 2018

### <a name="new-features"></a>Características nuevas

- **Debugging:** (Depuración)

  - Se agregó compatibilidad para los comandos UserLog y UserBreak.

  - Se agregó compatibilidad con la carga de tipo Lazy (optimizando la carga de red y la latencia de respuesta del depurador).

### <a name="bug-fixes"></a>Correcciones de errores

- **Evaluación:**

  - Se mejoró la búsqueda de métodos y la evaluación de expresiones de operador binario.

## <a name="3800"></a>3.8.0.0

Publicado el 30 de mayo de 2018

### <a name="new-features"></a>Características nuevas

- **Debugging:** (Depuración)

  - Se agregó compatibilidad para mostrar variables en construcciones asincrónicas.

  - Se agregó compatibilidad para el procesamiento de tipos anidados al establecer puntos de interrupción, para evitar advertencias de construcciones del compilador.

- **Integración:**

  - Se agregó compatibilidad para las gramáticas de textmate para sombreadores (la carga de trabajo de C++ ya no es necesaria para el coloreado de código del sombreador).

### <a name="bug-fixes"></a>Correcciones de errores

- **Project Generation:**

  - No convierta más archivos PDB portátiles a MDB con el nuevo entorno de ejecución de Unity.

## <a name="3701"></a>3.7.0.1

Publicado el 7 de mayo de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Instalador:**

  - Se ha corregido el problema de dependencia cuando se usan compilaciones experimentales.

## <a name="3700"></a>3.7.0.0

Publicado el 7 de mayo de 2018

### <a name="new-features"></a>Características nuevas

- **Debugging:** (Depuración)

  - Se ha agregado compatibilidad con la depuración orquestada (depuración de varios reproductores/editor en la misma sesión de Visual Studio).

  - Se ha agregado compatibilidad con la depuración del reproductor USB de Android.

  - Se ha agregado compatibilidad con la depuración del reproductor UWP/IL2CPP.

- **Evaluación:**

  - Se ha agregado compatibilidad con especificadores hexadecimales.

  - Se ha mejorado la experiencia de evaluación de la ventana Inspección.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido el uso de valores de excepción.

- **Project Generation:**

  - Se excluyen las unidades de compilación del administrador de paquetes de la generación.

## <a name="3605"></a>3.6.0.5

Publicado el 13 de marzo de 2018

### <a name="new-features"></a>Características nuevas

- **Project Generation:**

  - Se ha agregado compatibilidad con el nuevo generador de proyectos en Unity 2018.1.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido el tratamiento de estados dañados en los proyectos personalizados.

- **Depurador:**

  - Se ha corregido el error que impedía establecer la siguiente instrucción.

## <a name="3604"></a>3.6.0.4

Publicado el 5 de marzo de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Project Generation:**

  - Se ha corregido la detección de la versión de Mono.

- **Integración:**

  - Se han corregido problemas de temporización con 2018.1 y la activación de complementos.

## <a name="3603"></a>3.6.0.3

Publicado el 23 de febrero de 2018

### <a name="new-features"></a>Características nuevas

- **Project Generation:**

  - Se ha agregado compatibilidad con .NET Standard.

### <a name="bug-fixes"></a>Correcciones de errores

- **Project Generation:**

  - Se ha corregido la detección de la plataforma de destino de Unity.

- **Depurador:**

  - Se ha corregido la separación de excepciones que se generan fuera del código de usuario.

## <a name="3602"></a>3.6.0.2

Publicado el 7 de febrero de 2018

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Actualice la superficie de la API de UnityMessage para 2017.3.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Vuelva a cargar solo proyectos en los cambios externos (con limitación).

## <a name="3601"></a>3.6.0.1

Publicado el 24 de enero de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se corrigió la conversión del símbolo de depuración de pdb automático a mdb.

  - Se ha corregido la llamada indirecta a EditorPrefs.GetBool que afecta al inspector al tratar de cambiar el tamaño de la matriz.

## <a name="3600"></a>3.6.0.0

Publicado el 10 de enero de 2018

### <a name="new-features"></a>Características nuevas

- **Project Generation:**

  - Se ha agregado compatibilidad para el modelo de referencia de MonoIsland 2018.1.

- **Evaluación:**

  - Se ha agregado compatibilidad para el identificador $exception.

- **Depurador:**

  - Se ha agregado compatibilidad para los atributos DebuggerHidden/DebuggerStepThrough con el nuevo tiempo de ejecución de Unity.

- **Asistentes:**

  - Introduzca la versión "Latest" para los asistentes.

### <a name="bug-fixes"></a>Correcciones de errores

- **Project Generation:**

  - Se ha corregido el cálculo del GUID de proyectos para los proyectos de jugador.

- **Depurador:**

  - Se ha corregido una carrera en el control de eventos importantes.

- **Asistentes:**

  - Actualice el contexto de Roslyn antes de insertar el método.

## <a name="3503"></a>3.5.0.3

Publicado el 9 de enero de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se corrigió la conversión del símbolo de depuración de pdb automático a mdb.

## <a name="3502"></a>3.5.0.2

Publicado el 4 de diciembre de 2017

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Los proyectos de Unity ahora se recargan automáticamente en Visual Studio al agregar o quitar un script de Unity.

- **Depurador:**

  - Se ha incluido una opción que permite usar el depurador de Mono compartido por Xamarin y Visual Studio para Mac para depurar el Editor de Unity.

  - Se ha agregado compatibilidad con archivos de símbolo de depuración portátiles.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se han corregido problemas de dependencias de instalación.

  - Se ha corregido un problema que hacía que el menú de ayuda de la API de Unity no se mostrara.

- **Project Generation:**

  - Se ha corregido un problema de generación de proyectos de reproductor al trabajar en un juego para UWP con el back-end IL2CPP/.NET 4.6.

  - Se ha corregido un problema por el que la extensión .dll se agregaba erróneamente al nombre de archivo de ensamblado.

  - Se ha corregido un problema por el que se usaba un nivel específico de compatibilidad de API de proyecto en lugar del nivel global.

  - No fuerce el uso de la marca AllowAttachedDebuggingOfEditor de Unity, ya que el valor predeterminado es ahora "true".

## <a name="3402"></a>3.4.0.2

Publicado el 19 de septiembre de 2017

### <a name="new-features"></a>Características nuevas

- **Project Generation:**

  - Se agregó compatibilidad con las unidades de compilación assembly.json.

  - Se detuvo la copia de ensamblados Unity en la carpeta de proyecto.

- **Depurador:**

  - Se agregó compatibilidad con la definición de la siguiente instrucción con el nuevo entorno de ejecución de Unity.

  - Se agregó compatibilidad con el tipo decimal con el nuevo entorno de ejecución de Unity.

  - Se agregó compatibilidad con las conversiones implícitas o explícitas.

### <a name="bug-fixes"></a>Correcciones de errores

- **Evaluación:**

  - Se corrigió la creación de matrices con tamaño implícito.

  - Se corrigieron los elementos generados mediante compilador con variables locales.

- **Project Generation:**

  - Se corrigió la referencia al nivel de API de Microsoft.CSharp para 4.6.

## <a name="3302"></a>3.3.0.2

Publicado el 15 de agosto de 2017

### <a name="bug-fixes"></a>Correcciones de errores

- **Project Generation:**

  - Se ha corregido la generación de soluciones de Visual Studio en Unity 5.5 y versiones anteriores.

## <a name="3300"></a>3.3.0.0

Publicado el 14 de agosto de 2017

### <a name="new-features"></a>Características nuevas

- **Evaluación:**

  - Se agregó compatibilidad con la creación de estructuras con el nuevo entorno de ejecución de Unity.

  - Se agregó compatibilidad minimalista con punteros.

### <a name="bug-fixes"></a>Correcciones de errores

- **Evaluación:**

  - Se corrigió la invocación del método en los primitivos.

  - Se corrigió la evaluación de campos con tipos marcados con BeforeFieldInit.

  - Se corrigió la incompatibilidad de las llamadas con operadores binarios (sustrato).

  - Se corrigieron los problemas al agregar elementos a la inspección de Visual Studio.

- **Project Generation:**

  - Se corrigieron las referencias al nombre de ensamblado con archivos mcs.rsp.

  - Se corrigieron las definiciones con niveles de API.

## <a name="3200"></a>3.2.0.0

Publicado el 10 de mayo de 2017

### <a name="new-features"></a>Características nuevas

- **Instalador:**

  - Se agregó compatibilidad con la limpieza de la caché de MEF.

### <a name="bug-fixes"></a>Correcciones de errores

- **Editor de código:**

  - Se corrigió la clasificación/finalización con atributos personalizados.

  - Se corrigió el parpadeo con mensajes de Unity.

## <a name="3100"></a>3.1.0.0

Publicado el 7 de abril de 2017

### <a name="new-features"></a>Características nuevas

- **Depurador:**

  - Se ha agregado compatibilidad con el nuevo tiempo de ejecución de Unity (con compatibilidad con .NET 4.6 o C# 6).

- **Project Generation:**

  - Se ha agregado compatibilidad con el perfil de .NET 4.6.

  - Se ha agregado compatibilidad con los archivos mcs.rsp.

  - Habilite siempre el modificador de compilación no seguro cuando se use Unity 5.6.

  - Se ha agregado compatibilidad para la generación de proyectos "Player" cuando se usa la plataforma Tienda Windows y el back-end il2cpp.

### <a name="bug-fixes"></a>Correcciones de errores

- **Editor de código:**

  - Se ha corregido la posición del acento circunflejo después de insertar métodos con finalización automática.

- **Project Generation:**

  - Se ha quitado el procesamiento posterior a la versión de ensamblado.

## <a name="3001"></a>3.0.0.1

Publicado el 7 de marzo de 2017

### <a name="this-version-includes-all-new-features-and-bug-fixes-introduced-with-28x-series"></a>Esta versión incluye todas las nuevas características y correcciones de errores que se introdujeron en la serie 2.8.x.

## <a name="2820---30-preview-3"></a>2.8.2.0 - 3.0 (versión preliminar 3)
Publicado el 25 de enero de 2017

### <a name="bug-fixes"></a>Correcciones de errores

- **Generación de proyectos:**

  - Se corrigió la regresión cuando se hacía referencia dos veces a los proyectos de complementos, primero como un archivo DLL binario y después como una referencia de proyecto.

## <a name="2810---30-preview-2"></a>2.8.1.0 (3.0 versión preliminar 2)
Publicado el 23 de enero de 2017

### <a name="bug-fixes"></a>Correcciones de errores

- **Editor de código:**

  - Se corrigió un bloqueo al iniciar una declaración de atributo sin finalización de llave.

- **Depurador:**

  - Se corrigieron puntos de interrupción de función con corrutinas bajo el nuevo compilador o tiempo de ejecución de Unity.

  - Se agregó una advertencia en el caso de un punto de interrupción desenlazable (cuando no se encuentra ninguna ubicación de origen correspondiente).

- **Project Generation:**

  - Se corrigió la generación de csproj con caracteres especiales o localizados.

  - Se corrigieron referencias fuera de Activos, como Biblioteca (por ejemplo, el SDK de Facebook).

- **Varios:**

  - Se agregó comprobación para impedir que se ejecute Unity al instalar o desinstalar.

  - Se cambió a https para tener como destino la documentación remota de Unity.

## <a name="2800---30-preview"></a>2.8.0.0 (versión preliminar 3.0)
Publicado el 17 de noviembre de 2016

### <a name="new-features"></a>Características nuevas

- **General:**

  - Se agregó compatibilidad con el instalador de Visual Studio de 2017.

  - Se agregó compatibilidad con las extensiones de Visual Studio de 2017.

  - Se agregó compatibilidad de localización.

- **Editor de código:**

  - Se agregó C# IntelliSense para mensajes de Unity.

  - Se agregaron colores de código de C# para mensajes de Unity.

- **Depurador:**

  - Se agregó compatibilidad para expresiones `is`, `as`, conversión directa, `default`, `new`.

  - Se agregó compatibilidad para expresiones string concat.

  - Se agregó compatibilidad para la presentación hexadecimal de valores enteros.

  - Se agregó compatibilidad para la creación de nuevas variables temporales (instrucciones).

  - Se agregó compatibilidad para conversiones implícitas de primitivas.

  - Se agregaron mensajes de error mejorados cuando se espera un tipo o no se encuentra.

- **Project Generation:**

  - Se quitó el sufijo CSharp de los nombres de proyecto.

  - Se quitó la referencia a un archivo de destinos de msbuild de todo el sistema.

- **Asistentes:**

  - Se agregó compatibilidad para mensajes de Unity en tipos que no son de comportamiento como Editor o EditorWindow.

  - Se cambió a Roslyn para insertar y dar formato a los mensajes de Unity.

### <a name="bug-fixes"></a>Correcciones de errores

- **Depurador:**

  - Se corrigió un error que bloqueaba Unity al evaluar los tipos genéricos.

  - Se corrigió el control de tipos que aceptan valores NULL.

  - Se corrigió el control de las enumeraciones.

  - Se corrigió el control de tipos miembro anidados.

  - Se corrigió el acceso al indizador de colecciones.

  - Se corrigió la compatibilidad para la depuración de marcos de iterador con el nuevo compilador de C#.

- **Project Generation:**

  - Se corrigió un error que impedía la compilación cuando el destino es el reproductor web de Unity.

  - Se corrigió un error que impedía la compilación al compilar un script con un nombre de archivo codificado para web.

## <a name="2300"></a>2.3.0.0

Publicado el 14 de julio de 2016

### <a name="new-features"></a>Características nuevas

- **General:**

  - Se agregó una opción para deshabilitar los registros de la consola de Unity en la lista de errores de Visual Studio.

  - Se agregó una opción para permitir la modificación de propiedades de proyectos generados.

- **Depurador:**

  - Se agregaron los visualizadores de cadenas de texto, XML, HTML y JSON.

- **Asistentes:**

  - Se agregaron MonoBehaviors que faltaban.

### <a name="bug-fixes"></a>Correcciones de errores

- **General:**

  - Se corrigió un conflicto con ReSharper que impedía que se mostraran controles dentro de la configuración de Visual Studio.

  - Se corrigió un conflicto con Xamarin que impedía la depuración en algunos casos.

- **Depurador:**

  - Se ha corregido un problema que provocó Visual Studio se bloqueara durante la depuración.

  - Se corrigió un problema con los puntos de interrupción de función en Visual Studio 2015.

  - Se corrigieron varios problemas de evaluación de expresiones.

## <a name="2200"></a>2.2.0.0

Publicado el 4 de febrero de 2016

### <a name="new-features"></a>Características nuevas

- **Asistentes:**

  - Se ha agregado búsqueda inteligente en el asistente **Implementar MonoBehavior** .

  - Hace que los asistentes tengan en cuenta el contexto; por ejemplo, los mensajes de NetworkBehavior solo están disponibles cuando se trabaja con un elemento NetworkBehavior.

  - Se ha agregado compatibilidad con mensajes de NetworkBehavior en los asistentes.

- **IU:**

  - Se ha agregado una opción para configurar la visibilidad de los mensajes de MonoBehavior.

  - Se han quitado páginas de propiedades de Visual Studio que no son relevantes para los proyectos de Unity.

### <a name="bug-fixes"></a>Correcciones de errores

- **Generación de proyectos:**

  - Se han corregido las referencias a UnityEngine y UnityEditor en Unity 4.6.

  - Se ha corregido la generación de archivos de proyecto cuando Unity se está ejecutando en OSX.

  - Se ha corregido el control de nombres de proyecto que contienen caracteres de almohadilla (#).

  - Se han restringido los proyectos generados a C# 4,

- **Depurador:**

  - Se ha corregido un problema con la evaluación de expresiones durante la depuración dentro de un corrutina de Unity.

  - Se ha corregido un problema que provocó Visual Studio se bloqueara durante la depuración.

- **IU:**

  - Se ha corregido una incompatibilidad con la extensión de Visual Studio [Tabs Studio](https://tabsstudio.com/) .

- **Instalador:**

  - Se admite la instalación en todo el equipo de VSTU (instalación para todos los usuarios) mediante la creación de entradas del Registro HKLM.

  - Se han corregido problemas con la desinstalación de VSTU cuando está instalada la misma versión de VSTU en varias versiones distintas de Visual Studio. Por ejemplo, cuando se han instalado VSTU **2015** 2.1.0.0 y VSTU **2013** 2.1.0.0.

## <a name="2100"></a>2.1.0.0

Publicado el 8 de septiembre de 2015

### <a name="new-features"></a>Características nuevas

- Compatibilidad con Unity 5.2

### <a name="bug-fixes"></a>Correcciones de errores

- Mostrar elementos de menú en Unity < 4.2

- Cuando Visual Studio bloquea los archivos de Intellisense XML, ya no aparece ningún mensaje de error.

- Controle los puntos de interrupción condicionales <\<When Changed>> cuando el argumento condicional no es un valor booleano.

- Referencias fijas a ensamblados UnityEngine y UnityEditor para las aplicaciones de la Tienda Windows.

- Se ha corregido el error al entrar en el depurador: No se puede administrar, excepción general.

- Puntos de interrupción de recuento de visitas fijas en Visual Studio 2015.

## <a name="2000"></a>2.0.0.0

Publicado el 20 de julio de 2015

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración de Unity:**

  - Conversión fija de símbolos de depuración creados con Visual Studio de 2015 al importar un archivo DLL y sus símbolos de depuración (PDB).

  - Siempre se generan archivos MDB al importar un archivo DLL y sus símbolos de depuración (PDB), excepto cuando también se proporciona un archivo MDB.

  - Contaminación fija del directorio del proyecto de Unity con un directorio obj.

  - Generación fija de referencias a System.Xml.Link y System.Runtime.Serialization.

  - Compatibilidad agregada con varios suscriptores a los enlaces de API de generación del archivo del proyecto.

  - Generación del archivo de proyecto siempre completo incluso cuando se bloquea uno de los archivos que se va a generar.

  - Compatibilidad agregada con los caracteres comodín * en el filtro de extensión al especificar la inclusión de archivos en el proyecto de C#.

- **Integración de Visual Studio**

  - Corrección de un problema de compatibilidad con las herramientas de productividad avanzadas.

  - Corrección de la generación de eventos relacionados con MonoBehaviors y declaraciones de delegados.

- **Depurador:**

  - Fijación de una inmovilización potencial en la depuración.

  - Corrección de un problema de visualización de variables locales en determinados marcos de pila.

  - Corrección de inspección de matrices vacías.

## <a name="1990---20-preview-2"></a>1.9.9.0 - 2.0 (versión preliminar 2)
Publicado el 2 de abril de 2015

### <a name="new-features"></a>Características nuevas

- **Explorador de proyectos de Unity:**

  - Cambia automáticamente el nombre de clase al cambiar el nombre de un archivo en el Explorador de proyectos de Unity (consulte el diálogo **Opciones** ).

  - Selecciona automáticamente los scripts creados recientemente en el Explorador de proyectos de Unity.

  - Realiza un seguimiento del script activo en el Explorador de proyectos de Unity (consulte el diálogo **Opciones** ).

  - Realiza un sincronizado doble del Explorador de soluciones de Visual Studio (consulte el diálogo **Opciones** ).

  - Se han adoptado los iconos de Visual Studio en el Explorador de proyectos de Unity.

- **Depurador:**

  - Selecciona el destino de depuración activo de una lista de destinos de depuración guardados o usados recientemente (consulte el diálogo **Opciones** ).

  - Crea puntos de interrupción de funciones en los métodos MonoBehavior y los aplica a varias clases MonoBehavior.

  - Permite crear el identificador del objeto en el depurador.

  - Permite contar el número de llamadas del punto de interrupción.

  - Admite interrupciones en caso de excepción en el depurador (Experimental. Consulte el diálogo **Opciones** ).

  - Permite crear objetos y matrices al evaluar expresiones en el depurador.

  - Permite comparar valores null al evaluar expresiones en el depurador.

  - Filtra miembros obsoletos en las ventanas de inspección del depurador.

- **Instalador:**

  - Registro de extensiones de Visual Studio Tools para Unity optimizado.

  - Instala el paquete de Visual Studio Tools para Unity para Unity 5.

- **Documentación:** Se mejora el rendimiento de la generación de documentación.

- **Asistentes:** Compatibilidad con nuevos métodos de MonoBehavior para Unity 4.6 y 5.

- **Unity:** Indicadores no seguros de búsqueda y definiciones personalizadas en archivos .rsp durante la generación de archivos de proyecto.

- **IU:** Se ha agregado Visual Studio Tools para Unity al cuadro de diálogo **Opciones** de Visual Studio.

### <a name="bug-fixes"></a>Correcciones de errores

- **Explorador de proyectos de Unity:**

  - Se actualiza el Explorador de proyectos de Unity después de que se muevan archivos o se cambie el nombre de archivos desde el Explorador de soluciones de Visual Studio.

  - Se conservan las selecciones al cambiar el nombre de archivos en el Explorador de proyectos de Unity.

  - Se impide la expansión y contracción automáticas al hacer doble clic en archivos en el Explorador de proyectos de Unity.

  - Se asegura de que los archivos recién seleccionados estén visibles en el Explorador de proyectos de Unity.

- **Depurador:**

  - Se evita una posible inmovilización de Visual Studio al evaluar expresiones en el depurador.

  - Se asegura que las invocaciones de método se produzcan en el dominio adecuado en el depurador.

- **Unity:**

  - Se ha corregido la ubicación de UnityVS.OpenFile con Unity 5.

  - Se ha corregido la ubicación de pdb2mdb con Unity 5.

  - Se evita una posible excepción durante la generación de archivos del proyecto.

  - Se evita una posible inmovilización al ejecutar Unity en OSX.

  - Se controlan las excepciones internas.

  - Se envían registros de la consola de Unity a la lista de errores de VS.

- **Documentación:** Se ha corregido la generación de documentación para la nueva documentación de Unity.

- **Proyecto:** Se mueve y se cambia el nombre de los archivos .meta de Unity cuando es necesario, incluso en las carpetas.

- **Asistentes:** Se ha corregido el orden de los parámetros de métodos MonoBehavior al generar código.

- **IU:** Compatibilidad con temas de Visual Studio para iconos y menú contextual.

## <a name="1980---20-preview"></a>1.9.8.0 - 2.0 (versión preliminar)
Publicado el 12 de noviembre de 2014

### <a name="new-features"></a>Características nuevas

- Compatible con Visual Studio 2015.

- Coloreado de código para los sombreadores de Unity en Visual Studio 2015.

- Visualización mejorada de valores al depurar:

  - Mejor visualización de listas de matrices, listas, tablas hash y diccionarios.

  - Muestra miembros no públicos y estáticos como categorías en las vistas locales y de inspección.

  - Visualización mejorada de SerializedProperty de Unity para evaluar únicamente el campo de valor válido de la propiedad.

  - Compatible con DebuggerDisplayAttribute para clases y estructuras.

  - Compatible con DebuggerTypeProxyAttribute.

- Se insertan métodos de MonoBehaviour usando nuestros asistentes para respetar las convenciones de código de usuario.

- Se ha implementado la compatibilidad con plantillas de texto de tiempo de compilación en proyectos generados por UnityVS.

- Se ha implementado la compatibilidad con recursos ResX en proyectos generados por UnityVS.

- Permite abrir sombreadores en Visual Studio desde Unity.

### <a name="bug-fixes"></a>Correcciones de errores

- Se limpian los sockets antes de iniciar el juego en Unity después de que se haya iniciado Adjuntar y reproducir en Visual Studio. Esto corrige algunos problemas de estabilidad de la conexión entre Unity y VS al usar Adjuntar y reproducir.

- Se evita llamar a aquellos métodos en la interfaz del depurador del motor de scripting de Unity que tienden a inmovilizar Unity. Esto impide la inmovilización de Unity al adjuntar el depurador.

- Se ha corregido la visualización de pilas de llamadas cuando no hay símbolos disponibles.

- No se registra la devolución de llamada de registro si no es necesario.

## <a name="1920"></a>1.9.2.0

Publicado el 9 de octubre de 2014

### <a name="new-features"></a>Características nuevas

- Se ha mejorado la detección de reproductores de Unity.

- Al usar nuestro abridor de archivos, se hace que Unity pase el número de línea y el nombre de archivo.

- Si no hay documentación local, se establece la documentación en línea de Unity como la documentación predeterminada.

### <a name="bug-fixes"></a>Correcciones de errores

- Se ha corregido un posible bloqueo de Unity al alcanzar un punto de interrupción después de volver a cargar un dominio.

- Se han corregido las excepciones que se muestran en la consola de Unity al cerrar nuestras ventanas Configuración o Acerca de, después de volver a cargar un dominio.

- Se ha corregido la detección de Unity de 64 bits que se ejecuta localmente.

- Se ha corregido el filtrado de MonoBehaviours por versión de Unity en asistentes.

- Se ha corregido el error por el que todos los activos se incluían en los archivos de proyecto si el filtro de extensión estaba vacío.

## <a name="1910"></a>1.9.1.0

Publicado el 22 de septiembre de 2014

### <a name="new-features"></a>Características nuevas

- Se optimiza el enlazado de un punto de interrupción con ubicaciones de origen.

- Compatible con métodos sobrecargados en la Evaluación de expresiones del depurador.

- Compatible con conversión boxing de tipos de valor y primitivos en la Evaluación de expresiones del depurador.

- Permite volver a crear el entorno de variables locales de C# al depurar métodos anónimos.

- Se eliminan y se cambia el nombre de archivos .meta al eliminar o cambiar el nombre de archivos desde Visual Studio.

### <a name="bug-fixes"></a>Correcciones de errores

- Se ha corregido el procesamiento de temas de Visual Studio. Anteriormente, los cuadros de diálogo en temas negros podían aparecer vacíos.

- Se ha corregido la congelación de Unity al conectar el depurador durante la recompilación de Unity.

- Se han corregido los puntos de interrupción al depurar editores o reproductores remotos compilados en otro sistema.

- Se ha corregido un posible bloqueo de Visual Studio cuando se alcanza un punto de interrupción.

- Se ha corregido el enlazado de puntos de interrupción para evitar que los puntos de interrupción se muestren como descargados.

- Se ha corregido el procesamiento de ámbito de variable en el depurador para evitar variables activas que aparecen fuera del ámbito.

- Se ha corregido la búsqueda de miembros estáticos en la evaluación de expresiones del depurador.

- Se ha corregido la visualización de tipos en la Evaluación de expresiones del depurador para mostrar las propiedades y los campos estáticos.

- Se ha corregido la generación de soluciones cuando los nombres de proyecto de Unity incluyen caracteres especiales que Visual Studio prohíbe (Problema de conexión #948666).

- Se ha corregido el paquete de Visual Studio Tools para Unity para que deje de inmediato de enviar eventos de consola después de que se haya desactivado la opción (Problema de conexión #933357).

- Se ha corregido la detección de referencias para volver a generar correctamente referencias a las nuevas API, como UnityEngine.UI, en los proyectos de generados en UnityVS.

- Se ha corregido el instalador para que requiera que Visual Studio se cierre antes de la instalación con el objetivo de evitar instalaciones dañadas.

- Se ha corregido el instalador para que instale los Ensamblados de referencia de Unity como un auténtico componente independiente, compartido entre todas las versiones de VSTU.

- Se han corregido los scripts de apertura con VSTU en las versiones de 64 bits de Unity.

## <a name="1900"></a>1.9.0.0

Publicado el 29 de julio de 2014

### <a name="new-features"></a>Características nuevas

- En la ventana Adjuntar depurador de Unity, se ha agregado la capacidad de introducir una dirección IP y un puerto personalizados para depurar.

- Se ha agregado una opción de configuración para establecer si Unity se ejecuta o no en segundo plano.

- Se ha agregado la opción de configuración para generar los archivos de proyecto y solución o solo los archivos de proyecto.

- Destino de inicio: elige entre Adjuntar a Unity o Adjuntar a Unity y reproducir.

- Muestra matrices multidimensionales en el depurador.

- Se procesan los nuevos puertos de depuración del Reproductor de Unity.

- Se procesan las referencias a nuevos ensamblados de Unity como ensamblados de la GUI de Unity 4.6.

- Se deconstruyen cierres para que se muestren correctamente las variables locales al depurar.

- Se deconstruyen las variables de iteradores generadas en argumentos durante la depuración.

- Se conserva el estado del Explorador de proyectos de Unity después de volver a cargar un proyecto.

- Se agrega un comando para sincronizar el Explorador de proyectos de Unity con el documento actual.

### <a name="bug-fixes"></a>Correcciones de errores

- Se han corregido los puntos de interrupción condicionales cuyas condiciones se establecen antes de iniciar al depurador.

- Se han corregido las referencias a UnityEngine para evitar advertencias.

- Se ha corregido el análisis de versiones beta de Unity.

- Se ha corregido el problema por el que las variables no aparecían en la ventana de variables locales al alcanzar un punto de interrupción o de ejecución paso a paso.

- Se ha corregido la información sobre herramientas de variables en Visual Studio 2013.

- Se ha corregido la generación de la documentación de IntelliSense para Unity 4.5.

- Se ha corregido la comunicación entre Unity y Visual Studio después de la recarga de un dominio (reproducir/detener en Unity).

- Se ha corregido el procesamiento de partes de temas de Visual Studio.

> [!IMPORTANT]
> Dado que C# es el lenguaje predominante en el ecosistema de Unity (los nuevos activos de muestra están en C# y la documentación de Unity se presentará en C# de forma predeterminada), eliminamos nuestro soporte básico para UnityScript y Boo con el fin de centrarnos mejor en la experiencia en C#. Como resultado, las soluciones de VSTU ahora solo están en C# y se cargan mucho más rápido.

## <a name="1820"></a>1.8.2.0

Publicado el 7 de enero de 2014

### <a name="new-features"></a>Características nuevas

- Solución alternativa de un problema en la capa de red del motor de scripting de Unity en Mavericks para la detección remota de editores.

- Procesa los nuevos puertos para detectar reproductores remotos de Unity.

- Hace referencia al ensamblado UnityEngine específico para el destino de compilación actual.

- Agrega ajuste para filtrar archivos que se incluirán en los proyectos generados.

- Agrega ajuste para deshabilitar el envío de registros de consola a la lista de errores de Visual Studio. Esto es útil si está usando PlayMaker o Console Pro, ya que solo podía haber una devolución de llamada registrada en Unity para recibir registros de consola.

- Agrega ajuste para deshabilitar la generación de símbolos de depuración de mdb. Esto es útil si usted está generando la mdb.

### <a name="bug-fixes"></a>Correcciones de errores

- Se ha corregido una regresión por la que los archivos abiertos en VS desde Unity 4.2 (o versión más reciente) perdían IntelliSense.

- Se han corregido nuestros diálogos de VS para que procesen temas personalizados.

- Se ha corregido el cierre del menú contextual de UPE.

- Se evita el bloqueo en Unity cuando el ensamblado generado específico de la versión no está sincronizado.

## <a name="1810"></a>1.8.1.0

Publicado el 21 de noviembre de 2013

### <a name="new-features"></a>Características nuevas

- Se han ajustado los asistentes de MonoBehaviour con las API de Unity 4.3.

- Los asistentes de MonoBehaviour filtran las API de Unity según la versión que utilice.

- Se ha agregado una referencia a System.Xml.Linq a los proyectos de Unity > 4.1.

- Se ha mejorado el aspecto de nuestras llamadas a Debug.Log para que no incluyan el principio de la stacktrace en el mensaje.

### <a name="bug-fixes"></a>Correcciones de errores

- Se ha corregido un error por el que interferíamos con el procesamiento predeterminado de archivos JavaScript en Visual Studio.

- Se ha corregido definitivamente la visualización de un píxel blanco en VS.

- Se ha corregido la eliminación del ensamblado de UnityVS.VersionSpecific si está marcado como de solo lectura por un SCM.

- Se han corregido las excepciones que se producían al crear sockets en el paquete de UnityVS.

- Se ha corregido un bloqueo en Visual Studio que se producía al cargar imágenes de archivo desde ensamblados de Visual Studio.

- Se ha corregido un error en la generación de UnityVS.VersionSpecific para compilaciones de código fuente de Unity.

- Se ha corregido una posible inmovilización que se producía al abrir un socket en el paquete de Unity.

- Se ha corregido el procesamiento de proyectos de Unity que tenían un guión (-) en su nombre.

- Se han corregido los scripts de apertura de Unity para que no confundan la orden ALT+TAB en Unity 4.2 y versiones posteriores.

## <a name="1800"></a>1.8.0.0

Publicado el 24 de septiembre de 2013

### <a name="new-features"></a>Características nuevas

- Se ha mejorado mucho la velocidad de conexión del depurador.

- Se controla automáticamente la navegación al archivo y la línea en Unity 4.2 y versiones posteriores.

- Puntos de interrupción condicionales.

- El generador de archivos de proyecto ahora es capaz de procesar plantillas T4.

- Se han actualizado los asistentes de MonBehavior con nuevas API.

- Documentación de IntelliSense en C# para tipos de Unity.

- Evaluación de expresiones lógicas y aritméticas.

- Se ha mejorado la detección de editores remotos para la vista previa de depuración remota.

### <a name="bug-fixes"></a>Correcciones de errores

- Se ha corregido un error por el que se podía perder un subproceso en VS tras desconectar el depurador.

- Se ha corregido la visualización de un píxel blanco en VS.

- Se ha corregido el procesamiento de clics en el icono de la barra de estado.

- Se ha corregido la generación de referencias con ensamblados en carpetas de complementos.

- Se ha corregido la creación de sockets desde el paquete UnityVS en caso de que haya excepciones.

- Se ha corregido la detección de nuevas versiones de UnityVS.

- Se ha corregido el mensaje del administrador de licencias al caducar la licencia.

- Se ha corregido un error por el que la lista de procesos se podía mostrar vacía en la ventana Adjuntar depurador a proceso de VS.

- Se ha corregido el cambio de valores de booleanos en la vista local.

## <a name="1220"></a>1.2.2.0

Publicado el 9 de julio de 2013

### <a name="bug-fixes"></a>Correcciones de errores

- Se procesan nombres completos en el evaluador de expresiones.

- Se ha corregido una inmovilización relacionada con el control de excepciones mediante la cual el motor de scripting de Unity enviaba datos de stackframe incorrectos.

- Se ha corregido el proceso de compilación de destinos Web.

- Se ha corregido un error que podía producirse si Visual Studio se iniciaba y en la lista de archivos para abrir durante el inicio había un archivo eliminado.

- Se ha corregido UnityVS.OpenFile para que procese archivos que no sean de script, como, por ejemplo, sombreadores compilados.

- Ahora hacemos referencia a Boo.Lang y UnityScript.Lang desde todos los proyectos de C#.

- Se ha corregido la generación de referencias de proyectos si el proyecto contiene caracteres especiales.

- Se ha encontrado una solución alternativa a un problema de VS por el que las llamadas a métodos en proyectos eliminados generaban varios NullReferenceException MessageBox.

- Se ha corregido el procesamiento de ensamblados de la versión beta de Unity 4.2.

## <a name="1210"></a>1.2.1.0

Publicado el 9 de abril de 2013

### <a name="bug-fixes"></a>Correcciones de errores

- Se ha corregido la implementación local de ensamblados de Unity para la finalización de código en caso de que se produzca un error de E/S (como archivos de sólo lectura o archivos bloqueados por Visual Studio).

- Se ha corregido una regresión por la que al abrir un script desde Unity no se centraría en el archivo si ya estaba abierto en Visual Studio.

- Se ha corregido el problema de rendimiento del nuevo control de excepciones.

- Se ha corregido el enlace de puntos de interrupción en algunos archivos DLL externos.

## <a name="1200"></a>1.2.0.0

Publicado el 25 de marzo de 2013

### <a name="new-features"></a>Características nuevas

- Se ha mejorado mucho la velocidad de conexión del depurador.

- Explorador de proyectos de Unity optimizado para proyectos grandes.

- Respeta la configuración de Visual Studio en lo referente a si se debe generar una interrupción (o no) en caso de encontrar excepciones controladas y no controladas.

- Respeta la configuración de Visual Studio en cuanto a realizar llamadas a ToString en variables locales.

- Se ha agregado un nuevo menú Depurar -> Adjuntar depurador de Unity, que puede utilizar para depurar reproductores de Unity.

- Se conservan los proyectos personalizados agregados a la solución de UnityVS tras generar los archivos de la solución.

- Se ha agregado un nuevo método abreviado de teclado CTRL+ALT+M -> CTRL+H para mostrar la documentación de Unity para la función de Unity o el miembro en la posición del cursor de inserción.

- Se tienen en cuenta los archivos de respuesta del compilador (rsp) al compilar desde Visual Studio.

- Se deconstruyen los tipos generados por el compilador para mostrar las variables al depurar los métodos de generador.

- Se simplifica la depuración remota eliminando la necesidad de configurar una carpeta compartida para Unity. Ahora solo necesita tener acceso a su proyecto de Unity desde Windows.

- Instale un perfil de Unity personalizado como perfil de destino .NET estándar. Esto corrige todos los falsos positivos que podía mostrar ReSharper.

- Se ha encontrado una solución alternativa a un error del motor de scripting de Unity para que el depurador no se interrumpa al encontrar subprocesos que no se hayan registrado debidamente.

- Se ha modificado el abridor de archivos para evitar una condición de carrera en VS por la que alegaba ser capaz de abrir archivos, pero se bloqueaba durante una solicitud de apertura de archivo.

- UnityVS ya no solicita actualizar la compilación al guardar el archivo, sino cuando VS compila el proyecto.

### <a name="bug-fixes"></a>Correcciones de errores

- Se ha corregido el perfil .NET personalizado.

- Se ha corregido la integración de temas, lo que termina con los problemas relacionados con el tema oscuro de VS 2012.

- Se ha corregido el acceso directo rápido de comportamiento de VS 2012.

- Se ha corregido un problema de ejecución paso a paso que podía producirse con la depuración y si un subproceso no principal alcanzaba un punto de interrupción.

- Se ha corregido la finalización de UnityScript y Boo de alias de tipo, como int.

- Se ha corregido una excepción que se generaba al escribir una nueva cadena UnityScript o Boo.

- Se han corregido las excepciones en los menús de Unity que se generaban cuando no se cargaba una solución.

- Se ha corregido el UVS-48: escribir dobles comillas a veces produce un error e interrumpe todas las funciones (finalización de código, resaltado de sintaxis, etc.).

- Se ha corregido el error UVS-46: Archivo de script abierto duplicado (UnityScript) al hacer clic en la Lista de errores de Visual Studio.

- Se ha corregido el error UVS-42: El logotipo de conectividad de Unity de la barra de estado no procesa eventos de mouse en VS 2012.

- Se ha corregido el error UVS-44: CTRL+MAYÚS+Q no está disponible en VS 2012 para clases MonoBehaviour rápidas.

- Se ha corregido el error UVS-40: Los elementos seleccionados en el Explorador de proyectos de Unity no se pueden leer si la ventana está inactiva en el tema "oscuro" de VS2012.

- Se ha corregido el error UVS-39: Problema al convertir cadenas de caracteres de escape en tokens.

- Se ha corregido el error UVS-35: Invocar ToString en objetos al inspeccionar variables.

- Se ha corregido el error UVS-27: Incoherencia de la ventana Ir al símbolo con el tema "oscuro" en VS2012.

- Se ha corregido el error UVS-11: Variables locales en las corrutinas.

## <a name="1100---beta-release"></a>1.1.0.0 (versión beta)
Publicado el 9 de marzo de 2013

## <a name="10130"></a>1.0.13.0
Publicado el 21 de enero de 2013

### <a name="bug-fixes"></a>Correcciones de errores

- Se ha corregido un bloqueo de Visual Studio que podía ocurrir si el código depurado de destino enviaba eventos de subproceso no válidos. Esto solía pasar al depurar un Unity remoto en OSX.

- Se ha corregido un bloqueo de Visual Studio que podía ocurrir si una excepción apagaba el depurador.

- Se han corregido nuestros asistentes de MonoBehavior cuando un MonoBehavior en C# se encuentra en un espacio de nombres.

- Se ha corregido la información sobre herramientas del depurador de UnityScript en Visual Studio 2012.

- Se ha corregido la generación de proyecto cuando solo se cambian constantes de depuración desde Unity.

- Se ha corregido la navegación mediante teclado en el Explorador de proyectos de Unity.

- Se ha corregido el coloreado de UnityScript para las cadenas de escape.

- Se ha corregido nuestro abridor de archivos para que adivine mejor el nombre del proyecto cuando se utiliza fuera de Unity. Eso es necesario cuando el usuario utiliza un abridor de archivos de terceros en Unity que delega a UnityVS.

- Se ha corregido el procesamiento de mensajes largos enviados desde Unity a UnityVS. Antes de solucionar este problema, los mensajes largos podían bloquear nuestra parte de mensajería de UnityVS. Como consecuencia, a veces UnityVS no abría un archivo desde Unity.

## <a name="10120"></a>1.0.12.0
Publicado el 3 de enero de 2013

### <a name="bug-fixes"></a>Correcciones de errores

- Se ha corregido el bloqueo de Visual Studio que podía producirse cuando Visual Studio estaba eliminando un punto de interrupción.

- Se ha corregido un error por el que algunos puntos de interrupción no se alcanzaban después de que Unity volviese a compilar los scripts de juegos.

- Se ha corregido el depurador para que notifique correctamente a Visual Studio cuando haya puntos de interrupción no enlazados.

- Se ha corregido un problema del registro que podía impedir que el depurador de Visual Studio depurase programas nativos.

- Se ha corregido una excepción que podía generarse al evaluar expresiones de UnityScript y Boo.

- Se ha corregido una regresión en la que el cambio de nivel de API de .NET en Unity no desencadenaría una actualización de los archivos de proyecto.

- Se ha corregido un problema de la API por el que el código de usuario no podía participar en el controlador de devolución de llamada de registro.

## <a name="10110"></a>1.0.11.0
Publicado el 28 de noviembre de 2012

### <a name="new-features"></a>Características nuevas

- Soporte oficial de Unity 4.

- Manipulación de scripts desde el Explorador de proyectos de Unity.

- Integración en la ventana Navegar a de Visual Studio.

- Se analiza el mensaje de la consola de información, para que al hacer clic en la Lista de errores, acceda a la primera stackframe que tenga símbolos.

- Se ha agregado una [API](../cross-platform/customize-project-files-created-by-vstu.md) para dejar al usuario participar en la generación del proyecto.

- Se ha agregado una [API](../cross-platform/share-the-unity-log-callback-with-vstu.md) para dejar al usuario participar en la LogCallback.

### <a name="bug-fixes"></a>Correcciones de errores

- Se ha corregido la regresión en segundo plano del Explorador de proyectos de Unity en Visual Studio 2012.

- Se ha corregido la generación de proyectos de usuarios del perfil .NET completo.

- Se ha corregido la generación de proyectos para usuarios del destino web.

- Se ha corregido la generación de proyectos para que incluya símbolos de DEPURAR y RASTREAR tal como hace Unity.

- Se ha corregido el bloqueo que se producía al usar caracteres especiales en la ventana de símbolo de Ir a.

- Se ha corregido el bloqueo que se producía si no podíamos inyectar nuestro icono en la barra de estado de Visual Studio.

## <a name="10100"></a>1.0.10.0
Publicado el 9 de octubre de 2012

### <a name="bug-fixes"></a>Correcciones de errores

- Se ha corregido el segundo plano del Explorador de proyectos de Unity en Visual Studio 2010.

- Se ha corregido una inmovilización de Visual Studio que podía producirse si UnityVS intentaba adjuntar el depurador a un Unity con una interfaz de depurador que se hubiese bloqueado anteriormente.

- Se ha corregido una inmovilización de Visual Studio que podía producirse cuando se había establecido un punto de interrupción y se recargaba AppDomain.

- Se ha corregido cómo se recuperan los ensamblados desde Unity para evitar el bloqueo de archivos y confusiones durante el proceso de compilación de Unity.

## <a name="1090"></a>1.0.9.0

Publicado el 3 de octubre de 2012

### <a name="bug-fixes"></a>Correcciones de errores

- Se ha corregido la generación de proyectos cuando el proyecto de Unity incluye activos reales de JavaScript.

- Se ha corregido el control de errores en la evaluación de expresiones.

- Se ha corregido el establecimiento de nuevos valores en campos de tipos de valor.

- Se han corregido los efectos secundarios que se podían producir al colocar el puntero del mouse sobre expresiones del editor de código.

- Se ha corregido cómo se buscan los tipos en los ensamblados cargados para la evaluación de expresiones.

- Se ha corregido el error UVS-21: La evaluación de asignación en objetos de Unity no tiene ningún efecto.

- Se ha corregido el error UVS-21: Puntero no válido al evaluar una invocación de método a la API Math de Unity.

## <a name="1080"></a>1.0.8.0

Publicado el 26 de septiembre de 2012

### <a name="bug-fixes"></a>Correcciones de errores

- Se ha corregido la forma en que nuestro abridor de scripts adquiere la ruta de acceso al proyecto para asegurarse de que sea capaz de abrir Visual Studio y los scripts.

- Se ha corregido un error por el que se creaban puntos de interrupción mientras se estaba ejecutando la sesión de depuración, que podía dar lugar al bloqueo de Visual Studio.

- Se ha corregido cómo se registra UnityVS en Visual Studio 2010.

## <a name="1070"></a>1.0.7.0

Publicado el 14 de septiembre de 2012

### <a name="new-features"></a>Características nuevas

- Soporte de Visual Studio 2012.

### <a name="bug-fixes"></a>Correcciones de errores

- Se ha corregido la generación de archivos de proyectos de complementos y del Editor para que coincida con el comportamiento de Unity.

- Se ha corregido la traducción de los símbolos .pdb en Unity 4.

> [!IMPORTANT]
> Debido a la compatibilidad con Visual Studio 2012, tuvimos que cambiar el nombre de algunos archivos y mover otros. El paquete de UnityVS para importar Unity ahora se llama UnityVS 2010 o UnityVS 2012, para Visual Studio 2010 y Visual Studio 2012 respectivamente. Esta versión también requiere que se vuelvan a generar los archivos de proyecto de UnityVS.

## <a name="1060---internal-build"></a>1.0.6.0 (compilación interna)
Publicado el 12 de septiembre de 2012

## <a name="1050"></a>1.0.5.0

Publicado el 10 de septiembre de 2012

### <a name="bug-fixes"></a>Correcciones de errores

- Se ha corregido la generación de archivos de proyecto cuando los scripts o sombreadores tenían un carácter xml no válido.

- Se ha corregido la detección de instancias de Unity cuando Unity estaba conectado al servidor de activos. Esto producía errores al abrir archivos desde Unity y la conexión automática del depurador de Visual Studio.

## <a name="1040"></a>1.0.4.0

Publicado el 5 de septiembre de 2012

### <a name="new-features"></a>Características nuevas

- Conversión automática de símbolos de depuración en Unity.

    Si tiene un ensamblado .dll de .NET con su .pdb asociado en la carpeta de activos, simplemente vuelva a importar el ensamblado y UnityVS convertirá el archivo .pdb en un archivo de símbolos de depuración que comprende el motor de scripting de Unity. De este modo, podrá acceder a los ensamblados de .NET desde UnityVS.

### <a name="bug-fixes"></a>Correcciones de errores

- Se ha corregido el bloqueo de UnityVS que tenía lugar durante la depuración como consecuencia de excepciones producidas por métodos o propiedades ubicadas dentro de Unity.

## <a name="1030"></a>1.0.3.0

Publicado el 4 de septiembre de 2012

### <a name="new-features"></a>Características nuevas

- Nueva opción de configuración para deshabilitar el uso de UnityVS para abrir archivos desde Unity.

### <a name="bug-fixes"></a>Correcciones de errores

- Se ha corregido la generación de referencias a UnityEditor para proyectos que no sean del editor.

- Se ha corregido la definición del símbolo UNITY_EDITOR para proyectos que no sean del editor.

- Se ha corregido el bloqueo aleatorio de VS causado por nuestra barra de estado personalizada.

## <a name="1020"></a>1.0.2.0

Publicado el 30 de agosto de 2012

### <a name="bug-fixes"></a>Correcciones de errores

- Se ha corregido el conflicto con el depurador de PythonTools.

- Se han corregido las referencias a Mono.Cecil.

- Se ha corregido el error sobre cómo se recuperaban los ensamblados de scripting desde Unity mediante Unity 4.

## <a name="1010"></a>1.0.1.0

Publicado el 28 de agosto de 2012

### <a name="new-features"></a>Características nuevas

- Compatibilidad con la vista previa de Unity 4.0 Beta.

### <a name="bug-fixes"></a>Correcciones de errores

- Se ha corregido la inspección de propiedades que producen excepciones.

- Se ha corregido el descenso a objetos base al inspeccionar objetos.

- Se ha corregido la lista desplegable en blanco del punto de inserción en el asistente de MonoBehavior.

- Se ha corregido la finalización de archivos .dll dentro de la carpeta de activos para UnityScript y Boo.

## <a name="1000---initial-release"></a>1.0.0.0 (versión inicial)
Publicado el 22 de agosto de 2012
