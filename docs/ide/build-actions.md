---
title: Acciones de compilación para archivos
description: Sepa que todos los archivos de un proyecto de Visual Studio tienen una acción de compilación y que esta controla lo que ocurre en el archivo cuando se compila el proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/19/2018
ms.technology: vs-ide-compile
ms.topic: reference
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 86df6673608359dcc7158762c3ef9d86c184fff6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850486"
---
# <a name="build-actions"></a>Acciones de compilación

Todos los archivos de un proyecto de Visual Studio tienen una acción de compilación. La acción de compilación controla lo que le sucede al archivo cuando se compila el proyecto.

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Acciones de compilación](/visualstudio/mac/build-actions).

## <a name="set-a-build-action"></a>Establecer una acción de compilación

Para establecer la acción de compilación para un archivo, abra las propiedades del archivo en la ventana **Propiedades** seleccionando el archivo en el **Explorador de soluciones** y presionando **Alt**+**ENTRAR**. O bien, haga clic con el botón derecho en el archivo en el **Explorador de soluciones** y elija **Propiedades**. En la ventana **Propiedades**, en la sección **Avanzadas**, use la lista desplegable situada junto a **Acción de compilación** para establecer una acción de compilación para el archivo.

![Acciones de compilación para un archivo en Visual Studio](media/build-actions.png)

## <a name="build-action-values"></a>Valores de acción de compilación

Algunas de las acciones de compilación más comunes para los archivos de proyecto de C# y de Visual Basic son:

|Acción de compilación | Tipos de proyecto | Descripción |
|-|-|
| **AdditionalFiles** | C#, Visual Basic | Un archivo de texto que no es parte del código fuente que se pasa al compilador de C# o de Visual Basic como entrada. Esta acción de compilación se usa principalmente para proporcionar entradas a [analizadores](../code-quality/roslyn-analyzers-overview.md) a los que hace referencia un proyecto para comprobar la calidad del código. Para obtener más información, vea [Use additional files](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md) (Usar archivos adicionales).|
| **ApplicationDefinition** | WPF | El archivo que define la aplicación. La primera vez que crea un proyecto, es *App.xaml*. |
| **CodeAnalysisDictionary** | .NET | Un diccionario personalizado que Análisis de código usa para la revisión ortográfica. Vea [Cómo: Personalizar el diccionario de Análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)|
| **Compile** | cualquiera | El archivo se pasa al compilador como un archivo de código fuente.|
| **Contenido** | .NET | Un archivo marcado como **Contenido** se puede recuperar como un flujo mediante una llamada a <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType>. En proyectos de ASP.NET, estos archivos se incluyen como parte del sitio cuando se implementa.|
| **DesignData** | WPF | Se usa para los archivos ViewModel XAML, para permitir que los controles de usuario se vean en tiempo de diseño, con datos de ejemplo y tipos ficticios. |
| **DesignDataWithDesignTimeCreateable** | WPF | Como **DesignData**, pero con tipos reales.  |
| **Embedded Resource** | .NET | El archivo se pasa al compilador de C# como un recurso que se va a insertar en el ensamblado. Puede llamar a <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> para leer el archivo del ensamblado.|
| **EntityDeploy** | .NET | Para los archivos .edmx de Entity Framework que especifican la implementación de artefactos de EF. |
| **Fakes** | .NET | Se usan para la plataforma de pruebas de Microsoft Fakes. Consulte [Aislar el código sometido a prueba con Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md). |
| **None** | cualquiera | El archivo no forma parte de la compilación de ninguna manera. Este valor puede usarse para archivos de documentación como "Léame", por ejemplo.|
| **Page** | WPF | Compile un archivo XAML en un archivo .baml binario para agilizar la carga en tiempo de ejecución. |
| **Recurso** | WPF | Especifica que el archivo se va a insertar en un archivo de recursos de manifiesto del ensamblado con la extensión *.g.resources*. |
| **Shadow** | .NET | Se usa para un archivo .accessor que contiene una lista de nombres de archivos de ensamblado, uno por línea. Para cada ensamblado de la lista, genere clases públicas con los nombres `ClassName_Accessor` que sean iguales a las originales, pero con métodos públicos en lugar de privados. Se usa para las pruebas unitarias. |
| **Pantalla de presentación** | WPF | Especifica un archivo de imagen que se mostrará en tiempo de ejecución cuando se inicia la aplicación. |
| **XamlAppDef** | Windows Workflow Foundation | Indica a la compilación que compile un archivo XAML de flujo de trabajo en un ensamblado con un flujo de trabajo insertado. |

> [!NOTE]
> Tipos de proyecto específicos pueden definir otras acciones de compilación, por lo que la lista de acciones de compilación depende del tipo de proyecto y es posible que aparezcan valores que no están en esta lista.

## <a name="see-also"></a>Consulte también

- [Opciones del compilador de C#, por orden alfabético](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Opciones del compilador de Visual Basic alfabético](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [Acciones de compilación](/visualstudio/mac/build-actions)
