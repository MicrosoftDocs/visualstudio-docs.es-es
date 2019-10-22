---
title: Depuración de proyectos DLL | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 898eb0eb1489d83e97ec9f0a5b38b475bda0199d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72450413"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Depurar archivos dll enC#visual C++Studio (, F#, Visual Basic,)

Un archivo DLL (biblioteca de vínculos dinámicos) es una biblioteca que contiene código y datos que puede usar más de una aplicación. Puede usar Visual Studio para crear, compilar, configurar y depurar archivos dll.

## <a name="create-a-dll"></a>Crear un archivo DLL

Las siguientes plantillas de proyecto de Visual Studio pueden crear archivos dll:

- C#, Visual Basic o F# biblioteca de clases
- C#o Visual Basic biblioteca de control de Windows Forms (WCF)
- C++Biblioteca de vínculos dinámicos (DLL)

Para obtener más información, vea [Técnicas de depuración de MFC](../debugger/mfc-debugging-techniques.md).

La depuración de una biblioteca de WCF es similar a la depuración de una biblioteca de clases. Para obtener más información, vea [controles de Windows Forms](/dotnet/framework/winforms/controls/index).

Normalmente, se llama a un archivo DLL desde otro proyecto. Al depurar el proyecto que realiza la llamada, en función de la configuración del archivo DLL, puede depurar paso a paso por instrucciones el código DLL y depurarlo.

## <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a>Configuración de depuración de DLL

Cuando se usa una plantilla de proyecto de Visual Studio para crear una aplicación, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea automáticamente la configuración necesaria para las configuraciones de compilación de depuración y versión. Puede cambiar esta configuración si es necesario. Para obtener más información, vea los artículos siguientes:

- [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Configuración de proyectos para configuraciones de depuración en C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Configuración de proyectos para una configuración de depuración en Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [How to: Set Debug and Release configurations](../debugger/how-to-set-debug-and-release-configurations.md) (Definición de configuraciones Debug y Release)

### <a name="set-c-debuggableattribute"></a>Establecer C++ DebuggableAttribute

Para que el depurador se asocie C++ a un archivo C++ dll, el código debe emitir `DebuggableAttribute`.

**Para establecer `DebuggableAttribute`:**

1. Seleccione el C++ Proyecto DLL en **Explorador de soluciones** y seleccione el icono **propiedades** , o haga clic con el botón derecho en el proyecto y seleccione **propiedades**.

1. En el panel **propiedades** , en **vinculador**  > **depuración**, seleccione **sí (/AssemblyDebug)** para **ensamblado depurable**.

Para obtener más información, vea [/AssemblyDebug](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="vxtskdebuggingdllprojectsexternal"></a>Establecer ubicaciones deC++ archivos de C/dll

Para depurar un archivo DLL externo, un proyecto que realiza una llamada debe ser capaz de encontrar el archivo DLL, su [archivo. pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)y cualquier otro archivo que necesite el archivo dll. Puede crear una tarea de compilación personalizada para copiar estos archivos en la *carpeta \<project >* carpeta de salida \debug, o puede copiar los archivos allí manualmente.

Para proyectos deC++ C/, puede establecer las ubicaciones de los archivos de encabezado y lib en las páginas de propiedades del proyecto, en lugar de copiarlas en la carpeta de salida.

**Para establecer las ubicacionesC++ de los archivos de encabezado C/y lib:**

1. Seleccione el proyecto deC++ C/DLL en **Explorador de soluciones** y seleccione el icono de **propiedades** , o haga clic con el botón derecho en el proyecto y seleccione **propiedades**.

1. En la parte superior del panel **propiedades** , en **configuración**, seleccione **todas las configuraciones**.

1. En **C/C++**   > **General**  > **directorios de inclusión adicionales**, especifique la carpeta que contiene los archivos de encabezado.

1. En **vinculador**  > **General**  > **directorios de bibliotecas adicionales**, especifique la carpeta que contiene los archivos lib.

1. En **vinculador**  > **entrada**  > **dependencias adicionales**, especifique la ruta de acceso completa y el nombre de archivo de los archivos lib.

1. Seleccione **Aceptar**.

Para obtener más información C++ sobre la configuración del proyecto, consulte referencia de la [Página de propiedades de Windows C++ ](/cpp/build/reference/property-pages-visual-cpp).

## <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a>Compilar una versión de depuración

Asegúrese de compilar una versión de depuración del archivo DLL antes de iniciar la depuración. Para depurar un archivo DLL, una aplicación que realiza la llamada debe poder encontrar su [archivo. pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) y los demás archivos que necesita el archivo dll.

Puede crear una tarea de compilación personalizada para copiar los archivos DLL en el *\<calling carpeta de proyecto >* carpeta de salida de \debug, o puede copiar los archivos allí manualmente.

Asegúrese de llamar a la DLL en su ubicación correcta. Esto puede parecer obvio, pero si una aplicación que llama encuentra y carga una copia diferente del archivo DLL, el depurador nunca alcanzará los puntos de interrupción establecidos.

## <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a>Depurar un archivo DLL

No se puede ejecutar un archivo DLL directamente. Una aplicación debe llamarla, normalmente un archivo *. exe* . Para obtener más información, vea [proyectos de Visual C++Studio: ](/cpp/ide/creating-and-managing-visual-cpp-projects).

Para depurar un archivo DLL, puede [iniciar la depuración desde la aplicación que realiza la llamada](#vxtskdebuggingdllprojectsthecallingapplication)o [depurar desde el proyecto dll](how-to-debug-from-a-dll-project.md) especificando su aplicación de llamada. También puede usar la [ventana inmediato](#vxtskdebuggingdllprojectstheimmediatewindow) del depurador para evaluar las funciones o métodos de la dll en tiempo de diseño, sin usar una aplicación que llama.

Para obtener más información, vea [primer vistazo al depurador](../debugger/debugger-feature-tour.md).

### <a name="vxtskdebuggingdllprojectsthecallingapplication"></a>Iniciar la depuración desde la aplicación que realiza la llamada

La aplicación que llama a un archivo DLL puede:

- Una aplicación de un proyecto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en la misma solución o en otra diferente del archivo DLL.
- Una aplicación existente que ya está implementada y en ejecución en un equipo de prueba o de producción.
- Ubicada en Internet y accesible mediante una dirección URL.
- Una aplicación web con una página web que incrusta el archivo DLL.

Para depurar un archivo DLL desde una aplicación que llama, puede:

- Abra el proyecto de la aplicación que realiza la llamada e inicie la depuración seleccionando **depurar  > ** **iniciar depuración** o presionando **F5**.

  o

- Asociar a una aplicación que ya está implementada y en ejecución en un equipo de prueba o de producción. Use este método para archivos dll en sitios web o en Web Apps. Para obtener más información, vea [Asociar con procesos en ejecución con el depurador de Visual Studio](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Antes de iniciar la depuración de la aplicación que realiza la llamada, establezca un punto de interrupción en el archivo DLL. Vea [usar puntos de interrupción](../debugger/using-breakpoints.md). Cuando se alcanza el punto de interrupción del archivo DLL, puede recorrer el código y observar la acción en cada línea. Para obtener más información, vea [navegar por el código en el depurador](../debugger/navigating-through-code-with-the-debugger.md).

Durante la depuración, puede utilizar la ventana **módulos** para comprobar los archivos dll y *. exe* que carga la aplicación. Para abrir la ventana **módulos** , durante la depuración, seleccione **depurar**  > **módulos**de**Windows**  > . Para obtener más información, consulta [Ver los archivos DLL y ejecutables en la ventana Módulos (C#, C++, Visual Basic, F#)](../debugger/how-to-use-the-modules-window.md).

### <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a>Usar la ventana inmediato

Puede utilizar la ventana **inmediato** para evaluar las funciones o métodos de la dll en tiempo de diseño. La ventana **inmediato** desempeña el rol de una aplicación que llama.

>[!NOTE]
>Puede usar la ventana **inmediato** en tiempo de diseño con la mayoría de los tipos de proyecto. No es compatible con SQL, proyectos web o script.

Por ejemplo, para probar un método denominado `Test` en la clase `Class1`:

1. Con el proyecto DLL abierto, abra la ventana **inmediato** seleccionando **depurar**  > **Windows**  > **inmediato** o presionando **Ctrl** +**Alt** +**I**.

1. Cree una instancia de un objeto de tipo `Class1` escribiendo el C# código siguiente en la ventana **inmediato** y presionando **entrar**. Este código administrado funciona para C# y Visual Basic, con los cambios de sintaxis adecuados:

   ```csharp
   Class1 obj = new Class1();
   ```

   En C#, todos los nombres deben estar completos. Cualquier método o variable debe estar en el ámbito y contexto actuales cuando el servicio de lenguaje intenta evaluar la expresión.

1. Suponiendo que `Test` acepte un parámetro `int` , evalúe `Test` mediante la ventana **Inmediato** :

   ```csharp
   ?obj.Test(10);
   ```

   El resultado se imprime en la ventana **inmediato** .

1. Para continuar la depuración de `Test`, coloque un punto de interrupción dentro de ella y evalúe nuevamente la función.

   Se alcanzará el punto de interrupción y podrá recorrer `Test`. Después de que la ejecución sale de `Test`, el depurador regresa al modo de diseño.

## <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Depuración en modo mixto

Puede escribir una aplicación de llamada para un archivo DLL en código administrado o nativo. Si la aplicación nativa llama a un archivo DLL administrado y desea depurar ambos, puede habilitar los depuradores administrados y nativos en las propiedades del proyecto. El proceso exacto depende de si desea iniciar la depuración desde el proyecto DLL o desde el proyecto de aplicación que realiza la llamada. Para obtener más información, vea [Cómo: depurar en modo mixto (C#, C++, Visual Basic)](../debugger/how-to-debug-in-mixed-mode.md).

También puede depurar un archivo DLL nativo desde un proyecto de llamada administrado. Para obtener más información, vea [Cómo depurar código administrado y nativo](how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Vea también
- [Depuración del código administrado](../debugger/debugging-managed-code.md)
- [Preparar la depuración C++ de proyectos](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Tipos de proyectos de C#, F# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Configuración del proyecto para configuraciones de depuración en C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Configuración del proyecto para una configuración de depuración de Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Seguridad del depurador](../debugger/debugger-security.md)
