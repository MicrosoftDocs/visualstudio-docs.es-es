---
title: Página de aplicación, Diseñador de proyectos (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesApplicationWPF
- cs.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
ms.assetid: f13701a8-4e2e-4474-9d60-bb43decbe0c1
caps.latest.revision: 61
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dcd9b9d5e336bfa0595ddd6d70032f7ba7fe780a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299398"
---
# <a name="application-page-project-designer-c"></a>Página de aplicación, Diseñador de proyectos (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use la página **Aplicación** del **Diseñador de proyectos** para especificar la configuración de la aplicación y las propiedades del proyecto.

 En la página **Aplicación**, seleccione un nodo de proyecto (no el nodo **Solución**) en el **Explorador de soluciones**. Después, pulse **Proyecto**, **Propiedades** en la barra de menús. Cuando aparezca el Diseñador de proyectos, haga clic en la pestaña **Aplicación**.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="general-application-settings"></a>Configuración de aplicación general
 Las opciones siguientes le permiten configurar opciones generales para la aplicación.

 **Nombre del ensamblado** Especifica el nombre del archivo de salida que contendrá el manifiesto del ensamblado. Si cambia esta propiedad también cambiará la propiedad **Nombre de archivo de salida**. También puede hacer este cambio desde la línea de comandos usando [/out (opciones del compilador de C#)](https://msdn.microsoft.com/library/70d91d01-7bd2-4aea-ba8b-4e9807e9caa5). Para obtener acceso a esta propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

 **Espacio de nombres predeterminado** Especifica el espacio de nombres base para los archivos agregados al proyecto.

 Vea [espacio de nombres](https://msdn.microsoft.com/library/0a788423-9110-42e0-97d9-bda41ca4870f) para obtener más información sobre cómo crear espacios de nombres en el código.

 Para obtener acceso a esta propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

 **Plataforma de destino** Especifica la versión de .NET Framework a la que se destina la aplicación. Esta opción puede tener valores diferentes dependiendo de qué versiones de .NET Framework están instaladas en el equipo.

 El valor predeterminado es el del marco de destino que ha seleccionado en el cuadro de diálogo **Nuevo proyecto**.

> [!NOTE]
> Los paquetes de requisitos previos incluidos en el [cuadro de diálogo Requisitos previos](../../ide/reference/prerequisites-dialog-box.md) se establecen automáticamente la primera vez que abre el cuadro de diálogo. Si posteriormente cambia la plataforma de destino del proyecto, deberá seleccionar manualmente los requisitos previos para que coincidan con la nueva plataforma de destino.

 Para obtener más información, vea [Cómo: Usar como destino una versión de .NET Framework](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) e [Información general sobre la compatibilidad con múltiples versiones (multi-targeting) en Visual Studio](../../ide/visual-studio-multi-targeting-overview.md).

 **Tipo de aplicación** Especifica el tipo de aplicación que se va a compilar. Para aplicaciones de [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)], puede especificar **Aplicación de la Tienda Windows**, **Biblioteca de clases** o **Archivo WinMD**. Para la mayoría de tipos de aplicación, puede especificar **Aplicación Windows**, **Aplicación de consola**, **Biblioteca de clases**, **Servicio de Windows** o **Biblioteca de controles web**.

 Para un proyecto de aplicación web, debe especificar **Biblioteca de clases**.

 Si especifica la opción **Archivo WinMD**, los tipos se pueden proyectar en cualquier lenguaje de programación de Windows Runtime. Al empaquetar la salida del proyecto como un archivo WinMD, puede codificar una aplicación en varios lenguajes y que el código interopere como si lo escribiera todo en el mismo lenguaje. Puede especificar esta opción para las soluciones destinadas a las bibliotecas de Windows Runtime, incluidas las aplicaciones de [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]. Para obtener más información, vea [Crear componentes de Windows Runtime en C# y Visual Basic](https://go.microsoft.com/fwlink/?LinkId=231895).

> [!NOTE]
> Windows Runtime puede proyectar tipos, de manera que aparezcan como objetos nativos en cualquier lenguaje que los use. Por ejemplo, las aplicaciones de JavaScript que interactúan con Windows Runtime lo usan como un conjunto de objetos JavaScript y las aplicaciones de C# usan la biblioteca como una colección de objetos. NET. Al empaquetar la salida del proyecto como un archivo WinMD, puede aprovechar la misma tecnología que usa Windows Runtime.

 Para obtener más información sobre la propiedad **Tipo de aplicación**, vea [/target (Opciones del compilador de C#)](https://msdn.microsoft.com/library/a18bbd8e-bbf7-49e7-992c-717d0eb1f76f). Para obtener información sobre cómo tener acceso a esta propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.OutputType%2A>.

 **Información de ensamblado** Al hacer clic en este botón se muestra el [cuadro de diálogo Información de ensamblado](../../ide/reference/assembly-information-dialog-box.md).

 **Objeto de inicio** Define el punto de entrada al que se va a llamar cuando se cargue la aplicación. Normalmente, esto se establece en el formulario principal de la aplicación o en el procedimiento `Main` que debe ejecutarse cuando se inicia la aplicación. Dado que las bibliotecas de clases no tiene un punto de entrada, la única opción para esta propiedad es **(Sin establecer)** .

 De manera predeterminada, en un proyecto de Aplicación de explorador WPF, esta opción es **(Sin establecer)** . La otra opción es *Projectname*.App. En este tipo de proyecto, debe establecer el URI de inicio para cargar un recurso de la interfaz de usuario cuando se inicia la aplicación. Para ello, abra el archivo Application.xaml en el proyecto y establezca la propiedad `StartupUri` en un archivo .xaml del proyecto, por ejemplo, Window1.xaml. Para obtener una lista de elementos raíz aceptables, vea <xref:System.Windows.Application.StartupUri%2A>. También tiene que definir un método `public static void Main()` en una clase del proyecto. Esta clase aparecerá en la lista **Objeto de inicio** como *ProjectName.ClassName*. Después, puede seleccionar la clase como el objeto de inicio.

 Para obtener más información, vea [/main (Opciones del compilador de C#)](https://msdn.microsoft.com/library/975cf4d5-36ac-4530-826c-4aad0c7f2049). Para obtener acceso a esta propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

## <a name="resources"></a>Recursos
 Las opciones siguientes le permiten configurar opciones generales para la aplicación.

 **Icono y manifiesto** De manera predeterminada, este botón de radio está seleccionado y las opciones **Icono** y **Manifiesto** están habilitadas. Esto le permite seleccionar su propio icono o seleccionar opciones de generación de manifiestos diferentes. Deje este botón de radio seleccionado a menos que proporcione un archivo de recursos para el proyecto.

 **Icono** Establece el archivo .ico que se quiere usar como el icono del programa. Haga clic en el botón de puntos suspensivos para buscar un gráfico existente o escriba el nombre del archivo que quiera. Para obtener más información, vea [/win32icon (Opciones del compilador de C#)](https://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138). Para obtener acceso a esta propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

 **Manifiesto** Selecciona una opción de generación de manifiesto cuando la aplicación se ejecuta en Windows Vista en el Control de cuentas de usuario (UAC). Esta opción puede tener los valores siguientes:

- **Incrustar manifiesto con la configuración predeterminada**. Admite la manera típica en la que funciona Visual Studio en Windows Vista, que consiste en insertar información de seguridad en el archivo ejecutable de la aplicación al especificar que `requestedExecutionLevel` sea `AsInvoker`. Ésta es la opción predeterminada.

- **Crear aplicación sin un manifiesto**. Este método se conoce como *virtualización*. Use esta opción para obtener compatibilidad con aplicaciones anteriores.

- **Properties\app.manifest**. Esta opción es necesaria para las aplicaciones implementadas mediante ClickOnce o COM sin registro. Si publica una aplicación mediante la implementación de ClickOnce, **Manifiesto** se establece automáticamente en esta opción.

  **Archivo de recursos** Seleccione este botón de opción si va a proporcionar un archivo de recursos para el proyecto. Al seleccionar esta opción se deshabilitan las opciones **Icono** y **Manifiesto**.

  Escriba un nombre de ruta o use el botón Examinar ( **...** ) para agregar un archivo de recursos de Win32 al proyecto.

## <a name="see-also"></a>Otras referencias
[Administrar las propiedades de la aplicación](../../ide/application-properties.md) [Escribir código en soluciones de Office](https://msdn.microsoft.com/library/2d4d8fd0-e881-4829-976f-0d1a9221dec0)
