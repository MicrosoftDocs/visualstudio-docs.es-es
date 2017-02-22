---
title: "P&#225;gina Compilaci&#243;n, Dise&#241;ador de proyectos (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesCompile"
helpviewer_keywords: 
  - "compilación, proyectos de Visual Basic"
  - "compilación, opciones [Visual Basic]"
  - "compiladores, opciones de Visual Basic"
  - "compilación, instrucciones [Visual Basic]"
  - "opciones del compilador, Visual Basic"
  - "Diseñador de proyectos, página Compilar"
  - "Página Compilar del Diseñador de proyectos"
ms.assetid: b2a80230-906e-4e85-b3e0-fcd9c40426e1
caps.latest.revision: 60
caps.handback.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# P&#225;gina Compilaci&#243;n, Dise&#241;ador de proyectos (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilice la página **Compilación** del Diseñador de proyectos para especificar las instrucciones de compilación.  En esta página, también pueden especificarse opciones avanzadas del compilador y eventos anteriores o posteriores a la compilación.  
  
 Para tener acceso a la página **Compilar**, elija un nodo del proyecto \(no el nodo **Solución** \) en **Explorador de soluciones**.  A continuación **proyecto**, **propiedades** en la barra de menús.  Cuando aparezca el Diseñador de proyectos, haga clic en la ficha **Compilar**.  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## Configuración y plataforma  
 Las opciones siguientes permiten seleccionar la configuración y la plataforma que se va a mostrar o modificar.  
  
> [!NOTE]
>  Con las configuraciones de compilación simplificadas, el sistema del proyecto determina si se genera la versión Debug o Release.  Por lo tanto, no se muestran las listas **Configuración** y **Plataforma**.  Para obtener más información, vea [Debug and Release Project Configurations](http://msdn.microsoft.com/es-es/0440b300-0614-4511-901a-105b771b236e).  
  
 **Configuración**  
 Especifica qué opciones de configuración se van a mostrar o modificar.  La configuración es **Depurar** \(predeterminado\), **Liberar** o **Todas las configuraciones**.  Para obtener más información, vea [Debug and Release Project Configurations](http://msdn.microsoft.com/es-es/0440b300-0614-4511-901a-105b771b236e) y [Cómo: Crear y editar configuraciones](../../ide/how-to-create-and-edit-configurations.md).  
  
 **Plataforma**  
 Especifica qué opciones de plataforma se van a mostrar o modificar.  Puede especificar **Cualquier CPU** \(valor predeterminado\), **x64**, o **x86**.  Para obtener más información, vea [Debug and Release Project Configurations](http://msdn.microsoft.com/es-es/0440b300-0614-4511-901a-105b771b236e).  
  
## Opciones de configuración del compilador  
 Las opciones siguientes permiten establecer las opciones de configuración del compilador.  
  
 **Ruta de acceso de salida de la compilación**  
 Especifica la ubicación de los archivos de salida para la configuración de este proyecto.  Escriba la ruta de acceso del resultado de la compilación en este cuadro o haga clic en el botón **Examinar** para seleccionar una ruta de acceso.  Observe que la ruta de acceso es relativa; si escribe una ruta de acceso absoluta, se guardará como relativa.  La ruta predeterminada es bin\\Debug\\ o bin\\Release\\.  Para obtener más información, vea [Debug and Release Project Configurations](http://msdn.microsoft.com/es-es/0440b300-0614-4511-901a-105b771b236e).  
  
 Con las configuraciones de compilación simplificadas, el sistema del proyecto determina si se genera la versión Debug o Release.  El comando **Generar** del menú **Depurar** \(F5\) colocará la compilación en la ubicación de depuración, sin tener en cuenta la **Ruta de acceso de los resultados** especificada.  Sin embargo, el comando **Compilar** del menú **Compilar** la coloca en la ubicación que especifique.  Para obtener más información, vea [Debug and Release Project Configurations](http://msdn.microsoft.com/es-es/0440b300-0614-4511-901a-105b771b236e).  
  
 **Option Explicit**  
 Especifica si se permitirá la declaración de variables implícita.  Seleccione **On** para requerir la declaración explícita de variables.  Hace que el compilador notifique errores si no se declaran las variables antes de utilizarlas.  Seleccione **Off** para permitir la declaración implícita de variables.  
  
 Esta configuración corresponde a la opción del compilador [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).  
  
 Si un archivo de código fuente contiene un valor [Option Explicit \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/option-explicit-statement), el valor `On` u `Off` de la instrucción invalida el valor **Option Explicit** en la **página de compilación**.  
  
 Cuando se crea un nuevo proyecto, el valor de **Option Explicit** en la pestaña **Compilar página** se establece en el valor de **Option Explicit** del cuadro de diálogo **Opciones**.  Para ver o cambiar la configuración en este cuadro de diálogo, en el menú **Herramientas**, haga clic en **Opciones**.  En el cuadro de diálogo **Opciones**, expanda **Proyectos y soluciones** y, a continuación, haga clic en **Valores predeterminados de VB**.  El valor predeterminado inicial de **Option Explicit** en **Valores predeterminados de VB** es **On**.  
  
 Establecer **Option Explicit** en `Off` generalmente no es una buena práctica.  Pudo escribir un nombre de variable incorrectamente en una o más ubicaciones, lo que podría causar resultados inesperados cuando se ejecute el programa.  
  
 **Option Strict**  
 Especifica si se va a aplicar la semántica de tipos estricta.  Si **Option Strict** tiene el valor**On**, las condiciones siguientes producen un error en tiempo de compilación:  
  
-   Conversiones de restricción implícitas  
  
-   Enlace en tiempo de ejecución  
  
-   Tipo implícito que da como resultado un tipo `Object`  
  
 Se producen errores implícitos de la conversión de restricción cuando hay una conversión de tipo de datos implícita que es una conversión de restricción.  Para obtener más información, vea [Option Strict \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Conversiones implícitas y explícitas](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) y [Conversiones de ampliación y de restricción](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions).  
  
 Un objeto se enlaza en tiempo de ejecución cuando se asigna a una propiedad o método de una variable que se declara de tipo `Object`.  Para obtener más información, vea [Option Strict \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/option-strict-statement) y [Enlace en tiempo de compilación y en tiempo de ejecución](/dotnet/visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding).  
  
 Los errores implícitos del tipo de objeto se producen cuando no se puede deducir un tipo adecuado para una variable declarada, por lo que se deduce un tipo `Object`.  Esto se produce principalmente cuando se usa una instrucción `Dim` para declarar una variable sin usar una cláusula `As` y `Option Infer` está desactivada.  Para obtener más información, vea [Option Strict \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Option Infer \(instrucción\)](/dotnet/visual-basic/language-reference/statements/option-infer-statement) y [Especificación del lenguaje de Visual Basic](/dotnet/visual-basic/reference/language-specification).  
  
 La configuración de **Option Strict** corresponde a la opción de compilador [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).  
  
 Si un archivo de código fuente contiene un valor [Option Strict \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/option-strict-statement), `On` u `Off` en la instrucción invalida **Option Strict** en la **página de compilación**.  
  
 Cuando se crea un proyecto, el valor de **Option Strict** en la página **Compilación** se establece en el valor de **Option Strict** del cuadro de diálogo **Opciones**.  Para ver o cambiar la configuración en este cuadro de diálogo, en el menú **Herramientas**, haga clic en **Opciones**.  En el cuadro de diálogo **Opciones**, expanda **Proyectos y soluciones** y, a continuación, haga clic en **Valores predeterminados de VB**.  El valor predeterminado inicial de **Option Strict** en **Valores predeterminados de VB** es **Off**.  
  
 **Advertencias individuales de Option Strict.** La sección **Configuración de advertencias** de la página **Compilación** tiene valores correspondientes a las tres condiciones que producen un error en tiempo de compilación si `Option Strict` se establece en On.  A continuación se muestran estos valores:  
  
-   **Conversión implícita**  
  
-   **Enlace en tiempo de ejecución; la llamada podría dar error en tiempo de ejecución**  
  
-   **Tipo implícito; se asume el objeto**  
  
 Al establecer **Option Strict** en **On**, los tres valores de configuración de advertencias se establecen en **Error**.  Al establecer **Option Strict** en **Off**, los tres valores se establecen en **None**.  
  
 Puede cambiar individualmente cada valor de configuración de advertencias a **Ninguno**, **Advertencia** o **Error**.  Si la tres configuración de advertencias se establecen en **Error**, `On` aparece en el cuadro `Option strict`.  Si los tres se establecen en **None**, `Off` aparece en este cuadro.  Para cualquier otra combinación de estos valores, aparece **\(personalizado\)**.  
  
 **Option Compare**  
 Especifica el tipo de comparación entre cadenas que se utilizará.  Seleccione **Binary** para indicar al compilador que comparaciones de cadenas binarias, con distinción de mayúsculas y minúsculas.  Seleccione **Texto** para utilizar las comparaciones de cadena de texto específicas de la configuración regional, sin distinción de mayúsculas y minúsculas.  
  
 Esta configuración corresponde a la opción del compilador [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).  
  
 Si un archivo de código fuente contiene un valor [Option Compare \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/option-compare-statement), `Binary` o `Text` en la instrucción invalida **Option Compare** en la **página de compilación**.  
  
 Cuando se crea un proyecto, el valor de **Option Compare** en la página **Compilación** se establece en el valor de **Option Compare** del cuadro de diálogo **Opciones**.  Para ver o cambiar la configuración en este cuadro de diálogo, en el menú **Herramientas**, haga clic en **Opciones**.  En el cuadro de diálogo **Opciones**, expanda **Proyectos y soluciones** y, a continuación, haga clic en **Valores predeterminados de VB**.  El valor predeterminado inicial de **Option Compare** en **Valores predeterminados de VB** es **Binary**.  
  
 **Option infer**  
 Especifica si se permitirá la inferencia de tipos local en las declaraciones de variables.  Seleccione **On** para permitir el uso de la inferencia de tipos local.  Seleccione **Off** para bloquear la inferencia de tipos local.  
  
 Esta configuración corresponde a la opción del compilador [\/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).  
  
 Si un archivo de código fuente contiene un valor [Option Infer \(instrucción\)](/dotnet/visual-basic/language-reference/statements/option-infer-statement), `On` u `Off` en la instrucción invalida **Option Infer** en la **página de compilación**.  
  
 Cuando se crea un proyecto, el valor de **Option Infer** en la página **Compilación** se establece en el valor de **Option Infer** del cuadro de diálogo **Opciones**.  Para ver o cambiar la configuración en este cuadro de diálogo, en el menú **Herramientas**, haga clic en **Opciones**.  En el cuadro de diálogo **Opciones**, expanda **Proyectos y soluciones** y, a continuación, haga clic en **Valores predeterminados de VB**.  El valor predeterminado inicial de **Option Infer** en **Valores predeterminados de VB** es **On**.  
  
 **CPU de destino**  
 Especifica el procesador de destino del archivo de salida.  Especifique **x86** para cualquier procesador compatible con Intel de 32 bits, **x64** para cualquier procesador compatible con Intel de 64 bits, **ARM** para cualquier procesador de ARM, o **Cualquier CPU** para especificar que cualquier procesador es aceptable.  **Cualquier CPU** es el valor predeterminado para los nuevos proyectos porque permite la aplicación para ejecutarse en el mayor número de tipos de hardware.  
  
 Para obtener más información, vea [\/platform](/dotnet/visual-basic/reference/command-line-compiler/platform).  
  
 **Preferencia de 32 bits**  
 Si activa la casilla **Prefer32\-bit**, la aplicación se ejecuta como una aplicación de 32 bits en versiones de 32 bits y de 64 bits de Windows.  Si no, la aplicación se ejecuta como una aplicación de 32 bits en versiones de 32 bits de Windows y como una aplicación de 64 bits en versiones de 64 bits de Windows.  
  
 La ejecución como duplica una aplicación de 64 bits el tamaño de puntero, y ésta pueden ocasionar problemas de compatibilidad con las bibliotecas que son exclusivamente de 32 bits.  Tiene sentido de ejecutar una aplicación como 64 bits sólo si ejecuta mucho más rápidamente o necesita más de 4 GB de memoria.  
  
 Esta casilla solo está disponible si se cumplen todas las condiciones siguientes:  
  
-   En **Página de compilación**, la lista **CPU de destino** se establece en **Cualquier CPU**.  
  
-   En **Página de aplicación**, la lista **Tipo de aplicación** especifica que se trata de una aplicación.  
  
-   En **Página de aplicación**, la lista **Marco de trabajo de destino** especifica .NET Framework 4,5.  
  
 **Configuración de advertencias**  
 Esta tabla muestra las condiciones de compilación y el nivel de notificación correspondiente de **Ninguno**, **Advertencia** o **Error** para cada uno.  
  
 De manera predeterminada, todas las advertencias del compilador se agregan a la Lista de tareas durante la compilación.  Seleccione **Deshabilitar todas las advertencias** para indicar al compilador que no emita advertencias ni errores.  Seleccione **Considerar todas las advertencias como errores** si desea que el compilador trate las advertencias como errores que se deben corregir.  
  
 **Deshabilitar todas las advertencias**  
 Especifica si se permitirá que el compilador emita las notificaciones como se especifica en la tabla **Condición o notificación** descrita anteriormente en este documento.  Esta casilla se encuentra desactivada de forma predeterminada.  Active esta casilla para indicar al compilador que no emita advertencias o errores.  
  
 Esta configuración corresponde a la opción del compilador [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).  
  
 **Tratar todas las advertencias como errores**  
 Especifica cómo tratar las advertencias.  De forma predeterminada, esta casilla está desactivada, para que todas las notificaciones de la advertencia permanezcan establecidas en **Advertencia**.  Active esta casilla para cambiar todas las notificaciones de advertencia a **Error**.  
  
 Esta opción sólo está disponible si se desactiva **Deshabilitar todas las advertencias**.  
  
 **Generar archivo de documentación XML**  
 Especifica si se generará información de documentación.  De manera predeterminada, esta casilla está activada, indicando el compilador que genere información de la documentación y la incluya en un archivo XML.  Desactive esta casilla para indicar al compilador que no debe crear documentación.  
  
 Esta configuración corresponde a la opción del compilador [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).  
  
 **Registrar para interoperabilidad COM**  
 Especifica si la aplicación administrada expondrá un objeto COM \(un contenedor invocable mediante COM\) que permite a un objeto COM interactuar con la aplicación.  
  
 De manera predeterminada, esta casilla está desactivada, lo que especifica que la aplicación no permitirá la interoperabilidad COM.  Active esta casilla para permitir la interoperabilidad COM.  
  
 Esta opción no está disponible para los proyectos de Aplicación para Windows o Aplicación de consola.  
  
 **Eventos de compilación**  
 Haga clic en este botón para tener acceso al cuadro de diálogo **Eventos de compilación**.  Utilice este cuadro de diálogo para especificar las instrucciones de configuración de compilación previas y posteriores para el proyecto.  Este cuadro de diálogo se aplica únicamente a los proyectos de Visual Basic.  Para obtener más información, vea [Eventos de compilación \(Cuadro de diálogo\) \(Visual Basic\)](../../ide/reference/build-events-dialog-box-visual-basic.md).  
  
 **Opciones de compilación avanzadas**  
 Haga clic en este botón para tener acceso al cuadro de diálogo **Configuración de compilador avanzada**.  Utilice el cuadro de diálogo **Configuración de compilador avanzada** para especificar las propiedades de configuración de compilación avanzadas de un proyecto.  Este cuadro de diálogo se aplica únicamente a los proyectos de Visual Basic.  Para obtener más información, vea [Configuración de compilador avanzada \(Cuadro de diálogo, Visual Basic\)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).  
  
## Vea también  
 [Debug and Release Project Configurations](http://msdn.microsoft.com/es-es/0440b300-0614-4511-901a-105b771b236e)   
 [Managing Compilation Properties](http://msdn.microsoft.com/es-es/94308881-f10f-4caf-a729-f1028e596a2c)   
 [Cómo: Especificar eventos de compilación \(Visual Basic\)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Compilador de línea de comandos de Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [Cómo: Crear y editar configuraciones](../../ide/how-to-create-and-edit-configurations.md)