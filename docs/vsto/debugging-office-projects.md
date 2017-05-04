---
title: "Depurar proyectos de Office | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Proyectos de Excel [desarrollo de Office en Visual Studio], depurar"
  - "Proyectos de Word [desarrollo de Office en Visual Studio], depurar"
  - "Outlook [desarrollo de Office en Visual Studio], depurar"
  - "depurar [desarrollo de Office en Visual Studio], proyectos de Outlook"
  - "proyectos de Office [desarrollo de Office en Visual Studio], depurar"
  - "Outlook [desarrollo de Office en Visual Studio], proyectos"
ms.assetid: e360b9e9-9f36-48f0-a0c5-a6980fb47a87
caps.latest.revision: 52
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# Depurar proyectos de Office
  Puede depurar proyectos de Office con las mismas herramientas de Microsoft [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] que usa para otros proyectos de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Las características del depurador [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], como la capacidad para insertar puntos de interrupción y ver variables en la ventana **Variables locales**, también están disponibles cuando se depuran proyectos de Office. Para más información sobre las herramientas de depuración [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vea [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md).  
  
> [!TIP]  
>  Para simplificar la depuración, cierre todas las instancias abiertas de la aplicación de Office antes de compilarla y depurarla.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Iniciar y detener el depurador  
 Puede comenzar a depurar un proyecto de Office tal y como inicia la depuración de otros proyectos de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]; por ejemplo, presionando la tecla F5. Al iniciar la depuración de un proyecto de complemento de VSTO, se inicia un nuevo proceso para la aplicación de Office de destino y se carga el complemento de VSTO.  
  
 Al iniciar la depuración de un proyecto de nivel de documento, el documento o libro se abre en un nuevo proceso de Word o Excel.  
  
 Cuando se detiene el depurador, este finaliza el proceso de aplicación repentinamente o, si lo tiene configurado para desasociarse, el depurador se desasocia. También se cierran sin previo aviso todos los documentos que estuvieran abiertos en el proceso de aplicación de Office finalizado y se pierden los cambios no guardados. Esto puede incluir todos los documentos o libros que estén abiertos mientras se ejecuta el depurador.  
  
 Normalmente, antes de detener el depurador es mejor desasociarlo del proceso para poder salir de la aplicación de Office de la forma normal. También puede desasociarlo antes del proceso si desea seguir trabajando con un documento u hoja de cálculo abiertos después de detener al depurador.  
  
 Si está depurando una personalización de nivel de documento para Word, detener el depurador y hacer que Word se cierre repentinamente una y otra vez puede dañar la plantilla Normal. Si esto ocurre, puede eliminar la plantilla Normal dañada y ésta se volverá a crear automáticamente la próxima vez que abra Word. Sin embargo, las macros que se hayan almacenado en la plantilla Normal no se volverán a crear.  
  
### Depurar complementos de VSTO de Office 2013 con Office 2013 u Office 2016  
 Si está utilizando Visual Studio 2015 y tiene ambas versiones de Office instaladas en paralelo, Visual Studio inicia Office 2016. Si utiliza Visual Studio 2013, Visual Studio inicia Office 2013.  
  
 Si desea depurar el complemento de VSTO empleando una versión diferente de Office \(2013 o 2016\), abra el **Diseñador de proyectos** y, en la ficha **Depurar**, elija el botón de opción **Iniciar programa externo**. A continuación, busque la ubicación del ejecutable de la aplicación de Office apropiada.  
  
## Comportamiento de F10 y F11  
 Al iniciar la depuración de un proyecto de Office, F10 y F11 no tienen el mismo comportamiento que al iniciar la depuración de otros proyectos de Visual Basic o C\#. En los proyectos de Visual Basic o C\#, el depurador se detiene en la función principal; en los proyectos de Office, Visual Studio no tiene control sobre la función principal de la aplicación de Office. Sin embargo, durante la depuración, F10 y F11 tienen las mismas funciones que en los proyectos de Visual Basic y C\#.  
  
## Mostrar excepciones  
 Debido al modo en que el código administrado interactúa con el código no administrado, Visual Studio no muestra los errores que producen las aplicaciones de Microsoft Office. Por ejemplo, si un complemento de VSTO creado con las herramientas de desarrollo de Office en Visual Studio produce una excepción, la aplicación de Microsoft Office continúa sin mostrar ningún error. Para ver estos errores, configure el depurador para que se interrumpa al aparecer excepciones de Common Language Runtime. Para obtener más información, consulta [Cómo: Interrumpir cuando se produce una excepción](~/misc/how-to-break-when-an-exception-is-thrown.md).  
  
 Si configura el depurador para que se detenga al aparecer excepciones de Common Language Runtime, el depurador se interrumpirá con todas las excepciones, tanto las que se han controlado como algunas excepciones de primera oportunidad del tiempo de ejecución, que podrían no ser pertinentes para el proyecto. En todos los proyectos aparecen errores relacionados con msosec no encontrado, pero son seguros omitir. Las excepciones de msosec no afectarán a la solución.  
  
 También puede utilizar instrucciones **Try...Catch** en torno a sus métodos para detectar excepciones.  
  
 De forma predeterminada, Visual Studio tampoco muestra errores de depuración de Just\-In\-Time para proyectos de Office. Sin embargo, puede habilitar esta característica para ver los errores que se produzcan. Para obtener más información, consulta [Depuración Just-In-Time en Visual Studio](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
## Argumentos de la línea de comandos  
 Si la **Acción de inicio** de la página de propiedades **Depurar** se establece en **Iniciar proyecto**, Visual Studio no utiliza argumentos de línea de comandos al depurar el proyecto, incluso aunque haya especificado argumentos de línea de comandos como opciones de inicio. Si desea utilizar argumentos de línea de comandos al iniciar la depuración, debe seleccionar una **Acción de inicio** distinta de **Iniciar proyecto**.  
  
## Control de código fuente  
 Las propiedades de depuración no se comparten entre varios usuarios cuando se trabaja con control de código fuente. Los proyectos de Visual Basic y C\# almacenan las propiedades de depuración en un archivo específico de cada usuario \(*NombredeProyecto*.vbproj.user o *NombredeProyecto*.csproj.user\), y este archivo no está bajo control de código fuente. Si hay más de una persona depurando, cada una debe introducir manualmente las propiedades de depuración.  
  
## Depurar conjuntos de datos en caché en un proyecto de nivel de documento  
 Cada vez que se compila un proyecto, el conjunto de datos se vacía y se vuelve a crear. Si desea depurar un conjunto de datos en caché, debe abrir el documento fuera de Visual Studio y, a continuación, asociar el depurador.  
  
## Depurar proyectos de documento de Word basados en el formato de documento de Word 97\-2003 \(\*.doc\)  
 Para depurar un proyecto de documento de Word basado en el formato de documento de Word 97\-2003 \(\*.doc\), debe agregar la carpeta del proyecto a la lista de carpetas de confianza. Para obtener más información sobre cómo realizar esta operación, vea [Otorgar confianza a los documentos](../vsto/granting-trust-to-documents.md).  
  
## Depurar complementos deshabilitados  
 Las aplicaciones de Microsoft Office pueden deshabilitar los complementos de VSTO que se comporten de forma inesperada. La aplicación de Microsoft Office deshabilita los complementos de VSTO para evitar que se cargue código problemático cada vez que se inicie la aplicación. Sin embargo, esto también puede producir un comportamiento inesperado durante la depuración típica. Para obtener información sobre cómo volver a habilitar los complementos de VSTO, vea [Cómo: Volver a habilitar un complemento de VSTO que se ha deshabilitado](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md).  
  
 Las aplicaciones de Microsoft Office usan dos tipos de deshabilitación para los complementos de VSTO: deshabilitación total y deshabilitación parcial.  
  
### Deshabilitación total  
 La deshabilitación total puede producirse cuando un complemento de VSTO hace que la aplicación se cierre inesperadamente. También puede ocurrir en el equipo de desarrollo si detiene el depurador mientras se está ejecutando el controlador de eventos <xref:Microsoft.Office.Tools.AddIn.Startup> en el complemento de VSTO. Cuando un complemento de VSTO se deshabilita totalmente, aparece en la lista **Elementos deshabilitados** de la aplicación.  
  
 Si una aplicación de Office deshabilita totalmente un complemento de VSTO creado con las herramientas de desarrollo de Office en Visual Studio, la aplicación deshabilita únicamente el complemento de VSTO que produjo el error. Los demás complementos de VSTO creados con las herramientas de desarrollo de Office en Visual Studio para esa aplicación de Office continuarán cargándose.  
  
### Deshabilitación parcial  
 La deshabilitación parcial puede producirse cuando un complemento de VSTO genera un error que no hace que la aplicación se cierre inesperadamente. Por ejemplo, una aplicación podría deshabilitar parcialmente un complemento de VSTO si produce una excepción no controlada mientras se ejecuta el controlador de eventos <xref:Microsoft.Office.Tools.AddIn.Startup>. Cuando un complemento de VSTO se deshabilita parcialmente, aparece en la lista **Complementos de aplicación inactivos** de la aplicación, y esta cambia el valor de la entrada del Registro **LoadBehavior** del complemento de VSTO para indicar que no está cargado. Para obtener más información sobre la entrada del Registro **LoadBehavior**, consulte [Entradas del registro para complementos de VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## Solucionar errores de instalación con el Visor de eventos  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] escribe mensajes en el Visor de eventos de Windows para todas las excepciones que se producen cuando se instalan o desinstalan soluciones de Office. Puede utilizar estos mensajes para resolver problemas de implementación y de instalación.  
  
## Solucionar errores de inicio mediante un archivo de registro y mensajes de error  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] puede escribir en un archivo de registro todos los errores que se producen durante el inicio o mostrar cada error en un cuadro de mensaje. Estas opciones están desactivadas de forma predeterminada. Para activarlas, puede crear variables de entorno.  
  
 Si desea mostrar cada error en un cuadro de mensaje, cree una variable de entorno denominada `VSTO_SUPPRESSDISPLAYALERTS` y establézcala en 0 \(cero\). Para suprimir los mensajes, puede eliminar la variable de entorno o establecerla en 1 \(uno\).  
  
 Si desea escribir los errores en un archivo de registro, cree una variable de entorno denominada `VSTO_LOGALERTS` y establézcala en 1 \(uno\).[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] crea el archivo de registro en la carpeta que contiene el manifiesto de implementación del complemento de VSTO o en la carpeta que contiene el documento o libro asociado con la personalización. Si eso no es posible, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] crea el archivo de registro en la carpeta temporal local %TEMP%. Para complementos de VSTO de nivel de aplicación, el nombre predeterminado es *nombre de complemento*.vsto.log. Para los proyectos de nivel de documento, el nombre del archivo de registro es *nombre de documento*.*extensión*.log, por ejemplo, ExcelWorkbook1.xlsx.log. Para detener el registro de errores, elimine la variable de entorno o establézcala en 0 \(cero\).  
  
## Vea también  
 [Compilar soluciones de Office](../vsto/building-office-solutions.md)   
 [Cómo: Volver a habilitar un complemento de VSTO que se ha deshabilitado](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)   
 [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md)  
  
  