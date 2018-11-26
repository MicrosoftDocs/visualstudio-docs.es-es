---
title: Acciones de compilación para archivos
ms.date: 11/19/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5eb4c000973afd1eef92d283e5688862413add16
ms.sourcegitcommit: f61ad0e8babec8810295f039e67629f4bdebeef0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2018
ms.locfileid: "52002130"
---
# <a name="build-actions"></a>Acciones de compilación

Todos los archivos de un proyecto de Visual Studio tienen una acción de compilación. La acción de compilación controla lo que le sucede al archivo cuando se compila el proyecto.

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Acciones de compilación](/visualstudio/mac/build-actions).

## <a name="set-a-build-action"></a>Establecer una acción de compilación

Para establecer la acción de compilación para un archivo, abra las propiedades del archivo en la ventana **Propiedades** seleccionando el archivo en el **Explorador de soluciones** y presionando **Alt**+**ENTRAR**. O bien, haga clic con el botón derecho en el archivo en el **Explorador de soluciones** y elija **Propiedades**. En la ventana **Propiedades**, en la sección **Avanzadas**, use la lista desplegable situada junto a **Acción de compilación** para establecer una acción de compilación para el archivo.

![Acciones de compilación para un archivo en Visual Studio](media/build-actions.png)

## <a name="build-action-values"></a>Valores de acción de compilación

Algunas de las acciones de compilación para los archivos de proyecto de C# y de Visual Basic son:

* **None**: el archivo no forma parte de la compilación de ninguna manera. Este valor puede usarse para archivos de documentación como "Léame", por ejemplo.
* **Compile**: el archivo se pasa al compilador como un archivo de código fuente.
* **Content**: un archivo marcado como **Contenido** se puede recuperar como un flujo mediante una llamada a <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType>. En proyectos de ASP.NET, estos archivos se incluyen como parte del sitio cuando se implementa.
* **Embedded Resource**: el archivo se pasa al compilador de C# como un recurso que se va a insertar en el ensamblado. Puede llamar a <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> para leer el archivo del ensamblado.
* **AdditionalFiles**: un archivo de texto que no es parte del código fuente que se pasa al compilador de C# o de Visual Basic como entrada. Esta acción de compilación se usa principalmente para proporcionar entradas a [analizadores](../code-quality/roslyn-analyzers-overview.md) a los que hace referencia un proyecto para comprobar la calidad del código. Para obtener más información, vea [Use additional files](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md) (Usar archivos adicionales).

## <a name="see-also"></a>Vea también

- [Opciones del compilador de C#, por orden alfabético](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Opciones del compilador de Visual Basic alfabético](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [Acciones de compilación](/visualstudio/mac/build-actions)