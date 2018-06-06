---
title: General, depuración, cuadro de diálogo Opciones | Documentos de Microsoft
ms.custom: ''
ms.date: 05/23/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b7af8c68764b3a9ed85bf6a52a3a6c4a0568203
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572055"
---
# <a name="general-debugging-options-dialog-box"></a>General, Depuración, Opciones (Cuadro de diálogo)
El **Herramientas > Opciones > depuración > General** página permite establecer las opciones descritas en este artículo.

Si tiene que restaurar la configuración predeterminada, puede hacer que el uso de **herramientas** > **importar y exportar configuraciones** > **restablecer todas las configuraciones**. Si solo desea restablecer un subconjunto de valores, guardar la configuración en el **importar y exportar configuraciones** antes de realizar los cambios que desea probar, importar, a continuación, la configuración guardada más adelante.
  
**Preguntar antes de eliminar todos los puntos de interrupción** requiere una confirmación antes de completar la **eliminar todos los puntos de interrupción** comando.  
  
**Interrumpir todos los procesos cuando se interrumpa uno** interrumpe simultáneamente todos los procesos a los que está asociado el depurador cuando se produce una interrupción.  
  
**Interrumpir cuando las excepciones crucen AppDomain o los límites administrados o nativos** en la depuración administrada o en modo mixto, common language runtime puede capturar excepciones que atraviesen los límites del dominio de aplicación o los límites administrados o nativos cuando lo siguiente las condiciones son true:  
  
1\) cuando código nativo llama a código administrado utilizando la interoperabilidad COM y el código administrado produce una excepción. Vea [introducción sobre la interoperabilidad COM](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).  
  
2\) cuando el código administrado que se ejecuta en el dominio de aplicación 1 llama a código administrado en el dominio de aplicación 2, y el código en el dominio de aplicación 2 produce una excepción. Vea [programar con dominios de aplicación](/dotnet/articles/framework/app-domains/index).  

3\) cuando el código llama a una función utilizando la reflexión, y la función produce una excepción. Vea [reflexión](/dotnet/framework/reflection-and-codedom/reflection).  
  
En la condición 2 y 3, a veces detecta la excepción mediante código administrado en `mscorlib` en lugar de common language runtime. Esta opción no afecta a la interrupción en excepciones detectadas por `mscorlib`.  
  
**Habilitar la depuración de nivel de dirección** habilita las características avanzadas para la depuración en el nivel de dirección (el **desensamblado** ventana, el **registra** ventana y los puntos de interrupción de dirección).  
  
- **Mostrar desensamblado si el origen no está disponible** muestra automáticamente el **desensamblado** ventana cuando se intenta depurar código cuyo código fuente no está disponible.  
  
**Habilitar filtros de punto de interrupción** le permite establecer filtros en puntos de interrupción para que afecten a sólo procesos específicos, subprocesos o equipos.  
 
**Use el nuevo auxiliar de excepciones** permite que la aplicación auxiliar de excepciones (Visual Studio 2017) que reemplaza el Asistente de excepciones.
  
> [!NOTE]
> Para código administrado, esta opción se ha llamado anteriormente **habilitar el Asistente de excepciones** . 
  
**Habilitar sólo mi código** el depurador muestra y los pasos en código de usuario ("mi código"), pasando por alto el código de sistema y otro código optimizado o que no tenga símbolos de depuración.

- **Advertir si ningún código de usuario al iniciar (solo administrado)** cuando inicia la depuración con sólo mi código habilitada, esta opción le advierte si no hay ningún código de usuario ("mi código"). 

**Habilitar .NET Framework del origen de ejecución paso a paso** permite al depurador ir al código fuente de .NET Framework. Si se habilita esta opción, Solo mi código se deshabilita automáticamente. Los símbolos de .NET Framework se descargan a una ubicación en caché. Puede cambiar la ubicación de caché en el **opciones** cuadro de diálogo, **depuración** categoría, **símbolos** página.  
  
**Saltar propiedades y operadores (solo administrado)** impide que el depurador de ejecución paso a paso en las propiedades y operadores en código administrado.  
  
**Habilitar evaluación de propiedades y otras llamadas a función implícitas** llama activa la evaluación automática de propiedades y funciones implícitas en ventanas de variables y la **Inspección rápida** cuadro de diálogo.  
  
- **Llamar a la función de conversión de cadenas en objetos en ventanas de variables (C# y JavaScript solamente)** ejecuta una llamada de conversión de cadena implícita al evaluar objetos en ventanas de variables. El resultado se muestra como una cadena en lugar del nombre de tipo. Solo se aplica mientras se lleva a cabo la depuración en código C#. El atributo DebuggerDisplay puede invalidar esta configuración (vea [utilizando el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
**Habilitar compatibilidad de servidor de origen** indica al depurador de Visual Studio para obtener archivos de origen desde los servidores de origen que implementan la SrcSrv (`srcsrv.dll`) protocolo. Team Foundation Server y las herramientas de depuración para Windows son dos servidores de origen que implementan el protocolo. Para obtener más información acerca de la configuración de SrcSrv, vea el [SrcSrv](https://msdn.microsoft.com/library/windows/hardware/ff558791(v=vs.85).aspx) documentación. Además, consulte [especificar símbolos (.pdb) y archivos de código fuente](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
>  Dado que la lectura de archivos .pdb puede ejecutar código arbitrario en los archivos, asegúrese de que el servidor es de confianza.  
  
- **Imprimir los mensajes de diagnóstico del servidor de origen a la ventana de salida** cuando está habilitada la compatibilidad del servidor de origen, esta opción activa la presentación de diagnóstico.  
  
- **Permitir que el servidor de origen para ensamblados de confianza parcial (solo administrado)** cuando está habilitada la compatibilidad del servidor de origen, esta configuración invalida el comportamiento predeterminado de no recuperar los orígenes de ensamblados de confianza parcial.  

**Habilitar la compatibilidad con vínculo a origen** indica al depurador de Visual Studio para descargar archivos de origen de archivos .pdb que contienen información de los vínculos de origen. Para obtener más información acerca de vínculo de origen, consulte el [especificación de vinculación de origen](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

    > [!IMPORTANT]
    >  Because Source Link will download files using http or https, make sure you trust the .pdb file.  
  
**Resaltar la línea completa para los puntos de interrupción y la instrucción actual (solo en C++)** cuando el depurador resalta un punto de interrupción o la instrucción actual, resalta toda la línea.  
  
**Requieren archivos de origen para coincidir exactamente con la versión original** indica al depurador que compruebe que un archivo de origen coincide con la versión de código fuente utilizada para generar el archivo ejecutable que se está depurando. Si la versión no coincide, se le pedirá para buscar un origen de búsqueda de coincidencias. Si no se encuentra este archivo, el código fuente no se mostrará durante la depuración. 
  
**Redirigir el texto de la ventana de salida a la ventana Inmediato** envía todos los mensajes del depurador que normalmente aparecerían en el **salida** ventana para el **inmediato** ventana en su lugar.  
  
**Mostrar la estructura de los objetos en ventanas de variables** desactiva todas las personalizaciones de la vista de estructura de objeto. Para obtener más información acerca de las personalizaciones de vistas, vea [crear vistas personalizadas de objetos de .managed](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
**Suprimir optimización JIT al cargar el módulo (solo administrado)** deshabilita la optimización JIT de código administrado cuando se carga un módulo y JIT mientras se asocia el depurador. Al deshabilitar la optimización se puede simplificar la depuración de algunos problemas, aunque el rendimiento se verá afectado. Si se utiliza Solo mi código, suprimir la optimización JIT puede hacer que el código que no sea de usuario aparezca como código de usuario ("Mi código"). Para obtener más información, consulte [optimización JIT y depuración](../debugger/jit-optimization-and-debugging.md).

**Habilitar la depuración de JavaScript de ASP.NET (Chrome e IE)** permite al depurador de script para las aplicaciones ASP.NET. Por primera vez en Chrome, debe iniciar sesión en el explorador por primera vez para habilitar extensiones de Chrome que ha instalado. Deshabilitar esta opción para revertir al comportamiento heredado.    

**Cargar exportaciones de dll** tablas de exportación de archivos dll de carga. La información de símbolos de las tablas de exportación de archivos DLL puede resultar útil si se trabaja con mensajes de Windows, procedimientos de Windows (WindowProc), objetos COM, serialización o cualquier archivo DLL para el que no disponga de símbolos. La lectura de la información de exportación de archivos DLL implica cierta sobrecarga. Por lo tanto, esta funcionalidad está desactivada de forma predeterminada.  
  
Para ver los símbolos que están disponibles en la tabla de exportación de un archivo dll, utilice `dumpbin /exports`. Los símbolos están disponibles para cualquier archivo DLL de sistema de 32 bits. Si lee el resultado de `dumpbin /exports` , podrá ver el nombre exacto de la función, incluidos los caracteres no alfanuméricos. Esto resulta útil para establecer un punto de interrupción en una función. Los nombres de función procedentes de tablas de exportación de archivos DLL pueden aparecer truncados en otras partes del depurador. Las llamadas se muestran en una lista según el orden de llamada, y la función actual (la que está anidada a mayor profundidad) aparece en la parte superior. Para obtener más información, vea [dumpbin /exports](/cpp/build/reference/dash-exports).  
  
**Mostrar pilas paralelas ascendente de diagrama** controla la dirección en la que las pilas se muestran en la **pilas paralelas** ventana.
  
**Omitir las excepciones de acceso de memoria GPU si los datos escritos no modificaron el valor** omite las condiciones de carrera que se detectaron durante la depuración si los datos no cambiaron. Para obtener más información, consulte [depurar código de GPU](../debugger/debugging-gpu-code.md).  
  
**Usar el modo de compatibilidad administrado** reemplaza el motor con una versión heredada para habilitar estos escenarios de depuración predeterminado:  
  
- Cuando se usa un lenguaje .NET Framework distinto de C#, VB o F#, que proporciona su propio evaluador de expresiones (incluido C++/CLI).  
  
- Cuando se desea habilitar Editar y continuar para los proyectos de C++ durante la depuración en modo mixto.  
  
> [!NOTE]
> Elección de compatibilidad administrado modo deshabilitan algunas características que solo están implementadas en el motor de depuración predeterminado. 

**Usar los evaluadores de expresión de C# y VB heredados** el depurador usará los evaluadores de expresión de Visual Studio 2013 C# /VB en lugar de los evaluadores de expresión basados en Roslyn de Visual Studio 2015.    
  
**Advertir al usar visualizadores del depurador personalizados con procesos potencialmente inseguros (solo administrado)** Visual Studio le advierte cuando se usa un visualizador del depurador personalizado que se ejecuta código en el proceso de depuración, ya que podría ejecutar no seguro código.  
  
**Habilitar el asignador de montón de depuración de Windows (solo nativo)** habilita el montón de depuración de windows mejorar los diagnósticos del montón. Habilitar esta opción afectará al rendimiento de la depuración.  
  
**Habilitar herramientas de depuración de la interfaz de usuario para XAML** aparecerán Live Visual Tree y las ventanas de propiedades dinámico al iniciar la depuración (F5 un tipo de proyecto compatible). Para obtener más información, consulte [propiedades inspeccionar XAML durante la depuración](../debugger/inspect-xaml-properties-while-debugging.md).  
  
- **Obtener una vista previa de los elementos seleccionados en el árbol Visual dinámico** también se selecciona el elemento de la XAML cuyo contexto está seleccionado en el **Live Visual Tree** ventana.  
  
- **Mostrar herramientas de tiempo de ejecución en la aplicación** muestra la **Live Visual Tree** comandos en una barra de herramientas en la ventana principal de la aplicación XAML que se está depurando. Esta opción se introdujo en Visual Studio 2015 Update 2. 

- **Habilitar XAML editar y continuar** permite utilizar editar y continuar la característica para código XAML. 
  
**Habilitar herramientas de diagnóstico durante la depuración** el **herramientas de diagnóstico** ventana aparece durante la depuración.
  
**Mostrar PerfTip de tiempo transcurrido durante la depuración** la ventana de código muestra el tiempo transcurrido de una llamada al método especificado cuando se depura.  
  
**Habilitar Editar y continuar** se puede usar Editar y continuar funcionalidad durante la depuración.  
  
- **Habilitar Editar y continuar nativa** se puede usar Editar y continuar funcionalidad mientras se depura el código C++ nativo. Para obtener más información, consulte [editar y continuar (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
- **Aplicar cambios al continuar (solo nativo)** Visual Studio compila automáticamente y aplica los cambios de código pendientes realizados al continuar el proceso desde un estado de interrupción. Si no está seleccionada, puede aplicar los cambios con el elemento "Aplicar cambios en el código" en el menú Depurar.  
  
- **Avisar cuando haya código obsoleto (solo nativo)** Obtenga advertencias sobre código obsoleto.    

**Mostrar ejecución haga clic en botón en el editor de durante la depuración** cuando se selecciona esta opción, el [ejecutar, haga clic en](debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) botón se mostrará durante la depuración.

## <a name="options-supported-in-older-versions-of-visual-studio"></a>Opciones admitidas en versiones anteriores de Visual Studio

Si está utilizando una versión anterior de Visual Studio, algunas opciones adicionales podrían estar presentes.

**Habilitar el Asistente de excepciones** para código administrado, habilitar el Asistente de excepciones. En Visual Studio de 2017, la aplicación auxiliar de excepciones reemplaza al Asistente de excepciones.

**Desenredar la pila de llamadas de las excepciones no controladas** hace que el **pila de llamadas** ventana revierta la pila de llamadas hasta el punto anterior se produjo la excepción no controlada. 

**Advertir si no hay símbolos al iniciar (solo nativo)** muestra un cuadro de diálogo de advertencia cuando se intenta depurar un programa para que el depurador no tiene ninguna información de símbolos. 

**Advertir si la depuración de scripts está deshabilitada al inicio** muestra un cuadro de diálogo de advertencia cuando el depurador se inicia con la depuración de scripts deshabilitada.

**Usar el modo de compatibilidad nativa** cuando se selecciona esta opción, el depurador usa el depurador nativo de Visual Studio 2010 en lugar del nuevo depurador nativo.  
  
Use esta opción cuando depure código de C++ de .NET, ya que el nuevo motor de depuración no admite evaluar expresiones de C++ de .NET. Sin embargo, habilitar el modo de compatibilidad nativa deshabilita muchas características que dependen de la implementación actual del depurador para funcionar. Por ejemplo, el motor heredado carece de muchos visualizadores para tipos integrados como `std::string` en proyectos de Visual Studio 2015.   Usar proyectos de Visual Studio 2013 para la experiencia de depuración óptima en estos casos.
  
## <a name="see-also"></a>Vea también  
 [Depurar en Visual Studio](../debugger/index.md)  
 [Guía de características del depurador](../debugger/debugger-feature-tour.md)
