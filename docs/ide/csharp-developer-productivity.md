---
title: Aumento de la productividad de desarrollo de .NET
description: Información general sobre la navegación, el análisis de código, las pruebas unitarias y otras características para ayudarle a escribir código .NET mejor y más rápido.
author: kuhlenh
ms.author: gewarren
manager: jillfra
ms.date: 03/26/2019
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 07584f9e04be805ed699676c678b2147ec3679ff
ms.sourcegitcommit: cd91a8a4f6086cda9ba6948be25864fc7d6b8e44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59537629"
---
# <a name="visual-studio-productivity-guide-for-c-developers"></a>Guía de productividad de Visual Studio para desarrolladores de C#

Descubra cómo Visual Studio aumenta la productividad de los desarrolladores a un nivel nunca visto. Aproveche las mejoras de productividad y rendimiento, como la navegación a los ensamblados descompilados, las sugerencias de nombres de variable mientras se escribe, una vista jerárquica en el **Explorador de pruebas**, Ir a todo (**CTRL**+**T**) para navegar a las declaraciones de archivo/tipo/miembro/símbolo, un **asistente de excepciones** inteligente, la configuración y la aplicación de estilo de código, así como numerosas correcciones de código y refactorizaciones.

## <a name="im-used-to-keyboard-shortcuts-from-a-different-editor"></a>Estoy habituado a los métodos abreviados de teclado de otro editor

::: moniker range="vs-2017"

**Novedad de Visual Studio 2017 versión 15.8**

::: moniker-end

Si ya conoce otro IDE o entorno de programación, puede cambiar las combinaciones de teclado a *Visual Studio Code* o *ReSharper* (Visual Studio):

![Combinaciones de teclado de Visual Studio](../ide/media/VS2017Guide-Keyboard.png)

Algunas extensiones también ofrecen combinaciones de teclado:

- [HotKeys for Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emacs Emulación](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Estos son accesos directos populares de Visual Studio:

| Métodos abreviados (todos los perfiles) | Comando | Descripción |
|-|-|-|
| **Ctrl**+**T** | Ir a todo | Navegar a cualquier declaración de archivo, tipo, miembro o símbolo |
| **F12** (también **CTRL**+**clic**) | Ir a definición | Navegar hasta donde se define un símbolo |
| **CTRL**+**F12** | Ir a implementación | Navegar desde cualquier tipo base o miembro a sus distintas implementaciones |
| **MAYÚS**+**F12** | Buscar todas las referencias | Ver todas las referencias de símbolos o literales |
| **Ctrl**+**.** (también **Alt**+**Entrar** en el perfil de C#) | Acciones rápidas y refactorizaciones | Ver qué correcciones de código, acciones de generación de código, refactorizaciones u otras acciones rápidas están disponibles en la posición del cursor o selección de código |
| **Ctrl**+**D** | Línea duplicada | Duplica la línea de código en la que se encuentra el cursor (disponible en la **Visual Studio 2017, versión 15.6** y posteriores) |
| **Mayús**+**Alt**+**+**/**-** | Expandir o contraer la selección | Expande o contrae la selección actual en el editor (disponible en **Visual Studio 2017 versión 15.5** y posteriores). |
| **Mayús** + **Alt** + **.** | Inserción del siguiente símbolo de inserción coincidente | Permite agregar una selección y el símbolo de inserción en la ubicación siguiente que coincida con la actual (disponible en la **versión 15.8 de Visual Studio 2017** y versiones posteriores). |
| **Ctrl**+**Q** | Buscar | Buscar todos los valores de Visual Studio |
| **F5** | Iniciar depuración | Iniciar la depuración de la aplicación |
| **CTRL**+**F5** | Ejecutar sin depurar | Ejecutar la aplicación localmente sin depuración |
| **CTRL**+**K**,**D** (perfil predeterminado) o **CTRL**+**E**,**D** (perfil de C#) | [Dar formato al documento](code-styles-and-quick-actions.md#format-document-command) | Limpiar el formato de las infracciones en el archivo según la configuración de nueva línea, espaciado y sangría |
| **Ctrl**+**\\**,**Ctrl**+**E** (perfil predeterminado) o **Ctrl**+**W**,**E** (perfil de C#) | Ver lista de errores | Ver todos los errores en el documento, proyecto o solución |
| **Alt** + **RePág o AvPág** | Ir al problema siguiente o anterior | Permite ir al error, advertencia o sugerencia siguiente o anterior del documento (disponible en la **versión 15.8 de Visual Studio 2017** y versiones posteriores). |

> [!NOTE]
> Algunas extensiones desenlazan los enlaces de teclado de Visual Studio predeterminados. Para usar los anteriores comandos, restaure los enlaces de teclado a los valores predeterminados de Visual Studio. Para ello, vaya a **Herramientas** > **Importar y exportar configuración** > **Restablecer todas las configuraciones** o **Herramientas** > **Opciones** > **Teclado** > **Restablecer**.

Para más información sobre los métodos abreviados de teclado y los comandos, consulte [Métodos abreviados de teclado de Visual Studio](../ide/tips-and-tricks-for-visual-studio.md).

## <a name="navigate-quickly-to-files-or-types"></a>Navegación rápida a archivos o tipos

Visual Studio 2017 tiene una característica denominada **Ir a todo** (**Ctrl**+**T**). **Ir a todo** permite saltar rápidamente a cualquier archivo, tipo, miembro o declaración de símbolo.

- Cambie la ubicación de esta barra de búsqueda o desactive la vista previa en vivo de la navegación en el icono de **engranaje**.
- Filtre los resultados mediante una sintaxis como `t mytype`.
- Puede definir el ámbito de la búsqueda solo al documento actual.
- Se admite el uso de mayúsculas intermedias (camelCase).

![Ir a todo en Visual Studio](../ide/media/VS2017Guide-go-to-all.png)

## <a name="enforce-code-style-rules-on-a-codebase"></a>Aplicación de reglas de estilo de código en un código base

Puede utilizar un archivo *.editorconfig* para codificar las convenciones de codificación y que viajen con el origen.

::: moniker range="vs-2017"

- Puede instalar la [extensión de servicios EditorConfig](https://aka.ms/editorconfig), que facilita la tarea de agregar y editar un archivo *.editorconfig* en Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

- Cree automáticamente un archivo *.editorconfig* a partir de la configuración del estilo de código en **Herramientas** > **Opciones** > **Editor de texto** > **C#** > **Estilo de código**.

   ![Generación del archivo .editorconfig desde la configuración en VS 2019](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- Pruebe la [extensión IntelliCode para Visual Studio](/visualstudio/intellicode/intellicode-visual-studio). Esta extensión experimental deduce los estilos de código a partir del código existente y, a continuación, crea un valor *.editorconfig* no vacío con sus preferencias de estilo de código ya definidas.

- Consulte la documentación [de las opciones de convención de codificación de .NET](editorconfig-code-style-settings-reference.md).

- Consulte [esta página](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8) para ver un ejemplo de archivo *.editorconfig*.

![Cumplimiento con el estilo de código en Visual Studio](../ide/media/VSGuide_CodeStyle.png)

## <a name="refactorings-and-code-fixes"></a>Refactorizaciones y correcciones de código

Visual Studio incluye un gran número de refactorizaciones, acciones de generación de código y correcciones de código. Un subrayado ondulado rojo representa un error, un subrayado ondulado verde representa una advertencia y tres puntos de color gris representan sugerencias de código. Para acceder a las correcciones de código, puede hacer clic en el icono de bombilla o destornillador, o bien presionar **Ctrl**+**.** o **Alt**+**Enter**. Cada corrección incluye una ventana de vista previa que muestra un diff de código activo con el funcionamiento de la solución.

Las correcciones rápidas y las refactorizaciones populares incluyen:

- *Cambiar nombre*
- *Extracción de método*
- *Cambio de signatura del método*
- *Generación de constructor*
- *Generación de método*
- *Mover tipo a archivo*
- *Agregar comprobación de valores Null*
- *Agregar parámetro*
- *Quitar directivas Using innecesarias*
- *Bucle foreach para una consulta LINQ o un método LINQ*
- *Extracción de miembros*
- Para más información, consulte las [características de generación de código](code-generation-in-visual-studio.md).

Puede [instalar analizadores de FxCop](../code-quality/install-fxcop-analyzers.md) para marcar los problemas de código. O bien puede escribir su propia refactorización o corrección de código con [analizadores de Roslyn](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix).

Varios miembros de la comunidad han escrito extensiones gratuitas que agregan inspecciones de código adicionales:

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
- [SonarLint para Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

![Refactorizaciones en Visual Studio](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>Características Encontrar usos, Ir a implementación y Navegar a ensamblados descompilados

Visual Studio tiene muchas características para ayudarle a buscar código base y [navegar por él](../ide/navigating-code.md).

| Característica | Acceso directo | Detalles y mejoras |
|- | - | -|
| Buscar todas las referencias | **MAYÚS**+**F12**| Los resultados aparece en color y se pueden agrupar por proyecto, definición y tipo de referencia como lectura o escritura. También puede "bloquear" resultados. |
| Ir a implementación | **CTRL**+**F12** | Puede usar Ir a definición en la palabra clave `override` para navegar al miembro reemplazado. |
| Ir a definición | **F12** o **CTRL**+**Clic**| Presione **Ctrl** mientras hace clic para navegar a la definición. |
| Definición de Peek | **Alt**+**F12** | Vista en línea de una definición. |
| Visualizador de estructura | Líneas discontinuas grises entre llaves | Mantenga el puntero del mouse para ver la estructura del código. |
| Navegación a los ensamblados descompilados | **F12** o **CTRL**+**Clic** | Navegue a un origen externo (descompilado con ILSpy) habilitando la característica: **Herramientas** > **Opciones** > **Editor de texto** > **C#** > **Opciones avanzadas** > **Habilitar la navegación a orígenes descompilados**. |

![Ir a todo y buscar todas las referencias](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="improved-intellisense"></a>IntelliSense mejorado

Descargue la [extensión IntelliCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.VSIntelliCode) para obtener [finalizaciones de código en contexto](/visualstudio/intellicode/intellicode-visual-studio) en lugar de simplemente una lista alfabética. También puede entrenar un [modelo IntelliSense personalizado](/visualstudio/intellicode/custom-model-faq) basado en sus propias bibliotecas específicas de dominio.

## <a name="unit-testing"></a>Pruebas unitarias

A partir de Visual Studio 2017, hay muchas mejoras en la experiencia de prueba. Puede realizar pruebas con los marcos de pruebas MSTest v1, MSTest v2, NUnit o XUnit.

- La detección de pruebas del **Explorador de pruebas** es rápida.
- Organice las pruebas en el **Explorador de pruebas** con *ordenación jerárquica*.
- [Live Unit Testing](../test/live-unit-testing.md) ejecuta de manera continua pruebas afectadas por el cambio en el código y actualiza los iconos del editor insertado para que el desarrollador conozca el estado de las pruebas. Incluya o excluya pruebas específicas o proyectos de prueba desde su conjunto de pruebas en directo.

![Vista de jerarquía para el Explorador de pruebas en Visual Studio](../ide/media/VSGuide_Testing.png)

## <a name="debugging"></a>Depuración

Estas son algunas de las funcionalidades de depuración de Visual Studio:

::: moniker range=">=vs-2019"

- La capacidad de buscar una cadena dentro de las ventanas **Watch** (Inspeccionar), **Autos** (Autos) y **Locals** (Variables locales).
- *Ejecutar hasta hacer clic*, que permite mantener el puntero junto a una línea de código, hacer clic en el icono verde "reproducir" que aparece y ejecutar el programa hasta que llegue a esa línea.
- El **asistente de excepciones**, que pone la información más importante en el nivel superior del cuadro de diálogo, por ejemplo, qué variable es `null` en `NullReferenceException`.
- La depuración [Retroceder](../debugger/view-historical-application-state.md), que permite volver a puntos de interrupción anteriores y ver el estado de la aplicación tal y como estaba en un momento anterior.
- [Depuración de instantáneas](/azure/application-insights/app-insights-snapshot-debugger), que permite investigar el estado de una aplicación web en directo en el momento en que se inició una excepción (debe estar en Azure).

::: moniker-end

::: moniker range="vs-2017"

- *Ejecutar hasta hacer clic*, que permite mantener el puntero junto a una línea de código, hacer clic en el icono verde "reproducir" que aparece y ejecutar el programa hasta que llegue a esa línea.
- El **asistente de excepciones**, que pone la información más importante en el nivel superior del cuadro de diálogo, por ejemplo, qué variable es `null` en `NullReferenceException`.
- La depuración [Retroceder](../debugger/view-historical-application-state.md), que permite volver a puntos de interrupción anteriores y ver el estado de la aplicación tal y como estaba en un momento anterior.
- [Depuración de instantáneas](/azure/application-insights/app-insights-snapshot-debugger), que permite investigar el estado de una aplicación web en directo en el momento en que se inició una excepción (debe estar en Azure).

::: moniker-end

![Asistente de excepciones de Visual Studio](../ide/media/VSGuide_Debugging.png)

## <a name="version-control"></a>Control de versiones

Puede usar git o TFVC para almacenar y actualizar el código en Visual Studio.

::: moniker range=">=vs-2019"

- Instale la extensión [Pull requests for Visual Studio](https://marketplace.visualstudio.com/items?itemName=vsideversioncontrolmsft.pr4vs) para crear, revisar, modificar y ejecutar solicitudes de incorporación de cambios sin salir de Visual Studio.

::: moniker-end

- Organice los cambios locales con [Team Explorer](reference/team-explorer-reference.md) y use la barra de estado para realizar el seguimiento de las confirmaciones y cambios pendientes.

- Configure la integración y entrega continuas de sus proyectos de ASP.NET dentro de Visual Studio con la extensión [Herramientas de entrega continua para Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio).

![Control de código fuente en Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-should-i-know-about"></a>¿Qué otras características tengo que conocer?

La lista siguiente incluye características de editor y productividad que aumentan la eficacia a la hora de escribir código. Puede que sea necesario habilitar algunas de las características porque están desactivadas de forma predeterminada (porque indexan el contenido del equipo, son controvertidas o están controvertidos o son actualmente experimentales).

| Característica | Detalles | Cómo habilitar |
|-|-|-|
| Buscar archivo en el Explorador de soluciones | Resalta el archivo activo en el **Explorador de soluciones** | **Herramientas** > **Opciones** > **Proyectos y soluciones** > **Realizar seguimiento del elemento activo en el Explorador de soluciones** |
| Agregar usos para tipos de ensamblados de referencia y paquetes NuGet | Muestra una bombilla de error con una corrección de código para instalar un paquete NuGet para un tipo sin referencia | **Herramientas** > **Opciones** > **Editor de texto** > **C#** > **Opciones avanzadas** > **Sugerir usos para tipos de ensamblados de referencia** y **Sugerir usos para tipos de paquetes NuGet** |
| Habilitar análisis de la solución completa | Ver todos los errores de la solución en la **Lista de errores** | **Herramientas** > **Opciones** > **Editor de texto** > **C#** > **Opciones avanzadas** > **Habilitar análisis de la solución completa** |
| Habilitar la navegación a orígenes descompilados | Permite Ir a definición en tipos y miembros de orígenes externos y usar el descompilador ILSpy para mostrar los cuerpos de método | **Herramientas** > **Opciones** > **Editor de texto** > **C#** > **Opciones avanzadas** > **Habilitar la navegación a orígenes descompilados** |
| Modo de finalización y sugerencias | Cambia el comportamiento de finalización de IntelliSense. Los desarrolladores con conocimientos de IntelliJ tienden a usar aquí una configuración no predeterminada. | **Menú** > **Editar** > **IntelliSense** > **Alternar el modo de finalización** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Muestra la información de referencia de código y el historial de cambios en el editor | **Herramientas** > **Opciones** > **Editor de texto** > **Todos los lenguajes** > **CodeLens** |
| [Fragmentos de código](../ide/visual-csharp-code-snippets.md) | Ayudan al código auxiliar fuera del texto reutilizable común | Escriba un nombre de fragmento de código y presione **Tabulación** dos veces. |
