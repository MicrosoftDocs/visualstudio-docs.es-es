---
title: Registro de cambios (Visual Studio Tools para Unity, Mac) | Microsoft Docs
ms.custom: ''
ms.date: 5/19/2020
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: e817318f7b16040ed598ac4dce8f1c6017bdf83e
ms.sourcegitcommit: 43df639b2cd99200f725a8ebb941477481a6f0ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2020
ms.locfileid: "87471537"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Registro de cambios (Visual Studio Tools para Unity, Mac)

Registro de cambios de Visual Studio Tools para Unity.

## <a name="2710"></a>2.7.1.0
Publicado el 5 de agosto de 2020

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - API de mensajes de Unity actualizada a 2019.4.

  - Se ha agregado el supresor [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md) para `CA1823`. Los campos privados con los atributos `SerializeField` o `SerializeReference` no deben marcarse como sin usar (FxCop).
  
  - Se ha agregado el supresor [`USP0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0014.md) para `CA1822`. Los mensajes de Unity no deben marcarse como candidatos para el modificador `static` (FxCop).

  - Se ha agregado el supresor [`USP0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0015.md) para `CA1801`. Los parámetros sin utilizar no se deben quitar de los mensajes de Unity (FxCop).
  
  - Se ha agregado compatibilidad de `MenuItem` con el supresor [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md).  

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se han corregido los supresores [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) y [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) que no funcionaban con paréntesis adicionales o con argumentos de método.
  
  - Se ha corregido la actualización obligatoria de la base de datos de recursos incluso cuando la actualización automática estaba deshabilitada en la configuración de Unity.

## <a name="2700"></a>2.7.0.0
Publicado el 23 de junio de 2020

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad para conservar carpetas de soluciones mientras Unity regenera la solución y proyectos.

  - Se ha agregado el diagnóstico [`UNT0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0015.md). Detecte una signatura del método incorrecta con el atributo `InitializeOnLoadMethod` o `RuntimeInitializeOnLoadMethod`.

  - Se ha agregado el diagnóstico [`UNT0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0016.md). El uso de `Invoke`, `InvokeRepeating`, `StartCoroutine` o `StopCoroutine` con un literal de cadena como primer argumento no posee seguridad de tipos.

  - Se ha agregado el diagnóstico [`UNT0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0017.md). La invocación `SetPixels` es lenta.

### <a name="bug-fixes"></a>Correcciones de errores

- **Depurador:**

  - Se ha corregido la creación de puntos de interrupción mientras el juego se ejecuta en el entorno de ejecución Mono anterior (intentando enlazar el punto de interrupción nada más crearse). 
  
- **Integración:**

  - No restablezca la selección al filtrar mensajes en el asistente de mensajes de Unity.
  
  - Se han corregido los supresores [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md), [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) y [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) con las siguientes reglas: suprima `IDE0044` (solo lectura), `IDE0051` (sin usar), `CS0649` (nunca se asignó) en todos los campos decorados con el atributo SerializeField. Suprima `CS0649` (nunca se asignó) en los campos públicos de todos los tipos que amplían `Unity.Object`.

  - Se ha corregido la comprobación de los parámetros de tipo genérico para  [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md).

- **Evaluación:**

  - Se ha corregido la comparación de igualdad con enumeraciones.

## <a name="2610"></a>2.6.1.0
Fecha de publicación: 19 de mayo de 2020

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se advierte si no se puede crear el servidor de mensajería en el lado de Unity.

  - Los analizadores se ejecutan correctamente durante la compilación ligera.

  - Se corrigió la documentación sobre API con instalaciones de Unity Hub.
  
  - Se corrigieron los bloqueos del visualizador del depurador.

## <a name="2600"></a>2.6.0.0
Fecha de publicación: 14 de abril de 2020

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se agregó el diagnóstico [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0012.md). Detecte y ajuste las llamadas a las corrutinas en `StartCoroutine()`.

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

  - Se corrigió el control de instrucciones Using con alias.
  
  - Se corrigió el control de valores NULL.  

## <a name="2520"></a>2.5.2.0

Fecha de publicación: 23 de marzo de 2020

### <a name="bug-fixes"></a>Correcciones de errores

- **Depurador:**

  - Se ha corregido el registro de subprocesos al realizar asociaciones.

## <a name="2510"></a>2.5.1.0

Fecha de publicación: 3 de marzo de 2020

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado el supresor [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md) para `IDE0051`. Los métodos privados usados con Invoke, InvokeRepeating, StartCoroutine o StopCoroutine no se deben marcar como sin usar.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido la documentación sobre OnDrawGizmos/OnDrawGizmosSelected.

- **Evaluación:**

  - Se ha corregido la inspección del argumento lambda.

## <a name="2501"></a>2.5.0.1

Fecha de publicación: 19 de febrero de 2020

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido la comprobación de diagnósticos [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) para la signatura de mensaje incorrecta. Al inspeccionar tipos con varios niveles de herencia, este diagnóstico podría producir un error con el mensaje siguiente: `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added`.

## <a name="2500"></a>2.5.0.0

Fecha de publicación: 22 de enero de 2020

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad con archivos HLSL.
  
  - Se ha implementado una nueva interfaz de usuario para el cuadro de diálogo de nueva carpeta.
  
  - Se ha implementado una cuadrícula de propiedades nueva y accesible para la configuración.

  - Se agregó el supresor [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) para `IDE0051`. Los campos privados con el atributo `SerializeField` no deben marcarse como sin usar.

  - Se ha agregado el supresor [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) para `CS0649`. Los campos con el atributo `SerializeField` no deben marcarse como sin asignar.  

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se corrigió la generación de proyectos (el destino de `GenerateTargetFrameworkMonikerAttribute` no siempre se encontraba correctamente).

- **Evaluación:**

  - Se ha corregido la evaluación de cadenas (sin usar llamadas a ToString()).

## <a name="2420"></a>2.4.2.0

Fecha de publicación: 3 de diciembre de 2019

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Diagnósticos corregidos con interfaces definidas por el usuario.

  - Información sobre herramientas rápida corregida con expresiones con formato incorrecto.
  
## <a name="2410"></a>2.4.1.0

Fecha de publicación: 6 de noviembre de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad con los procesos en segundo plano de Unity. (El depurador puede conectarse automáticamente al proceso principal en lugar de a un proceso secundario).

  - Se ha agregado una información sobre herramientas rápida para mensajes de Unity que muestran la documentación asociada.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido el analizador de comparación de etiquetas `UNT0002` con expresiones binarias y de invocación avanzadas.

### <a name="deprecated-features"></a>Características en desuso

- **Integración:**

  - A partir de ahora, Visual Studio Tools para Unity solo admitirá Visual Studio 2017+.

## <a name="2400"></a>2.4.0.0

Fecha de publicación: 15 de octubre de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado el supresor [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) para `IDE0060` (parámetro sin usar) para todos los mensajes de Unity.

  - Se ha agregado una información sobre herramientas rápida para los campos etiquetados con `TooltipAttribute`. (Esto funcionará para un descriptor de acceso get sencillo mediante este campo también).

## <a name="2330"></a>2.3.3.0

Fecha de publicación: 23 de septiembre de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado un nuevo supresor para IDE0060, con el fin de evitar que el IDE muestre una corrección rápida para quitar los parámetros sin usar.
    - `USP0005` para `IDE0060`: los mensajes de Unity se invocan mediante el tiempo de ejecución de Unity.

## <a name="2320"></a>2.3.2.0

Fecha de publicación: 16 de septiembre de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Hemos aumentado el reconocimiento que tiene Visual Studio para los proyectos de Unity mediante la adición de nuevos diagnósticos específicos para Unity. También hemos hecho que el entorno de desarrollo integrado sea más inteligente suprimiendo los diagnósticos generales de C# que no se aplican a los proyectos de Unity. Por ejemplo, el IDE no mostrará una corrección rápida para cambiar una variable del inspector a `readonly`, lo que le impediría modificar la variable en el editor de Unity.
    - `UNT0001`: El tiempo de ejecución llama a los mensajes de Unity aunque estén vacíos; no los declare para evitar el procesamiento innecesario por parte del tiempo de ejecución de Unity.
    - `UNT0002`: La comparación de etiquetas con la igualdad de cadenas es más lenta que el método CompareTag integrado.
    - `UNT0003`: Se prefiere el uso de la forma genérica de GetComponent para la seguridad de tipos.
    - `UNT0004`: El mensaje de actualización depende de la velocidad de fotogramas y debe usar Time.deltaTime en lugar de Time.fixedDeltaTime.
    - `UNT0005`: El mensaje de FixedUpdate no depende de la velocidad de fotogramas y debe usar Time.fixedDeltaTime en lugar de Time.deltaTime.
    - `UNT0006`: se ha detectado una firma de método incorrecta para este mensaje de Unity.
    - `UNT0007`: Unity invalida el operador de comparación NULL para objetos de Unity que es incompatible con el uso combinado de NULL.
    - `UNT0008`: Unity invalida el operador de comparación NULL para objetos de Unity que es incompatible con la propagación de tipo NULL.
    - `UNT0009`: Al aplicar el atributo InitializeOnLoad a una clase, debe proporcionar un constructor estático. El atributo InitializeOnLoad garantiza que se le llamará cuando se inicie el editor.
    - `UNT0010`: El componente MonoBehaviours solo debe crearse con AddComponent(). MonoBehaviour es un componente y debe adjuntarse a un elemento GameObject.
    - `UNT0011`: El componente ScriptableObject solo debe crearse con CreateInstance(). ScriptableObject debe crearse mediante el motor de Unity para controlar los métodos de mensajes de Unity.
    - `USP0001` para `IDE0029`: los objetos de Unity no deben usar la fusión nula.
    - `USP0002` para `IDE0031`: los objetos de Unity no deben usar la propagación nula.
    - `USP0003` para `IDE0051`: los mensajes de Unity se invocan mediante el tiempo de ejecución de Unity.
    - `USP0004` para `IDE0044`: los campos con un atributo SerializeField no deben ser de solo lectura.

## <a name="2310"></a>2.3.1.0

Fecha de publicación: 4 de septiembre de 2019

### <a name="new-features"></a>Características nuevas

- **Evaluación:**

  - Se ha agregado compatibilidad para mejorar la presentación de tipos, es decir, `List<object>` en lugar de `List'1[[System.Object, <corlib...>]]`.

  - Se ha agregado compatibilidad con el acceso a miembros de puntero, es decir, `p->data->member`.

  - Se ha agregado compatibilidad con las conversiones implícitas en inicializadores de matriz, es decir, `new byte [] {1,2,3,4}`.

  - Se ha agregado compatibilidad con el editor hexadecimal al inspeccionar matrices y cadenas de bytes.

## <a name="2300"></a>2.3.0.0

Fecha de publicación: 13 de agosto de 2019

### <a name="bug-fixes"></a>Correcciones de errores

- **Evaluación:**

  - Se han corregido los problemas de ejecución paso a paso con excepciones.

  - Se ha corregido la evaluación de los pseudoidentificadores (como $exception).

  - Se ha evitado el bloqueo al desreferenciar direcciones no válidas.  

  - Se ha corregido el problema con los dominios de aplicación descargados.

## <a name="2200"></a>2.2.0.0

Publicado el 25 de julio de 2019

### <a name="bug-fixes"></a>Correcciones de errores

- **Evaluación:**

  - Se ha corregido la inspección con los tipos IntPtr.

- **Depurador:**

  - Se ha corregido el control de puntos de captura y puntos de interrupción de función.

## <a name="2130"></a>2.1.3.0

Publicado el 9 de julio de 2019

### <a name="new-features"></a>Características nuevas

- **Depurador:**

  - Se ha agregado compatibilidad con la captura de subclases de excepciones.

  - Se ha agregado compatibilidad con el protocolo MDS 2.51.

- **Integración:**

  - Se ha agregado compatibilidad con archivos asmdef.

  - Cambio al modo de cambio de nombre cuando se agrega un archivo desde una plantilla (para imitar el comportamiento del editor de Unity).

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido el control de los mensajes con formato incorrecto al comunicarse con reproductores de Unity.

- **Evaluación:**

  - Se ha corregido el control de los espacios de nombres en las expresiones.

## <a name="2120"></a>2.1.2.0

Publicado el 2 de julio de 2019

### <a name="bug-fixes"></a>Correcciones de errores

- **Evaluación:**

  - Se ha corregido la generación de informes de errores con expresiones no analizables.

## <a name="2110"></a>2.1.1.0

Publicado el 27 de junio de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha actualizado la API MonoBehaviour a 2019.1.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido el rendimiento del explorador de proyectos de Unity.

  - Se ha corregido la notificación de advertencias y errores que se genera cuando está habilitada la compilación ligera.

  - Se ha corregido el rendimiento de la compilación ligera.

## <a name="2100"></a>2.1.0.0

Publicado el 20 de junio de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha deshabilitado la compilación completa para los proyectos de Unity, en favor del uso de los errores y advertencias de IntelliSense. De hecho, Unity crea una solución de Visual Studio con proyectos de biblioteca de clases que representan lo que Unity hace internamente. Dicho esto, el resultado de la compilación en Visual Studio nunca se utiliza o selecciona por Unity, ya que su canal de compilación está cerrado. La compilación en Visual Studio solo está consumiendo recursos para nada. Si necesita una compilación completa porque tiene herramientas o una configuración que dependen de ella, puede deshabilitar esta optimización (Herramientas/Opciones/Tools para Unity/Deshabilitar la compilación completa de proyectos).
  
  - Se ha agregado compatibilidad para paquetes de Unity en el Explorador de proyectos de Unity. Solo son visibles los paquetes a los que se hace referencia (mediante manifest.json en la carpeta `Packages`) y los paquetes locales (insertados en la carpeta `Packages`).

## <a name="2021"></a>2.0.2.1

Publicado el 30 de mayo de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado un icono personalizado para los destinos de ejecución de Unity.

## <a name="2020"></a>2.0.2.0

Publicada el 2 de abril de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad con la actualización automática de la base de datos de recursos de Unity al guardarla. Esta característica está habilitada de forma predeterminada y desencadenará una recompilación en el lado de Unity al guardar un script en Visual Studio. Puede deshabilitar esta característica en la base de datos de recursos ubicada en Tools\Options\Tools for Unity\Refresh al guardarla.

  - Se ha agregado compatibilidad para configurar la instalación de Unity preferida para la documentación sin conexión.

  - Se ha agregado un menú contextual para el nuevo editor.

### <a name="bug-fixes"></a>Correcciones de errores

- **Depurador:**

  - Se han corregido el filtrado de ensamblados y la inspección de marcos con marcos vacíos.

## <a name="2011"></a>2.0.1.1
 
 Publicada el 26 de marzo de 2019

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Convertir Mono temporalmente en la opción predeterminada y solo usar el depurador para esta versión tan específica.

## <a name="2006"></a>2.0.0.6

Publicada el 26 de marzo de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad con "Asociar a Unity y reproducir".

## <a name="2005"></a>2.0.0.5

Publicada el 20 de marzo de 2019

### <a name="new-features"></a>Características nuevas

- **Project Generation:**

  - Conservar las propiedades externas al procesar el archivo de solución.
  
- **Evaluación:**

  - Se ha agregado compatibilidad para nombres calificados con el alias (solo el espacio de nombres global por ahora). Así pues, el evaluador de expresiones acepta ahora tipos con el formato global::namespace.type.

  - Se ha agregado compatibilidad con el formato `pointer[index]`, que es semánticamente idéntico al formato `*(pointer+index)` de desreferencia de puntero.

## <a name="2004"></a>2.0.0.4

Publicada el 5 de marzo de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha actualizado la API `ScriptableObject`.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se han quitado los espacios de nombres de las plantillas.

## <a name="2003"></a>2.0.0.3
 
 Publicada el 5 de marzo de 2019

### <a name="new-features"></a>Características nuevas

- **Project Generation:**

  - Los campos públicos y serializados ya no generarán advertencias. Hemos suprimido automáticamente las advertencias del compilador `CS0649` y `IDE0051` en los proyectos de Unity que crearon estos mensajes.

- **Integración:**

  - Solicitud de conexión a una instancia específica si hay más de un proceso de Unity en ejecución.

- **Evaluación:**

  - Se ha agregado compatibilidad con las funciones locales.

### <a name="bug-fixes"></a>Correcciones de errores

- **Depurador:**

  - Se ha corregido la lectura de atributos personalizados de los argumentos con nombre al usar versiones de protocolo anteriores.

## <a name="2002"></a>2.0.0.2

Publicada el 4 de febrero de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha actualizado la API MonoBehaviour.

### <a name="bug-fixes"></a>Correcciones de errores

- **Depurador:**

  - Se ha corregido la configuración de los valores primitivos en el depurador.

## <a name="2001"></a>2.0.0.1

Publicada el 4 de diciembre de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido la contención automática del paquete de instalación.

## <a name="2000"></a>2.0.0.0
 Publicada el 4 de diciembre de 2018

### <a name="new-features"></a>Características nuevas

- **Depurador:**

  - Se ha reemplazado el depurador de Unity de Mac por el mismo depurador de Unity básico de Windows.

  - Se ha reemplazado NRefactory a favor de Roslyn para la evaluación de expresiones.

  - Se ha agregado compatibilidad con los punteros: desreferencia, conversión y aritmética de puntero (tanto Unity 2018.2+ y el nuevo tiempo de ejecución son necesarios para esto).

  - Se ha agregado compatibilidad con la vista del puntero de matrices (como en C++). Adopte una expresión de puntero y, a continuación, anexe una coma y el número de elementos que desea ver.

  - Se ha agregado compatibilidad con las construcciones asincrónicas.

  - Se ha agregado compatibilidad con las pseudovariables (identificadores de excepción y objetos).

### <a name="bug-fixes"></a>Correcciones de errores

- **Depurador:**

  - Se ha corregido la evaluación de expresiones con expresiones con un formato incorrecto o no admitidas.

## <a name="1700"></a>1.7.0.0

Publicado el 13 de noviembre de 2018

### <a name="new-features"></a>Características nuevas

- **Depurador:**

  - Se ha agregado más información del cliente (IP, nombre del equipo) en el cuadro de diálogo Adjuntar.

### <a name="bug-fixes"></a>Correcciones de errores

- **Depurador:**

  - Se ha corregido un interbloqueo en la biblioteca usada para comunicarse con el motor de depuración de Unity, que hacía que Visual Studio o Unity se congelara, especialmente al ejecutar 'Asociar a Unity' o reiniciar el juego.

- **Integración:**

  - Se ha corregido la activación de los complementos de Unity cuando se seleccionaba otro editor predeterminado.

  - Se ha corregido la creación de plantillas de archivo de Unity.

## <a name="1602"></a>1.6.0.2

Publicado el 24 de julio de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se revirtió la solución a un error de rendimiento de Unity que se ha corregido en Unity.

## <a name="1601"></a>1.6.0.1

Publicado el 10 de julio de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Corrección de la compatibilidad con la coloración del sombreador.

## <a name="1600"></a>1.6.0.0

Publicado el 26 de junio de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Asistentes:**

  - Corrección de un error ortográfico en el mensaje OnApplicationFocus.

- **Project Generation:**

  - Solución alternativa temporal de un error de rendimiento de Unity: MonoIslands en caché al generar proyectos.

  - No convierta más archivos PDB portátiles a MDB con el nuevo entorno de ejecución de Unity.

## <a name="1502"></a>1.5.0.2

Publicado el 18 de abril de 2018

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado la compatibilidad con la finalización del código básico del sombreador.

  - Se ha agregado la compatibilidad con la alternancia de comentarios en los archivos del sombreador.

## <a name="1501"></a>1.5.0.1

Publicado el 28 de marzo de 2018

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad con las plantillas adicionales en el Explorador de proyectos de Unity.

## <a name="1500"></a>1.5.0.0

Publicado el 21 de marzo de 2018

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad con la detección y conexión de reproductores Android conectados a través de USB.

## <a name="1403"></a>1.4.0.3

Publicado el 5 de marzo de 2018

### <a name="new-features"></a>Características nuevas

- **Project Generation:**

  - Se ha agregado compatibilidad con el nuevo generador de proyectos en Unity 2018.1.

- **Integración:**

  - Se ha agregado un panel de opciones para la configuración dedicada.

## <a name="1402"></a>1.4.0.2

Publicado el 24 de enero de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Project Generation:**

  - Se ha corregido la detección de la versión de Mono.

- **Integración:**

  - Se han corregido problemas de temporización con 2018.1 y la activación de complementos.

  - Se han corregido las notificaciones cuando se detecta un nuevo reproductor.

## <a name="1401"></a>1.4.0.1

Publicado el 23 de enero de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido la expansión o contracción de carpetas al hacer doble clic.

## <a name="1400"></a>1.4.0.0

Publicado el 13 de diciembre de 2017

### <a name="new-features"></a>Características nuevas

- **Project Generation:**

  - Se ha agregado compatibilidad con .NET Standard.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se corrigió la conversión del símbolo de depuración de pdb automático a mdb.

## <a name="1301"></a>1.3.0.1

Publicado el 12 de diciembre de 2017

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido la llamada indirecta a EditorPrefs.GetBool que afecta al inspector al tratar de cambiar el tamaño de la matriz.

- **Asistentes:**

  - Actualice el contexto de Roslyn antes de insertar el método.

## <a name="1300"></a>1.3.0.0

Publicado el 20 de noviembre de 2017

### <a name="new-features"></a>Características nuevas

- **Asistentes:**

  - Se ha agregado el asistente "Implementar mensaje de Unity".

  - Se ha agregado compatibilidad con la nueva API de finalización en VS para Mac 7.4.

## <a name="1200"></a>1.2.0.0

Publicado el 23 de octubre de 2017

### <a name="new-features"></a>Características nuevas

- **Depurador:**

  - Se ha agregado compatibilidad con archivos de símbolo de depuración portátiles.

### <a name="bug-fixes"></a>Correcciones de errores

- **Project Generation:**

  - Se ha corregido un problema por el que la extensión .dll se agregaba erróneamente al nombre de archivo de ensamblado.

  - No fuerce el uso de la marca AllowAttachedDebuggingOfEditor de Unity, ya que el valor predeterminado es ahora "true".

## <a name="1103"></a>1.1.0.3

Publicado el 23 de octubre de 2017

### <a name="new-features"></a>Características nuevas

- **Project Generation:**

  - Se ha agregado compatibilidad con el perfil de .NET 4.6.

## <a name="1102"></a>1.1.0.2

Publicado el 8 de agosto de 2017

### <a name="new-features"></a>Características nuevas

- **Depurador:**

  - Se inicia el cuadro de diálogo Asociar al proceso si no se está seguro de a qué Unity se asocia.

- **Project Generation:**

  - Habilite siempre el modificador de compilación no seguro cuando se use Unity 5.6.

## <a name="1101"></a>1.1.0.1

Publicado el 20 de julio de 2017

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad con los recursos localizados.

## <a name="1100"></a>1.1.0.0

Publicado el 12 de julio de 2017

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad con la asociación a reproductores y editores a través de la ventana Asociar al proceso.

- **Project Generation:**

  - Se corrigieron las referencias al nombre de ensamblado con archivos mcs.rsp.

  - Se agregó compatibilidad con las unidades de compilación assembly.json.

  - Se corrigieron las definiciones con niveles de API.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido un mensaje de error del sombreador al compilar.

## <a name="1001"></a>1.0.0.1

Publicado el 4 de mayo de 2017

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido el seguimiento del documento activo con proyectos híbridos y normales.

## <a name="1000"></a>1.0.0.0

Publicado el 3 de mayo de 2017
