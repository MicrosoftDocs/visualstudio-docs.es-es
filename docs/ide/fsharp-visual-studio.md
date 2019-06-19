---
title: Herramientas de F#
description: Obtenga información sobre qué características de Visual Studio son compatibles con F#.
ms.date: 07/11/2018
ms.topic: reference
helpviewer_keywords:
- F# features [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f71e17eae1e728ab755d048daee2c0d156425964
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747598"
---
# <a name="develop-with-visual-f-in-visual-studio"></a>Desarrollar con Visual F# en Visual Studio

Este artículo incluye información sobre las características de Visual Studio para el desarrollo de F#.

## <a name="install-f-support"></a>Instalar compatibilidad con F#

Para desarrollar con F# en Visual Studio, en primer lugar instale la carga de trabajo de **desarrollo de escritorio de .NET** si aún no lo ha hecho. Las cargas de trabajo de Visual Studio se instalan por medio del Instalador de Visual Studio, que se puede abrir al seleccionar **Herramientas** > **Obtener herramientas y características**.

![Carga de trabajo de desarrollo de escritorio de .NET de Visual Studio](media/dotnet-desktop-development-workload.png)

## <a name="f-project-features"></a>Características de proyecto de F#

En Visual Studio, hay disponibles varias plantillas de proyecto y elemento para F#. En la imagen siguiente se muestran algunas de las plantillas de proyecto de F# para .NET Core y .NET Standard:

![Plantillas de proyecto de F# de Visual Studio](media/fsharp-project-templates.png)

En la imagen siguiente se muestran algunas de las plantillas de elemento de F#:

![Plantillas de elemento de F# de Visual Studio](media/fsharp-item-templates.png)

Para obtener más información sobre las plantillas de elemento para el acceso a datos, vea [Proveedores de tipos de F#](/dotnet/fsharp/tutorials/type-providers/index).

En la tabla siguiente se resumen las características de las propiedades de proyecto de F#:

|Propiedad de proyecto|¿Admitida en F#?|Notas|
|---------------|----------------|-----|
|Archivos de recursos|Sí||
|Configuración de compilación, depuración y referencia|Sí||
|Compatibilidad con múltiples versiones (multi-targeting)|Sí||
|Icono y manifiesto|No|Disponible a través de las opciones de la línea de comandos del compilador.|
|Servicios de cliente ASP.NET|No||
|ClickOnce|No|Use un proyecto de cliente en otro lenguaje de .NET, si es aplicable.|
|Nombres seguros|No|Disponible a través de las opciones de la línea de comandos del compilador.|
|Publicación de ensamblados y control de versiones|No||
|Análisis de código|No|Las herramientas de análisis de código se pueden ejecutar manualmente o como parte de un comando posterior a la compilación.|
|Seguridad (cambiar niveles de confianza)|No||

## <a name="project-designer"></a>Diseñador de proyectos

El **Diseñador de proyectos** consta de varias páginas de propiedades de proyecto agrupadas por funcionalidad relacionada. Las páginas disponibles para los proyectos de F# son principalmente un subconjunto de las disponibles para otros lenguajes; se describen en la tabla siguiente. Se proporcionan vínculos a la página del **Diseñador de proyectos** de C# correspondiente.

|Página del Diseñador de proyectos|Vínculos relacionados|Descripción|
| - |-------------|-----------|
|Administración de|[Página de aplicación, Diseñador de proyectos](reference/application-page-project-designer-csharp.md)|Permite especificar la configuración y las propiedades de nivel de aplicación, por ejemplo si se está creando una biblioteca o un archivo ejecutable, qué versión de .NET tiene la aplicación como destino e información sobre la ubicación de almacenamiento de los archivos de recursos que usa la aplicación.|
|Compilar|[Página Compilación, Diseñador de proyectos](reference/build-page-project-designer-csharp.md)|Permite controlar cómo se compila el código.|
|Eventos de compilación|[Eventos de compilación (Página, Diseñador de proyectos)](reference/build-events-page-project-designer-csharp.md)|Permite especificar comandos que se van a ejecutar antes o después de una compilación.|
|Depuración|[Página Depuración, Diseñador de proyectos](reference/debug-page-project-designer.md)|Permite controlar cómo se ejecuta la aplicación durante la depuración. Esto incluye qué comandos se van a usar y cuál es el directorio de inicio de la aplicación, así como los modos de depuración especiales que quiera habilitar, como código nativo y SQL.|
|Paquete (solo SDK de .NET)|N/D|Permite definir metadatos de paquete NuGet al publicar como paquete NuGet.|
|Rutas de referencia|[Administración de referencias en un proyecto](managing-references-in-a-project.md)|Permite especificar dónde buscar los ensamblados de los que depende el código.|
|Recursos (solo SDK de .NET)|N/D|Permite generar y administrar un archivo de recursos predeterminado.|

### <a name="f-specific-settings"></a>Propiedades específicas de F#

En la tabla siguiente se resumen las propiedades específicas de F#:

|Página del Diseñador de proyectos|Parámetro|Descripción|
| - |-------|-----------|
|Compilar|Generar llamadas de cola|Si está seleccionado, permite usar la instrucción de Lenguaje Intermedio de Microsoft (MSIL) de cola. Esto hace que el marco de pila se vuelva a usar para las funciones recursivas de cola. Es equivalente a la opción del compilador `--tailcalls`.|
|Compilar|Otras marcas|Permite especificar otras opciones de línea de comandos del compilador.|

## <a name="code-and-text-editor-features"></a>Características del editor de código y texto

En F# se admiten las siguientes características de los editores de código y texto de Visual Studio:

|Característica|Descripción|¿Admitida en F#?|
|-------|-----------|----------------|
|Comentar automáticamente|Permite escribir o eliminar comentarios en secciones de código.|Sí|
|Aplicar formato automáticamente|Cambia el formato del código con la sangría y el estilo estándar.|No|
|Marcadores|Permite guardar ubicaciones en el editor.|Sí|
|Cambiar sangría|Aplica sangría o la quita en líneas seleccionadas.|Sí|
|Sangría inteligente|Aplica o quita sangría automáticamente al cursor según las reglas de ámbito de F#.|Sí|
|[Buscar y reemplazar texto](finding-and-replacing-text.md)|Permite buscar en un archivo, un proyecto o una solución y, potencialmente, cambiar texto.|Sí|
|Ir a definición para la API de .NET|Cuando el cursor está colocado en una API de .NET, muestra código generado a partir de metadatos de .NET.|No|
|Ir a definición para API definida por el usuario|Cuando el cursor está en una entidad de programa que ha definido, mueve el cursor a la ubicación del código donde se ha definido la entidad.|Sí|
|Ir a la línea|Permite ir a una línea determinada de un archivo, por número de línea.|Sí|
|Barras de navegación en la parte superior del archivo|Permite saltar a ubicaciones del código, por ejemplo, por nombre de función.|Sí|
|Guías de estructura de bloque|Muestra guías que indican ámbitos de F# sobre los que se puede colocar el cursor para obtener una vista previa.|Sí|
|[Esquematización](outlining.md)|Permite contraer secciones del código para crear una vista más compacta.|Sí|
|Aplicar tabulación|Convierte espacios en tabulaciones.|Sí|
|Uso de colores para el tipo|Muestra nombres de tipo definidos en un color especial.|Sí|
|Búsqueda rápida. Vea Búsqueda rápida, ventana Buscar y reemplazar.|Permite buscar en un archivo o un proyecto.|Sí|
|**Ctrl**+**clic** para Ir a definición|Permite mantener presionado **Ctrl** y hacer clic en un símbolo de F# para invocar Ir a definición.|Sí|
|Ir a definición desde información rápida|Símbolos interactivos en informaciones sobre herramientas que invocan Ir a definición.|Sí|
|Ir a todo|Permite la navegación global, de coincidencia aproximada para todas las construcciones de F# mediante **Ctrl**+**T**.|Sí|
|Cambio de nombre en línea|Cambia el nombre de todas las apariciones de un símbolo en línea.|Sí|
|Buscar todas las referencias|Busca todas las apariciones de un símbolo en un código base.|Sí|
|Corrección de código Simplificar nombre|Quita los calificadores innecesarios de símbolos de F#.|Sí|
|Corrección de código Quitar instrucción `open` no usada|Quita todas las instrucciones `open` innecesarias de un documento.|Sí|
|Corrección de código Valor no usado|Sugiere el cambio de nombre de un identificador no usado para subrayar.|Sí|

Para obtener información general sobre la edición de código en Visual Studio y las características del editor de texto, vea [Escribir código en el editor](writing-code-in-the-code-and-text-editor.md).

## <a name="intellisense-features"></a>características de Intellisense

En la tabla siguiente se resumen las características de IntelliSense compatibles y no compatibles con F#:

|Característica|Descripción|¿Admitida en F#?|
|-------|-----------|----------------|
|Implementar interfaces automáticamente|Genera código stub para métodos de interfaz.|Sí|
|Fragmentos de código|Inserta código de una biblioteca de construcciones de codificación comunes en temas.|No|
|Palabra completa|Ahorra escribir al completar las palabras y los nombres a medida que escribe.|Sí|
|Finalización automática|Si está habilitada, hace que la finalización de palabras seleccione la primera coincidencia a medida que escribe en lugar de esperar a que seleccione una o presione **Ctrl**+**Espacio**.|Sí|
|Oferta de finalización de símbolos en espacios de nombres sin abrir|Con la finalización automática, se sugiere un símbolo coincidente que reside en un espacio de nombres sin abrir, ofreciendo completar con la instrucción `open` correspondiente, si está seleccionada.|Sí|
|Generar elementos de código|Permite generar código stub para una serie de construcciones.|No|
|Lista de miembros|Cuando se escribe el operador de acceso a miembros (.), muestra los miembros de un tipo.|Sí|
|Organizar Usings/Open|Organiza los espacios de nombres a los que se hace referencia mediante instrucciones **using** de C# o directivas **open** de F#.|No|
|Información de parámetros|Muestra información útil sobre los parámetros a medida que se escribe una llamada de función.|Sí|
|Información rápida|Muestra la declaración completa de cualquier identificador del código.|Sí|
|Finalización automática de llaves|Completa automáticamente construcciones de sintaxis de llave de F# de forma transaccional.|Sí|

Para obtener información general sobre IntelliSense, vea [Usar IntelliSense](using-intellisense.md).

## <a name="debugging-features"></a>Características de depuración

En la siguiente tabla se resumen las características disponibles al depurar código de F#:

|Característica|Descripción|¿Admitida en F#?|
|-------|-----------|----------------|
|Ventana Automático|Muestra variables automáticas o temporales.|No|
|Puntos de interrupción|Permite pausar la ejecución de código en puntos concretos durante la depuración.|Sí|
|Puntos de interrupción condicionales|Permite puntos de interrupción que comprueban una condición que determina si se debe pausar la ejecución.|Sí|
|Editar y continuar|Permite modificar y compilar el código a medida que se depura un programa en ejecución sin detener y reiniciar el depurador.|No|
|Evaluador de expresiones|Evalúa y ejecuta código en tiempo de ejecución.|No, pero se puede usar el evaluador de expresiones de C#, aunque se debe emplear la sintaxis de C#.|
|Depuración histórica|Permite ir a código ejecutado anteriormente.|Sí|
|Ventana Locales|Muestra valores y variables definidos localmente.|Sí|
|Ejecutar hasta el cursor|Permite ejecutar código hasta que se alcanza la línea que contiene el cursor.|Sí|
|Paso a paso por instrucciones|Permite avanzar la ejecución e ir a cualquier llamada de función.|Sí|
|Paso a paso por procedimientos|Permite avanzar la ejecución en el marco de pila actual e ir más allá de cualquier llamada de función.|Sí|

Para obtener información general sobre el depurador de Visual Studio, vea [Depurar en Visual Studio](../debugger/index.md).

## <a name="additional-tools"></a>Herramientas adicionales

En la tabla siguiente se resume la compatibilidad con F# de Visual Studio Tools.

|Herramienta|Descripción|¿Admitida en F#?|
|----|-----------|----------------|
|Jerarquía de llamadas|Muestra la estructura anidada de llamadas de función del código.|No|
|Métricas de código|Recopila información sobre el código, como recuentos de línea.|No|
|Vista de clases|Proporciona una vista basada en tipos del código de un proyecto.|No|
|[Lista de errores (ventana)](reference/error-list-window.md)|Muestra una lista de errores del código.|Sí|
|[F# Interactive](/dotnet/fsharp/tutorials/fsharp-interactive/)|Permite escribir (o copiar y pegar) código de F# y ejecutarlo inmediatamente, independientemente de la compilación del proyecto. La ventana F# interactivo es un REPL (Read, Evaluate, Print Loop).|Sí|
|Examinador de objetos|Permite ver los tipos de un ensamblado.|Los tipos de F#, tal y como aparecen en los ensamblados compilados, no aparecen exactamente como se crean. Puede examinar la representación compilada de tipos de F#, pero no puede ver los tipos tal y como aparecen desde F#.|
|[Resultados (Ventana)](reference/output-window.md)|Muestra los resultados de la compilación.|Sí|
|Análisis de rendimiento|Proporciona herramientas para medir el rendimiento del código.|Sí|
|Propiedades (ventana)|Muestra y permite la edición de propiedades del objeto en el entorno de desarrollo que tiene el foco.|Sí|
|Explorador de servidores|Proporciona formas de interactuar con una serie de recursos de servidor.|Sí|
|Explorador de soluciones|Permite ver y administrar proyectos y archivos.|Sí|
|Lista de tareas|Permite administrar los elementos de trabajo que pertenecen al código.|No|
|Proyectos de prueba|Proporciona características que ayudan a probar el código.|No|
|Cuadro de herramientas|Muestra pestañas que contienen objetos que se pueden arrastrar, como controles y secciones de texto o código.|Sí|

## <a name="see-also"></a>Vea también

- [Guía de F# (.NET Framework)](/dotnet/fsharp/)
- [Empezar a trabajar con F# en Visual Studio](/dotnet/fsharp/get-started/get-started-visual-studio)