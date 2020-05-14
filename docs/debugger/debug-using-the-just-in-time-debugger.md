---
title: Depuración con el depurador Just-In-Time | Microsoft Docs
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188671"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Depuración con el depurador Just-In-Time en Visual Studio

La depuración Just-in-Time puede iniciar Visual Studio automáticamente cuando se produce un error en una aplicación que se ejecuta fuera de Visual Studio o esta se bloquea. Con la depuración Just-in-Time puede probar aplicaciones fuera de Visual Studio y abrir Visual Studio para empezar a depurar cuando se produce un problema.

La depuración Just-in-Time es compatible con aplicaciones de escritorio de Windows. No es compatible con las aplicaciones universales de Windows ni con el código administrado que se hospeda en una aplicación nativa, como los visualizadores.

> [!TIP]
> Si solo desea que deje de aparecer el cuadro de diálogo del depurador Just-in-Time pero no tiene Visual Studio instalado, vea [Deshabilitar el depurador Just-in-Time](../debugger/just-in-time-debugging-in-visual-studio.md). Si alguna vez ha tenido instalado Visual Studio, puede [deshabilitar la depuración Just-in-Time en el registro de Windows](#disable-just-in-time-debugging-from-the-windows-registry).

## <a name="enable-or-disable-just-in-time-debugging-in-visual-studio"></a><a name="BKMK_Enabling"></a> Habilitar o deshabilitar la depuración Just-In-Time en Visual Studio

>[!NOTE]
>Para habilitar o deshabilitar la depuración Just-in-Time, debe ejecutar Visual Studio como administrador. Al habilitar o deshabilitar la depuración Just-In-Time, se establece una clave del Registro y es posible que se necesiten privilegios de administrador para modificar dicha clave. Para abrir Visual Studio como administrador, haga clic con el botón derecho en la aplicación de Visual Studio y elija **Ejecutar como administrador**.

Puede configurar la depuración Just-in-Time desde el cuadro de diálogo de Visual Studio **Herramientas** > **Opciones** (o **Depurar** > **Opciones**).

**Para habilitar o deshabilitar la depuración Just-In-Time:**

1. En el menú **Herramientas** o **Depurar**, seleccione **Opciones** > **Depuración** > **Just-In-Time**.

   ![Habilitar o deshabilitar la depuración JIT](../debugger/media/dbg-jit-enable-or-disable.png "Habilitar o deshabilitar la depuración JIT")

1. En el cuadro **Habilitar la depuración Just-in-Time de estos tipos de código**, seleccione los tipos de código que desee que depure la depuración Just-in-Time: **Administrado**, **Nativo** o **Script**.

1. Seleccione **Aceptar**.

Si habilita el depurador Just-in-Time pero no se abre cuando se produce un error en una aplicación o esta se bloquea, vea [Solución de problemas de la depuración Just-in-Time](#jit_errors).

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Deshabilitar la depuración Just-in-Time en el registro de Windows

La depuración Just-In-Time todavía puede habilitarse aunque ya no esté instalado Visual Studio en el equipo. Si Visual Studio ya no está instalado, puede deshabilitar la depuración Just-In-Time editando el Registro de Windows.

**Para deshabilitar la depuración Just-In-Time mediante la edición del Registro:**

1. En el menú **Inicio** de Windows, ejecute el **editor del Registro** (*regedit.exe*).

2. En la ventana **Editor del Registro**, busque y elimine las siguientes entradas del registro:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![Clave del Registro JIT](../debugger/media/dbg-jit-registry.png "Clave del Registro JIT")

3. Si el equipo está ejecutando un sistema operativo de 64 bits, elimine también las siguientes entradas del registro:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Asegúrese de no eliminar ni cambiar ninguna otra clave del Registro.

5. Cierre la ventana del **Editor del Registro**.

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Habilitar la depuración Just-In-Time de una aplicación Windows Form

De forma predeterminada, las aplicaciones Windows Forms tienen un controlador de excepciones de nivel superior que permite que la aplicación siga ejecutándose si se puede recuperar. Si una aplicación Windows Forms produce una excepción no controlada, muestra el siguiente cuadro de diálogo:

![Excepción no controlada de Windows Forms](../debugger/media/windowsformsunhandledexception.png "Excepción no controlada de Windows Forms")

Para habilitar la depuración Just-in-Time en lugar de un control de errores estándar de Windows Forms, agregue esta configuración:

- En la sección `system.windows.forms` del archivo *machine.config* o *\<nombre_aplicación>.exe.config*, establezca el valor `jitDebugging` en `true`:

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- En una aplicación de Windows Forms de C++, establezca también `DebuggableAttribute` en `true` en un archivo *.config* o en el código. Si compila con la opción [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) y sin la opción [/Og](/cpp/build/reference/og-global-optimizations), el compilador establece este atributo automáticamente. Pero si desea depurar una compilación de versión no optimizada, deberá establecer `DebuggableAttribute` agregando la siguiente línea en el archivo *AssemblyInfo.cpp* de la aplicación:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   Para obtener más información, vea <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="use-just-in-time-debugging"></a><a name="BKMK_Using_JIT"></a>Uso de la depuración Just-In-Time
Este ejemplo le guía a través de la depuración Just-in-Time cuando una aplicación produce un error.

- Debe tener instalado Visual Studio para seguir estos pasos. Si aún no tiene Visual Studio, puede descargar y usar la edición gratis de [Visual Studio Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).

- Asegúrese de que la depuración Just-in-Time está [habilitada](#BKMK_Enabling) en **Herramientas** > **Opciones** > **Depuración** > **Just-in-Time**.

En este ejemplo creará una aplicación de consola de C# en Visual Studio que produzca una excepción [NullReferenceException](/dotnet/api/system.nullreferenceexception).

1. En Visual Studio, cree una aplicación de consola de C# (**Archivo** > **Nuevo** > **Proyecto** > **Visual C#**  > **Aplicación de consola**) llamada *ThrowsNullException*. Para obtener más información sobre la creación de proyectos en Visual Studio, vea [Tutorial: Crear una aplicación sencilla](../get-started/csharp/tutorial-wpf.md).

1. Cuando se abra el proyecto en Visual Studio, abra el archivo *Program.cs*. Reemplace el método Main() por el siguiente código, que imprime una línea en la consola y, a continuación, produce una excepción NullReferenceException:

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. Para compilar la solución, elija la configuración **Depurar** (predeterminada) o **Versión** y, a continuación, seleccione **Compilación** > **Recompilar solución**.

   > [!NOTE]
   > - Elija la configuración **Depurar** para obtener una experiencia de depuración completa.
   > - Si selecciona la configuración [Versión](../debugger/how-to-set-debug-and-release-configurations.md), deberá desactivar [Solo mi código](../debugger/just-my-code.md) para que este procedimiento funcione. En **Herramientas** > **Opciones** > **Depuración**, anule la selección de **Habilitar Solo mi código**.

   Para más información sobre las configuraciones de compilación, consulte [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).

1. Abra la aplicación compilada *ThrowsNullException.exe* en la carpeta del proyecto de C# ( *...\ThrowsNullException\ThrowsNullException\bin\Debug* o *...\ThrowsNullException\ThrowsNullException\bin\Release*).

   Debería ver la siguiente ventana de comandos:

   ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

1. Se abrirá el cuadro de diálogo **Elegir depurador Just-in-Time**.

   ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

   En **Depuradores disponibles**, seleccione **Nueva instancia de \<versión o edición preferida de Visual Studio>** , si aún no la ha seleccionado.

1. Seleccione **Aceptar**.

   El proyecto ThrowsNullException se abre en una nueva instancia de Visual Studio, con la ejecución detenida en la línea que produjo la excepción:

   ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

Puede iniciar la depuración en este punto. Si estaba depurando una aplicación real, deberá averiguar por qué el código está produciendo la excepción.

> [!CAUTION]
> Si la aplicación contiene código que no es de confianza, aparecerá un cuadro de diálogo de advertencia de seguridad que le permite decidir si desea continuar con la depuración. Antes de continuar con la depuración, decida si confía en el código. ¿Escribió el código usted mismo? Si la aplicación se ejecuta en un equipo remoto, ¿reconoce el nombre del proceso? Si la aplicación se ejecuta de forma local, considere la posibilidad de que se ejecute código malintencionado en el equipo. Si decide que el código es de confianza, seleccione **Aceptar**. En caso contrario, haga clic en **Cancelar**.

## <a name="troubleshoot-just-in-time-debugging"></a><a name="jit_errors"></a> Solución de problemas de la depuración Just-in-Time

Si la depuración Just-in-Time no se inicia cuando una aplicación se bloquea, aunque esté habilitada en Visual Studio:

- Informe de errores de Windows podría asumir el control de errores del equipo.

  Para corregir este problema, use el editor del Registro para agregar un **valor DWORD** de **Deshabilitado**, con los **datos de valor** de **1**, a las siguientes claves del Registro:

  - **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows Error Reporting**

  - (Para equipos de 64 bits): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows Error Reporting**

  Para obtener más información, vea [Configuración de WER](/windows/desktop/wer/wer-settings).

- Un problema conocido de Windows puede estar causando un error en el depurador Just-in-Time.

  La solución consiste en agregar un **valor DWORD** de **Automático**, con los **datos de valor** de **1**, en las siguientes claves del Registro:

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (Para equipos de 64 bits): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Es posible que vea los siguientes mensajes de error durante la depuración Just-in-Time:

- **No se puede adjuntar al proceso de bloqueo. El programa especificado no es un programa para Windows o MS-DOS.**

    El depurador intentó asociarse a un proceso que se ejecuta en otro usuario.

    Para solucionar este problema, en Visual Studio, abra **Depurar** > **Asociar al proceso** y busque el proceso que desea depurar en la lista de **procesos disponibles**. Si desconoce el nombre del proceso, busque el identificador del proceso en el cuadro de diálogo **Depurador Just-in-Time de Visual Studio**. Seleccione el proceso en la lista de **procesos disponibles** y seleccione **Asociar**. Seleccione **No** para descartar el cuadro de diálogo del depurador Just-in-Time.

- **No se pudo iniciar el depurador porque no hay usuarios conectados.**

    No hay ningún usuario que haya iniciado sesión en la consola, por lo que no hay ninguna sesión de usuario para mostrar el cuadro de diálogo de depuración Just-in-Time.

    Para solucionar este problema, inicie una sesión en el equipo.

- **No se ha registrado la clase.**

    El depurador intentó crear una clase COM que no está registrada, probablemente debido a un problema de instalación.

    Para corregir este problema, use el instalador de Visual Studio para reinstalar o reparar la instalación de Visual Studio.

## <a name="see-also"></a>Vea también

- [Seguridad del depurador](../debugger/debugger-security.md)
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
- [Opciones, Depuración, Just-In-Time (cuadro de diálogo)](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Advertencia de seguridad: Adjuntar a un proceso que pertenezca a un usuario que no sea de confianza puede ser peligroso. Si la información siguiente le resulta sospechosa o no está seguro de su procedencia, no la adjunte a este proceso](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
