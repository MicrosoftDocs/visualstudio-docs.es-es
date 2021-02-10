---
title: Depuración de proyectos DLL | Microsoft Docs
description: Depure archivos de biblioteca de vínculos dinámicos (DLL) en Visual Studio. Use Visual Studio para crear, compilar, configurar y depurar archivos .dll.
ms.custom: SEO-VS-2020
ms.date: 11/06/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b6ad51d6b791def360f12b2d64e4ef6841c7bcda
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872799"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Depuración de archivos DLL en Visual Studio (C#, C++, Visual Basic, F#)

Un archivo DLL (biblioteca de vínculos dinámicos) es una biblioteca que contiene código y datos que puede usar más de una aplicación. Puede usar Visual Studio para crear, compilar, configurar y depurar archivos DLL.

## <a name="create-a-dll"></a>Creación de un archivo DLL

Con las siguientes plantillas de proyecto de Visual Studio se pueden crear archivos DLL:

- Biblioteca de clases: C#, Visual Basic o F#
- Biblioteca de controles de Windows Forms (WCF): C# o Visual Basic
- Biblioteca de vínculos dinámicos (DLL): C++

Para obtener más información, vea [Técnicas de depuración de MFC](../debugger/mfc-debugging-techniques.md).

La depuración de una biblioteca de WCF es similar a la de una biblioteca de clases. Para más información, vea [Controles de Windows Forms](/dotnet/framework/winforms/controls/index).

Normalmente, se llama a un archivo DLL desde otro proyecto. Al depurar el proyecto que realiza la llamada, según la configuración del archivo DLL, se puede ejecutar el código DLL paso a paso por instrucciones y depurarlo.

## <a name="dll-debug-configuration"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Configuración de depuración de DLL

Cuando se usa una plantilla de proyecto de Visual Studio para crear una aplicación, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea automáticamente los valores necesarios para las configuraciones de compilación de depuración y de versión. Puede cambiar estos valores si es necesario. Para obtener más información, vea los artículos siguientes:

- [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Configuración de proyectos para configuraciones de depuración en C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Configuración de proyectos para una configuración de depuración en Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Cómo: Establecer configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>Establecimiento de DebuggableAttribute de C++

Para que el depurador se asocie un archivo DLL de C++, el código de C++ debe emitir `DebuggableAttribute`.

**Para establecer `DebuggableAttribute`:**

1. Elija el proyecto DLL de C++ en el **Explorador de soluciones** y seleccione el icono **Propiedades**, o bien haga clic con el botón derecho en el proyecto y seleccione **Propiedades**.

1. En el panel **Propiedades**, en **Enlazador** > **Depuración**, seleccione **Sí (/ASSEMBLYDEBUG)** como **Ensamblado depurable**.

Para más información, vea [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="set-cc-dll-file-locations"></a><a name="vxtskdebuggingdllprojectsexternal"></a> Establecimiento de ubicaciones de archivo DLL de C/C++

Para depurar un archivo DLL externo, un proyecto que realiza una llamada debe ser capaz de encontrar el archivo DLL, su [archivo. pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) y cualquier otro archivo que necesite el archivo DLL. Puede crear una tarea de compilación personalizada para copiar estos archivos en la carpeta de salida *\<project folder>\Debug*, o bien copiarlos en ella de forma manual.

Para proyectos de C/C++, puede establecer las ubicaciones de los archivos LIB y de encabezado en las páginas de propiedades del proyecto, en lugar de copiarlas en la carpeta de salida.

**Para establecer las ubicaciones de los archivos LIB y de encabezado de C/C++:**

1. Elija el proyecto DLL de C/C++ en el **Explorador de soluciones** y seleccione el icono **Propiedades**, o bien haga clic con el botón derecho en el proyecto y seleccione **Propiedades**.

1. En la parte superior del panel **Propiedades**, en **Configuración**, seleccione **Todas las configuraciones**.

1. En **C/C++**  > **General** > **Directorios de inclusión adicionales**, especifique la carpeta que contiene los archivos de encabezado.

1. En **Enlazador** > **General** > **Directorios de bibliotecas adicionales**, especifique la carpeta que contiene los archivos LIB.

1. En **Enlazador** > **Entrada** > **Dependencias adicionales**, especifique la ruta de acceso completa y el nombre de archivo de los archivos LIB.

1. Seleccione **Aceptar**.

Para más información sobre la configuración de proyectos de C++, vea [Referencia de la página de propiedades de Windows C++](/cpp/build/reference/property-pages-visual-cpp).

## <a name="build-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Compilación de una versión de depuración

Asegúrese de compilar una versión de depuración del archivo DLL antes de iniciar la depuración. Para depurar un archivo DLL, una aplicación que realiza una llamada debe ser capaz de encontrar su [archivo .pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) y cualquier otro archivo que necesite el archivo DLL.

Puede crear una tarea de compilación personalizada para copiar los archivos DLL en la carpeta de salida *\<calling project folder>\Debug*, o bien puede copiarlos en ella de forma manual.

Asegúrese de llamar al archivo DLL en su ubicación correcta. Esto puede parecer obvio, pero si una aplicación que llama encuentra y carga una copia diferente del archivo DLL, el depurador nunca alcanzará los puntos de interrupción que se establezcan.

## <a name="debug-a-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Depuración de un archivo DLL

No se puede ejecutar un archivo DLL directamente. Debe llamarlo una aplicación, normalmente un archivo *.exe*. Para más información, vea [Proyectos de Visual Studio: C++](/cpp/ide/creating-and-managing-visual-cpp-projects).

Para depurar un archivo DLL, puede [iniciar la depuración desde la aplicación que realiza la llamada](#vxtskdebuggingdllprojectsthecallingapplication) o [depurar desde el proyecto DLL](how-to-debug-from-a-dll-project.md) especificando la aplicación que realiza la llamada. También puede usar la [ventana Inmediato](#vxtskdebuggingdllprojectstheimmediatewindow) del depurador para evaluar las funciones o los métodos del archivo DLL en tiempo de diseño, sin usar una aplicación que llama.

Para más información, vea [Primer vistazo al depurador](../debugger/debugger-feature-tour.md).

### <a name="start-debugging-from-the-calling-app"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Inicio de la depuración desde la aplicación que realiza la llamada

La aplicación que llama a un archivo DLL puede ser:

- Una aplicación de un proyecto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que forme parte de la misma solución que el archivo DLL o de otra.
- Una aplicación existente que ya esté implementada y en ejecución en un equipo de pruebas o de producción.
- Ubicada en Internet y accesible mediante una dirección URL.
- Una aplicación web con una página web que inserta el archivo DLL.

Para depurar un archivo DLL desde una aplicación que llama, puede:

- Abrir el proyecto de la aplicación que realiza la llamada e iniciar la depuración seleccionando **Depurar** > **Iniciar depuración** o presionando **F5**.

  o

- Asociarlo a una aplicación que ya esté implementada y en ejecución en un equipo de prueba o de producción. Use este método para archivos DLL que estén en sitios o aplicaciones web. Para obtener más información, vea [Cómo: Adjuntar a un proceso en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Para poder iniciar la depuración de la aplicación que realiza la llamada, establezca un punto de interrupción en el archivo DLL. Vea [Uso de puntos de interrupción en el depurador de Visual Studio](../debugger/using-breakpoints.md). Al llegar al punto de interrupción del archivo DLL, se puede recorrer el código paso a paso y observar la acción en cada línea. Para más información, vea [Navegue por el código con el depurador de Visual Studio](../debugger/navigating-through-code-with-the-debugger.md).

Durante la depuración, puede usar la ventana **Módulos** para comprobar los archivos DLL y los archivos *.exe* que carga la aplicación. Para abrir la ventana **Módulos**, seleccione **Depurar** > **Ventanas** > **Módulos** durante la depuración. Para obtener más información, vea [Cómo: Uso de la ventana Módulos](../debugger/how-to-use-the-modules-window.md).

### <a name="use-the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Uso de la ventana Inmediato

Puede usar la ventana **Inmediato** para evaluar las funciones o los métodos del archivo DLL en tiempo de diseño. La ventana **Inmediato** desempeña el rol de una aplicación que llama.

>[!NOTE]
>Puede usar la ventana **Inmediato** en tiempo de diseño con la mayoría de los tipos de proyecto. No es compatible con SQL, proyectos web ni scripts.

Por ejemplo, para probar un método denominado `Test` en la clase `Class1`:

1. Con el proyecto DLL abierto, abra la ventana **Inmediato** seleccionando **Depurar** > **Ventanas** > **Inmediato** o presionando **Ctrl**+**Alt**+**I**.

1. Cree una instancia de un objeto de tipo `Class1` escribiendo el siguiente código de C# en la ventana **Inmediato** y presionando **Entrar**. Este código administrado funciona para C# y Visual Basic, con los cambios de sintaxis adecuados:

   ```csharp
   Class1 obj = new Class1();
   ```

   En C#, todos los nombres deben estar completos. Cualquier método o variable debe estar en el ámbito y contexto actuales cuando el servicio de lenguaje intenta evaluar la expresión.

1. Suponiendo que `Test` acepte un parámetro `int` , evalúe `Test` mediante la ventana **Inmediato** :

   ```csharp
   ?obj.Test(10);
   ```

   El resultado se imprimirá en la ventana **Inmediato**.

1. Para continuar la depuración de `Test`, coloque un punto de interrupción dentro de ella y evalúe nuevamente la función.

   Se llegará al punto de interrupción y podrá recorrer `Test` paso a paso. Después de que la ejecución sale de `Test`, el depurador regresa al modo de diseño.

## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Depuración en modo mixto

Puede escribir una aplicación que llama para un archivo DLL en código administrado o nativo. Si la aplicación nativa llama a un archivo DLL administrado y quiere depurarlos ambos, puede habilitar ambos depuradores, el administrado y el nativo, en las propiedades del proyecto. El proceso exacto depende de si quiere iniciar la depuración desde el proyecto DLL o desde el proyecto de la aplicación que hace la llamada. Para obtener más información, vea [Cómo: Depurar en modo mixto](../debugger/how-to-debug-in-mixed-mode.md).

También puede depurar un archivo DLL nativo desde un proyecto que llama administrado. Para más información, vea el artículo sobre [cómo depurar código administrado y nativo](how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Vea también
- [Depuración del código administrado](../debugger/debugging-managed-code.md)
- [Preparación de la depuración de proyectos de C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Tipos de proyectos de C#, F# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Configuración del proyecto para configuraciones de depuración en C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Configuración del proyecto para una configuración de depuración de Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Seguridad del depurador](../debugger/debugger-security.md)
