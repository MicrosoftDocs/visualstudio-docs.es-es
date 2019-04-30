---
title: General, depuración, cuadro de diálogo Opciones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf4a3b699d3854ef2a502fb1bf1d7fb2d6204acb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446483"
---
# <a name="general-debugging-options-dialog-box"></a>General, Depuración, Opciones (Cuadro de diálogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El**herramientas / opciones / depuración / General** página permite establecer las siguientes opciones:  
  
 **Preguntar antes de eliminar todos los puntos de interrupción**  
 Requiere confirmación antes de ejecutar el comando **Eliminar todos los puntos de interrupción**.  
  
 **Interrumpir todos los procesos cuando se interrumpa uno**  
 Interrumpe simultáneamente todos los procesos a los que está asociado el depurador cuando se produce una interrupción.  
  
 **Interrumpir cuando las excepciones crucen AppDomain o los límites administrados o nativos**  
 En la depuración administrada o en modo mixto, Common Language Runtime puede capturar excepciones que atraviesen los límites del dominio de aplicación o los límites administrados o nativos, cuando se cumplen las siguientes condiciones:  
  
 1\) cuando código nativo llama a código administrado mediante la interoperabilidad COM y el código administrado produce una excepción. Consulte [Introducción a la interoperabilidad COM](http://msdn.microsoft.com/library/8bd62e68-383d-407f-998b-29aa0ce0fd67).  
  
 2\) al código administrado que se ejecuta en el dominio de aplicación 1 llama a código administrado en el dominio de aplicación 2 y el código en el dominio de aplicación 2 produce una excepción. Consulte [programar con dominios de aplicación](http://msdn.microsoft.com/bd36055b-56bd-43eb-b4d8-820c37172131).  
  
 3\) al código llama a una función mediante la reflexión y la función produce una excepción. Consulte [reflexión](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775).  
  
 En los casos 2) y 3), el código administrado de `mscorlib` a veces detecta la excepción, en lugar de Common Language Runtime. Esta opción no afecta a la interrupción en excepciones detectadas por `mscorlib`.  
  
 **Habilitar la depuración de nivel de dirección**  
 Habilita las características avanzadas para la depuración en el nivel de dirección (ventana **Desensamblado**, ventana **Registros** y puntos de interrupción de dirección).  
  
 **Mostrar desensamblado si el origen no está disponible**  
 Muestra automáticamente el **desensamblado** ventana cuando se intenta depurar código cuyo código fuente no está disponible.  
  
 **Habilitar filtros de punto de interrupción**  
 Permite establecer filtros en puntos de interrupción, de manera que solo afecten a procesos, subprocesos o equipos concretos.  
  
 **Habilitar al Asistente de excepciones**  
 Solo para código administrado. Las excepciones administradas abren el cuadro de diálogo Asistente de excepciones.  Consulte [Asistente de excepciones](http://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb).  
  
 **Desenredar la pila de llamadas en las excepciones no controladas**  
 Hace que la ventana **Pila de llamadas** revierta la pila de llamadas hasta el punto anterior en el que se produjo la excepción no controlada.  
  
 **Habilite Solo mi código**  
 El depurador solo muestra y accede al código de usuario ("Mi código"), y pasa por alto el código de sistema u otro código optimizado o que no tenga símbolos de depuración.  
  
 **Mostrar a todos los miembros para objetos que no son de usuario en ventanas de variables (sólo Visual Basic)**  
 Activa la presentación de miembros no públicos en objetos que están en código que no es de usuario (que no es de tipo "Mi código").  
  
 **Advertir si ningún código de usuario al iniciar**  
 Cuando se inicia la depuración con la opción Solo mi código habilitada, esta opción le advierte si no hay código de usuario ("Mi código").  
  
 **Habilitar .NET Framework del origen de ejecución paso a paso**  
 Permite al depurador ejecutar paso a paso el código fuente de .NET Framework. Si se habilita esta opción, Solo mi código se deshabilita automáticamente. Los símbolos de .NET Framework se descargan a una ubicación en caché. Puede cambiar la ubicación de caché en el **opciones** cuadro de diálogo, **depuración** categoría, **símbolos** página.  
  
 **Saltar propiedades y operadores (solo administrado)**  
 Impide que el depurador ejecute paso a paso las propiedades y operadores en código administrado.  
  
 **Habilitar evaluación de propiedades y otras llamadas a función implícitas**  
 Activa la evaluación automática de propiedades y de llamadas a funciones implícitas en ventanas de variables y en el cuadro de diálogo **Inspección rápida**.  
  
 **Llamar a la función de conversión de cadenas en objetos en ventanas de variables (C# y JavaScript solo)**  
 Ejecuta una llamada de conversión de cadena implícita al evaluar objetos en ventanas de variables. Por lo tanto, el resultado se muestra como una cadena en lugar del nombre de tipo. Solo se aplica mientras se lleva a cabo la depuración en código C#. Este valor puede reemplazarse por el atributo DebuggerDisplay (consulte [utilizando el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
 **Habilitar compatibilidad de servidor de origen**  
 Indica al depurador de Visual Studio que obtenga los archivos de código fuente de los servidores de origen que implementan el protocolo SrcSrv (`srcsrv.dll`). Team Foundation Server y las herramientas de depuración para Windows son dos servidores de origen que implementan el protocolo. Para más obtener información sobre la configuración de SrcSrv, vea la documentación de las Herramientas de depuración para Windows. Además, consulte [especificar símbolos (.pdb) y archivos de código fuente](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
> Dado que la lectura de archivos .pdb puede ejecutar código arbitrario en los archivos, asegúrese de que el servidor es de confianza.  
  
 **Imprimir los mensajes de diagnóstico del servidor de origen a la ventana de salida**  
 Cuando se habilita la compatibilidad del servidor de origen, esta configuración activa la presentación de información de diagnóstico.  
  
 **Permitir a servidor de origen para ensamblados de confianza parcial (solo administrado)**  
 Cuando la compatibilidad del servidor de origen está habilitada, esta configuración invalida el comportamiento predeterminado de no recuperar los orígenes de los ensamblados de confianza parcial.  
  
 **Resaltar la línea de puntos de interrupción y la instrucción actual**  
 Cuando el depurador resalta un punto de interrupción o la instrucción actual, resalta toda la línea.  
  
 **Requieren archivos de código fuente coincidan con la versión original**  
 Indica al depurador que compruebe que un archivo de código fuente coincide con la versión del código fuente utilizada para compilar el archivo ejecutable que se está depurando. Si la versión no coincide, se solicitará que busque el archivo de código fuente correspondiente. Si no se encuentra este archivo, el código fuente no se mostrará durante la depuración.  
  
 **Redirigir el texto de la ventana de salida a la ventana Inmediato**  
 Envía a la ventana **Inmediato** todos los mensajes del depurador que normalmente irían a la ventana **Salida**.  
  
 **Mostrar la estructura de los objetos en ventanas de variables**  
 Desactiva todas las personalizaciones de vistas de estructuras de objetos. Para obtener más información acerca de las personalizaciones de vistas, consulte [crear vistas personalizadas de objetos administrados](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
 **Suprimir optimización JIT al cargar el módulo (solo administrado)**  
 Deshabilita la optimización JIT de código administrado cuando se carga un módulo con compilación JIT mientras se asocia el depurador. Al deshabilitar la optimización se puede simplificar la depuración de algunos problemas, aunque el rendimiento se verá afectado. Si se utiliza Solo mi código, suprimir la optimización JIT puede hacer que el código que no sea de usuario aparezca como código de usuario ("Mi código").  
  
 **Advertir si no hay símbolos al iniciar (solo nativo)**  
 Se muestra un cuadro de diálogo de advertencia al intentar depurar un programa para el que el depurador no tiene información de símbolos.  
  
 **Advertir si la depuración de scripts está deshabilitada al inicio**  
 Se muestra un cuadro de diálogo de advertencia cuando el depurador se inicia con la depuración de scripts deshabilitada.  
  
 **Cargar exportaciones de dll**  
 Carga las tablas de exportación de archivos DLL. La información de símbolos de las tablas de exportación de archivos DLL puede resultar útil si se trabaja con mensajes de Windows, procedimientos de Windows (WindowProc), objetos COM, cálculo de referencias o cualquier archivo DLL para el que no disponga de símbolos. La lectura de la información de exportación de archivos DLL implica cierta sobrecarga. Por lo tanto, esta funcionalidad está desactivada de forma predeterminada.  
  
 Para ver los símbolos que están disponibles en la tabla de exportación de un archivo DLL, utilice `dumpbin /exports`. Los símbolos están disponibles para cualquier archivo DLL de sistema de 32 bits. Si lee el resultado de `dumpbin /exports` , podrá ver el nombre exacto de la función, incluidos los caracteres no alfanuméricos. Esto resulta útil para establecer un punto de interrupción en una función. Los nombres de función procedentes de tablas de exportación de archivos DLL pueden aparecer truncados en otras partes del depurador. Las llamadas se muestran en una lista según el orden de llamada, y la función actual (la que está anidada a mayor profundidad) aparece en la parte superior. Para obtener más información, vea [dumpbin /exports](http://msdn.microsoft.com/library/2971ab7e-4ee6-478b-9c85-cda42a4ce1bf).  
  
 **Mostrar diagrama de pilas paralelas abajo a arriba**  
 Controla la dirección en la que las pilas se muestran en la ventana **Pilas paralelas**.  
  
 **Omitir las excepciones de acceso de memoria GPU si los datos escritos no modificaron el valor**  
 Omite las condiciones de carrera que se detectaron durante la depuración si los datos no cambiaron. Para obtener más información, consulte [depurar código de GPU](../debugger/debugging-gpu-code.md).  
  
 **Usar el modo de compatibilidad administrado**  
 Reemplaza el motor de depuración predeterminado por una versión heredada para habilitar estos escenarios:  
  
- Cuando se usa un lenguaje .NET Framework distinto de C#, VB o F#, que proporciona su propio evaluador de expresiones (incluido C++/CLI).  
  
- Cuando se desea habilitar Editar y continuar para los proyectos de C++ durante la depuración en modo mixto.  
  
  Tenga en cuenta que al elegir el Modo de compatibilidad administrado se deshabilitan algunas características que solo están implementadas en el motor de depuración predeterminado.  
  
  **Usar el modo de compatibilidad nativa**  
  Cuando se selecciona esta opción, el depurador usa el depurador nativo de Visual Studio 2010 en lugar del nuevo depurador nativo.  
  
  Use esta opción cuando depure código de C++ de .NET, ya que el nuevo motor de depuración no admite evaluar expresiones de C++ de .NET. Sin embargo, habilitar el modo de compatibilidad nativa deshabilita muchas características que dependen de la implementación actual del depurador para funcionar. Por ejemplo, el motor heredado carece de muchos visualizadores para tipos integrados como `std::string` en proyectos de Visual Studio 2015.   En estos casos, use los proyectos de Visual Studio 2013 para una experiencia de depuración óptima.  
  
  **Usar los evaluadores de expresión de C# y VB heredados**  
  El depurador usará los evaluadores de expresión de C# /VB de Visual Studio 2013 en lugar de los evaluadores de expresión basados en Roslyn de Visual Studio 2015.  
  
  **Advertir al usar visualizadores del depurador personalizados procesos potencialmente no seguros (solo administrado)**  
  Visual Studio le advierte cuando se usa un visualizador del depurador personalizado que ejecuta código en el proceso de depuración, dado que podría ejecutar código no seguro.  
  
  **Habilitar asignador de montón de depuración de Windows (solo nativo)**  
  Habilita el montón de depuración de Windows para mejorar los diagnósticos del montón. Habilitar esta opción afectará al rendimiento de la depuración.  
  
  **Habilitar herramientas de depuración para XAML de la interfaz de usuario**  
  Aparecerán las ventanas Árbol visual dinámico y Explorador de propiedades dinámico al iniciar la depuración (F5) de un tipo de proyecto compatible. Para obtener más información, consulte [propiedades XAML inspeccionar durante la depuración](../debugger/inspect-xaml-properties-while-debugging.md).  
  
  **Obtener una vista previa de los elementos seleccionados en el árbol Visual dinámico**  
  También se selecciona en el **árbol visual dinámico** el elemento XAML cuyo contexto está seleccionado.  
  
  **Mostrar herramientas de tiempo de ejecución de aplicación**  
  Muestra el **Live Visual Tree** comandos en una barra de herramientas en la ventana principal de la aplicación XAML que se está depurando. Esta opción se introdujo en Visual Studio 2015 Update 2.  
  
  **Habilitar herramientas de diagnóstico durante la depuración**  
  Durante la depuración, se abre la ventana de **Herramientas de diagnóstico**. Para obtener más información, consulte [integradas del depurador de generación de perfiles](http://msdn.microsoft.com/library/a1f40370-7b61-42c2-afc4-0e13eba98859).  
  
  **Mostrar PerfTip de tiempo transcurrido durante la depuración**  
  La ventana de código muestra el tiempo transcurrido de una determinada llamada de método durante la depuración.  
  
  **Habilitar Editar y continuar**  
  Puede usar la función Editar y continuar la durante la depuración.  
  
  **Nativo de habilitar editar y continuar**  
  Puede usar la función Editar y continuar durante la depuración de código nativo de C++. Para obtener más información, consulte [editar y continuar (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
  **Aplicar cambios al continuar (solo nativo)**  
  Al continuar el proceso desde un estado de interrupción, Visual Studio compila y aplica los cambios de código pendientes realizados automáticamente. Si no está seleccionada, puede aplicar los cambios con el elemento "Aplicar cambios en el código" en el menú Depurar.  
  
  **Advertir sobre el código obsoleto (solo nativo)**  
  Obtenga advertencias sobre código obsoleto.  
  
  **Permitir precompilación (solo nativo)**  
  Se permite la precompilación.  
  
## <a name="see-also"></a>Vea también  
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)
