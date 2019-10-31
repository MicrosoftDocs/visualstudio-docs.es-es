---
title: Depurar mediante el depurador Just-in-Time | Microsoft Docs
ms.date: 09/24/2018
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b842fa4ce7c75e061a58d980cefe5648094c2ef7
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188671"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Depurar mediante el depurador Just-in-Time en Visual Studio

La depuración Just-in-Time puede iniciar Visual Studio automáticamente cuando se produce un error en una aplicación que se ejecuta fuera de Visual Studio o se bloquea. Con la depuración Just-in-Time, puede probar aplicaciones fuera de Visual Studio y abrir Visual Studio para comenzar la depuración cuando se produce un problema.

La depuración Just-in-Time funciona para aplicaciones de escritorio de Windows. No funciona para las aplicaciones universales de Windows ni para el código administrado que se hospeda en una aplicación nativa, como los visualizadores.

> [!TIP]
> Si solo desea detener el cuadro de diálogo del depurador Just-in-Time, pero no tiene Visual Studio instalado, consulte [deshabilitar el depurador Just-in-Time](../debugger/just-in-time-debugging-in-visual-studio.md). Si una vez instalado Visual Studio, es posible que tenga que [deshabilitar la depuración Just-in-Time en el registro de Windows](#disable-just-in-time-debugging-from-the-windows-registry).

## <a name="BKMK_Enabling"></a>Habilitar o deshabilitar la depuración Just-in-Time en Visual Studio

>[!NOTE]
>Para habilitar o deshabilitar la depuración Just-in-Time, debe ejecutar Visual Studio como administrador. Al habilitar o deshabilitar la depuración Just-in-Time, se establece una clave del registro y es posible que se requieran privilegios de administrador para cambiar esa clave. Para abrir Visual Studio como administrador, haga clic con el botón derecho en la aplicación de Visual Studio y elija **Ejecutar como administrador**.

Puede configurar la depuración Just-in-Time en el cuadro de diálogo **herramientas** de Visual Studio > **Opciones** (o **depurar** > **Opciones**).

**Para habilitar o deshabilitar la depuración Just-In-Time:**

1. En el menú **herramientas** o **depurar** , seleccione **opciones** > **depuración** > **Just-in-Time**.

   ![Habilitar o deshabilitar la depuración JIT](../debugger/media/dbg-jit-enable-or-disable.png "Habilitar o deshabilitar la depuración JIT")

1. En el cuadro **Habilitar la depuración Just-in-Time para estos tipos de código** , seleccione los tipos de código que desea que depure la depuración Just-in-Time: **administrado**, **nativo**o **script**.

1. Seleccione **Aceptar**.

Si habilita el depurador Just-in-Time, pero no se abre cuando una aplicación se bloquea o se producen errores, consulte [solución de problemas de depuración Just-in-Time](#jit_errors).

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Deshabilitar la depuración Just-in-Time en el registro de Windows

La depuración Just-In-Time todavía puede habilitarse aunque ya no esté instalado Visual Studio en el equipo. Si Visual Studio ya no está instalado, puede deshabilitar la depuración Just-in-Time editando el registro de Windows.

**Para deshabilitar la depuración Just-In-Time mediante la edición del Registro:**

1. En el menú **Inicio** de Windows, ejecute el **Editor del registro** (*regedit. exe*).

2. En la ventana **Editor del registro** , busque y elimine las siguientes entradas del registro:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![Clave del registro JIT](../debugger/media/dbg-jit-registry.png "Clave del registro JIT")

3. Si el equipo ejecuta un sistema operativo de 64 bits, elimine también las siguientes entradas del registro:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Asegúrese de no eliminar ni cambiar ninguna otra clave del registro.

5. Cierre la ventana **del editor del registro** .

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Habilitar la depuración Just-in-Time de Windows Forms

De forma predeterminada, las aplicaciones de Windows Forms tienen un controlador de excepciones de nivel superior que permite que la aplicación siga ejecutándose si se puede recuperar. Si una aplicación Windows Forms produce una excepción no controlada, muestra el siguiente cuadro de diálogo:

![Excepción no controlada de Windows Forms](../debugger/media/windowsformsunhandledexception.png "Excepción no controlada de Windows Forms")

Para habilitar la depuración Just-in-Time en lugar de un control de errores estándar de Windows Forms, agregue esta configuración:

- En la sección `system.windows.forms` del archivo *Machine. config* o *\<nombre de la aplicación >. exe. config* , establezca el valor `jitDebugging` en `true`:

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- En una C++ aplicación de Windows Forms, establezca también`DebuggableAttribute`en`true`en un archivo *. config* o en el código. Si compila con la opción [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) y sin la opción [/Og](/cpp/build/reference/og-global-optimizations), el compilador establece este atributo automáticamente. Sin embargo, si desea depurar una compilación de versión no optimizada, debe establecer `DebuggableAttribute` agregando la siguiente línea en el archivo *AssemblyInfo. cpp* de la aplicación:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   Para obtener más información, vea <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="BKMK_Using_JIT"></a>Usar la depuración Just-in-Time
Este ejemplo le guía a través de la depuración Just-in-Time cuando una aplicación produce un error.

- Debe tener instalado Visual Studio para seguir estos pasos. Si no tiene Visual Studio, puede descargar la edición gratuita de [Visual Studio Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).

- Asegúrese de que la depuración Just-in-Time está [habilitada](#BKMK_Enabling) en **herramientas** > **opciones** > **depuración** > **Just-in-Time**.

En este ejemplo, creará una C# aplicación de consola en Visual Studio que genere una [excepción NullReferenceException](/dotnet/api/system.nullreferenceexception).

1. En Visual Studio, cree una C# aplicación de consola (**archivo** > **nuevo** > **proyecto** > **aplicación de consola**de **Visual C#**  > ) llamado *ThrowsNullException*. Para obtener más información sobre la creación de proyectos en Visual Studio, consulte [Tutorial: crear una aplicación sencilla](../get-started/csharp/tutorial-wpf.md).

1. Cuando se abra el proyecto en Visual Studio, abra el archivo *Program.CS* . Reemplace el método Main () por el siguiente código, que imprime una línea en la consola y, a continuación, produce una excepción NullReferenceException:

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. Para compilar la solución, elija la configuración **depurar** (valor predeterminado) o **versión** y, a continuación, seleccione **compilar** > **recompilar solución**.

   > [!NOTE]
   > - Elija Configuración de **depuración** para la experiencia de depuración completa.
   > - Si selecciona la configuración de [lanzamiento](../debugger/how-to-set-debug-and-release-configurations.md) , debe desactivar [solo mi código](../debugger/just-my-code.md) para que este procedimiento funcione. En **herramientas** > **Opciones** > **depuración**, anule la selección de **Habilitar solo mi código**.

   Para más información sobre las configuraciones de compilación, consulte [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).

1. Abra la aplicación compilada *ThrowsNullException. exe* en la carpeta del C# proyecto ( *. ..\ThrowsNullException\ThrowsNullException\bin\Debug* o *. ..\ThrowsNullException\ThrowsNullException\bin\Release*).

   Debería ver la siguiente ventana de comandos:

   ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

1. Se abre el cuadro de diálogo **elegir el depurador Just-in-Time** .

   ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

   En **depuradores disponibles**, seleccione **nueva instancia de \<su versión o edición de Visual Studio preferida >** , si aún no está seleccionada.

1. Seleccione **Aceptar**.

   El proyecto ThrowsNullException se abre en una nueva instancia de Visual Studio, con la ejecución detenida en la línea que produjo la excepción:

   ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

En este momento puede iniciar la depuración. Si estaba depurando una aplicación real, deberá averiguar por qué el código está produciendo la excepción.

> [!CAUTION]
> Si la aplicación contiene código que no es de confianza, aparece un cuadro de diálogo de advertencia de seguridad que le permite decidir si desea continuar con la depuración. Antes de continuar con la depuración, decida si confía en el código. ¿Escribió el código usted mismo? Si la aplicación se ejecuta en un equipo remoto, ¿reconoce el nombre del proceso? Si la aplicación se ejecuta localmente, tenga en cuenta la posibilidad de que se ejecute código malintencionado en el equipo. Si decide que el código es de confianza, haga clic en **Aceptar**. En caso contrario, haga clic en **Cancelar**.

## <a name="jit_errors"></a>Solución de problemas de depuración Just-in-Time

Si la depuración Just-in-Time no se inicia cuando se bloquea una aplicación, aunque esté habilitada en Visual Studio:

- Informe de errores de Windows podría asumir el control de errores en el equipo.

  Para corregir este problema, use el editor del registro para agregar un **valor DWORD** de **Disabled**, con los **datos de valor** de **1**, a las siguientes claves del registro:

  - **Informe de errores de HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows**

  - (Para equipos de 64 bits): **Informe de errores de HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows**

  Para obtener más información, vea [. Configuración de WER](/windows/desktop/wer/wer-settings).

- Un problema conocido de Windows puede estar causando un error en el depurador Just-in-Time.

  La solución consiste en agregar un **valor DWORD** de **auto**, con **datos de valor** de **1**, a las siguientes claves del registro:

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (Para equipos de 64 bits): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Es posible que vea los siguientes mensajes de error durante la depuración Just-in-Time:

- **No se puede asociar al proceso de bloqueo. El programa especificado no es un programa de Windows o MS-DOS.**

    El depurador intentó asociar a un proceso que se ejecuta bajo otro usuario.

    Para solucionar este problema, en Visual Studio, Abra **Depurar** > **adjuntar al proceso**y busque el proceso que desea depurar en la lista **procesos disponibles** . Si no conoce el nombre del proceso, busque el identificador del proceso en el cuadro de diálogo del **depurador Just-in-Time de Visual Studio** . Seleccione el proceso en la lista **procesos disponibles** y seleccione **adjuntar**. Seleccione **no** para descartar el cuadro de diálogo del depurador Just-in-Time.

- **No se pudo iniciar el depurador porque no hay usuarios conectados.**

    No hay ningún usuario que haya iniciado sesión en la consola, por lo que no hay ninguna sesión de usuario para mostrar el cuadro de diálogo de depuración Just-in-Time.

    Para solucionar este problema, inicie una sesión en el equipo.

- **No se ha registrado la clase.**

    El depurador intentó crear una clase COM que no está registrada, probablemente debido a un problema de instalación.

    Para corregir este problema, use el Instalador de Visual Studio para reinstalar o reparar la instalación de Visual Studio.

## <a name="see-also"></a>Vea también

- [Seguridad del depurador](../debugger/debugger-security.md)
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
- [Opciones, depuración, cuadro de diálogo Just-in-Time](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Advertencia de seguridad Adjuntar a un proceso que pertenezca a un usuario de confianza puede ser peligroso. Si la información siguiente le resulta sospechosa o no está seguro de su procedencia, no la adjunte a este proceso](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
