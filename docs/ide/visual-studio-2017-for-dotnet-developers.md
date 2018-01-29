---
title: Visual Studio 2017 para desarrolladores de .NET | Microsoft Docs
description: "Información general de las características de Visual Studio 2017 para ayudarle a escribir código de .NET mejor y más rápidamente."
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
ms.openlocfilehash: db1e944f3ce12369b096c75a7fc12648a2d7e91d
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="visual-studio-2017-for-net-developers"></a>Visual Studio 2017 para desarrolladores de .NET

## <a name="smart-code-editor"></a>Editor de código inteligente

[Documentación: uso de IntelliSense](using-intellisense.md)  
[Documentación: características del editor inteligente](writing-code-in-the-code-and-text-editor.md)

Visual Studio tiene una comprensión profunda de su código a través del compilador Roslyn para proporcionarle características de edición automática, como colores de sintaxis, finalización de código, revisión ortográfica de variables que se han escrito incorrectamente, resolución de tipos no importados, esquematización, visualizadores de estructuras, [CodeLens](find-code-changes-and-other-history-with-codelens.md), jerarquía de llamadas, información rápida sobre la que se puede mantener el mouse, ayuda sobre parámetros, así como herramientas para refactorización, aplicación de acciones rápidas y generación de código.

![Editor de código inteligente de Visual Studio](../ide/media/VSIDE_Productivity_SmartCodeEditor.png "VSIDE_Productivity_SmartCodeEditor")

## <a name="navigate-and-search-your-codebase"></a>Navegar y buscar el código base

[Documentación: navegar por el código](navigating-code.md)

Navegue con rapidez por el código de .NET saltando a cualquier archivo, tipo, miembro o declaración de símbolo con el método abreviado *Ir a todo* (**Ctrl+T**). Busque todas las referencias de un símbolo o literal en el código, incluidas las referencias entre lenguajes de .NET (**Mayús+F12**). Y use nuestros comandos de navegación dirigidos para saltar directamente a las definiciones de símbolos (**F12**) o implementaciones (**Ctrl+F12**).

![Ir a todo y Buscar todas las referencias](../ide/media/VSIDE_Productivity_Navigation.png "VSIDE_Productivity_Navigation")

## <a name="live-code-analysis-for-code-quality"></a>Análisis de código activo para la calidad del código

[Documentación: refactorizaciones y acciones rápidas](refactoring-code-generation-quick-actions.md)

Visual Studio tiene diagnósticos de código activos que le ayudan a mejorar la calidad del código mediante la detección de errores y código potencialmente problemático. Proporcionamos acciones rápidas (**Ctrl+.**) para resolver los problemas detectados en el documento, proyecto o solución. Habilite el *análisis completo de la solución* para encontrar problemas en toda la solución, incluso si no tiene esos archivos abiertos en el editor.

Además, use las sugerencias de código para obtener información sobre los procedimientos recomendados, código auxiliar o generar el código, refactorizar el código y adoptar nuevas características del lenguaje con el método abreviado acceso directo.

![Aplicar revisiones rápidas y refactorizaciones mediante el menú de bombilla](../ide/media/VSIDE_Productivity_CodeAnalysis.png "VSIDE_Productivity_CodeAnalysis")

## <a name="unit-testing"></a>Pruebas unitarias

[Documentación: pruebas unitarias en Visual Studio](../test/improve-code-quality.md)

Ejecute y depure las pruebas unitarias basadas en los marcos de pruebas MSTest, NUnit o XUnit para cualquier aplicación destinada a .NET Framework, .NET Standard o .NET Core. Explore y revise las pruebas en el *Explorador de pruebas* o vea inmediatamente cómo afectan los cambios en el código a las pruebas unitarias en el editor con *Live Unit Testing* (solo para el SKU de Enterprise). 

![Live Unit Testing en Visual Studio](../ide/media/VSIDE_Productivity_LiveUnitTesting.png "VSIDE_Productivity_LiveUnitTesting")

## <a name="code-consistency-and-style"></a>Coherencia y estilo del código

[Documentación: opciones del editor personalizadas y portátiles](create-portable-custom-editor-options.md)  
[Documentación: configuración de estilo de código .NET para EditorConfig](editorconfig-code-style-settings-reference.md)

Visual Studio permite la configuración de convenciones de codificación, detecta infracciones de estilo de codificación y proporciona soluciones rápidas para solucionar problemas de estilo con el método abreviado Ctrl+. Configure y aplique las convenciones de formato, nomenclatura y estilo de código del equipo en un repositorio, lo que permite invalidar valores en el nivel de proyecto y archivo, con *EditorConfig*.

![Configurar y aplicar las convenciones de codificación con EditorConfig](../ide/media/VSIDE_Productivity_CodeStyle.png "VSIDE_Productivity_CodeStyle")

## <a name="debugging"></a>Depuración

[Documentación: depuración en Visual Studio](../debugger/index.md)

Visual Studio incluye un depurador de primer nivel que permite depurar las aplicaciones de .NET destinadas a .NET Framework, .NET Standard y .NET Core. Alterne y defina puntos de interrupción condicionales (**F9**), depure llamadas de método paso a paso por instrucciones, evalúe expresiones LINQ y lambda, establezca inspecciones de variables, vuelva a adjuntar a procesos, examine la pila de llamadas o incluso realice modificaciones en tiempo real en el código durante la depuración con *Editar y continuar*.

Si el servicio se ejecuta en Azure, use *Depuración de instantáneas* para diagnosticar problemas en sus aplicaciones de nube activas implementadas en Visual Studio 2017 Enterprise.

![Depuración en Visual Studio](../ide/media/VSIDE_Productivity_Debugging.png "VSIDE_Productivity_Debugging")

## <a name="version-control"></a>Control de versiones

[Documentación: control de versiones en Visual Studio](/vsts/index)

Use git o TFVC para almacenar y actualizar el código en Visual Studio. En el editor, organice los cambios locales con Team Explorer y use la barra de estado para realizar el seguimiento de las confirmaciones y cambios pendientes. Configure la integración y entrega continuas dentro de Visual Studio con nuestra extensión [Herramientas de entrega continua para Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) para adoptar el flujo de trabajo de un desarrollador rápido.

![Control de código fuente en Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png "VSIDE_Productivity_SourceControl")

## <a name="extensibility"></a>Extensibilidad

[Documentación: extender Visual Studio](../extensibility/index.md)

Visual Studio tiene un ecosistema completo de extensiones que puede instalar o crear según sea necesario. Instale las extensiones desde la *Galería de extensiones* o *Visual Studio Marketplace*, compile su propio complemento de editor con el *SDK de VS* o cree su propio analizador de código activo o refactorización mediante el *SDK de la plataforma del compilador de .NET*. Puede encontrar sugerencias y correcciones de código adicionales mediante la descarga de la extensión [Análisis de código de Microsoft](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

![Galería de extensiones de Visual Studio](../ide/media/VSIDE_Productivity_Extensibility.png "VSIDE_Productivity_Extensibility")

## <a name="popular-extensions--shortcuts"></a>Extensiones y métodos abreviados más conocidos

Si anteriormente usaba otro IDE o entorno de codificación, es posible que la instalación de una de estas extensiones le sea útil:

- [Emacs Emulación](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation )
- [HotKeys for Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Estos son accesos directos populares de Visual Studio. Tenga en cuenta que algunas extensiones desenlazan los enlaces de teclado de Visual Studio y debe restaurar estos enlaces de teclado para usar los comandos que aparecen a continuación. Para restaurar los enlaces de teclado a los valores predeterminados de Visual Studio, vaya a **Herramientas > Importar y exportar configuraciones... > Restablecer todas las configuraciones**.

| Métodos abreviados (todos los perfiles) | Comando | Description |
|-|-|-|
| **Ctrl+T** | Ir a todo | Navegar a cualquier declaración de archivo/tipo/miembro/símbolo |
| **F12** (también **Ctrl+clic**) | Ir a definición | Navegar hasta donde se define un símbolo |
| **Ctrl+F12** | Ir a implementación | Navegar desde cualquier tipo base o miembro a sus distintas implementaciones |
| **Mayús+F12** | Buscar todas las referencias | Ver todas las referencias de símbolos o literales |
| **Ctrl+.** (también **Alt+Entrar** en el perfil de C#) | Acciones rápidas y refactorizaciones | Ver qué correcciones de código, acciones de generación de código, refactorizaciones u otras acciones rápidas están disponibles en la posición del cursor o selección de código |
| **Ctrl**+**E**,**V** | Línea duplicada | Duplica la línea de código en la que se encuentra el cursor (disponible en la **versión 15.6 de Visual Studio 2017 (versión preliminar 2)** y posteriores) |
| **Ctrl**+**W** | Expandir selección | Expande la selección actual en una unidad estructural (disponible en la **versión 15.5 de Visual Studio 2017**) |
| **Ctrl**+**Shift**+**W** | Contraer selección | Contrae (disminuye) la selección actual en una unidad estructural (disponible en la **versión 15.5 de Visual Studio 2017**) |
| **Ctrl+Q** | Inicio rápido | Buscar todos los valores de Visual Studio |
| **F5** | Iniciar depuración | Iniciar la depuración de la aplicación |
| **Ctrl+F5** | Ejecutar sin depurar | Ejecutar la aplicación localmente sin depuración |
| **Ctrl+K,D** (perfil predeterminado) o **Ctrl+E,D** (perfil de C#) | Dar formato al documento | Limpiar el formato de las infracciones en el archivo según la configuración de nueva línea, espaciado y sangría |
| **Ctrl+\\,E** (perfil predeterminado) o **Ctrl+W,E** (perfil de C#) | Ver lista de errores | Ver todos los errores en el documento, proyecto o solución |