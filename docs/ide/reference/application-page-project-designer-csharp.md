---
title: Página Aplicación de propiedades de proyecto de C#
ms.date: 10/30/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesApplicationWPF
- cs.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4a501ec056a3d8754d8f855a1584035e087f34b0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55034004"
---
# <a name="application-page-project-designer-c"></a>Página de aplicación, Diseñador de proyectos (C#)

Use la página **Aplicación** del **Diseñador de proyectos** para especificar la configuración de la aplicación y las propiedades del proyecto.

En la página **Aplicación**, seleccione un nodo de proyecto (no el nodo **Solución**) en el **Explorador de soluciones**. Después, seleccione **Proyecto** > **Propiedades** en la barra de menús. Cuando aparezca el **Diseñador de proyectos**, haga clic en la pestaña **Aplicación**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Configuración de aplicación general

Las opciones siguientes le permiten configurar opciones generales para la aplicación.

**Nombre del ensamblado**

Especifica el nombre del archivo de salida que contendrá el manifiesto del ensamblado. Si cambia esta propiedad, también modifica la propiedad **Nombre de salida**.

También puede hacer este cambio desde la línea de comandos usando [/out (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option).

Para obtener acceso a esta propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

**Espacio de nombres predeterminado**

Especifica el espacio de nombres base para los archivos agregados al proyecto.

Vea [espacio de nombres](/dotnet/csharp/language-reference/keywords/namespace) para obtener más información sobre cómo crear espacios de nombres en el código.

Para obtener acceso a esta propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

**Marco de destino**

Especifica la versión de .NET Framework a la que se destina la aplicación. Esta opción puede tener valores diferentes dependiendo de qué versiones de .NET Framework están instaladas en el equipo.

El valor predeterminado es el del marco de destino que ha seleccionado en el cuadro de diálogo **Nuevo proyecto**.

> [!NOTE]
> Los paquetes de requisitos previos incluidos en el [cuadro de diálogo Requisitos previos](../../ide/reference/prerequisites-dialog-box.md) se establecen automáticamente la primera vez que abre el cuadro de diálogo. Si posteriormente cambia la plataforma de destino del proyecto, debe seleccionar manualmente los requisitos previos para que coincidan con la nueva plataforma de destino.

Para obtener más información, vea [Cómo: Usar como destino una versión de .NET Framework](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) e [Información general sobre la compatibilidad con múltiples versiones (multi-targeting) en Visual Studio](../../ide/visual-studio-multi-targeting-overview.md).

**Tipo de salida**

Especifica el tipo de aplicación que se va a compilar. Los valores difieren según el tipo de proyecto. Por ejemplo, en un proyecto **Aplicación de consola**, puede especificar **Aplicación Windows**, **Aplicación de consola** o **Biblioteca de clases** como tipo de salida.

Para un proyecto de aplicación web, debe especificar **Biblioteca de clases**.

Para obtener más información sobre la propiedad **Tipo de salida**, vea [-target (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option).

Para obtener información sobre cómo tener acceso a esta propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.OutputType%2A>.

**Generar automáticamente redireccionamientos de enlace**

Los redireccionamientos de enlace se agregan al proyecto si la aplicación o sus componentes hacen referencia a más de una versión del mismo ensamblado. Si quiere definir manualmente los redireccionamientos de enlace en el archivo de proyecto, desactive **Generar automáticamente redireccionamientos de enlace**. Esta casilla se incorporó en Visual Studio 2017, versión 15.7.

Para obtener más información sobre los redireccionamientos, vea [Redirecting assembly versions](/dotnet/framework/configure-apps/redirect-assembly-versions) (Redireccionamiento de versiones de ensamblado).

**Objeto de inicio**

Define el punto de entrada que se llamará cuando se cargue la aplicación. Normalmente, esto se establece en el formulario principal de la aplicación o en el procedimiento `Main` que debe ejecutarse cuando se inicia la aplicación. Dado que las bibliotecas de clases no tienen un punto de entrada, su única opción para esta propiedad es **(Sin establecer)**.

De forma predeterminada, en un proyecto de aplicación de WPF, esta opción está establecida en **(Sin establecer)**. La otra opción es \[projectname].App. En un proyecto de WPF, debe establecer el URI de inicio para cargar un recurso de UI cuando se inicia la aplicación. Para ello, abra el archivo *Application.xaml* del proyecto y establezca la propiedad `StartupUri` en un archivo *.xaml* del proyecto, como *Window1.xaml*. Para obtener una lista de elementos raíz aceptables, vea <xref:System.Windows.Application.StartupUri%2A>. También tiene que definir un método `public static void Main()` en una clase del proyecto. Esta clase aparecerá en la lista **Objeto de inicio** como *ProjectName.ClassName*. Después, puede seleccionar la clase como el objeto de inicio.

Para obtener más información, vea [/main (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). Para obtener acceso a esta propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

**Información de ensamblado**

Este botón abre el cuadro de diálogo [Información de ensamblado](../../ide/reference/assembly-information-dialog-box.md).

## <a name="resources"></a>Recursos

Las opciones **Recursos** ayudan a configurar los valores de recursos de la aplicación.

**Icono y manifiesto**

De manera predeterminada, este botón de radio está seleccionado y las opciones **Icono** y **Manifiesto** están habilitadas. Esto le permite seleccionar su propio icono o seleccionar opciones de generación de manifiestos diferentes. Deje este botón de radio seleccionado a menos que vaya a proporcionar un archivo de recursos para el proyecto.

**Iconos**

Establece el archivo *.ico* que quiere usar como icono del programa. Haga clic en **Examinar** para buscar un gráfico existente o escriba el nombre del archivo que quiere. Para obtener más información, vea [/win32icon (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option).

Para obtener acceso a esta propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

**Manifest**

Selecciona una opción de generación de manifiesto cuando la aplicación se ejecuta en Windows Vista en el Control de cuentas de usuario (UAC). Esta opción puede tener los valores siguientes:

- **Incrustar manifiesto con la configuración predeterminada**. Admite la manera típica en la que funciona Visual Studio en Windows Vista, que consiste en insertar información de seguridad en el archivo ejecutable de la aplicación al especificar que `requestedExecutionLevel` sea `AsInvoker`. Ésta es la opción predeterminada.

- **Crear aplicación sin un manifiesto**. Este método se conoce como *virtualización*. Use esta opción para obtener compatibilidad con aplicaciones anteriores.

- **Properties\app.manifest**. Esta opción es necesaria para las aplicaciones implementadas mediante ClickOnce o COM sin registro. Si publica una aplicación mediante la implementación de ClickOnce, **Manifiesto** se establece automáticamente en esta opción.

**Archivo de recursos**

Seleccione este botón de radio si va a proporcionar un archivo de recursos para el proyecto. Al seleccionar esta opción se deshabilitan las opciones **Icono** y **Manifiesto**.

Escriba un nombre de ruta o use el botón Examinar (**...**) para agregar un archivo de recursos de Win32 al proyecto.