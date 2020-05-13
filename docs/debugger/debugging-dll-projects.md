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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301168"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Depurar archivos DLL en Visual Studio (C, C++, Visual Basic, F)

Un archivo DLL (biblioteca de vínculos dinámicos) es una biblioteca que contiene código y datos que puede usar más de una aplicación. Puede usar Visual Studio para crear, compilar, configurar y depurar archivos DLL.

## <a name="create-a-dll"></a>Crear un archivo DLL

Las siguientes plantillas de proyecto de Visual Studio pueden crear archivos DLL:

- Biblioteca de clases de C, Visual Basic o F
- Biblioteca de Control de formularios Windows Forms (WCF) de Visual Basic o De C.
- Biblioteca de vínculos dinámicos C++ (DLL)

Para obtener más información, vea [Técnicas de depuración de MFC.](../debugger/mfc-debugging-techniques.md)

Depurar una biblioteca WCF es similar a depurar una biblioteca de clases. Para obtener más información, vea Controles de [formularios Windows Forms](/dotnet/framework/winforms/controls/index).

Normalmente se llama a un archivo DLL desde otro proyecto. Al depurar el proyecto de llamada, dependiendo de la configuración del archivo DLL, puede entrar y depurar el código DLL.

## <a name="dll-debug-configuration"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a>Configuración de depuración de DLL

Cuando se usa una plantilla de proyecto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de Visual Studio para crear una aplicación, se crea automáticamente la configuración necesaria para las configuraciones de compilación Depurar y Liberar. Puede cambiar esta configuración si es necesario. Para más información, consulte los siguientes artículos.

- [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Configuración del proyecto para las configuraciones de depuración de C-](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Configuración de proyectos para una configuración de depuración en Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Cómo: Establecer configuraciones de depuración y versión](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>Establecer C++ DebuggableAttribute

Para que el depurador se asocie a un archivo DLL `DebuggableAttribute`de C++, el código C++ debe emitir .

**Para `DebuggableAttribute`configurar :**

1. Seleccione el proyecto DLL de C++ en el **Explorador** de soluciones y seleccione el icono **Propiedades** o haga clic con el botón derecho en el proyecto y seleccione **Propiedades**.

1. En el panel **Propiedades** , en**Depuración**del **vinculador** > , seleccione **Sí (/ASSEMBLYDEBUG)** en **Ensamblado depurable**.

Para obtener más información, vea [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="set-cc-dll-file-locations"></a><a name="vxtskdebuggingdllprojectsexternal"></a>Establecer ubicaciones de archivos DLL C/C++

Para depurar un archivo DLL externo, un proyecto de llamada debe ser capaz de encontrar el archivo DLL, su [archivo .pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)y cualquier otro archivo que requiera el archivo DLL. Puede crear una tarea de compilación personalizada para copiar estos archivos en la carpeta del * \<proyecto>* carpeta de salida de depuración, o puede copiar los archivos allí manualmente.

Para los proyectos de C/C++, puede establecer ubicaciones de encabezado y archivo LIB en las páginas de propiedades del proyecto, en lugar de copiarlas en la carpeta de salida.

**Para establecer las ubicaciones de encabezado y archivo LIB de C/C++:**

1. Seleccione el proyecto DLL de C/C++ en el **Explorador** de soluciones y seleccione el icono **Propiedades** o haga clic con el botón derecho en el proyecto y seleccione **Propiedades**.

1. En la parte superior del panel **Propiedades** , en **Configuración**, seleccione **Todas las configuraciones**.

1. En Directorios de**General** > **inclusión adicionales**adicionales generales > de **C/C++**, especifique la carpeta que tiene archivos de encabezado.

1. En Directorios de**bibliotecas adicionales****generales** > del **vinculador** > , especifique la carpeta que tiene archivos LIB.

1. En**Dependencias adicionales**de**entrada** > del **vinculador** > , especifique la ruta de acceso completa y el nombre de archivo de los archivos LIB.

1. Seleccione **Aceptar**.

Para obtener más información sobre la configuración del proyecto C++, vea Referencia de página de propiedades de [Windows C++.](/cpp/build/reference/property-pages-visual-cpp)

## <a name="build-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a>Crear una versión de depuración

Asegúrese de crear una versión de depuración del archivo DLL antes de iniciar la depuración. Para depurar un archivo DLL, una aplicación que realiza la llamada debe poder encontrar su [archivo .pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) y cualquier otro archivo que requiera el archivo DLL.

Puede crear una tarea de compilación personalizada para copiar los archivos DLL en la carpeta del proyecto de * \<llamada>* carpeta de salida de depuración, o puede copiar los archivos allí manualmente.

Asegúrese de llamar al archivo DLL en su ubicación correcta. Esto puede parecer obvio, pero si una aplicación que realiza la llamada encuentra y carga una copia diferente del archivo DLL, el depurador nunca alcanzará los puntos de interrupción establecidos.

## <a name="debug-a-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a>Depurar un archivo DLL

No se puede ejecutar un archivo DLL directamente. Debe ser llamado por una aplicación, por lo general un archivo *.exe.* Para obtener más información, vea Proyectos de [Visual Studio - C++](/cpp/ide/creating-and-managing-visual-cpp-projects).

Para depurar un archivo DLL, puede iniciar la [depuración desde la aplicación que realiza la llamada](#vxtskdebuggingdllprojectsthecallingapplication)o depurar desde el proyecto [DLL](how-to-debug-from-a-dll-project.md) especificando su aplicación que realiza la llamada. También puede usar la [ventana Inmediata](#vxtskdebuggingdllprojectstheimmediatewindow) del depurador para evaluar las funciones o métodos DLL en tiempo de diseño, sin usar una aplicación que realiza la llamada.

Para obtener más información, consulte [Primero, examine el depurador.](../debugger/debugger-feature-tour.md)

### <a name="start-debugging-from-the-calling-app"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a>Inicie la depuración desde la aplicación que realiza la llamada

La aplicación que llama a un archivo DLL puede ser:

- Una aplicación [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de un proyecto en la misma solución o en una solución diferente del archivo DLL.
- Una aplicación existente que ya está implementada y ejecutándose en un equipo de prueba o producción.
- Ubicada en Internet y accesible mediante una dirección URL.
- Una aplicación web con una página web que incrusta el archivo DLL.

Para depurar un archivo DLL desde una aplicación que realiza la llamada, puede:

- Abra el proyecto de la aplicación que realiza la llamada e inicie la depuración seleccionando **Depurar Iniciar** > **depuración** o presionando **F5**.

  or

- Adjuntar a una aplicación que ya está implementada y ejecutándose en un equipo de prueba o producción. Utilice este método para DLL en sitios web o en aplicaciones web. Para obtener más información, consulte [Cómo: Adjuntar a un proceso](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)en ejecución .

Antes de empezar a depurar la aplicación que realiza la llamada, establezca un punto de interrupción en el archivo DLL. Consulte [Uso de puntos](../debugger/using-breakpoints.md)de interrupción . Cuando se alcanza el punto de interrupción DLL, puede recorrer el código, observando la acción en cada línea. Para obtener más información, vea [Navegar por el código en el depurador.](../debugger/navigating-through-code-with-the-debugger.md)

Durante la depuración, puede usar la ventana **Módulos** para comprobar los archivos DLL y *.exe* que carga la aplicación. Para abrir la ventana **Módulos,** durante la depuración, seleccione **Depurar** > **módulos**de**Windows** > . Para obtener más información, consulte [Cómo: Usar la ventana Módulos](../debugger/how-to-use-the-modules-window.md).

### <a name="use-the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a>Utilice la ventana Inmediato

Puede utilizar la ventana **Inmediato** para evaluar funciones o métodos DLL en tiempo de diseño. La ventana **Inmediato** desempeña el papel de una aplicación que realiza la llamada.

>[!NOTE]
>Puede utilizar la ventana **Inmediato** en tiempo de diseño con la mayoría de los tipos de proyecto. No se admite para SQL, proyectos web o script.

Por ejemplo, para probar `Test` un `Class1`método denominado en la clase:

1. Con el proyecto DLL abierto, abra la ventana **Inmediato** seleccionando **Depurar** > **Windows** > **inmediato** o presionando **Ctrl**+**Alt**+**I**.

1. Cree una instancia `Class1` de un objeto de tipo escribiendo el siguiente código de Cá en la ventana **Inmediato** y presionando **Intro**. Este código administrado funciona para C- y Visual Basic, con los cambios de sintaxis adecuados:

   ```csharp
   Class1 obj = new Class1();
   ```

   En C#, todos los nombres deben estar completos. Los métodos o variables deben estar en el ámbito y el contexto actuales cuando el servicio de lenguaje intenta evaluar la expresión.

1. Suponiendo que `Test` acepte un parámetro `int` , evalúe `Test` mediante la ventana **Inmediato** :

   ```csharp
   ?obj.Test(10);
   ```

   El resultado se imprime en la ventana **Inmediato.**

1. Para continuar la depuración de `Test`, coloque un punto de interrupción dentro de ella y evalúe nuevamente la función.

   El punto de interrupción se golpeará, y se puede paso a través `Test`de . Después de que la ejecución sale de `Test`, el depurador regresa al modo de diseño.

## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a>Depuración en modo mixto

Puede escribir una aplicación de llamada para un archivo DLL en código administrado o nativo. Si la aplicación nativa llama a un archivo DLL administrado y desea depurar ambos, puede habilitar los depuradores administrados y nativos en las propiedades del proyecto. El proceso exacto depende de si desea iniciar la depuración desde el proyecto DLL o el proyecto de aplicación que realiza la llamada. Para obtener más información, vea [Cómo: Depurar en modo mixto](../debugger/how-to-debug-in-mixed-mode.md).

También puede depurar un archivo DLL nativo desde un proyecto de llamada administrada. Para obtener más información, vea [Cómo depurar código administrado y nativo.](how-to-debug-managed-and-native-code.md)

## <a name="see-also"></a>Consulte también
- [Depuración del código administrado](../debugger/debugging-managed-code.md)
- [Prepárese para depurar proyectos C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Tipos de proyectos de C#, F# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Configuración del proyecto para las configuraciones de depuración de C-](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Configuración del proyecto para una configuración de depuración de Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Seguridad del depurador](../debugger/debugger-security.md)
