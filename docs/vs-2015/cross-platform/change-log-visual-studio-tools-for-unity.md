---
title: Registro de cambios (Visual Studio Tools para Unity) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
caps.latest.revision: 14
author: conceptdev
ms.author: crdun
manager: ghogen
ms.openlocfilehash: f21a5491d1b0e23bff90ce0105b81eb6291ac7e5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807198"
---
# <a name="change-log-visual-studio-tools-for-unity"></a>Registro de cambios (Visual Studio Tools para Unity)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Registro de cambios de Visual Studio Tools para Unity.

## <a name="23"></a>2.3
 Lanzamiento 14-07-2016

### <a name="new-features"></a>Características nuevas

-   **General:**

    -   Se agregó una opción para deshabilitar los registros de la consola de Unity en la lista de errores de Visual Studio.

    -   Se agregó una opción para permitir la modificación de propiedades de proyectos generados.

-   **Depurador:**

    -   Se agregaron los visualizadores de cadenas de texto, XML, HTML y JSON.

-   **Asistentes:**

    -   Se agregaron MonoBehaviors que faltaban.

### <a name="bug-fixes"></a>Correcciones de errores

-   **General:**

    -   Se corrigió un conflicto con ReSharper que impedía que se mostraran controles dentro de la configuración de Visual Studio.

    -   Se corrigió un conflicto con Xamarin que impedía la depuración en algunos casos.

-   **Depurador:**

    -   Se ha corregido un problema que provocó Visual Studio se bloqueara durante la depuración.

    -   Se corrigió un problema con los puntos de interrupción de función en Visual Studio 2015.

    -   Se corrigieron varios problemas de evaluación de expresiones.

## <a name="22"></a>2.2
 Lanzamiento 04-02-2016

### <a name="new-features"></a>Características nuevas

-   **Asistentes:**

    -   Se ha agregado búsqueda inteligente en el asistente **Implementar MonoBehavior** .

    -   Hace que los asistentes tengan en cuenta el contexto; por ejemplo, los mensajes de NetworkBehavior solo están disponibles cuando se trabaja con un elemento NetworkBehavior.

    -   Se ha agregado compatibilidad con mensajes de NetworkBehavior en los asistentes.

-   **IU:**

    -   Se ha agregado una opción para configurar la visibilidad de los mensajes de MonoBehavior.

    -   Se han quitado páginas de propiedades de Visual Studio que no son relevantes para los proyectos de Unity.

### <a name="bug-fixes"></a>Correcciones de errores

-   **Generación de proyectos:**

    -   Se han corregido las referencias a UnityEngine y UnityEditor en Unity 4.6.

    -   Se ha corregido la generación de archivos de proyecto cuando Unity se está ejecutando en OSX.

    -   Se ha corregido el control de nombres de proyecto que contienen caracteres de almohadilla (#).

    -   Se han restringido los proyectos generados a C# 4,

-   **Depurador:**

    -   Se ha corregido un problema con la evaluación de expresiones durante la depuración dentro de un corrutina de Unity.

    -   Se ha corregido un problema que provocó Visual Studio se bloqueara durante la depuración.

-   **IU:**

    -   Se ha corregido una incompatibilidad con la extensión de Visual Studio [Tabs Studio](https://tabsstudio.com/) .

-   **Instalador:**

    -   Se admite la instalación en todo el equipo de VSTU (instalación para todos los usuarios) mediante la creación de entradas del Registro HKLM.

    -   Se han corregido problemas con la desinstalación de VSTU cuando está instalada la misma versión de VSTU en varias versiones distintas de Visual Studio. Por ejemplo, cuando se han instalado VSTU **2015** 2.1.0.0 y VSTU **2013** 2.1.0.0.

## <a name="21"></a>2.1
 Lanzamiento el 08-09-2015

### <a name="new-features"></a>Características nuevas

-   Compatibilidad con Unity 5.2

### <a name="bug-fixes"></a>Correcciones de errores

-   Mostrar elementos de menú en Unity < 4.2

-   Cuando Visual Studio bloquea los archivos de Intellisense XML, ya no aparece ningún mensaje de error.

-   Los puntos de interrupción condicionales <\<When Changed>> se controlan cuando el argumento condicional no es un valor booleano.

-   Referencias fijas a ensamblados UnityEngine y UnityEditor para las aplicaciones de la Tienda Windows.

-   Error fijo al entrar en el depurador: No se puede administrar, excepción general.

-   Puntos de interrupción de recuento de visitas fijas en Visual Studio 2015.

## <a name="20"></a>2.0
 Lanzamiento el 20-07-2015

### <a name="bug-fixes"></a>Correcciones de errores

-   **Integración de Unity:**

    -   Conversión fija de símbolos de depuración creados con Visual Studio de 2015 al importar un archivo DLL y sus símbolos de depuración (PDB).

    -   Siempre se generan archivos MDB al importar un archivo DLL y sus símbolos de depuración (PDB), excepto cuando también se proporciona un archivo MDB.

    -   Contaminación fija del directorio del proyecto de Unity con un directorio obj.

    -   Generación fija de referencias a System.Xml.Link y System.Runtime.Serialization.

    -   Compatibilidad agregada con varios suscriptores a los enlaces de API de generación del archivo del proyecto.

    -   Generación del archivo de proyecto siempre completo incluso cuando se bloquea uno de los archivos que se va a generar.

    -   Compatibilidad agregada con los caracteres comodín * en el filtro de extensión al especificar la inclusión de archivos en el proyecto de C#.

-   **Integración de Visual Studio**

    -   Corrección de un problema de compatibilidad con las herramientas de productividad avanzadas.

    -   Corrección de la generación de eventos relacionados con MonoBehaviors y declaraciones de delegados.

-   **Depurador:**

    -   Fijación de una inmovilización potencial en la depuración.

    -   Corrección de un problema de visualización de variables locales en determinados marcos de pila.

    -   Corrección de inspección de matrices vacías.

## <a name="20-preview-2"></a>2.0 Preview 2
 Lanzamiento 02-04-2015

### <a name="new-features"></a>Características nuevas

-   **Explorador de proyectos de Unity:**

    -   Cambia automáticamente el nombre de clase al cambiar el nombre de un archivo en el Explorador de proyectos de Unity (consulte el diálogo **Opciones** ).

    -   Selecciona automáticamente los scripts creados recientemente en el Explorador de proyectos de Unity.

    -   Realiza un seguimiento del script activo en el Explorador de proyectos de Unity (consulte el diálogo **Opciones** ).

    -   Realiza un sincronizado doble del Explorador de soluciones de Visual Studio (consulte el diálogo **Opciones** ).

    -   Se han adoptado los iconos de Visual Studio en el Explorador de proyectos de Unity.

-   **Depurador:**

    -   Selecciona el destino de depuración activo de una lista de destinos de depuración guardados o usados recientemente (consulte el diálogo **Opciones** ).

    -   Crea puntos de interrupción de funciones en los métodos MonoBehavior y los aplica a varias clases MonoBehavior.

    -   Permite crear el identificador del objeto en el depurador.

    -   Permite contar el número de llamadas del punto de interrupción.

    -   Admite interrupciones en caso de excepción en el depurador (Experimental. Consulte el diálogo **Opciones** ).

    -   Permite crear objetos y matrices al evaluar expresiones en el depurador.

    -   Permite comparar valores null al evaluar expresiones en el depurador.

    -   Filtra miembros obsoletos en las ventanas de inspección del depurador.

-   **Instalador:**

    -   Registro de extensiones de Visual Studio Tools para Unity optimizado.

    -   Instala el paquete de Visual Studio Tools para Unity para Unity 5.

-   **Documentación:** mejora el rendimiento de la generación de documentación.

-   **Asistentes:** compatibilidad con nuevos métodos de MonoBehavior Unity 4.6 y 5.

-   **Unity:** busca indicadores no seguros y personaliza definiciones en archivos .rsp durante la generación de archivos de proyecto.

-   **UI:** diálogo **Opciones** de Visual Studio Tools para Unity agregado en Visual Studio.

### <a name="bug-fixes"></a>Correcciones de errores

-   **Explorador de proyectos de Unity:**

    -   Se actualiza el Explorador de proyectos de Unity después de que se muevan archivos o se cambie el nombre de archivos desde el Explorador de soluciones de Visual Studio.

    -   Se conservan las selecciones al cambiar el nombre de archivos en el Explorador de proyectos de Unity.

    -   Se impide la expansión y contracción automáticas al hacer doble clic en archivos en el Explorador de proyectos de Unity.

    -   Se asegura de que los archivos recién seleccionados estén visibles en el Explorador de proyectos de Unity.

-   **Depurador:**

    -   Se evita una posible inmovilización de Visual Studio al evaluar expresiones en el depurador.

    -   Se asegura que las invocaciones de método se produzcan en el dominio adecuado en el depurador.

-   **Unity:**

    -   Se ha corregido la ubicación de UnityVS.OpenFile con Unity 5.

    -   Se ha corregido la ubicación de pdb2mdb con Unity 5.

    -   Se evita una posible excepción durante la generación de archivos del proyecto.

    -   Se evita una posible inmovilización al ejecutar Unity en OSX.

    -   Se controlan las excepciones internas.

    -   Se envían registros de la consola de Unity a la lista de errores de VS.

-   **Documentación:** se ha corregido la generación de documentación para la nueva documentación de Unity.

-   **Proyecto:** se mueven y se cambia el nombre de los archivos .meta de Unity cuando es necesario, incluso en las carpetas.

-   **Asistentes:** se ha corregido el orden de los parámetros de métodos MonoBehavior al generar código.

-   **UI:** compatible con temas de Visual Studio para iconos y menú contextual.

## <a name="20-preview"></a>2.0 Preview
 Lanzamiento 12-11-2014

### <a name="new-features"></a>Características nuevas

-   Compatible con Visual Studio 2015.

-   Coloreado de código para los sombreadores de Unity en Visual Studio 2015.

-   Visualización mejorada de valores al depurar:

    -   Mejor visualización de listas de matrices, listas, tablas hash y diccionarios.

    -   Muestra miembros no públicos y estáticos como categorías en las vistas locales y de inspección.

    -   Visualización mejorada de SerializedProperty de Unity para evaluar únicamente el campo de valor válido de la propiedad.

    -   Compatible con DebuggerDisplayAttribute para clases y estructuras.

    -   Compatible con DebuggerTypeProxyAttribute.

-   Se insertan métodos de MonoBehaviour usando nuestros asistentes para respetar las convenciones de código de usuario.

-   Se ha implementado la compatibilidad con plantillas de texto de tiempo de compilación en proyectos generados por UnityVS.

-   Se ha implementado la compatibilidad con recursos ResX en proyectos generados por UnityVS.

-   Permite abrir sombreadores en Visual Studio desde Unity.

### <a name="bug-fixes"></a>Correcciones de errores

-   Se limpian los sockets antes de iniciar el juego en Unity después de que se haya iniciado Adjuntar y reproducir en Visual Studio. Esto corrige algunos problemas de estabilidad de la conexión entre Unity y VS al usar Adjuntar y reproducir.

-   Se evita llamar a aquellos métodos en la interfaz del depurador del motor de scripting de Unity que tienden a inmovilizar Unity. Esto impide la inmovilización de Unity al adjuntar el depurador.

-   Se ha corregido la visualización de pilas de llamadas cuando no hay símbolos disponibles.

-   No se registra la devolución de llamada de registro si no es necesario.

## <a name="192"></a>1.9.2
 Lanzamiento 09-10-2014

### <a name="new-features"></a>Características nuevas

-   Se ha mejorado la detección de reproductores de Unity.

-   Al usar nuestro abridor de archivos, se hace que Unity pase el número de línea y el nombre de archivo.

-   Si no hay documentación local, se establece la documentación en línea de Unity como la documentación predeterminada.

### <a name="bug-fixes"></a>Correcciones de errores

-   Se ha corregido un posible bloqueo de Unity al alcanzar un punto de interrupción después de volver a cargar un dominio.

-   Se han corregido las excepciones que se muestran en la consola de Unity al cerrar nuestras ventanas Configuración o Acerca de, después de volver a cargar un dominio.

-   Se ha corregido la detección de Unity de 64 bits que se ejecuta localmente.

-   Se ha corregido el filtrado de MonoBehaviours por versión de Unity en asistentes.

-   Se ha corregido el error por el que todos los activos se incluían en los archivos de proyecto si el filtro de extensión estaba vacío.

## <a name="191"></a>1.9.1
 Lanzamiento 22-09-2014

### <a name="new-features"></a>Características nuevas

-   Se optimiza el enlazado de un punto de interrupción con ubicaciones de origen.

-   Compatible con métodos sobrecargados en la Evaluación de expresiones del depurador.

-   Compatible con conversión boxing de tipos de valor y primitivos en la Evaluación de expresiones del depurador.

-   Permite volver a crear el entorno de variables locales de C# al depurar métodos anónimos.

-   Se eliminan y se cambia el nombre de archivos .meta al eliminar o cambiar el nombre de archivos desde Visual Studio.

### <a name="bug-fixes"></a>Correcciones de errores

-   Se ha corregido el procesamiento de temas de Visual Studio. Anteriormente, los cuadros de diálogo en temas negros podían aparecer vacíos.

-   Se ha corregido la congelación de Unity al conectar el depurador durante la recompilación de Unity.

-   Se han corregido los puntos de interrupción al depurar editores o reproductores remotos compilados en otro sistema.

-   Se ha corregido un posible bloqueo de Visual Studio cuando se alcanza un punto de interrupción.

-   Se ha corregido el enlazado de puntos de interrupción para evitar que los puntos de interrupción se muestren como descargados.

-   Se ha corregido el procesamiento de ámbito de variable en el depurador para evitar variables activas que aparecen fuera del ámbito.

-   Se ha corregido la búsqueda de miembros estáticos en la evaluación de expresiones del depurador.

-   Se ha corregido la visualización de tipos en la Evaluación de expresiones del depurador para mostrar las propiedades y los campos estáticos.

-   Se ha corregido la generación de soluciones cuando los nombres de proyecto de Unity incluyen caracteres especiales que Visual Studio prohíbe (Problema de conexión #948666).

-   Se ha corregido el paquete de Visual Studio Tools para Unity para que deje de inmediato de enviar eventos de consola después de que se haya desactivado la opción (Problema de conexión #933357).

-   Se ha corregido la detección de referencias para volver a generar correctamente referencias a las nuevas API, como UnityEngine.UI, en los proyectos de generados en UnityVS.

-   Se ha corregido el instalador para que requiera que Visual Studio se cierre antes de la instalación con el objetivo de evitar instalaciones dañadas.

-   Se ha corregido el instalador para que instale los Ensamblados de referencia de Unity como un auténtico componente independiente, compartido entre todas las versiones de VSTU.

-   Se han corregido los scripts de apertura con VSTU en las versiones de 64 bits de Unity.

## <a name="19"></a>1.9
 Lanzamiento 29-07-2014

### <a name="new-features"></a>Características nuevas

-   En la ventana Adjuntar depurador de Unity, se ha agregado la capacidad de introducir una dirección IP y un puerto personalizados para depurar.

-   Se ha agregado una opción de configuración para establecer si Unity se ejecuta o no en segundo plano.

-   Se ha agregado la opción de configuración para generar los archivos de proyecto y solución o solo los archivos de proyecto.

-   Destino de inicio: elige entre Adjuntar a Unity o Adjuntar a Unity y reproducir.

-   Muestra matrices multidimensionales en el depurador.

-   Se procesan los nuevos puertos de depuración del Reproductor de Unity.

-   Se procesan las referencias a nuevos ensamblados de Unity como ensamblados de la GUI de Unity 4.6.

-   Se deconstruyen cierres para que se muestren correctamente las variables locales al depurar.

-   Se deconstruyen las variables de iteradores generadas en argumentos durante la depuración.

-   Se conserva el estado del Explorador de proyectos de Unity después de volver a cargar un proyecto.

-   Se agrega un comando para sincronizar el Explorador de proyectos de Unity con el documento actual.

### <a name="bug-fixes"></a>Correcciones de errores

-   Se han corregido los puntos de interrupción condicionales cuyas condiciones se establecen antes de iniciar al depurador.

-   Se han corregido las referencias a UnityEngine para evitar advertencias.

-   Se ha corregido el análisis de versiones beta de Unity.

-   Se ha corregido el problema por el que las variables no aparecían en la ventana de variables locales al alcanzar un punto de interrupción o de ejecución paso a paso.

-   Se ha corregido la información sobre herramientas de variables en Visual Studio 2013.

-   Se ha corregido la generación de la documentación de IntelliSense para Unity 4.5.

-   Se ha corregido la comunicación entre Unity y Visual Studio después de la recarga de un dominio (reproducir/detener en Unity).

-   Se ha corregido el procesamiento de partes de temas de Visual Studio.

> [!IMPORTANT]
>  Dado que C# es el lenguaje predominante en el ecosistema de Unity (los nuevos activos de muestra están en C# y la documentación de Unity se presentará en C# de forma predeterminada), eliminamos nuestro soporte básico para UnityScript y Boo con el fin de centrarnos mejor en la experiencia en C#. Como resultado, las soluciones de VSTU ahora solo están en C# y se cargan mucho más rápido.

## <a name="182"></a>1.8.2
 Lanzamiento 07-01-2014

### <a name="new-features"></a>Características nuevas

-   Solución alternativa de un problema en la capa de red del motor de scripting de Unity en Mavericks para la detección remota de editores.

-   Procesa los nuevos puertos para detectar reproductores remotos de Unity.

-   Hace referencia al ensamblado UnityEngine específico para el destino de compilación actual.

-   Agrega ajuste para filtrar archivos que se incluirán en los proyectos generados.

-   Agrega ajuste para deshabilitar el envío de registros de consola a la lista de errores de Visual Studio. Esto es útil si está usando PlayMaker o Console Pro, ya que solo podía haber una devolución de llamada registrada en Unity para recibir registros de consola.

-   Agrega ajuste para deshabilitar la generación de símbolos de depuración de mdb. Esto es útil si usted está generando la mdb.

### <a name="bug-fixes"></a>Correcciones de errores

-   Se ha corregido una regresión por la que los archivos abiertos en VS desde Unity 4.2 (o versión más reciente) perdían IntelliSense.

-   Se han corregido nuestros diálogos de VS para que procesen temas personalizados.

-   Se ha corregido el cierre del menú contextual de UPE.

-   Se evita el bloqueo en Unity cuando el ensamblado generado específico de la versión no está sincronizado.

## <a name="181"></a>1.8.1
 Lanzamiento 21-11-2013

### <a name="new-features"></a>Características nuevas

-   Se han ajustado los asistentes de MonoBehaviour con las API de Unity 4.3.

-   Los asistentes de MonoBehaviour filtran las API de Unity según la versión que utilice.

-   Se ha agregado una referencia a System.Xml.Linq a los proyectos de Unity > 4.1.

-   Se ha mejorado el aspecto de nuestras llamadas a Debug.Log para que no incluyan el principio de la stacktrace en el mensaje.

### <a name="bug-fixes"></a>Correcciones de errores

-   Se ha corregido un error por el que interferíamos con el procesamiento predeterminado de archivos JavaScript en Visual Studio.

-   Se ha corregido definitivamente la visualización de un píxel blanco en VS.

-   Se ha corregido la eliminación del ensamblado de UnityVS.VersionSpecific si está marcado como de solo lectura por un SCM.

-   Se han corregido las excepciones que se producían al crear sockets en el paquete de UnityVS.

-   Se ha corregido un bloqueo en Visual Studio que se producía al cargar imágenes de archivo desde ensamblados de Visual Studio.

-   Se ha corregido un error en la generación de UnityVS.VersionSpecific para compilaciones de código fuente de Unity.

-   Se ha corregido una posible inmovilización que se producía al abrir un socket en el paquete de Unity.

-   Se ha corregido el procesamiento de proyectos de Unity que tenían un guión (-) en su nombre.

-   Se han corregido los scripts de apertura de Unity para que no confundan la orden ALT+TAB en Unity 4.2 y versiones posteriores.

## <a name="180"></a>1.8.0
 Lanzamiento 24-09-2013

### <a name="new-features"></a>Características nuevas

-   Se ha mejorado mucho la velocidad de conexión del depurador.

-   Se controla automáticamente la navegación al archivo y la línea en Unity 4.2 y versiones posteriores.

-   Puntos de interrupción condicionales.

-   El generador de archivos de proyecto ahora es capaz de procesar plantillas T4.

-   Se han actualizado los asistentes de MonBehavior con nuevas API.

-   Documentación de IntelliSense en C# para tipos de Unity.

-   Evaluación de expresiones lógicas y aritméticas.

-   Se ha mejorado la detección de editores remotos para la vista previa de depuración remota.

### <a name="bug-fixes"></a>Correcciones de errores

-   Se ha corregido un error por el que se podía perder un subproceso en VS tras desconectar el depurador.

-   Se ha corregido la visualización de un píxel blanco en VS.

-   Se ha corregido el procesamiento de clics en el icono de la barra de estado.

-   Se ha corregido la generación de referencias con ensamblados en carpetas de complementos.

-   Se ha corregido la creación de sockets desde el paquete UnityVS en caso de que haya excepciones.

-   Se ha corregido la detección de nuevas versiones de UnityVS.

-   Se ha corregido el mensaje del administrador de licencias al caducar la licencia.

-   Se ha corregido un error por el que la lista de procesos se podía mostrar vacía en la ventana Adjuntar depurador a proceso de VS.

-   Se ha corregido el cambio de valores de booleanos en la vista local.

## <a name="122"></a>1.2.2
 Lanzamiento 09-07-2013

### <a name="bug-fixes"></a>Correcciones de errores

-   Se procesan nombres completos en el evaluador de expresiones.

-   Se ha corregido una inmovilización relacionada con el control de excepciones mediante la cual el motor de scripting de Unity enviaba datos de stackframe incorrectos.

-   Se ha corregido el proceso de compilación de destinos Web.

-   Se ha corregido un error que podía producirse si Visual Studio se iniciaba y en la lista de archivos para abrir durante el inicio había un archivo eliminado.

-   Se ha corregido UnityVS.OpenFile para que procese archivos que no sean de script, como, por ejemplo, sombreadores compilados.

-   Ahora hacemos referencia a Boo.Lang y UnityScript.Lang desde todos los proyectos de C#.

-   Se ha corregido la generación de referencias de proyectos si el proyecto contiene caracteres especiales.

-   Se ha encontrado una solución alternativa a un problema de VS por el que las llamadas a métodos en proyectos eliminados generaban varios NullReferenceException MessageBox.

-   Se ha corregido el procesamiento de ensamblados de la versión beta de Unity 4.2.

## <a name="121"></a>1.2.1
 Lanzamiento 09-04-2013

### <a name="bug-fixes"></a>Correcciones de errores

-   Se ha corregido la implementación local de ensamblados de Unity para la finalización de código en caso de que se produzca un error de E/S (como archivos de sólo lectura o archivos bloqueados por Visual Studio).

-   Se ha corregido una regresión por la que al abrir un script desde Unity no se centraría en el archivo si ya estaba abierto en Visual Studio.

-   Se ha corregido el problema de rendimiento del nuevo control de excepciones.

-   Se ha corregido el enlace de puntos de interrupción en algunos archivos DLL externos.

## <a name="12"></a>1.2
 Lanzamiento 25-03-2013

### <a name="new-features"></a>Características nuevas

-   Se ha mejorado mucho la velocidad de conexión del depurador.

-   Explorador de proyectos de Unity optimizado para proyectos grandes.

-   Respeta la configuración de Visual Studio en lo referente a si se debe generar una interrupción (o no) en caso de encontrar excepciones controladas y no controladas.

-   Respeta la configuración de Visual Studio en cuanto a realizar llamadas a ToString en variables locales.

-   Se ha agregado un nuevo menú Depurar -> Adjuntar depurador de Unity, que puede utilizar para depurar reproductores de Unity.

-   Se conservan los proyectos personalizados agregados a la solución de UnityVS tras generar los archivos de la solución.

-   Se ha agregado un nuevo método abreviado de teclado CTRL+ALT+M -> CTRL+H para mostrar la documentación de Unity para la función de Unity o el miembro en la posición del cursor de inserción.

-   Se tienen en cuenta los archivos de respuesta del compilador (rsp) al compilar desde Visual Studio.

-   Se deconstruyen los tipos generados por el compilador para mostrar las variables al depurar los métodos de generador.

-   Se simplifica la depuración remota eliminando la necesidad de configurar una carpeta compartida para Unity. Ahora solo necesita tener acceso a su proyecto de Unity desde Windows.

-   Se instala un perfil de Unity personalizado como perfil de destino .net estándar. Esto corrige todos los falsos positivos que podía mostrar ReSharper.

-   Se ha encontrado una solución alternativa a un error del motor de scripting de Unity para que el depurador no se interrumpa al encontrar subprocesos que no se hayan registrado debidamente.

-   Se ha modificado el abridor de archivos para evitar una condición de carrera en VS por la que alegaba ser capaz de abrir archivos, pero se bloqueaba durante una solicitud de apertura de archivo.

-   UnityVS ya no solicita actualizar la compilación al guardar el archivo, sino cuando VS compila el proyecto.

### <a name="bug-fixes"></a>Correcciones de errores

-   Se ha corregido nuestro perfil de .net personalizado

-   Se ha corregido la integración de temas, lo que termina con los problemas relacionados con el tema oscuro de VS 2012.

-   Se ha corregido el acceso directo rápido de comportamiento de VS 2012.

-   Se ha corregido un problema de ejecución paso a paso que podía producirse con la depuración y si un subproceso no principal alcanzaba un punto de interrupción.

-   Se ha corregido la finalización de UnityScript y Boo de alias de tipo, como int.

-   Se ha corregido una excepción que se generaba al escribir una nueva cadena UnityScript o Boo.

-   Se han corregido las excepciones en los menús de Unity que se generaban cuando no se cargaba una solución.

-   Se ha corregido el UVS-48: escribir dobles comillas a veces produce un error e interrumpe todas las funciones (finalización de código, resaltado de sintaxis, etc.).

-   Se corrigió el error UVS-46: archivo de script abierto duplicado (UnityScript) al hacer clic en la Lista de errores de Visual Studio.

-   Se corrigió el error UVS-42: el logotipo de conectividad de Unity de la barra de estado no procesa eventos de mouse en VS 2012.

-   Se corrigió el error UVS-44: CTRL+MAYÚS+Q no está disponible en VS 2012 para MonoBehaviours rápidas.

-   Se corrigió el error UVS-40: los elementos seleccionados en el Explorador de proyectos de Unity no se pueden leer si la ventana está inactiva en el tema "oscuro" de VS2012.

-   Se corrigió el error UVS-39: problema al convertir cadenas de caracteres de escape en tokens.

-   Se corrigió el error UVS-35: invocar ToString en objetos al inspeccionar variables.

-   Se corrigió el error UVS-27: incoherencia de la ventana Ir al símbolo con el tema "oscuro" en VS2012.

-   Se corrigió el error UVS-11: variables locales en las corrutinas.

## <a name="11--beta-release"></a>1.1 – versión beta
 Fecha de publicación: 9 de octubre de 2014

## <a name="1013"></a>1.0.13
 Lanzamiento 21-01-2013

### <a name="bug-fixes"></a>Correcciones de errores

-   Se ha corregido un bloqueo de Visual Studio que podía ocurrir si el código depurado de destino enviaba eventos de subproceso no válidos. Esto solía pasar al depurar un Unity remoto en OSX.

-   Se ha corregido un bloqueo de Visual Studio que podía ocurrir si una excepción apagaba el depurador.

-   Se han corregido nuestros asistentes de MonoBehavior cuando un MonoBehavior en C# se encuentra en un espacio de nombres.

-   Se ha corregido la información sobre herramientas del depurador de UnityScript en Visual Studio 2012.

-   Se ha corregido la generación de proyecto cuando solo se cambian constantes de depuración desde Unity.

-   Se ha corregido la navegación mediante teclado en el Explorador de proyectos de Unity.

-   Se ha corregido el coloreado de UnityScript para las cadenas de escape.

-   Se ha corregido nuestro abridor de archivos para que adivine mejor el nombre del proyecto cuando se utiliza fuera de Unity. Eso es necesario cuando el usuario utiliza un abridor de archivos de terceros en Unity que delega a UnityVS.

-   Se ha corregido el procesamiento de mensajes largos enviados desde Unity a UnityVS. Antes de solucionar este problema, los mensajes largos podían bloquear nuestra parte de mensajería de UnityVS. Como consecuencia, a veces UnityVS no abría un archivo desde Unity.

## <a name="1012"></a>1.0.12
 Lanzamiento 03-01-2013

### <a name="bug-fixes"></a>Correcciones de errores

-   Se ha corregido el bloqueo de Visual Studio que podía producirse cuando Visual Studio estaba eliminando un punto de interrupción.

-   Se ha corregido un error por el que algunos puntos de interrupción no se alcanzaban después de que Unity volviese a compilar los scripts de juegos.

-   Se ha corregido el depurador para que notifique correctamente a Visual Studio cuando haya puntos de interrupción no enlazados.

-   Se ha corregido un problema del registro que podía impedir que el depurador de Visual Studio depurase programas nativos.

-   Se ha corregido una excepción que podía generarse al evaluar expresiones de UnityScript y Boo.

-   Se ha corregido una regresión en la que el cambio de nivel de API .net en Unity no activaba una actualización de los archivos de proyecto.

-   Se ha corregido un problema de la API por el que el código de usuario no podía participar en el controlador de devolución de llamada de registro.

## <a name="1011"></a>1.0.11
 Lanzamiento 28-11-2012

### <a name="new-features"></a>Características nuevas

-   Soporte oficial de Unity 4.

-   Manipulación de scripts desde el Explorador de proyectos de Unity.

-   Integración en la ventana Navegar a de Visual Studio.

-   Se analiza el mensaje de la consola de información, para que al hacer clic en la Lista de errores, acceda a la primera stackframe que tenga símbolos.

-   Se ha agregado una [API](../cross-platform/customize-project-files-created-by-vstu.md) para dejar al usuario participar en la generación del proyecto.

-   Se ha agregado una [API](../cross-platform/share-the-unity-log-callback-with-vstu.md) para dejar al usuario participar en la LogCallback.

### <a name="bug-fixes"></a>Correcciones de errores

-   Se ha corregido la regresión en segundo plano del Explorador de proyectos de Unity en Visual Studio 2012.

-   Se ha corregido la generación de proyectos de usuarios del perfil de .net completo.

-   Se ha corregido la generación de proyectos para usuarios del destino web.

-   Se ha corregido la generación de proyectos para que incluya símbolos de DEPURAR y RASTREAR tal como hace Unity.

-   Se ha corregido el bloqueo que se producía al usar caracteres especiales en la ventana de símbolo de Ir a.

-   Se ha corregido el bloqueo que se producía si no podíamos inyectar nuestro icono en la barra de estado de Visual Studio.

## <a name="1010"></a>1.0.10
 Lanzamiento 09-10-2012

### <a name="bug-fixes"></a>Correcciones de errores

-   Se ha corregido el segundo plano del Explorador de proyectos de Unity en Visual Studio 2010.

-   Se ha corregido una inmovilización de Visual Studio que podía producirse si UnityVS intentaba adjuntar el depurador a un Unity con una interfaz de depurador que se hubiese bloqueado anteriormente.

-   Se ha corregido una inmovilización de Visual Studio que podía producirse cuando se había establecido un punto de interrupción y se recargaba AppDomain.

-   Se ha corregido cómo se recuperan los ensamblados desde Unity para evitar el bloqueo de archivos y confusiones durante el proceso de compilación de Unity.

## <a name="109"></a>1.0.9
 Lanzamiento 03-10-2012

### <a name="bug-fixes"></a>Correcciones de errores

-   Se ha corregido la generación de proyectos cuando el proyecto de Unity incluye activos reales de JavaScript.

-   Se ha corregido el control de errores en la evaluación de expresiones.

-   Se ha corregido el establecimiento de nuevos valores en campos de tipos de valor.

-   Se han corregido los efectos secundarios que se podían producir al colocar el puntero del mouse sobre expresiones del editor de código.

-   Se ha corregido cómo se buscan los tipos en los ensamblados cargados para la evaluación de expresiones.

-   Se corrigió el error UVS-21: la evaluación de asignación en objetos de Unity no tiene ningún efecto.

-   Se corrigió el error UVS-21: puntero no válido al evaluar una invocación de método a la API Math de Unity.

## <a name="108"></a>1.0.8
 Lanzamiento 26-09-2012

### <a name="bug-fixes"></a>Correcciones de errores

-   Se ha corregido la forma en que nuestro abridor de scripts adquiere la ruta de acceso al proyecto para asegurarse de que sea capaz de abrir Visual Studio y los scripts.

-   Se ha corregido un error por el que se creaban puntos de interrupción mientras se estaba ejecutando la sesión de depuración, que podía dar lugar al bloqueo de Visual Studio.

-   Se ha corregido cómo se registra UnityVS en Visual Studio 2010.

## <a name="107"></a>1.0.7
 Lanzamiento 14-09-2012

### <a name="new-features"></a>Características nuevas

-   Soporte de Visual Studio 2012.

### <a name="bug-fixes"></a>Correcciones de errores

-   Se ha corregido la generación de archivos de proyectos de complementos y del Editor para que coincida con el comportamiento de Unity.

-   Se ha corregido la traducción de los símbolos .pdb en Unity 4.

> [!IMPORTANT]
>  Debido a la compatibilidad con Visual Studio 2012, tuvimos que cambiar el nombre de algunos archivos y mover otros. El paquete de UnityVS para importar Unity ahora se llama UnityVS 2010 o UnityVS 2012, para Visual Studio 2010 y Visual Studio 2012 respectivamente. Esta versión también requiere que se vuelvan a generar los archivos de proyecto de UnityVS.

## <a name="106---internal-build"></a>1.0.6 - versión de compilación interna
 Lanzamiento 12-09-2012

## <a name="105"></a>1.0.5
 Lanzamiento 10-09-2012

### <a name="bug-fixes"></a>Correcciones de errores

-   Se ha corregido la generación de archivos de proyecto cuando los scripts o sombreadores tenían un carácter xml no válido.

-   Se ha corregido la detección de instancias de Unity cuando Unity estaba conectado al servidor de activos. Esto producía errores al abrir archivos desde Unity y la conexión automática del depurador de Visual Studio.

## <a name="104"></a>1.0.4
 Lanzamiento 05-09-2012

### <a name="new-features"></a>Características nuevas

-   Conversión automática de símbolos de depuración en Unity.

     Si tiene un ensamblado .dll de .NET con su .pdb asociado en la carpeta de activos, simplemente vuelva a importar el ensamblado y UnityVS convertirá el archivo .pdb en un archivo de símbolos de depuración que comprende el motor de scripting de Unity. De este modo, podrá acceder a los ensamblados de .NET desde UnityVS.

### <a name="bug-fixes"></a>Correcciones de errores

-   Se ha corregido el bloqueo de UnityVS que tenía lugar durante la depuración como consecuencia de excepciones producidas por métodos o propiedades ubicadas dentro de Unity.

## <a name="103"></a>1.0.3
 Lanzamiento 04-09-2012

### <a name="new-features"></a>Características nuevas

-   Nueva opción de configuración para deshabilitar el uso de UnityVS para abrir archivos desde Unity.

### <a name="bug-fixes"></a>Correcciones de errores

-   Se ha corregido la generación de referencias a UnityEditor para proyectos que no sean del editor.

-   Se ha corregido la definición del símbolo UNITY_EDITOR para proyectos que no sean del editor.

-   Se ha corregido el bloqueo aleatorio de VS causado por nuestra barra de estado personalizada.

## <a name="102"></a>1.0.2
 Lanzamiento 30-08-2012

### <a name="bug-fixes"></a>Correcciones de errores

-   Se ha corregido el conflicto con el depurador de PythonTools.

-   Se han corregido las referencias a Mono.Cecil.

-   Se ha corregido el error sobre cómo se recuperaban los ensamblados de scripting desde Unity mediante Unity 4.

## <a name="101"></a>1.0.1
 Lanzamiento 28-08-2012

### <a name="new-features"></a>Características nuevas

-   Compatibilidad con la vista previa de Unity 4.0 Beta.

### <a name="bug-fixes"></a>Correcciones de errores

-   Se ha corregido la inspección de propiedades que producen excepciones.

-   Se ha corregido el descenso a objetos base al inspeccionar objetos.

-   Se ha corregido la lista desplegable en blanco del punto de inserción en el asistente de MonoBehavior.

-   Se ha corregido la finalización de archivos .dll dentro de la carpeta de activos para UnityScript y Boo.

## <a name="10--initial-release"></a>1.0 – versión inicial
 Lanzamiento 22-08-2012

