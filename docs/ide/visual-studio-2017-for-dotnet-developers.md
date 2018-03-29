---
title: Visual Studio 2017 para desarrolladores de .NET | Microsoft Docs
description: Información general de las características de Visual Studio 2017 para ayudarle a escribir código de .NET mejor y más rápidamente.
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.technology: vs-ide-general
ms.date: 01/16/2018
ms.topic: article
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 7e910c50682d45d209d993cb883ca01d1ea436f2
ms.sourcegitcommit: 236c250bb97abdab99d00c6525d106fc0035d7d0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2018
---
# <a name="visual-studio-2017-productivity-guide-for-net-developers"></a>Guía de productividad de Visual Studio 2017 para desarrolladores de .NET

- [Guía de productividad](#guide)
- [Introducción a Visual Studio 2017](#overview)

## <a name="a-idguide-productivity-guide"></a><a id="guide"/> Guía de productividad
[Visual Studio 2017](https://www.visualstudio.com/downloads/) aumenta la productividad de los desarrolladores a un nivel nunca visto. Hemos mejorado el rendimiento y la confiabilidad del inicio y la carga de la solución, la detección de pruebas y la latencia de escritura. También hemos agregado y mejorado características que agilizan la escritura de código de calidad. Algunas de estas características son: navegación a los ensamblados descompilados, sugerencias de nombres de variable mientras se escribe, una vista jerárquica en el Explorador de pruebas, Ir a todo (**Ctrl+T**) para navegar a las declaraciones de archivo/tipo/miembro/símbolo, una aplicación auxiliar de excepciones inteligente, la configuración y la aplicación de estilo de código, así como numerosas correcciones de código y refactorizaciones. 

Siga esta guía para optimizar su productividad.

###  <a name="im-used-to-my-keyboard-shortcuts-from-a-different-extensioneditoride"></a>Estoy habituado a los métodos abreviados de mi teclado de una extensión/editor/IDE diferente.

Si anteriormente usaba otro IDE o entorno de codificación, es posible que la instalación de una de estas extensiones le sea útil:

- [Emacs Emulación](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [HotKeys for Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Estos son accesos directos populares de Visual Studio. 

> [!NOTE]
> Algunas extensiones desenlazan los enlaces de teclado predeterminados de Visual Studio, por lo que es necesario restaurarlos para usar los comandos que aparecen a continuación. Para restaurar los enlaces de teclado a los valores predeterminados de Visual Studio, vaya a: **Herramientas > Importar y exportar configuración... > Restablecer todas las configuraciones** o **Herramientas > Opciones > Teclado > Restablecer**.

| Métodos abreviados (todos los perfiles) | Comando | Description |
|-|-|-|
| **Ctrl+T** | Ir a todo | Navegar a cualquier declaración de archivo/tipo/miembro/símbolo |
| **F12** (también **Ctrl+clic**) | Ir a definición | Navegar hasta donde se define un símbolo |
| **Ctrl+F12** | Ir a implementación | Navegar desde cualquier tipo base o miembro a sus distintas implementaciones |
| **Mayús+F12** | Buscar todas las referencias | Ver todas las referencias de símbolos o literales |
| **Ctrl**+**.** (también **Alt+Entrar** en el perfil de C#) | Acciones rápidas y refactorizaciones | Ver qué correcciones de código, acciones de generación de código, refactorizaciones u otras acciones rápidas están disponibles en la posición del cursor o selección de código |
| **Ctrl**+**D** | Línea duplicada | Duplica la línea de código en la que se encuentra el cursor (disponible en la **Visual Studio 2017, versión 15.6** y posteriores) |
| **Mayús**+**Alt**+**+**/**-** | Expandir o contraer la selección | Expande o contrae la selección actual en el editor (disponible en **Visual Studio 2017 versión 15.5** y posteriores). |
| **Ctrl+Q** | Inicio rápido | Buscar todos los valores de Visual Studio |
| **F5** | Iniciar depuración | Iniciar la depuración de la aplicación |
| **Ctrl+F5** | Ejecutar sin depurar | Ejecutar la aplicación localmente sin depuración |
| **Ctrl+K,D** (perfil predeterminado) o **Ctrl+E,D** (perfil de C#) | Dar formato al documento | Limpiar el formato de las infracciones en el archivo según la configuración de nueva línea, espaciado y sangría |
| **Ctrl+\\,E** (perfil predeterminado) o **Ctrl+W,E** (perfil de C#) | Ver lista de errores | Ver todos los errores en el documento, proyecto o solución |

### <a name="i-need-a-way-to-quickly-navigate-to-files-or-types"></a>Necesito una manera de desplazarme rápidamente a los archivos o tipos.
Visual Studio 2017 tiene una característica denominada _Ir a todo_ (**Ctrl+T**). Ir a todo permite saltar rápidamente a cualquier archivo, tipo, miembro o declaración de símbolo.
- Cambie la ubicación de esta barra de búsqueda o desactive la opción "vista previa en vivo de la navegación" con el icono de **engranaje**.
- Filtre los resultados utilizando nuestra sintaxis de consulta (por ejemplo, "t mytype"). También puede definir el ámbito de la búsqueda solo al documento actual.
- Se admite el uso de mayúsculas intermedias (camelCase).

![Ir a todo en Visual Studio](../ide/media/VS2017Guide-go-to-all.png "VS2017Guide-go-to-all")

### <a name="my-team-enforces-code-style-rules-on-our-codebase"></a>Mi equipo impone las reglas de estilo de código en el código base.
Puede utilizar un archivo .editorconfig para codificar las convenciones de codificación. Se recomienda instalar la [extensión EditorConfig Language Services](https://aka.ms/editorconfig) para agregar y editar un archivo .editorconfig. Recomendamos que consulte la [documentación](https://aka.ms/editorconfigDocs) para ver todas las opciones de convención de codificación de .NET.

Visite [esta página](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8) para ver un ejemplo de .editorconfig.

![Cumplimiento con el estilo de código en Visual Studio](../ide/media/VS2017Guide-code-style.png "VS2017Guide-code-style")

### <a name="i-need-more-refactorings-and-code-fixes"></a>Necesito más correcciones de código y refactorizaciones.
Visual Studio 2017 incluye un gran número de refactorizaciones, acciones de generación de código y correcciones de código. Puede verlas en nuestra [documentación](https://aka.ms/refactorings). Un subrayado ondulado rojo representa un error, un subrayado ondulado verde representa una advertencia y tres puntos de color gris representan sugerencias de código.

Para acceder a las correcciones de código, puede hacer clic en el icono de bombilla o destornillador, o bien presionar **Ctrl+.** o **Alt+Entrar**. Cada corrección incluye una ventana de vista previa que muestra un diff de código activo con el funcionamiento de la solución.

Estas son algunas refactorizaciones y correcciones rápidas populares: Cambiar el nombre, Extraer método, Cambiar signatura del método, Generar constructor, Generar método, Mover tipo a archivo, Agregar comprobación de valores null, Agregar parámetro, Eliminar instrucciones Using innecesarias.

Las refactorizaciones y las correcciones de código se pueden escribir fácilmente con [analizadores de Roslyn](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix). Varios miembros de la comunidad han escrito extensiones *gratuitas* que agregan más inspecciones de código: Roslynator y SonarLint para Visual Studio. 

![Refactorizaciones en Visual Studio](../ide/media/VS2017Guide-refactoring.png "VS2017Guide-refactoring")

### <a name="i-need-find-usages-go-to-implementation-navigate-to-decompiled-assemblies"></a>Necesito encontrar usos, ir a la implementación, navegar a ensamblados descompilados.
Visual Studio 2017 tiene muchas características que ayudan a buscar y desplazarse por el código base, como Buscar todas las referencias (**Mayús+F12**), Ir a la implementación (**Ctrl+F12**), Ir a la definición (**F12** o **Ctrl+Clic**). La navegación a ensamblados descompilados se agregó en la versión 15.6. Para activar esta característica, vaya a **Herramientas > Opciones > Editor de texto > C# > Avanzado > Habilitar la navegación a orígenes descompilados**.

![Navegar a orígenes descompilados en Visual Studio](../ide/media/VS2017Guide-navigate-to-source.png "VS2017Guide-navigate-to-source")

### <a name="i-want-to-run-and-see-my-unit-tests"></a>Quiero ejecutar y ver mis pruebas unitarias.
Tenemos dos ofertas para pruebas unitarias en Visual Studio 2017: Explorador de pruebas y _Live Unit Testing_. En la versión 15.6, hemos mejorado considerablemente la velocidad de la detección de pruebas en el Explorador de pruebas. También hemos rediseñado la interfaz de usuario para permitir la ordenación jerárquica.

Visual Studio también tiene una característica de pruebas unitarias denominada [Live Unit Testing](/test/live-unit-testing). Live Unit Testing se ejecuta de manera continua en segundo plano, ejecuta pruebas afectadas por el cambio en el código y actualiza los iconos del editor insertado para que el desarrollador conozca el estado de las pruebas.

![Vista de jerarquía para el Explorador de pruebas en Visual Studio](../ide/media/VS2017Guide-hiearchy-test-explorer.png "VS2017Guide-hiearchy-test-explorer")

### <a name="what-other-features-do-i-need-to-know-about"></a>¿Qué otras características es necesario conocer?
La lista siguiente incluye características de editor y productividad que aumentan la eficacia a la hora de escribir código. Puede que sea necesario habilitar algunas de las características porque están desactivadas de forma predeterminada (porque indexan el contenido del equipo, son controvertidas o están controvertidos o son actualmente experimentales).
- *Buscar archivo en el Explorador de soluciones* resalta el archivo activo en el Explorador de soluciones.
  - **Herramientas>Opciones>Proyectos y soluciones>Realizar seguimiento del elemento activo en el Explorador de soluciones**
- *Add usings for types in reference assemblies and NuGet packages* (Agregar instrucciones using para tipos de ensamblados de referencia y paquetes de NuGet) muestra una bombilla con una corrección de código para instalar un paquete de NuGet para un tipo sin referencia.
  - **Herramientas>Opciones>Editor de texto>C#>Opciones avanzadas>Sugerir usos para tipos de ensamblados de referencia** y **Sugerir usos para tipos de paquetes NuGet**
- *Habilitar análisis de la solución completa* permite ver todos los errores de la solución en la lista de errores.
  - **Herramientas>Opciones>Editor de texto>C#>Opciones avanzadas>Habilitar análisis de la solución completa**
- *Habilitar la navegación a orígenes descompilados* permite habilitar Ir a definición en tipos y miembros de orígenes externos, y usar el descompilador ILSpy para mostrar los cuerpos de método.
  - **Herramientas>Opciones>Editor de texto>C#>Opciones avanzadas>Habilitar la navegación a orígenes descompilados**.
- *Modo de autocompletar/sugerencia* en IntelliSense cambia el comportamiento de finalización. Los desarrolladores con conocimientos de IntelliJ tienden a cambiar esta configuración predeterminada.
  - **Menú > Editar > IntelliSense > Activar modo de autocompletar**
- Tenemos *fragmentos de código* para ayudar a crear código auxiliar reutilizable (presione "Tab" dos veces). Consulte la [lista completa](/ide/visual-csharp-code-snippets).

![Fragmentos de código en Visual Studio](../ide/media/VS2017Guide-code-snippet.png "VS2017Guide-code-snippet")

### <a name="missing-a-feature-that-makes-you-productive-or-experiencing-poor-performance"></a>¿Falta alguna característica que mejora su productividad o está experimentando un bajo rendimiento?
Tiene varias formas de enviarnos sus comentarios:
- Las solicitudes de características de .NET pueden presentarse en nuestro [repositorio de GitHub](https://github.com/dotnet/roslyn/issues).
- Las solicitudes de características, los errores y los problemas de rendimiento de Visual Studio se pueden notificar a través del icono **Enviar comentarios** situado en la parte superior de la ventana de Visual Studio.


## <a name="a-idoverview-overview-of-visual-studio-2017-for-net-developers"></a><a id="overview"/> Información general de Visual Studio 2017 para desarrolladores de .NET

### <a name="smart-code-editor"></a>Editor de código inteligente

- [Documentación: uso de IntelliSense](using-intellisense.md)
- [Documentación: características del editor inteligente](writing-code-in-the-code-and-text-editor.md)

Visual Studio tiene una comprensión profunda de su código a través del compilador de .NET ("Roslyn"), que le proporciona características de edición automática, como colores de sintaxis, finalización de código, revisión ortográfica de variables que se han escrito incorrectamente, resolución de tipos no importados, esquematización, visualizadores de estructuras, [CodeLens](find-code-changes-and-other-history-with-codelens.md), jerarquía de llamadas, información rápida sobre la que se puede mantener el mouse, ayuda sobre parámetros, así como herramientas para refactorización, aplicación de acciones rápidas y generación de código.

![Editor de código inteligente de Visual Studio](../ide/media/VSIDE_Productivity_SmartCodeEditor.png "VSIDE_Productivity_SmartCodeEditor")

### <a name="navigate-and-search-your-codebase"></a>Navegar y buscar el código base

[Documentación: navegar por el código](navigating-code.md)

Navegue con rapidez por el código de .NET saltando a cualquier archivo, tipo, miembro o declaración de símbolo con el método abreviado *Ir a todo* (**Ctrl+T**). Busque todas las referencias de un símbolo o literal en el código, incluidas las referencias entre lenguajes de .NET (**Mayús+F12**). Y use nuestros comandos de navegación dirigidos para saltar directamente a las definiciones de símbolos (**F12**) o implementaciones (**Ctrl+F12**).

![Ir a todo y Buscar todas las referencias](../ide/media/VSIDE_Productivity_Navigation.png "VSIDE_Productivity_Navigation")

### <a name="live-code-analysis-for-code-quality"></a>Análisis de código activo para la calidad del código

[Documentación: refactorizaciones y acciones rápidas](refactoring-code-generation-quick-actions.md)

Visual Studio tiene diagnósticos de código activos que le ayudan a mejorar la calidad del código mediante la detección de errores y código potencialmente problemático. Proporcionamos acciones rápidas (**Ctrl**+**.**) para resolver los problemas detectados en el documento, proyecto o solución. Habilite el *análisis completo de la solución* para encontrar problemas en toda la solución, incluso si no tiene esos archivos abiertos en el editor.

Además, use las sugerencias de código para obtener información sobre los procedimientos recomendados, código auxiliar o generar el código, adoptar nuevas características del lenguaje con el método abreviado **Ctrl**+**.**, Ctrl+.

![Aplicar revisiones rápidas y refactorizaciones mediante el menú de bombilla](../ide/media/VSIDE_Productivity_CodeAnalysis.png "VSIDE_Productivity_CodeAnalysis")

### <a name="unit-testing"></a>Pruebas unitarias

[Documentación: pruebas unitarias en Visual Studio](../test/improve-code-quality.md)

Ejecute y depure las pruebas unitarias basadas en los marcos de pruebas MSTest, NUnit o XUnit para cualquier aplicación destinada a .NET Framework, .NET Standard o .NET Core. Explore y revise las pruebas en el *Explorador de pruebas* o vea inmediatamente cómo afectan los cambios en el código a las pruebas unitarias en el editor con *Live Unit Testing* (solo para el SKU de Enterprise).

![Live Unit Testing en Visual Studio](../ide/media/VSIDE_Productivity_LiveUnitTesting.png "VSIDE_Productivity_LiveUnitTesting")

### <a name="code-consistency-and-style"></a>Coherencia y estilo del código

- [Documentación: opciones del editor personalizadas y portátiles](create-portable-custom-editor-options.md)
- [Documentación: configuración de estilo de código .NET para EditorConfig](editorconfig-code-style-settings-reference.md)

Visual Studio permite la configuración de convenciones de codificación, proporciona soluciones rápidas para solucionar problemas de estilo con el método abreviado **Ctrl**+**.** Ctrl+. Configure y aplique las convenciones de formato, nomenclatura y estilo de código del equipo en un repositorio, lo que permite invalidar valores en el nivel de proyecto y archivo, con *EditorConfig*.

![Configurar y aplicar las convenciones de codificación con EditorConfig](../ide/media/VSIDE_Productivity_CodeStyle.png "VSIDE_Productivity_CodeStyle")

### <a name="debugging"></a>Depuración

[Documentación: depuración en Visual Studio](../debugger/index.md)

Visual Studio incluye un depurador de primer nivel que permite depurar las aplicaciones de .NET destinadas a .NET Framework, .NET Standard y .NET Core. Alterne y defina puntos de interrupción condicionales (**F9**), depure llamadas de método paso a paso por instrucciones, evalúe expresiones LINQ y lambda, establezca inspecciones de variables, vuelva a adjuntar a procesos, examine la pila de llamadas o incluso realice modificaciones en tiempo real en el código durante la depuración con *Editar y continuar*.

Si el servicio se ejecuta en Azure, use *Depuración de instantáneas* para diagnosticar problemas en sus aplicaciones de nube activas implementadas en Visual Studio 2017 Enterprise.

![Depuración en Visual Studio](../ide/media/VSIDE_Productivity_Debugging.png "VSIDE_Productivity_Debugging")

### <a name="version-control"></a>Control de versiones

[Documentación: control de versiones en Visual Studio](/vsts/index)

Use git o TFVC para almacenar y actualizar el código en Visual Studio. En el editor, organice los cambios locales con Team Explorer y use la barra de estado para realizar el seguimiento de las confirmaciones y cambios pendientes. Configure la integración y entrega continuas dentro de Visual Studio con nuestra extensión [Herramientas de entrega continua para Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) para adoptar el flujo de trabajo de un desarrollador rápido.

![Control de código fuente en Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png "VSIDE_Productivity_SourceControl")

### <a name="extensibility"></a>Extensibilidad

[Documentación: extender Visual Studio](../extensibility/index.md)

Visual Studio tiene un ecosistema completo de extensiones que puede instalar o crear según sea necesario. Instale las extensiones desde la *Galería de extensiones* o *Visual Studio Marketplace*, compile su propio complemento de editor con el *SDK de VS* o cree su propio analizador de código activo o refactorización mediante el *SDK de la plataforma del compilador de .NET*. Puede encontrar sugerencias y correcciones de código adicionales mediante la descarga de la extensión [Análisis de código de Microsoft](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

![Galería de extensiones de Visual Studio](../ide/media/VSIDE_Productivity_Extensibility.png "VSIDE_Productivity_Extensibility")
