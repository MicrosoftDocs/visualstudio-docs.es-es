---
title: Depurar proyectos DLL | Microsoft Docs
ms.custom: ''
ms.date: 11/06/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c00740b31e5b9d7cc5678bfc248e673a57e59ccf
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305317"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Depurar archivos DLL en Visual Studio (C#, C++, Visual Basic, F#)

Un archivo DLL (biblioteca de vínculos dinámicos) es una biblioteca que contiene el código y los datos que pueden usarse por más de una aplicación. Puede usar Visual Studio para crear, compilar, configurar y depurar archivos DLL. 

## <a name="create-a-dll"></a>Crear un archivo DLL

Las siguientes plantillas de proyecto de Visual Studio pueden crear archivos DLL:

- C#, Visual Basic, o F# biblioteca de clases 
- C#o en la biblioteca de controles (WCF) de formularios de Windows de Visual Basic 
- Biblioteca de C++ vínculos dinámicos (DLL)

Para obtener más información, vea [Técnicas de depuración de MFC](../debugger/mfc-debugging-techniques.md).

Depurar una biblioteca de WCF es similar a depurar una biblioteca de clases. Para obtener más información, consulte [controles de formularios Windows Forms](/dotnet/framework/winforms/controls/index).  

Se suele llamar a un archivo DLL desde otro proyecto. Cuando se depura el proyecto que realiza la llamada, según la configuración del archivo DLL, puede paso a paso y depurar el código del archivo DLL. 

## <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Configuración de depuración del archivo DLL

Cuando se usa una plantilla de proyecto de Visual Studio para crear una aplicación, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea automáticamente la configuración requerida para configuraciones de compilación de depuración y lanzamiento. Puede cambiar esta configuración si es necesario. Para obtener más información, vea los artículos siguientes:

- [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Configuración de proyectos para configuraciones de depuración en C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Configuración de proyectos para una configuración de depuración en Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [How to: Set Debug and Release configurations](../debugger/how-to-set-debug-and-release-configurations.md) (Definición de configuraciones Debug y Release)  
  
### <a name="set-c-debuggableattribute"></a>Establezca el atributo DebuggableAttribute de C++

Para que el depurador se asocie a un archivo DLL de C++, debe emitir el código de C++ `DebuggableAttribute`. 

**Para establecer `DebuggableAttribute`:**

1. Seleccione el proyecto DLL de C++ en **el Explorador de soluciones** y seleccione el **propiedades** icono, o haga clic en el proyecto y seleccione **propiedades**. 
   
1. En el **propiedades** panel, en **vinculador** > **depuración**, seleccione **Sí (/ ASSEMBLYDEBUG)** para  **Ensamblado depurable**. 

Para obtener más información, consulte [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).  

### <a name="vxtskdebuggingdllprojectsexternal"></a> Establecer las ubicaciones de archivo DLL de C o C++ 

Para depurar un archivo DLL externo, un proyecto que realiza la llamada debe ser capaz de encontrar el archivo DLL, su [archivo .pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)y cualquier otro archivo que requiere el archivo DLL. Puede crear una tarea de compilación personalizada para copiar estos archivos a su  *\<carpeta del proyecto > \Debug* carpeta de salida, o bien puede copiar manualmente los archivos que no existe.

Para los proyectos de C o C++, puede establecer el encabezado y ubicaciones de los archivos LIB en las páginas de propiedades del proyecto, en lugar de copiarlos en la carpeta de salida. 

**Para establecer C o C++ ubicaciones del archivo de encabezado y LIB:**

1. Seleccione el proyecto DLL de C o C++ en **el Explorador de soluciones** y seleccione el **propiedades** icono, o haga clic en el proyecto y seleccione **propiedades**. 
   
1. En la parte superior de la **propiedades** panel, en **configuración**, seleccione **todas las configuraciones de**.
   
1. En **C o C++** > **General** > **directorios de inclusión adicionales**, especifique la carpeta que contiene los archivos de encabezado.
   
1. En **vinculador** > **General** > **directorios de bibliotecas adicionales**, especifique la carpeta que contiene los archivos LIB. 
   
1. En **vinculador** > **entrada** > **dependencias adicionales**, especifique la ruta de acceso completa y nombre de archivo para los archivos LIB.

1. Seleccione **Aceptar**.

Para obtener más información sobre la configuración del proyecto de C++, vea [páginas de propiedades (Visual C++)](/cpp/ide/property-pages-visual-cpp).
  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Compilar una versión de depuración  

Asegúrese de que al compilar una versión de depuración del archivo DLL antes de iniciar la depuración. Para depurar un archivo DLL, una aplicación que realiza la llamada debe ser capaz de encontrar su [archivo .pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) y cualquier otro archivo que requiere el archivo DLL. 

Puede crear una tarea de compilación personalizada para copiar los archivos DLL a su  *\<una llamada a la carpeta del proyecto > \Debug* carpeta de salida, o bien puede copiar manualmente los archivos que no existe.

Asegúrese de llamar a la DLL en su ubicación correcta. Esto puede parecer obvio, pero si una aplicación de llamada busca y carga una copia diferente de la DLL, el depurador nunca alcance los puntos de interrupción establecidos. 

##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Depurar un archivo DLL  

No se puede ejecutar un archivo DLL directamente. Debe llamarse por una aplicación, normalmente un *.exe* archivo. Para obtener más información, consulte [crear y administrar proyectos de Visual C++](/cpp/ide/creating-and-managing-visual-cpp-projects). 

Para depurar un archivo DLL, también puede [iniciar la depuración desde la aplicación que realiza la llamada](#vxtskdebuggingdllprojectsthecallingapplication), o [depurar desde el proyecto DLL](how-to-debug-from-a-dll-project.md) mediante la especificación de su aplicación que realiza la llamada. También puede usar el depurador [ventana Inmediato](#vxtskdebuggingdllprojectstheimmediatewindow) para evaluar las funciones DLL o métodos en tiempo de diseño, sin usar una aplicación que realiza la llamada.

Para obtener más información, consulte [empezar a trabajar con el depurador](getting-started-with-the-debugger.md).

### <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Iniciar la depuración desde la aplicación que realiza la llamada

La aplicación que llama a un archivo DLL puede ser:  
  
- Una aplicación desde un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto en la misma o una solución diferente en el archivo DLL.  
- Una aplicación existente que ya se ha implementado y en ejecución en un equipo de prueba o producción.  
- Ubicada en Internet y accesible mediante una dirección URL.  
- Una aplicación web con una página web que incrusta el archivo DLL.  
  
Para depurar un archivo DLL desde una aplicación que realiza la llamada, hacer lo siguiente:  
  
- Abra el proyecto para la aplicación que realiza la llamada e iniciar la depuración seleccionando **depurar** > **Iniciar depuración** o presionando **F5**.  

  o  

- Adjuntar a una aplicación que ya está implementado y ejecutándose en un equipo de prueba o producción. Utilice este método para archivos DLL en sitios Web o en aplicaciones web. Para obtener más información, vea [Asociar con procesos en ejecución con el depurador de Visual Studio](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
Antes de iniciar la depuración de la aplicación que realiza la llamada, establezca un punto de interrupción en el archivo DLL. Consulte [usar puntos de interrupción](../debugger/using-breakpoints.md). Cuando se alcanza el punto de interrupción de archivo DLL, puede avanzar por el código, observando la acción en cada línea. Para obtener más información, consulte [navegar por el código en el depurador](../debugger/navigating-through-code-with-the-debugger.md).
  
Durante la depuración, puede usar el **módulos** ventana para comprobar los archivos DLL y *.exe* archivos se cargue la aplicación. Para abrir el **módulos** ventana, durante la depuración, seleccione **depurar** > **Windows** > **módulos**. Para obtener más información, consulta [Ver los archivos DLL y ejecutables en la ventana Módulos (C#, C++, Visual Basic, F#)](../debugger/how-to-use-the-modules-window.md). 

###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Utilice la ventana Inmediato  

Puede usar el **inmediato** ventana para evaluar las funciones DLL o métodos en tiempo de diseño. El **inmediato** ventana desempeña la función de una aplicación que realiza la llamada. 

>[!NOTE]
>Puede usar el **inmediato** ventana en tiempo de diseño con la mayoría de los tipos de proyecto. No se admite para proyectos web, SQL o el script.

Por ejemplo, para probar un método denominado `Test` en clase `Class1`:

1. Con el proyecto DLL abierto, abra el **inmediato** ventana seleccionando **depurar** > **Windows** > **inmediato**o presionando **Ctrl**+**Alt**+**me**.  
   
1. Crear una instancia de un objeto de tipo `Class1` escribiendo lo siguiente C# de código en el **inmediato** ventana y presionar **ENTRAR**. Este código administrado funciona para C# y Visual Basic, con cambios de sintaxis adecuados:  
   
   ```csharp
   Class1 obj = new Class1();  
   ```  
  
   En C#, todos los nombres deben estar completos. Cualquier método o variable debe estar en el ámbito actual y el contexto cuando el servicio de lenguaje intenta evaluar la expresión.  
   
1. Suponiendo que `Test` acepte un parámetro `int` , evalúe `Test` mediante la ventana **Inmediato** :  
   
   ```csharp
   ?obj.Test(10);  
   ```  
   
   El resultado se imprime en la **inmediato** ventana.  
   
1. Para continuar la depuración de `Test`, coloque un punto de interrupción dentro de ella y evalúe nuevamente la función.  
   
   Se alcanzará el punto de interrupción y podrá recorrer `Test`. Después de que la ejecución sale de `Test`, el depurador regresa al modo de diseño.

##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Depuración en modo mixto  

Puede escribir una aplicación de llamada para un archivo DLL en código administrado o nativo. Si su aplicación nativa llama a un archivo DLL administrado y desea depurar ambos, puede habilitar a los depuradores administrados y nativos en las propiedades del proyecto. El proceso exacto depende de si desea iniciar la depuración desde el proyecto DLL o el proyecto de aplicación que realiza la llamada. Para obtener más información, vea [Cómo: depurar en modo mixto (C#, C++, Visual Basic)](../debugger/how-to-debug-in-mixed-mode.md). 

También puede depurar una DLL nativa desde un proyecto administrado que realiza la llamada. Para obtener más información, consulte [cómo depurar código administrado y nativo](how-to-debug-managed-and-native-code.md). 

## <a name="see-also"></a>Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Tipos de proyecto de Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Tipos de proyectos de C#, F# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Configuración de proyectos para configuraciones de depuración en C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configuración de proyectos para una configuración de depuración en Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)
