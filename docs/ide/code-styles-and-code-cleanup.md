---
title: Limpieza de código y opciones de estilo de código
ms.date: 04/25/2019
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 75b301f66f597f8b53a2561ffbbe05dfb8a4cb1c
ms.sourcegitcommit: 5a5f31a1a91bf243852c7da872211e63ab37fdaa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/16/2020
ms.locfileid: "90682690"
---
# <a name="code-style-preferences"></a>Preferencias de estilo del código

Puede definir ajustes de estilo de código en cada proyecto usando un [archivo EditorConfig file](#code-styles-in-editorconfig-files), o bien para todo el código que edite en Visual Studio, en la página [**Opciones** del editor de texto](#code-styles-in-the-options-dialog-box). Para el código de C#, también puede configurar Visual Studio para que aplique estas preferencias de estilo de código usando los comandos **Limpieza de código** (Visual Studio 2019) y **Dar formato al documento** (Visual Studio 2017).

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Comportamiento del editor en Visual Studio para Mac](/visualstudio/mac/editor-behavior).

## <a name="code-styles-in-editorconfig-files"></a>Estilos de código de los archivos EditorConfig

La [configuración del estilo de código](../ide/editorconfig-code-style-settings-reference.md) para .NET se puede especificar agregando un archivo [EditorConfig](create-portable-custom-editor-options.md) al proyecto. Los archivos EditorConfig están asociados con un código base en lugar de una cuenta de personalización de Visual Studio. La configuración de un archivo EditorConfig tiene prioridad sobre los estilos de código que se especifican en el cuadro de diálogo **Opciones**. Use un archivo EditorConfig cuando quiera aplicar los estilos de codificación para todos los colaboradores en el repositorio o proyecto.

::: moniker range=">=vs-2019"

Puede rellenar manualmente el archivo EditorConfig o generar manualmente el archivo a partir de la configuración de estilo de código que haya establecido en el cuadro de diálogo **Opciones** de Visual Studio. Esta página de opciones está disponible en **Herramientas** > **Opciones** > **Editor de texto** > [**C#** o **Basic**] > **Estilo de código** > **General**. Haga clic en **Generar archivo .editorconfig desde la configuración** para generar automáticamente un archivo *.editorconfig* de estilo de codificación basado en la configuración establecida en la página **Opciones**.

![Generación del archivo .editorconfig desde la configuración de Visual Studio 2019](media/vs-2019/generate-editorconfig-file-small.png)

::: moniker-end

## <a name="code-styles-in-the-options-dialog-box"></a>Estilos de código del cuadro de diálogo Opciones

Puede establecer las preferencias de estilo de código de los proyectos de C# y Visual Basic abriendo el cuadro de diálogo **Opciones** desde el menú **Herramientas**. En el cuadro de diálogo **Opciones**, seleccione **Editor de texto** > [**C#** o **Básica**] > **Estilo de código** > **General**.

Cada elemento de la lista muestra una vista previa de la preferencia cuando se selecciona:

::: moniker range="vs-2017"

![Opciones de estilo de código](media/code-style-quick-actions-dialog.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Opciones de estilo de código](media/vs-2019/code-style-quick-actions-dialog.png)

::: moniker-end

Las opciones que se establecen en esta ventana se aplican a la cuenta de personalización de Visual Studio y no están asociadas con un proyecto o código base determinado. Además, no se aplican en tiempo de compilación, lo que incluye las compilaciones de integración continua (CI). Si quiere asociar las preferencias de estilo de código con el proyecto y aplicar los estilos durante la compilación, especifique las preferencias en un [archivo .editorconfig](#code-styles-in-editorconfig-files) asociado con el proyecto.

### <a name="preference-and-severity"></a>Preferencia y gravedad

Para cada configuración de estilo de código de esta página, puede establecer los valores de **Preferencia** y **Gravedad** con las listas desplegables de cada línea. La gravedad se puede establecer en **Solo refactorización**, **Sugerencia**, **Advertencia** o **Error**. Si desea habilitar las [Acciones rápidas](../ide/quick-actions.md) para un estilo de código, asegúrese de que el valor **Gravedad** se establece en un valor distinto de **Solo refactorización**. El icono de bombilla ![Bombilla](media/light-bulb-dropdown.png), de bombilla de error ![Bombilla de error](media/error-bulb.png) o de destornillador ![Destornillador](media/screwdriver.png) de **Acciones rápidas** aparece cuando se usa un estilo no preferido, y puede elegir una opción en la lista **Acciones rápidas** para volver a escribir código de forma automática para el estilo preferido.

::: moniker range=">=vs-2019"

## <a name="enforce-code-styles-on-build"></a>Aplicación de estilos de código en la compilación

A partir de la versión 16.8 de Visual Studio 2019, que incluye el SDK de .NET 5.0 RC2, puede [aplicar las convenciones de codificación de .NET en la compilación](/dotnet/fundamentals/productivity/code-analysis#code-style-analysis) para todos los proyectos de .NET. En tiempo de compilación, las infracciones al estilo de código de .NET aparecerán como advertencias o errores con un prefijo "IDE". Esto le permite aplicar estrictamente estilos de código coherentes en el código base.

::: moniker-end

## <a name="apply-code-styles"></a>Aplicación de estilos de código

::: moniker range="vs-2017"

Puede configurar el comando **Dar formato al documento** (**Editar** > **Avanzado** > **Dar formato al documento**) para aplicar su configuración de estilo de código (desde las opciones de un archivo EditorConfig o **Estilo de código**) junto con el formato regular que aplica (como una sangría). Si existe un archivo *.editorconfig* para el proyecto, dicha configuración puede tener prioridad.

> [!NOTE]
> La opción de aplicar estilos de código usando el comando **Dar formato al documento** solo está disponible para los archivos de código de C#. Se trata de una característica experimental.

Establezca qué configuración quiere que **Dar formato al documento** aplique en la [página de opciones Formato](reference/options-text-editor-csharp-formatting.md#format-document-settings).

![Configuración de estilo de código para dar formato a un documento de Visual Studio 2017](media/format-document-settings-experiment.png)

> [!TIP]
> Las reglas configuradas con una gravedad de **Ninguna** no participan en la limpieza de código, pero se pueden aplicar de manera individual a través del menú **Acciones rápidas y refactorizaciones**.

La primera vez que desencadena el comando **Dar formato al documento**, una barra amarilla de información le pide que configure las opciones de limpieza de código.

::: moniker-end

::: moniker range=">=vs-2019"

Para los archivos de código de C#, Visual Studio 2019 tiene el botón **Limpieza de código** en la parte inferior del editor (teclado: **Ctrl**+**K**, **Ctrl**+**E**) para aplicar estilos de código desde un archivo EditorConfig o desde la página de opciones **Estilo de código**. Si existe un archivo *.editorconfig* para el proyecto, dicha configuración es la que tiene prioridad.

![Ejecución del comando Limpieza de código en Visual Studio 2019](media/execute-code-cleanup.png)

> [!TIP]
> Las reglas configuradas con una gravedad de **Ninguna** no participan en la limpieza de código, pero se pueden aplicar de manera individual a través del menú **Acciones rápidas y refactorizaciones**.

En primer lugar, configure qué estilos de código quiere aplicar (en uno de los dos perfiles) en el cuadro de diálogo **Configurar limpieza de código**. Para abrir este cuadro de diálogo, haga clic en la flecha de expansión situada junto al icono de escoba para la limpieza de código y, después, elija **Configurar limpieza de código**.

![Configurar limpieza de código en Visual Studio 2019](media/configure-code-cleanup.png)

Cuando haya configurado la limpieza de código, puede hacer clic en el icono de escoba o presionar **Ctrl**+**K**, **Ctrl**+**E** para ejecutar la limpieza de código. También puede ejecutar la limpieza de código en todo el proyecto o la solución. Haga clic con el botón derecho en el nombre del proyecto o la solución en el **Explorador de soluciones**, seleccione **Análisis y limpieza de código** y, luego, seleccione **Ejecutar limpieza de código**.

![Ejecución de la limpieza de código en todo el proyecto o la solución](media/run-code-cleanup-project-solution.png)

Si quiere que la configuración de estilo de código se aplique cada vez que guarde un archivo, es posible que le resulte útil la extensión [Limpieza de código al guardar](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.CodeCleanupOnSave).

::: moniker-end

## <a name="see-also"></a>Vea también

- [Acciones rápidas](../ide/quick-actions.md)
- [Configuración de la convención de codificación de .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
- [Comportamiento del editor (Visual Studio para Mac)](/visualstudio/mac/editor-behavior)
