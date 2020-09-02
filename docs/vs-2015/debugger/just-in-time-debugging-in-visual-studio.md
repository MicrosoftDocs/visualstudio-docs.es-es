---
title: Depuración Just-In-Time
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
- CSharp
- VB
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 51
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ad2814dffa75809a318dc7cebe7831b5ecec7d29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690607"
---
# <a name="just-in-time-debugging-in-visual-studio"></a>Depuración Just-In-Time en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La depuración Just-in-Time inicia Visual Studio automáticamente cuando se produce una excepción o un bloqueo en una aplicación que se ejecuta fuera de Visual Studio. Esto le permite probar la aplicación cuando Visual Studio no se está ejecutando y comenzar la depuración con Visual Studio cuando se produce un problema.

La depuración Just-in-Time es compatible con aplicaciones de escritorio de Windows. No funciona para las aplicaciones universales de Windows y no funciona para el código administrado que se hospeda en una aplicación nativa, como los visualizadores.

## <a name="did-the-just-in-time-debugger-dialog-box-appear-when-trying-to-run-an-app"></a><a name="BKMK_Scenario"></a> ¿Aparece el cuadro de diálogo del depurador Just-in-Time al intentar ejecutar una aplicación?

Las acciones que debe realizar cuando vea el cuadro de diálogo depurador Just-in-Time de Visual Studio dependen de lo que está intentando hacer:

#### <a name="if-you-want-to-get-rid-of-the-dialog-box-and-just-run-the-app-normally"></a>Si desea deshacerse del cuadro de diálogo y ejecutar la aplicación normalmente

1. (Usuarios avanzados) Si tiene Visual Studio instalado (o lo ha instalado previamente y lo quitó), [deshabilite la depuración Just-in-Time](#BKMK_Enabling) e intente ejecutar la aplicación de nuevo.

2. Si está ejecutando una aplicación web en Internet Explorer, deshabilite la depuración de scripts.

    Deshabilite la depuración de scripts en el cuadro de diálogo Opciones de Internet. Puede tener acceso a esta opción desde las opciones red del **Panel de control**  /  **e**Internet Internet  /  **Internet Options** (los pasos exactos dependen de la versión de Windows e Internet Explorer).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

3. Vuelva a abrir la página web donde encontró el error. Si esto no resuelve el problema, póngase en contacto con el propietario de la aplicación web para corregir el problema.

4. Si está ejecutando otro tipo de aplicación de Windows, deberá ponerse en contacto con el propietario de la aplicación para corregir el error y, a continuación, volver a instalar la versión fija de la aplicación.

#### <a name="if-you-want-to-fix-or-debug-the-error-advanced-users"></a>Si desea corregir o depurar el error (usuarios avanzados)

- Debe tener [Visual Studio instalado](https://visualstudio.microsoft.com/vs/older-downloads/) para ver la información detallada sobre el error y para intentar depurarlo. Vea [usar JIT](#BKMK_Using_JIT) para obtener instrucciones detalladas. Si no puede resolver el error y corregir la aplicación, póngase en contacto con el propietario de la aplicación para resolver el error.

## <a name="enable-or-disable-just-in-time-debugging"></a><a name="BKMK_Enabling"></a> Habilitar o deshabilitar la depuración Just-in-Time
 Puede habilitar o deshabilitar la depuración Just-in-Time en el cuadro de diálogo **herramientas/opciones** de Visual Studio.

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Para habilitar o deshabilitar la depuración Just-In-Time

1. Abra Visual Studio. En el menú **Herramientas** , haga clic en **Opciones**.

2. En el cuadro de diálogo **Opciones** , seleccione la carpeta **depuración** .

3. En la carpeta **depuración** , seleccione la página **Just-in-Time** .

4. En el cuadro **Habilitar depuración Just-in-Time de estos tipos de código** , Active o desactive los tipos de programa pertinentes: **administrado**, **nativo**o **script**.

    Para deshabilitar la depuración Just-In-Time, una vez habilitada, debe estar ejecutando con privilegios de Administrador. Al habilitar la depuración Just-In-Time, se establece una clave del Registro y se necesitan privilegios de Administrador para modificar dicha clave.

5. Haga clic en **OK**.

   La depuración Just-In-Time todavía puede habilitarse aunque ya no esté instalado Visual Studio en el equipo. Cuando Visual Studio no está instalado, no se puede deshabilitar la depuración Just-in-Time en el cuadro de diálogo **Opciones** de Visual Studio. En ese caso, puede deshabilitar la depuración Just-In-Time editando el Registro de Windows.

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Para deshabilitar la depuración Just-In-Time editando el Registro

1. En el menú **Inicio** , busque y ejecute `regedit.exe`

2. En la ventana **Editor del registro** , busque y elimine las siguientes entradas del registro:

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger

3. Si el equipo ejecuta un sistema operativo de 64 bits, elimine también las siguientes entradas del registro:

    - HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger

4. Tenga cuidado de no eliminar ni cambiar accidentalmente ninguna otra clave del Registro.

5. Cierre la ventana del **Editor del Registro**.

> [!NOTE]
> Si está intentando deshabilitar la depuración Just-in-Time para una aplicación del lado servidor y estos pasos no resuelven el problema, desactive la depuración del servidor en la configuración de la aplicación de IIS y vuelva a intentarlo.

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Para habilitar la depuración Just-In-Time para un Windows Form

1. De forma predeterminada, las aplicaciones de Windows Forms tienen un controlador de excepciones de nivel superior que permite que el programa continúe ejecutándose si puede recuperar. Por ejemplo, si la aplicación de Windows Forms produce una excepción no controlada, verá un cuadro de diálogo similar al siguiente:

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     Para habilitar la depuración Just-in-Time de una aplicación Windows Forms, debe realizar los siguientes pasos adicionales:

2. Establezca el `jitDebugging` valor `true` en en la `system.windows.form` sección del machine.config o *\<application name>*.exe.config archivo:

    ```
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3. En una aplicación de Windows Forms de C++, también debe establecer `DebuggableAttribute` en un archivo .config o en el código. Si compila con la opción [/Zi](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) y sin la opción [/Og](https://msdn.microsoft.com/library/d10630cc-b9cf-4e97-bde3-8d7ee79e9435), el compilador establece este atributo automáticamente. Sin embargo, si desea depurar una compilación de versión no optimizada, deberá establecerlo personalmente. Puede hacerlo agregando la siguiente línea al archivo AssemblyInfo.cpp de la aplicación:

    ```
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     Para obtener más información, vea <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="a-namebkmk_using_jituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Usar la depuración Just-in-Time
 En esta sección se muestra lo que sucede cuando un ejecutable inicia una excepción.

 Debe tener instalado Visual Studio para seguir estos pasos. Si no tiene Visual Studio, puede descargar la edición gratuita de [visual studio 2015 Community Edition](https://visualstudio.microsoft.com/vs/older-downloads/).

 Cuando se instala Visual Studio, la depuración Just-In-Time está habilitada de forma predeterminada.

 Para los fines de esta sección, crearemos una aplicación de consola de C# en Visual Studio que genere una <xref:System.NullReferenceException> .

 En Visual Studio, cree una aplicación de consola de C# (**archivo/nuevo/proyecto/Visual C#/aplicación de consola**) denominada **ThrowsNullException**. Para obtener más información sobre la creación de proyectos en Visual Studio, consulte [Tutorial: crear una aplicación sencilla](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).

 Cuando se abra el proyecto en Visual Studio, abra el archivo Program.cs. Reemplace el método Main() por el siguiente código, que imprime una línea en la consola y, a continuación, produce una excepción NullReferenceException:

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
> Para que este procedimiento funcione en una configuración de [lanzamiento](../debugger/how-to-set-debug-and-release-configurations.md), debe desactivar [solo mi código](../debugger/just-my-code.md). En Visual Studio, haga clic en **herramientas/opciones**. En el cuadro de diálogo **Opciones** , seleccione **depuración**. Quite la comprobación de **habilitar solo mi código**.

 Compile la solución (en Visual Studio, elija **compilar o recompilar solución**). Puede elegir la configuración de depuración o de lanzamiento. Para obtener más información sobre las configuraciones de compilación, vea Descripción de las [configuraciones de compilación](../ide/understanding-build-configurations.md).

 El proceso de compilación crea un ThrowsNullException.exe ejecutable. Puede encontrarlo en la carpeta donde creó el proyecto de C#: **. ..\ThrowsNullException\ThrowsNullException\bin\Debug** o **. ..\ThrowsNullException\ThrowsNullException\bin\Release**.

 Haga doble clic en el ThrowsNullException.exe. Debería ver una ventana de comandos similar a la siguiente:

 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

 Después de unos segundos, aparece una ventana de error:

 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")

 No haga clic en **Cancelar**. Después de unos segundos, debería ver dos botones, **depurar** y **cerrar programa**. Haga clic en **depurar**.

> [!CAUTION]
> Si la aplicación contiene código que no es de confianza, aparecerá un cuadro de diálogo con una advertencia de seguridad. Este cuadro de diálogo le permite decidir si desea continuar o no con la depuración. Antes de continuar con la depuración, decida si confía en el código. ¿Escribió el código usted mismo? ¿Confía en el codificador? Si la aplicación se ejecuta en un equipo remoto, ¿reconoce el nombre del proceso? Incluso si la aplicación se ejecuta localmente, no significa necesariamente que se pueda confiar en ella. Considere la posibilidad de que se ejecute código malintencionado en el equipo. Si decide que el código que va a depurar es de confianza, haga clic en **depurar**. En caso contrario, haga clic en **no depurar**.

 Aparece la ventana del **depurador Just-in-Time de Visual Studio** :

 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

 En los **depuradores posibles**, debería ver que la **nueva instancia de Microsoft Visual Studio línea 2015** está seleccionada. Si no está seleccionado, selecciónelo ahora.

 En la parte inferior de la ventana, en **¿desea depurar con el depurador seleccionado?**, haga clic en **sí**.

 El proyecto ThrowsNullException se abre en una nueva instancia de Visual Studio, con la ejecución detenida en la línea que produce la excepción:

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 Puede iniciar la depuración en este punto. Si se trata de una aplicación real, deberá averiguar por qué el código está produciendo la excepción.

## <a name="just-in-time-debugging-errors"></a>Errores de la depuración Just-In-Time
 Si no ve el cuadro de diálogo cuando el programa se bloquea, puede deberse a Informe de errores de Windows configuración del equipo. Para obtener más información, vea [. Configuración de WER](https://msdn.microsoft.com/library/windows/desktop/bb513638\(v=vs.85\).aspx).

 Es posible que aparezcan los siguientes mensajes de error asociados a la depuración Just-In-Time.

- **No se puede adjuntar al proceso de bloqueo. El programa especificado no es un programa para Windows o MS-DOS.**

     Este error se produce cuando se intenta asociar a un proceso que se ejecuta como otro usuario.

     Para solucionar este problema, inicie Visual Studio, abra el cuadro de diálogo **asociar al proceso** en el menú **depurar** y busque el proceso que desea depurar en la lista **procesos disponibles** . Si no conoce el nombre del proceso, mire el cuadro de diálogo del **depurador Just-in-Time de Visual Studio** y anote el identificador del proceso. Seleccione el proceso en la lista **procesos disponibles** y haga clic en **asociar**. En el cuadro de diálogo **depurador Just-in-Time de Visual Studio** , haga clic en **no** para descartar el cuadro de diálogo.

- **No se pudo iniciar el depurador porque no hay usuarios conectados.**

     Este error se produce cuando la depuración Just-In-Time intenta iniciar Visual Studio en un equipo en el que no hay ningún usuario que haya iniciado sesión en la consola. Como no ha iniciado sesión ningún usuario, no hay ninguna sesión de usuario que se pueda mostrar el cuadro de diálogo de depuración Just-In-Time.

     Para solucionar este problema, inicie una sesión en el equipo.

- **No se ha registrado la clase.**

     Este error indica que el depurador intentó crear una clase COM que no está registrada, probablemente debido a un problema de instalación.

     Para solucionar este problema, utilice el disco de instalación para reinstalar o reparar la instalación de Visual Studio.

## <a name="see-also"></a>Consulte también
 Información [básica](../debugger/debugger-basics.md) del depurador de [seguridad](../debugger/debugger-security.md) del depurador [Just-in-Time, depuración, opciones (cuadro de diálogo) ADVERTENCIA de](../debugger/just-in-time-debugging-options-dialog-box.md) [seguridad: adjuntar a un proceso que pertenece a un usuario que no es de confianza puede ser peligroso. Si la siguiente información es sospechosa o no está seguro, no se adjunte a este proceso](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)
