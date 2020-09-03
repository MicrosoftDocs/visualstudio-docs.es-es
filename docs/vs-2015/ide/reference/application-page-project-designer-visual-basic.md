---
title: Página Aplicación, Diseñador de proyectos (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
ms.assetid: 8cec9fea-cd92-47ff-88dd-7c928f0b4a74
caps.latest.revision: 68
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 893647303b493ea633caf076658edbdcf0664ccc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850839"
---
# <a name="application-page-project-designer-visual-basic"></a>Application Page, Project Designer (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use la página **Aplicación** del Diseñador de proyectos para especificar la configuración de la aplicación y las propiedades de un proyecto.

 Para obtener acceso a la página **Aplicación**, seleccione un nodo de proyecto (no el nodo **Solución**) en el **Explorador de soluciones**. Después, pulse **Proyecto**, **Propiedades** en la barra de menús. Cuando aparezca el Diseñador de proyectos, haga clic en la pestaña **Aplicación**.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="general-application-settings"></a>Configuración de aplicación general
 Las opciones siguientes le permiten configurar opciones generales para una aplicación.

 **Nombre del ensamblado** Especifica el nombre del archivo de salida que contendrá el manifiesto del ensamblado. Si cambia esta propiedad, también cambiará la propiedad **Nombre de archivo de salida**. También puede realizar este cambio en un símbolo del sistema usando [/out (Visual Basic)](https://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae). Para obtener información sobre cómo tener acceso a esta propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

 **Espacio de nombres raíz** Especifica el espacio de nombres base para todos los archivos del proyecto. Por ejemplo, si establece el **espacio de nombres raíz** en `Project1` y tiene un `Class1` fuera de cualquier espacio de nombres en el código, su espacio de nombres será `Project1.Class1`. Si tiene un `Class2` en un espacio de nombres `Order` en el código, su espacio de nombres será `Project1.Order.Class2`.

 Si desactiva el **espacio de nombres raíz**, puede especificar la estructura del espacio de nombres del proyecto en el código.

> [!NOTE]
> Si usa la palabra clave Global en una [Instrucción de espacio de nombres](https://msdn.microsoft.com/library/a31fbd95-9ace-4c3d-bbb1-51222a2272b2), puede definir un espacio de nombres fuera del espacio de nombres raíz del proyecto. Si borra el **espacio de nombres raíz**, `Global` se convierte en el espacio de nombres de nivel superior, lo que elimina la necesidad de la `Global` palabra clave en una `Namespace` instrucción. Para obtener más información, vea "Palabra clave Global en las instrucciones de espacio de nombres" en [Espacios de nombres en Visual Basic](https://msdn.microsoft.com/library/cffac744-ab8c-4f1f-ba50-732c22ab4b88).

 Para obtener información sobre cómo crear espacios de nombres en su código, vea [Namespace (Instrucción)](https://msdn.microsoft.com/library/a31fbd95-9ace-4c3d-bbb1-51222a2272b2).

 Para obtener más información sobre la propiedad de espacio de nombres raíz, vea [/rootnamespace](https://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783).

 Para obtener información sobre cómo tener acceso a esta propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

 Versión de **.NET Framework de destino (todas las configuraciones)** Especifica la versión de la .NET Framework a la que se destina la aplicación. Esta opción puede tener valores diferentes dependiendo de qué versiones de .NET Framework están instaladas en el equipo.

 El valor predeterminado coincide con la plataforma de destino que ha especificado en el cuadro de diálogo **Nuevo proyecto**.

> [!NOTE]
> Los paquetes de requisitos previos que se muestran en el [cuadro de diálogo Requisitos previos](../../ide/reference/prerequisites-dialog-box.md) se establecen automáticamente la primera vez que abre el cuadro de diálogo. Si posteriormente cambia la plataforma de destino del proyecto, debe especificar manualmente los requisitos previos para que coincidan con la nueva plataforma de destino.

 Para obtener más información, vea [Cómo: Usar como destino una versión de .NET Framework](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) e [Información general sobre la compatibilidad con múltiples versiones (multi-targeting) en Visual Studio](../../ide/visual-studio-multi-targeting-overview.md).

 **Tipo de aplicación** Especifica el tipo de aplicación que se va a compilar. Para aplicaciones de [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)], puede especificar **Aplicación de la Tienda Windows**, **Biblioteca de clases** o **Archivo WinMD**. Para la mayoría de tipos de aplicación, puede especificar **Aplicación Windows**, **Aplicación de consola**, **Biblioteca de clases**, **Servicio de Windows** o **Biblioteca de controles web**.

 Para un proyecto de aplicación web, debe especificar **Biblioteca de clases**.

 Si especifica la opción **Archivo WinMD**, los tipos se pueden proyectar en cualquier lenguaje de programación de Windows Runtime. Al empaquetar la salida del proyecto como un archivo WinMD, puede codificar una aplicación en varios lenguajes y que el código interopere como si lo escribiera todo en el mismo lenguaje. Puede usar la opción **Archivo WinMD** para las soluciones destinadas a las bibliotecas de Windows Runtime, incluidas las aplicaciones de [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]. Para obtener más información, vea [Crear componentes de Windows Runtime en C# y Visual Basic](https://msdn.microsoft.com/library/windows/apps/br230301(v=VS.85).aspx).

> [!NOTE]
> Windows Runtime puede proyectar tipos, de manera que aparezcan como objetos nativos en cualquier lenguaje que los use. Por ejemplo, las aplicaciones de JavaScript que interactúan con Windows Runtime lo usan como un conjunto de objetos JavaScript y las aplicaciones de C# usan la biblioteca como una colección de objetos. NET. Al empaquetar la salida del proyecto como un archivo WinMD, puede aprovechar la misma tecnología que usa Windows Runtime.

 Para obtener más información sobre la propiedad **Tipo de aplicación**, vea [/target (Visual Basic)](https://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c). Para obtener información sobre cómo tener acceso a esa propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.OutputType%2A>.

 **Icono** Establece el archivo .ico que se quiere usar como el icono del programa. Seleccione esta **\<Browse...>** información para buscar un gráfico existente. Para obtener más información, vea [/win32icon](https://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) (o [/win32icon (Opciones del compilador de C#)](https://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138). Para obtener acceso a esta propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

 **Formulario de inicio/objeto de inicio/URI de inicio** Especifica el punto de entrada o el formulario de inicio de la aplicación.

 Si **Habilitar marco de trabajo de la aplicación** está seleccionado (valor predeterminado), esta lista se titula **Formulario de inicio** y muestra solo formularios, ya que el marco de trabajo de la aplicación admite solo formularios de inicio, no objetos.

 Si el proyecto es una Aplicación de explorador WPF, esta lista se titula **URI de inicio** y el valor predeterminado es **Page1.xaml**. La lista **URI de inicio** le permite especificar el recurso de interfaz de usuario (un elemento XAML) que la aplicación muestra al iniciarse. Para obtener más información, vea <xref:System.Windows.Application.StartupUri%2A>.

 Si **Habilitar marco de trabajo de la aplicación** está desactivado, esta lista se convierte en **Objeto de inicio** y muestra los formularios y las clases o módulos con un `Sub Main`.

 **Objeto de inicio** define el punto de entrada al que se va a llamar cuando se cargue la aplicación. Normalmente, esto se establece en el formulario principal de la aplicación o en el procedimiento `Sub Main` que debe ejecutarse cuando se inicia la aplicación. Dado que las bibliotecas de clases no tienen un punto de entrada, la única opción para esta propiedad es **(None)**. Para obtener más información, vea [/main](https://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0). Para obtener acceso a esta propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

 **Información de ensamblado** Haga clic en este botón para mostrar el [cuadro de diálogo información de ensamblado](../../ide/reference/assembly-information-dialog-box.md).

 **Habilitar marco de trabajo** de la aplicación Especifica si un proyecto usará el marco de trabajo de la aplicación. La configuración de esta opción afecta a las opciones disponibles en el objeto de inicio del formulario de **Inicio** / **Startup object**.

 Si esta casilla está seleccionada, la aplicación usará el `Sub Main` estándar. Al seleccionar esta casilla se habilitan las características de la sección **Propiedades del marco de trabajo de la aplicación Windows**, y también es necesario seleccionar un formulario de inicio.

 Si esta casilla está desactivada, la aplicación usa el `Sub Main` personalizado que ha especificado en el **Formulario de inicio**. En este caso, puede especificar un objeto de inicio (un `Sub Main` personalizado en un método o una clase) o un formulario. Además, las opciones de la sección **Propiedades del marco de trabajo de la aplicación Windows** dejarán de estar disponibles.

 **Ver configuración de Windows** Haga clic en este botón para generar y abrir el archivo app. manifest. Visual Studio usa este archivo para generar datos de manifiesto para la aplicación. Después, para establecer el nivel de ejecución solicitado de UAC, modifique la etiqueta `<requestedExecutionLevel>` en app.manifest de la manera siguiente:

 `<requestedExecutionLevel level="asInvoker" />`

 ClickOnce funciona con un nivel de `asInvoker` o en modo virtualizado (sin generación de manifiesto). Para especificar el modo virtualizado, quite la etiqueta completa de app.manifest.

 Para obtener más información sobre la generación de manifiesto, vea [Implementación de ClickOnce en Windows Vista](../../deployment/clickonce-deployment-on-windows-vista.md).

## <a name="windows-application-framework-properties"></a>Propiedades del marco de trabajo de la aplicación Windows
 Las siguientes opciones de configuración están disponibles en la sección **Propiedades del marco de trabajo de la aplicación Windows**. Estas opciones están disponibles solo si la casilla **Habilitar marco de trabajo de la aplicación** está seleccionada. En la sección siguiente se describe la configuración de las **Propiedades del marco de trabajo de la aplicación Windows** para aplicaciones de Windows Presentation Foundation (WPF).

 **Habilitar estilos visuales de XP** Habilita o deshabilita los estilos visuales de Windows XP, también conocidos como *temas de Windows XP*. Los estilos visuales de Windows XP presentan, por ejemplo, controles con esquinas redondeadas y colores dinámicos. El valor predeterminado es habilitado. Para obtener más información sobre los estilos visuales de Windows XP, vea [Características de Windows XP y controles de Windows Forms](https://msdn.microsoft.com/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0).

 **Crear aplicación de instancia única** Active esta casilla para impedir que los usuarios ejecuten varias instancias de la aplicación. La configuración predeterminada de esta casilla está desactivada. Esta configuración permite que se ejecuten varias instancias de la aplicación.

 **Guardar My. Settings al apagar** Active esta casilla para especificar que la configuración de la aplicación `My.Settings` se guarde cuando los usuarios cierren sus equipos. La configuración predeterminada está habilitada. Si esta opción está deshabilitada, puede guardar la configuración de la aplicación manualmente llamando a `My.Settings.Save`.

 **Modo de autenticación** Seleccione **Windows** (valor predeterminado) para especificar el uso de la autenticación de Windows para identificar el usuario que ha iniciado sesión actualmente. Puede recuperar esta información en tiempo de ejecución con el objeto `My.User`. Seleccione **Definido por la aplicación** si proporcionará su propio código para autenticar usuarios en lugar de usar los métodos de autenticación de Windows predeterminados.

 **Modo de apagado** Seleccione **al cerrar el formulario de inicio** (valor predeterminado) para especificar que la aplicación se cierre cuando se cierre el formulario establecido como formulario de inicio, aunque haya otros formularios abiertos. Seleccione **Al cerrar el último formulario** para especificar que se salga de la aplicación cuando el último formulario se cierre o cuando se llame a `My.Application.Exit` o a la instrucción `End` explícitamente.

 Seleccione **Al apagar explícitamente** para especificar que se salga de la aplicación cuando llame a `Shutdown` explícitamente.

 Seleccione **Al cerrar la última ventana** para especificar que se salga de la aplicación cuando la última ventana se cierre o cuando llame a `Shutdown` explícitamente. Esta es la configuración predeterminada.

 Seleccione **Al cerrar la ventana principal** para especificar que se salga de la aplicación cuando la ventana principal se cierre o cuando llame a `Shutdown` explícitamente.

 **Pantalla de presentación** Seleccione el formulario que desea usar como pantalla de presentación. Debe haber creado anteriormente una pantalla de presentación con un formulario o una plantilla. El valor predeterminado es **(ninguno)**.

 **Ver eventos de aplicación** Haga clic en este botón para mostrar un archivo de código de eventos en el que puede escribir eventos para los eventos de marco de aplicación `Startup` , `Shutdown` , `UnhandledException` `StartupNextInstance` y `NetworkAvailabilityChanged` . También puede invalidar determinados métodos de marco de trabajo de la aplicación. Por ejemplo, puede invalidar `OnInitialize` para cambiar el comportamiento de la pantalla de presentación.

### <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-applications"></a>Propiedades del marco de trabajo de la aplicación Windows para aplicaciones de Windows Presentation Foundation (WPF)
 Las siguientes opciones de configuración están disponibles en la sección **Propiedades del marco de trabajo de la aplicación Windows** cuando el proyecto es una aplicación de Windows Presentation Foundation. Estas opciones están disponibles solo si la casilla **Habilitar marco de trabajo de la aplicación** está seleccionada. Las opciones enumeradas en esta tabla están disponibles solo para aplicaciones WPF o aplicaciones de explorador WPF. No están disponibles para bibliotecas de control personalizado o de controles de usuario de WPF.

 **Modo de apagado** Esta propiedad solo es aplicable a las aplicaciones Windows Presentation Foundation.

 Seleccione **Al apagar explícitamente** para especificar que se salga de la aplicación cuando llame a <xref:System.Windows.Application.Shutdown%2A> explícitamente.

 Seleccione **Al cerrar la última ventana** para especificar que se salga de la aplicación cuando la última ventana se cierre o cuando llame a <xref:System.Windows.Application.Shutdown%2A> explícitamente. Esta es la configuración predeterminada.

 Seleccione **Al cerrar la ventana principal** para especificar que se salga de la aplicación cuando la ventana principal se cierre o cuando llame a <xref:System.Windows.Application.Shutdown%2A> explícitamente.

 Para obtener más información sobre el uso de esta opción, vea <xref:System.Windows.Application.Shutdown%2A>.

 **Editar XAML** Haga clic en este botón para abrir y modificar el archivo de definición de la aplicación (Application. xaml) en el editor XAML. Cuando hace clic en este botón, Application.xaml se abre en el nodo de definición de aplicación. Puede que tenga que editar este archivo para realizar determinadas tareas, como la definición de recursos. Si el archivo de definición de aplicación no existe, el Diseñador de proyectos crea uno.

 **Ver eventos de aplicación** Haga clic en este botón para mostrar el `Application` archivo de clase parcial (Application. Xaml. VB) en un editor de código. Si el archivo no existe, el Diseñador de proyectos crea uno con el nombre de clase y el espacio de nombres adecuados.

 El objeto <xref:System.Windows.Application> genera eventos cuando se producen determinados cambios en el estado de la aplicación (por ejemplo, en el inicio de aplicación o en el apagado). Para obtener una lista completa de los eventos que expone esta clase, vea <xref:System.Windows.Application>. Estos eventos se controlan en la sección de código de usuario de la clase parcial `Application`.

## <a name="see-also"></a>Consulte también
[Administrar las propiedades de la aplicación](../../ide/application-properties.md) [Escribir código en soluciones de Office](https://msdn.microsoft.com/library/2d4d8fd0-e881-4829-976f-0d1a9221dec0)
