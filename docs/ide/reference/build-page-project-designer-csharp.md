---
title: "Compilar (P&#225;gina, Dise&#241;ador de proyectos) (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.ProjectPropertiesBuild"
helpviewer_keywords: 
  - "Opciones de compilación [C#]"
  - "Diseñador de proyectos, página Compilación"
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
caps.latest.revision: 43
caps.handback.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Compilar (P&#225;gina, Dise&#241;ador de proyectos) (C#)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La página **Generar** del **Diseñador de proyectos** se utiliza para especificar las propiedades de la configuración de compilación de proyectos.  Esta página sólo se aplica a los proyectos de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)].  
  
 Para tener acceso a la página **Compilación**, elija un nodo de proyecto \(no el nodo **Solución**\) en el **Explorador de soluciones**.  A continuación, elija **Proyecto**, **Propiedades** en la barra de menús.  Cuando aparezca el Diseñador de proyectos, haga clic en la pestaña **Generar**.  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## Configuración y plataforma  
 Las opciones siguientes permiten seleccionar la configuración y la plataforma que se va a mostrar o modificar.  
  
> [!NOTE]
>  Con las configuraciones de compilación simplificadas, el sistema del proyecto determina si se genera la versión Debug o Release.  Por consiguiente, no se muestran estas opciones.  Para obtener más información, vea [Debug and Release Project Configurations](http://msdn.microsoft.com/es-es/0440b300-0614-4511-901a-105b771b236e).  
  
 **Configuración**  
 Especifica qué opciones de configuración se van a mostrar o modificar.  La configuración puede ser **Activo \(Depurar\)** \(éste es el valor predeterminado\), **Depurar**, **Liberar** o **Todas las configuraciones**.  
  
 **Plataforma**  
 Especifica qué opciones de plataforma se van a mostrar o modificar.  La configuración predeterminada es **Activa \(cualquier CPU\)**.  Puede cambiar la plataforma activa mediante el **Administrador de configuración**.  Para obtener más información, vea [Cómo: Crear y editar configuraciones](../../ide/how-to-create-and-edit-configurations.md).  
  
## General  
 Las opciones siguientes permiten establecer varias opciones de configuración del compilador C\#.  
  
 **Símbolos de compilación condicional**  
 Especifica los símbolos en los que se llevará a cabo la compilación condicional.  Separe los símbolos con un punto y coma \(";"\).  Para obtener más información, vea [\/define \(Preprocessor Definition\)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).  
  
 **Definir constante DEBUG**  
 Define DEBUG como símbolo en todos los archivos de código fuente de la aplicación.  Si se seleccionar esta opción, equivale a utilizar la opción de la línea de comandos `/define:DEBUG`.  
  
 **Definir constante TRACE**  
 Define TRACE como símbolo en todos los archivos de código fuente de la aplicación.  Si se selecciona esta opción, equivale a utilizar la opción de la línea de comandos `/define:TRACE`.  
  
 **CPU de destino**  
 Especifica el procesador de destino del archivo de salida.  Elija **x86** para cualquier procesador de 32 bits compatible con Intel, elija **x64** para cualquier procesador de 64 bits compatible con Intel, elija **ARM** para procesadores ARM o elija **Cualquier CPU** para especificar que cualquier procesador es aceptable.  **Cualquier CPU** es el valor predeterminado para los proyectos, porque permite que la aplicación se ejecute en una amplia gama de dispositivos de hardware.  
  
 Para obtener más información, vea [\/platform \(Specify Output Platform\)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).  
  
 **Preferencia de 32 bits**  
 Si activa la casilla **Preferencia de 32 bits**, la aplicación se ejecutará como una aplicación de 32 bits en versiones de Windows de 32 bits y de 64 bits.  Si desactiva la casilla, la aplicación se ejecuta como una aplicación de 32 bits en versiones de Windows de 32 bits y como aplicación de 64 bits en versiones de Windows de 64 bits.  
  
 Si ejecuta una aplicación como una aplicación de 64 bits, se multiplica el tamaño de puntero y es posible que se produzcan problemas de compatibilidad con otras bibliotecas que son exclusivamente de 32 bits.  Resulta útil ejecutar una aplicación de 64 bits solo si necesita más de 4 GB de memoria o si las instrucciones 64 bits proporcionan una mejora significativa de rendimiento.  
  
 Esta casilla está disponible si todas las condiciones siguientes son verdaderas:  
  
-   En la **Página Compilar**, la lista **Destino de la plataforma** se establece en **Cualquier CPU**.  
  
-   En la **Página de aplicación**, la lista **Tipo de resultado** especifica que el proyecto es una aplicación.  
  
-   En la **Página de aplicación**, la lista **Versión de .NET Framework de destino** especifica .NET Framework 4.5.  
  
 **Permitir código no seguro**  
 Permite compilar código que utilice la palabra clave [unsafe](/dotnet/csharp/language-reference/keywords/unsafe).  Para obtener más información, vea [\/unsafe \(Enable Unsafe Mode\)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).  
  
 **Optimizar código**  
 Habilita o deshabilita las optimizaciones realizadas por el compilador para hacer que el archivo de salida sea más pequeño, rápido y eficiente.  Para obtener más información, vea [\/optimize \(Enable\/Disable Optimizations\)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).  
  
## Errores y advertencias  
 La configuración siguiente se utiliza para configurar las opciones de errores y advertencias del proceso de compilación.  
  
 **Nivel de advertencia**  
 Especifica el nivel de advertencia que deberá mostrar el compilador.  Para obtener más información, vea [\/warn \(Specify Warning Level\)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).  
  
 **Suprimir advertencias**  
 Bloquea la capacidad del compilador de generar una o más advertencias.  Si hay varios números de advertencia, hay que separarlos con una coma o un signo de punto y coma.  Para obtener más información, vea [\/nowarn \(Suppress Specified Warnings\)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).  
  
## Tratar advertencias como errores  
 La configuración siguiente se utiliza para especificar qué advertencias se tratarán como errores.  Seleccione una de las opciones siguientes para indicar en qué condiciones se devolverá un error cuando la compilación encuentre una advertencia.  Para obtener más información, vea [\/warnaserror \(Treat Warnings as Errors\)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).  
  
 **None**  
 No trata ninguna advertencia como errores.  
  
 **Advertencias específicas**  
 Trata las advertencias especificadas como errores.  Si hay varios números de advertencia, hay que separarlos con una coma o un signo de punto y coma.  
  
 **Todo**  
 Trata todas las advertencias como errores.  
  
## Output  
 La configuración siguiente se utiliza para configurar las opciones de resultados para el proceso de compilación.  
  
 **Ruta de acceso de los resultados**  
 Especifica la ubicación de los archivos de salida para la configuración de este proyecto.  Escriba la ruta de acceso del resultado de la compilación en este cuadro o seleccione **Examinar** para especificar una ruta de acceso.  Observe que la ruta de acceso es relativa; si escribe una ruta de acceso absoluta, se guardará como relativa.  La ruta predeterminada es bin\\Debug o bin\\Release\\.  Para obtener más información, vea [Debug and Release Project Configurations](http://msdn.microsoft.com/es-es/0440b300-0614-4511-901a-105b771b236e).  
  
 Con las configuraciones de compilación simplificadas, el sistema del proyecto determina si se genera la versión Debug o Release.  El comando **Generar** del menú **Depurar** \(F5\) colocará la compilación en la ubicación de depuración, sin tener en cuenta la **Ruta de acceso de los resultados** especificada.  Sin embargo, el comando **Compilar** del menú **Compilar** la coloca en la ubicación que especifique.  Para obtener más información, vea [Debug and Release Project Configurations](http://msdn.microsoft.com/es-es/0440b300-0614-4511-901a-105b771b236e).  
  
 **Archivo de documentación XML**  
 Especifica el nombre de un archivo en el que se procesarán comentarios sobre documentación.  Para obtener más información, vea [\/doc \(Process Documentation Comments\)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).  
  
 **Registrar para interoperabilidad COM**  
 Indica que la aplicación administrada expondrá un objeto COM \(un contenedor CCW\) que permite la interacción entre objeto COM y la aplicación.  La propiedad **Tipo de resultado** de la página [Aplicación](../../ide/reference/application-page-project-designer-visual-basic.md) del **Diseñador de proyectos** de esta aplicación debe establecerse en **Biblioteca de clases** con el fin de que esté disponible la propiedad **Registrar para interoperabilidad COM**.  Para ver una clase de ejemplo que se podría incluir en la aplicación de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] y exponer como objeto COM, vea [Clase COM de ejemplo](/dotnet/csharp/programming-guide/interop/example-com-class).  
  
 **Generar ensamblados de serialización**  
 Especifica si el compilador utilizará la herramienta Generador de serializador XML \(Sgen.exe\) para crear ensamblados de serialización XML.  Los ensamblados de serialización pueden mejorar el rendimiento de inicio de <xref:System.Xml.Serialization.XmlSerializer> si se ha utilizado esa clase para serializar los tipos del código.  De forma predeterminada, esta opción se establece en **Automático**, que especifica que los ensamblados de serialización se generan sólo si ha utilizado <xref:System.Xml.Serialization.XmlSerializer> para codificar los tipos del código en XML.  **Desactivado** especifica que nunca se van a generar los ensamblados de serialización, sin tener en cuenta si el código utiliza <xref:System.Xml.Serialization.XmlSerializer>.  **Activado** especifica que siempre se generan los ensamblados de serialización.  Los ensamblados de serialización se denominan `TypeName`.XmlSerializers.dll.  Para obtener más información, vea [Herramienta Generador de serializador XML \(Sgen.exe\)](../Topic/XML%20Serializer%20Generator%20Tool%20\(Sgen.exe\).md).  
  
 **Avanzado**  
 Haga clic para mostrar el cuadro de diálogo [Configuración de compilación avanzada \(Cuadro de diálogo, C\#\)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md).  
  
## Vea también  
 [Referencia de propiedades del proyecto](../../ide/reference/project-properties-reference.md)   
 [C\# Compiler Options](/dotnet/csharp/language-reference/compiler-options/index)