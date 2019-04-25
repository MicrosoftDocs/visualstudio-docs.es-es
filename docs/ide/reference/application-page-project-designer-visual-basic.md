---
title: Página Aplicación de propiedades de proyecto de VB
ms.date: 10/30/2018
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84874328c2f7a20a79370ff210eb51d966ec4648
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62791661"
---
# <a name="application-page-project-designer-visual-basic"></a>Application Page, Project Designer (Visual Basic)

Use la página **Aplicación** del Diseñador de proyectos para especificar la configuración de la aplicación y las propiedades de un proyecto.

En la página **Aplicación**, seleccione un nodo de proyecto (no el nodo **Solución**) en el **Explorador de soluciones**. Después, seleccione **Proyecto** > **Propiedades** en la barra de menús. Cuando aparezca el **Diseñador de proyectos**, seleccione la pestaña **Aplicación**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Configuración de aplicación general

Las opciones siguientes le permiten configurar opciones generales para una aplicación.

### <a name="assembly-name"></a>Nombre del ensamblado

Especifica el nombre del archivo de salida que contendrá el manifiesto del ensamblado. Si cambia esta propiedad, también cambia la propiedad **Nombre de archivo de salida**.

También puede especificar el nombre del archivo de salida desde un símbolo del sistema mediante el modificador de compilador [/out (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/out).

Para obtener información sobre cómo tener acceso a esta propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

### <a name="root-namespace"></a>Espacio de nombres raíz

Especifica el espacio de nombres base para todos los archivos del proyecto. Por ejemplo, si establece el **espacio de nombres raíz** en `Project1` y tiene un `Class1` fuera de cualquier espacio de nombres en el código, su espacio de nombres será `Project1.Class1`. Si tiene un `Class2` en un espacio de nombres `Order` en el código, su espacio de nombres será `Project1.Order.Class2`.

Si desactiva el **espacio de nombres raíz**, puede especificar la estructura del espacio de nombres del proyecto en el código.

> [!NOTE]
> Si usa la palabra clave `Global` en una [Instrucción de espacio de nombres](/dotnet/visual-basic/language-reference/statements/namespace-statement), puede definir un espacio de nombres fuera del espacio de nombres raíz del proyecto. Si desactiva el **espacio de nombres raíz**, `Global` se convierte en el espacio de nombres de nivel superior, lo que elimina la necesidad de la palabra clave `Global` en una instrucción `Namespace`. Para obtener más información, vea "Palabra clave Global en las instrucciones de espacio de nombres" en [Espacios de nombres en Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/namespaces).

Para obtener información sobre cómo crear espacios de nombres en su código, vea [Namespace (Instrucción)](/dotnet/visual-basic/language-reference/statements/namespace-statement).

Para obtener más información sobre la propiedad de espacio de nombres raíz, vea [/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace).

Para obtener información sobre cómo tener acceso a esta propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

### <a name="target-framework-all-configurations"></a>Plataforma de destino (todas las configuraciones)

Especifica la versión de .NET Framework a la que se destina la aplicación. Esta opción puede tener valores diferentes dependiendo de qué versiones de .NET Framework están instaladas en el equipo.

El valor predeterminado coincide con la plataforma de destino especificada al crear el proyecto.

> [!NOTE]
> Los paquetes de requisitos previos que se muestran en el [cuadro de diálogo Requisitos previos](../../ide/reference/prerequisites-dialog-box.md) se establecen automáticamente la primera vez que abre el cuadro de diálogo. Si posteriormente cambia la plataforma de destino del proyecto, debe especificar manualmente los requisitos previos para que coincidan con la nueva plataforma de destino.

Para obtener más información, vea [Cómo: Usar como destino una versión de .NET Framework](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) e [Información general sobre la compatibilidad con múltiples versiones (multi-targeting) en Visual Studio](../../ide/visual-studio-multi-targeting-overview.md).

### <a name="application-type"></a>Tipo de aplicación

Especifica el tipo de aplicación que se va a compilar. Los valores difieren según el tipo de proyecto. Por ejemplo, para un proyecto de **Aplicación de Windows Forms**, puede especificar **Aplicación de Windows Forms**, **Biblioteca de clases**, **Aplicación de consola**, **Servicio de Windows** o **Biblioteca de controles web**.

Para un proyecto de aplicación web, debe especificar **Biblioteca de clases**.

Para obtener más información sobre la propiedad **Tipo de aplicación**, vea [/target (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/target). Para obtener información sobre cómo tener acceso a esa propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.OutputType%2A>.

### <a name="auto-generate-binding-redirects"></a>Generar automáticamente redireccionamientos de enlace

Los redireccionamientos de enlace se agregan al proyecto si la aplicación o sus componentes hacen referencia a más de una versión del mismo ensamblado. Si quiere definir manualmente los redireccionamientos de enlace en el archivo de proyecto, desactive **Generar automáticamente redireccionamientos de enlace**.

Para obtener más información sobre los redireccionamientos, vea [Redirecting assembly versions](/dotnet/framework/configure-apps/redirect-assembly-versions) (Redireccionamiento de versiones de ensamblado).

### <a name="startup-form--startup-object--startup-uri"></a>Formulario de inicio / Objeto de inicio / URI de inicio

Especifica el punto de entrada o el formulario de inicio de la aplicación.

Si **Habilitar marco de trabajo de la aplicación** está seleccionado (valor predeterminado), esta lista se titula **Formulario de inicio** y muestra solo formularios, ya que el marco de trabajo de la aplicación admite solo formularios de inicio, no objetos.

Si el proyecto es una Aplicación de explorador WPF, esta lista se titula **URI de inicio** y el valor predeterminado es **Page1.xaml**. La lista **URI de inicio** le permite especificar el recurso de interfaz de usuario (un elemento XAML) que la aplicación muestra al iniciarse. Para obtener más información, vea <xref:System.Windows.Application.StartupUri%2A>.

Si **Habilitar marco de trabajo de la aplicación** está desactivado, esta lista se convierte en **Objeto de inicio** y muestra los formularios y las clases o módulos con un `Sub Main`.

**Objeto de inicio** define el punto de entrada al que se va a llamar cuando se cargue la aplicación. Normalmente, esto se establece en el formulario principal de la aplicación o en el procedimiento `Sub Main` que debe ejecutarse cuando se inicia la aplicación. Dado que las bibliotecas de clases no tienen un punto de entrada, la única opción para esta propiedad es **(None)**. Para obtener más información, vea [/main](/dotnet/visual-basic/reference/command-line-compiler/main). Para obtener acceso a esta propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

### <a name="icon"></a>Iconos

Establece el archivo .ico que quiere usar como su icono del programa. Seleccione **\<Examinar...>** para buscar un gráfico existente. Para obtener más información, vea [/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) (o [/win32icon (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). Para obtener acceso a esta propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

### <a name="assembly-information"></a>Información de ensamblado

Haga clic en este botón para mostrar el [cuadro de diálogo Información de ensamblado](../../ide/reference/assembly-information-dialog-box.md).

### <a name="enable-application-framework"></a>Habilitar marco de trabajo de la aplicación

Especifica si un proyecto usará el marco de trabajo de la aplicación. La configuración de esta opción afecta a las opciones disponibles en **Formulario de inicio**/**Objeto de inicio**.

Si esta casilla está seleccionada, la aplicación usará el `Sub Main` estándar. Al seleccionar esta casilla se habilitan las características de la sección **Propiedades del marco de trabajo de la aplicación Windows**, y también es necesario seleccionar un formulario de inicio.

Si esta casilla está desactivada, la aplicación usa el `Sub Main` personalizado que ha especificado en el **Formulario de inicio**. En este caso, puede especificar un objeto de inicio (un `Sub Main` personalizado en un método o una clase) o un formulario. Además, las opciones de la sección **Propiedades del marco de trabajo de la aplicación Windows** dejarán de estar disponibles.

### <a name="view-windows-settings"></a>Ver configuración de Windows

Haga clic en este botón para generar y abrir el archivo *app.manifest*. Visual Studio usa este archivo para generar datos de manifiesto para la aplicación. Luego, para establecer el nivel de ejecución solicitado de UAC, modifique la etiqueta `<requestedExecutionLevel>` de *app.manifest* de la manera siguiente:

`<requestedExecutionLevel level="asInvoker" />`

ClickOnce funciona con un nivel de `asInvoker` o en modo virtualizado (sin generación de manifiesto). Para especificar el modo virtualizado, quite la etiqueta completa de app.manifest.

Para obtener más información sobre la generación de manifiesto, vea [Implementación de ClickOnce en Windows Vista](../../deployment/clickonce-deployment-on-windows-vista.md).

## <a name="windows-application-framework-properties"></a>Propiedades del marco de trabajo de la aplicación Windows

Las siguientes opciones de configuración están disponibles en la sección **Propiedades del marco de trabajo de la aplicación Windows**. Estas opciones están disponibles solo si la casilla **Habilitar marco de trabajo de la aplicación** está seleccionada.

> [!TIP]
> En la sección siguiente a esta se describe la configuración de las **propiedades del marco de trabajo de la aplicación Windows** específicas de las aplicaciones de Windows Presentation Foundation (WPF).

### <a name="enable-xp-visual-styles"></a>Habilitar estilos visuales de XP

Habilita o deshabilita los estilos visuales de Windows XP, también conocidos como *Temas de Windows XP*. Los estilos visuales de Windows XP presentan, por ejemplo, controles con esquinas redondeadas y colores dinámicos. El valor predeterminado está habilitado.

### <a name="make-single-instance-application"></a>Crear aplicación de instancia única

Seleccione esta casilla para evitar que los usuarios ejecuten varias instancias de la aplicación. De forma predeterminada, la configuración de esta casilla está *desactivada*, lo que permite que varias instancias de la aplicación se ejecuten. Para obtener más información, vea el evento <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>.

### <a name="save-mysettings-on-shutdown"></a>Guardar My.Settings al apagar

Seleccione esta casilla para especificar que la configuración `My.Settings` de la aplicación se guarde cuando los usuarios apaguen sus equipos. La configuración predeterminada está habilitada. Si esta opción está deshabilitada, puede guardar la configuración de la aplicación manualmente llamando a `My.Settings.Save`.

### <a name="authentication-mode"></a>Modo de autenticación

Seleccione **Windows** (valor predeterminado) para especificar el uso de la autenticación de Windows para identificar el usuario que ha iniciado sesión en estos momentos. Puede recuperar esta información en tiempo de ejecución con el objeto `My.User`. Seleccione **Definido por la aplicación** si proporcionará su propio código para autenticar usuarios en lugar de usar los métodos de autenticación de Windows predeterminados.

### <a name="shutdown-mode"></a>Modo de apagado

Seleccione **Al cerrar el formulario de inicio** (valor predeterminado) para especificar que se salga de la aplicación cuando el formulario establecido como el formulario de inicio se cierre, incluso aunque otros formularios estén abiertos. Seleccione **Al cerrar el último formulario** para especificar que se salga de la aplicación cuando el último formulario se cierre o cuando se llame a `My.Application.Exit` o a la instrucción `End` explícitamente.

Seleccione **Al apagar explícitamente** para especificar que se salga de la aplicación cuando llame a `Shutdown` explícitamente.

Seleccione **Al cerrar la última ventana** para especificar que se salga de la aplicación cuando la última ventana se cierre o cuando llame a `Shutdown` explícitamente. Ésta es la configuración predeterminada.

Seleccione **Al cerrar la ventana principal** para especificar que se salga de la aplicación cuando la ventana principal se cierre o cuando llame a `Shutdown` explícitamente.

### <a name="splash-screen"></a>Pantalla de presentación

Seleccione el formulario que quiere usar como una pantalla de presentación. Debe haber creado anteriormente una pantalla de presentación con un formulario o una plantilla. El valor predeterminado es **(None)**.

### <a name="view-application-events"></a>Ver eventos de aplicaciones

Haga clic en este botón para mostrar un archivo de código de eventos en el que pueda escribir eventos para los eventos de marco de trabajo de la aplicación `Startup`, `Shutdown`, `UnhandledException`, `StartupNextInstance` y `NetworkAvailabilityChanged`. También puede invalidar determinados métodos de marco de trabajo de la aplicación. Por ejemplo, puede invalidar `OnInitialize` para cambiar el comportamiento de la pantalla de presentación.

## <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-apps"></a>Propiedades del marco de trabajo de la aplicación Windows para aplicaciones de Windows Presentation Foundation (WPF)

Las siguientes opciones están disponibles en la sección **Propiedades del marco de trabajo de la aplicación Windows** cuando el proyecto es una aplicación de Windows Presentation Foundation (WPF). Estas opciones están disponibles solo si la casilla **Habilitar marco de trabajo de la aplicación** está seleccionada. Las opciones enumeradas en esta tabla solo están disponibles para aplicaciones WPF o de explorador WPF. No están disponibles para bibliotecas de control personalizado o de controles de usuario de WPF.

### <a name="shutdown-mode"></a>Modo de apagado

Esta propiedad solo se aplica a aplicaciones de Windows Presentation Foundation (WPF).

Seleccione **Al apagar explícitamente** para especificar que se salga de la aplicación cuando llame a <xref:System.Windows.Application.Shutdown%2A> explícitamente.

Seleccione **Al cerrar la última ventana** para especificar que se salga de la aplicación cuando la última ventana se cierre o cuando llame a <xref:System.Windows.Application.Shutdown%2A> explícitamente. Ésta es la configuración predeterminada.

Seleccione **Al cerrar la ventana principal** para especificar que se salga de la aplicación cuando la ventana principal se cierre o cuando llame a <xref:System.Windows.Application.Shutdown%2A> explícitamente.

Para obtener más información sobre el uso de esta opción, vea <xref:System.Windows.Application.Shutdown%2A>.

### <a name="edit-xaml"></a>Editar XAML

Este botón abre el archivo de definición de aplicación (Application.xaml) en el editor XAML. Al hacer clic en este botón, se abre *Application.xaml* en el nodo de definición de aplicación. Puede que tenga que editar este archivo para realizar determinadas tareas, como la definición de recursos. Si el archivo de definición de aplicación no existe, el Diseñador de proyectos crea uno.

### <a name="view-application-events"></a>Ver eventos de aplicaciones

Este botón abre el archivo de clase `Application` (*Application.xaml.vb*) en un editor de código. Si el archivo no existe, el Diseñador de proyectos crea uno con el nombre de clase y el espacio de nombres adecuados.

El objeto <xref:System.Windows.Application> genera eventos cuando se producen determinados cambios en el estado de la aplicación (por ejemplo, en el inicio de aplicación o en el apagado). Para obtener una lista completa de los eventos que expone esta clase, vea <xref:System.Windows.Application>. Estos eventos se controlan en la sección de código de usuario de la clase parcial `Application`.