---
title: Depurar proyectos DLL | Documentos de Microsoft
ms.custom: 
ms.date: 05/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "38"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 92d888c04827f3df2c9bc5ede33d4dfd9a6742dc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-dll-projects-from-visual-studio"></a>Depurar proyectos DLL desde Visual Studio
Las siguientes plantillas de Visual Studio crean archivos DLL:  
  
-   (C++, C# y Visual Basic): Biblioteca de clases   

-   (C++): proyecto de DLL de consola Win32
  
     Para obtener más información, consulta [MFC Debugging Techniques](../debugger/mfc-debugging-techniques.md).

-   (C++, C# y Visual Basic): Biblioteca de controles de formularios Windows Forms
  
     Depurar una biblioteca de controles de Windows Forms es similar a depurar un proyecto de biblioteca de clases. En la mayoría de los casos, el control de Windows se llama desde otro proyecto. Cuando se depura el proyecto que hace la llamada, se puede ejecutar paso a paso el código del control de Windows, establecer puntos de interrupción y realizar otras operaciones de depuración. Para obtener más información, vea [Controles de formularios Windows Forms](/dotnet/framework/winforms/controls/index).  

  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Building a debug version  
 Cualquiera que sea la forma en la que inicia la depuración, primero debe asegurarse de compilar la versión de depuración del archivo DLL y, después, de que dicha versión está en la ubicación donde la aplicación espera encontrarla. Esto puede parecer una obviedad pero, si olvida este paso, la aplicación podría encontrar y cargar una versión diferente del archivo DLL. Después el programa continuará ejecutándose mientras se pregunta por qué nunca se visitó el punto de interrupción. Durante la depuración, para comprobar qué archivos DLL ha cargado el programa, abra la ventana **Módulos** del depurador. La ventana **Módulos** muestra cada uno de los archivos DLL o EXE cargados en el proceso que se depura. Para obtener más información, consulta [How to: Use the Modules Window](../debugger/how-to-use-the-modules-window.md).  
 Para que el depurador se asocie al código escrito en C++, el código debe emitir `DebuggableAttribute`. Puede agregar este atributo automáticamente al código vinculando con la opción [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) del vinculador.  
  
##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Mixed-Mode debugging  
 La aplicación que realiza la llamada a la DLL puede estar escrita en código administrado o en código nativo. Si el código nativo llama a la DLL administrada y se desea depurar ambos, deben habilitarse los depuradores administrados y nativos. Puede seleccionar esta opción en el  **\<proyecto > páginas de propiedades** cuadro de diálogo o ventana. La forma de hacerlo depende de si inicia la depuración desde el proyecto DLL o desde el proyecto de la aplicación que hace la llamada. Para obtener más información, consulta [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md).  
  
##  <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Changing default configurations  
 Cuando se crea un proyecto de aplicación de consola con la plantilla de proyecto, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea automáticamente la configuración requerida para las configuraciones Debug y Release. Si fuera necesario, puede cambiar esa configuración. Para obtener más información, consulte [configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [configuración del proyecto para configuraciones de depuración de C#](../debugger/project-settings-for-csharp-debug-configurations.md), [configuración del proyecto para una configuración de depuración de Visual Basic ](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), y [Cómo: conjunto de configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md).  
  
##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Ways to debug the DLL  
 Cada uno de los proyectos de esta sección crea un archivo DLL. No es posible ejecutar un archivo DLL directamente; se debe utilizar una aplicación para llamarlo, normalmente un archivo EXE. Para obtener más información, consulta [Creating and Managing Visual C++ Projects](/cpp/ide/creating-and-managing-visual-cpp-projects). La aplicación que realiza la llamada podría ajustarse a cualquiera de los criterios siguientes:  
  
-   Una aplicación integrada en otro proyecto de la misma solución de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que contiene la biblioteca de clases.  
  
-   Una aplicación existente ya implementada en un equipo de pruebas o de producción.  
  
-   Ubicada en Internet y accesible mediante una dirección URL.  
  
-   Una aplicación web que contiene una página web que incrusta el archivo DLL.  
  
###  <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Debugging the calling application  
Para depurar un archivo DLL, comience por depurar la aplicación que realiza la llamada, que por lo general es un archivo EXE o una aplicación Web. Hay varias formas de hacerlo.  
  
-   Si tiene un proyecto para la aplicación que hace la llamada, ábralo e inicie la ejecución desde el menú **Depurar** . Para obtener más información, consulte [introducción con el depurador](../debugger/getting-started-with-the-debugger.md).  
  
-   Si la aplicación que realiza la llamada es un programa existente, implementado en un equipo de pruebas o de producción que ya está en ejecución, asócielo a él. Utilice este método si el archivo DLL es un control hospedado en Internet Explorer o un control de una página Web. Para obtener más información, consulta [How to: Attach to a Running Process](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
-   Puede depurarlo desde el proyecto DLL. Para obtener más información, consulta [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md).  
  
-   Puede depurarlo desde la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [ventana Inmediato](#vxtskdebuggingdllprojectstheimmediatewindow). En este caso, la ventana **Inmediato** realiza el rol de la aplicación.  
  
Antes de iniciar la depuración de la aplicación que hace la llamada, normalmente es conveniente establecer un punto de interrupción en la biblioteca de clases. Para obtener más información, consulta [Using Breakpoints](../debugger/using-breakpoints.md). Cuando se visita el punto de interrupción, se puede ejecutar paso a paso el código y observar la acción en cada línea hasta aislar el problema. Para obtener más información, consulte [navegar por el código en el depurador](../debugger/navigating-through-code-with-the-debugger.md).
  
###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> La ventana Inmediato  
 Puede evaluar funciones o métodos en el archivo DLL sin necesidad de que una aplicación realice la llamada. Efectúe una depuración en tiempo de diseño y utilice la ventana **Inmediato** . Para depurar de esta manera, siga estos pasos mientras el proyecto DLL está abierto:  
  
1.  Abra la ventana **Inmediato** del depurador.  
  
2.  Para probar un método denominado `Test` en la clase `Class1`, cree instancias de un objeto de tipo `Class1` escribiendo el siguiente código de C# en la ventana Inmediato. Este código administrado funciona para Visual Basic y C++, con los cambios de sintaxis adecuados:  
  
    ```  
    Class1 obj = new Class1();  
    ```  
  
     En C#, todos los nombres deben estar completos. Además, cualquier método o variable debe estar en el ámbito y contexto actual de la sesión de depuración.  
  
3.  Suponiendo que `Test` acepte un parámetro `int` , evalúe `Test` mediante la ventana **Inmediato** :  
  
    ```  
    ?obj.Test(10)  
    ```  
  
     El resultado se imprimirá en la ventana **Inmediato** .  
  
4.  Para continuar la depuración de `Test` , coloque un punto de interrupción dentro de ella y evalúe nuevamente la función:  
  
    ```  
    ?obj.Test(10);  
    ```  
  
     Se llegará al punto de interrupción y podrá recorrer `Test`. Después de que la ejecución sale de `Test`, el depurador regresa al modo de diseño.

## <a name="vxtskdebuggingdllprojectsexternal"></a>Depurar un archivo DLL externo desde un proyecto de C++

Si está depurando un archivo DLL externo a su proyecto, las características de depuración (por ejemplo, recorrer el código) dependerá de la [configuración de depuración del archivo DLL](#vxtskdebuggingdllprojectsbuildingadebugversion) cuando se creó y si el [archivo .pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) y otros archivos necesarios para el archivo DLL están disponibles.

El proyecto debe ser capaz de encontrar el archivo DLL y el archivo .pdb utilizado para la depuración. Puede crear una tarea de compilación personalizada para copiar estos archivos a la  **\<carpeta del proyecto > \Debug** carpeta de salida, también puede copiar los archivos en la carpeta de salida manualmente.

Puede configurar ubicaciones de archivos de encabezado y archivos de *.lib fácilmente en las páginas de propiedades (haga clic en el proyecto de C++ y elija **ver propiedades**y, a continuación, elija **todas las configuraciones de**) sin necesidad de copiar ellos en la carpeta de salida:

- Carpeta C/C ++ (categoría General) - especificar la carpeta que contiene archivos de encabezado de la **directorios de inclusión adicionales** campo.
- Carpeta vinculador (categoría General) - especificar la carpeta que contiene el archivo .lib en el **directorios de bibliotecas adicionales** campo. 
- Carpeta vinculador (categoría de entrada): especifique la ruta de acceso completa y el nombre para el archivo .lib en el **dependencias adicionales** campo.

Si la configuración es correcta, puede depurar iniciando la ejecución de la **depurar** menú.

Para obtener más información sobre la configuración del proyecto, consulte [páginas de propiedades (Visual C++)](/cpp/ide/property-pages-visual-cpp).
  
## <a name="see-also"></a>Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Tipos de proyecto de Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Tipos de proyectos de C#, F# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Configuraciones de depuración de la configuración del proyecto de C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configuración de depuración de la configuración del proyecto para un de Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)