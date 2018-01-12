---
title: Depurar proyectos de Office | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel projects [Office development in Visual Studio], debugging
- Word projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], debugging
- debugging [Office development in Visual Studio], Outlook projects
- Office projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], projects
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c3a3b4d3eebd5b20c4e9eb56b30a8980ceafb8bf
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="debugging-office-projects"></a>Depurar proyectos de Office
  Puede depurar proyectos de Office con las mismas herramientas de Microsoft [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] que usa para otros proyectos de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Las características del depurador[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , como la capacidad para insertar puntos de interrupción y ver variables en la ventana **Variables locales** , también están disponibles cuando se depuran proyectos de Office. Para más información sobre las herramientas de depuración [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , vea [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
> [!TIP]  
>  Para simplificar la depuración, cierre todas las instancias abiertas de la aplicación de Office antes de compilarla y depurarla.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  ¿Está interesado en el desarrollo de soluciones que amplían la experiencia de Office en [varias plataformas](https://dev.office.com/add-in-availability)? Visite la nueva [modelo de complementos de Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Complementos de Office tienen una superficie pequeña en comparación con las soluciones y complementos VSTO, y puede compilarlas mediante prácticamente cualquier tecnología, como HTML5, JavaScript, CSS3 y XML de programación web.  
  
## <a name="starting-and-stopping-the-debugger"></a>Iniciar y detener el depurador  
 Puede comenzar a depurar un proyecto de Office tal y como inicia la depuración de otros proyectos de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ; por ejemplo, presionando la tecla F5. Al iniciar la depuración de un proyecto de complemento de VSTO, se inicia un nuevo proceso para la aplicación de Office de destino y se carga el complemento de VSTO.  
  
 Al iniciar la depuración de un proyecto de nivel de documento, el documento o libro se abre en un nuevo proceso de Word o Excel.  
  
 Cuando se detiene el depurador, este finaliza el proceso de aplicación repentinamente o, si lo tiene configurado para desasociarse, el depurador se desasocia. También se cierran sin previo aviso todos los documentos que estuvieran abiertos en el proceso de aplicación de Office finalizado y se pierden los cambios no guardados. Esto puede incluir todos los documentos o libros que estén abiertos mientras se ejecuta el depurador.  
  
 Normalmente, antes de detener el depurador es mejor desasociarlo del proceso para poder salir de la aplicación de Office de la forma normal. También puede desasociarlo antes del proceso si desea seguir trabajando con un documento u hoja de cálculo abiertos después de detener al depurador.  
  
 Si está depurando una personalización de nivel de documento para Word, detener el depurador y hacer que Word se cierre repentinamente una y otra vez puede dañar la plantilla Normal. Si esto ocurre, puede eliminar la plantilla Normal dañada y ésta se volverá a crear automáticamente la próxima vez que abra Word. Sin embargo, las macros que se hayan almacenado en la plantilla Normal no se volverán a crear.  
  
### <a name="debug-office-2013-vsto-add-ins-by-using-either-office-2013-or-office-2016"></a>Depurar complementos de VSTO de Office 2013 con Office 2013 u Office 2016  
 Si usa Visual Studio 2015 y tiene ambas versiones de Office instaladas en paralelo, Visual Studio inicia Office 2016. Si usa Visual Studio 2013, Visual Studio inicia Office 2013.  
  
 Si desea depurar el complemento de VSTO empleando una versión diferente de Office (2013 o 2016), abra el **Diseñador de proyectos**y, en la ficha **Depurar** , elija el botón de opción **Iniciar programa externo** . A continuación, busque la ubicación del ejecutable de la aplicación de Office apropiada.  
  
## <a name="f10-and-f11-behavior"></a>Comportamiento de F10 y F11  
 Al iniciar la depuración de un proyecto de Office, F10 y F11 no tienen el mismo comportamiento que al iniciar la depuración de otros proyectos de Visual Basic o C#. En los proyectos de Visual Basic o C#, el depurador se detiene en la función principal; en los proyectos de Office, Visual Studio no tiene control sobre la función principal de la aplicación de Office. Sin embargo, durante la depuración, F10 y F11 tienen las mismas funciones que en los proyectos de Visual Basic y C#.  
  
## <a name="displaying-exceptions"></a>Mostrar excepciones  
 Debido al modo en que el código administrado interactúa con el código no administrado, Visual Studio no muestra los errores que producen las aplicaciones de Microsoft Office. Por ejemplo, si un complemento de VSTO creado con las herramientas de desarrollo de Office en Visual Studio produce una excepción, la aplicación de Microsoft Office continúa sin mostrar ningún error. Para ver estos errores, configure el depurador para que se interrumpa al aparecer excepciones de Common Language Runtime. Para obtener más información, consulte [administrar excepciones con el depurador](/visualstudio/debugger/managing-exceptions-with-the-debugger).  
  
 Si configura el depurador para que se detenga al aparecer excepciones de Common Language Runtime, el depurador se interrumpirá con todas las excepciones, tanto las que se han controlado como algunas excepciones de primera oportunidad del tiempo de ejecución, que podrían no ser pertinentes para el proyecto. En todos los proyectos aparecen errores relacionados con msosec no encontrado, pero son seguros omitir. Las excepciones de msosec no afectarán a la solución.  
  
 También puede utilizar instrucciones **Try...Catch** en torno a sus métodos para detectar excepciones.  
  
 De forma predeterminada, Visual Studio tampoco muestra errores de depuración de Just-In-Time para proyectos de Office. Sin embargo, puede habilitar esta característica para ver los errores que se produzcan. Para obtener más información, consulte [depuración Just en Visual Studio](/visualstudio/debugger/just-in-time-debugging-in-visual-studio).  
  
## <a name="command-line-arguments"></a>Argumentos de la línea de comandos  
 Si la **Acción de inicio** de la página de propiedades **Depurar** se establece en **Iniciar proyecto**, Visual Studio no utiliza argumentos de línea de comandos al depurar el proyecto, incluso aunque haya especificado argumentos de línea de comandos como opciones de inicio. Si desea utilizar argumentos de línea de comandos al iniciar la depuración, debe seleccionar una **Acción de inicio** distinta de **Iniciar proyecto**.  
  
## <a name="source-control"></a>Control de código fuente  
 Las propiedades de depuración no se comparten entre varios usuarios cuando se trabaja con control de código fuente. Los proyectos de Visual Basic y C# almacenan las propiedades de depuración en un archivo específico de cada usuario (*NombredeProyecto*.vbproj.user o *NombredeProyecto*.csproj.user), y este archivo no está bajo control de código fuente. Si hay más de una persona depurando, cada una debe introducir manualmente las propiedades de depuración.  
  
## <a name="debugging-cached-datasets-in-a-document-level-project"></a>Depurar conjuntos de datos en caché en un proyecto de nivel de documento  
 Cada vez que se compila un proyecto, el conjunto de datos se vacía y se vuelve a crear. Si desea depurar un conjunto de datos en caché, debe abrir el documento fuera de Visual Studio y, a continuación, asociar el depurador.  
  
## <a name="debugging-word-document-projects-based-on-the-word-97-2003-document-doc-format"></a>Depurar proyectos de documento de Word basados en el formato de documento de Word 97-2003 (*.doc)  
 Para depurar un proyecto de documento de Word basado en el formato de documento de Word 97-2003 (*.doc), debe agregar la carpeta del proyecto a la lista de carpetas de confianza. Para obtener más información sobre cómo realizar esta operación, vea [Granting Trust to Documents](../vsto/granting-trust-to-documents.md).  
  
## <a name="debugging-disabled-add-ins"></a>Depurar complementos deshabilitados  
 Las aplicaciones de Microsoft Office pueden deshabilitar los complementos de VSTO que se comporten de forma inesperada. La aplicación de Microsoft Office deshabilita los complementos de VSTO para evitar que se cargue código problemático cada vez que se inicie la aplicación. Sin embargo, esto también puede producir un comportamiento inesperado durante la depuración típica. Para obtener información acerca de cómo volver a habilitar los complementos de VSTO, consulte [Cómo: volver a habilitar un VSTO Add-in That Has Been Disabled](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md).  
  
 Las aplicaciones de Microsoft Office usan dos tipos de deshabilitación para los complementos de VSTO: deshabilitación total y deshabilitación parcial.  
  
### <a name="hard-disabling"></a>Deshabilitación total  
 La deshabilitación total puede producirse cuando un complemento de VSTO hace que la aplicación se cierre inesperadamente. También puede ocurrir en el equipo de desarrollo si detiene el depurador mientras se está ejecutando el controlador de eventos <xref:Microsoft.Office.Tools.AddIn.Startup> en el complemento de VSTO. Cuando un complemento de VSTO se deshabilita totalmente, aparece en la lista **Elementos deshabilitados** de la aplicación.  
  
 Si una aplicación de Office deshabilita totalmente un complemento de VSTO creado con las herramientas de desarrollo de Office en Visual Studio, la aplicación deshabilita únicamente el complemento de VSTO que produjo el error. Los demás complementos de VSTO creados con las herramientas de desarrollo de Office en Visual Studio para esa aplicación de Office continuarán cargándose.  
  
### <a name="soft-disabling"></a>Deshabilitación parcial  
 La deshabilitación parcial puede producirse cuando un complemento de VSTO genera un error que no hace que la aplicación se cierre inesperadamente. Por ejemplo, una aplicación podría deshabilitar parcialmente un complemento de VSTO si produce una excepción no controlada mientras se ejecuta el controlador de eventos <xref:Microsoft.Office.Tools.AddIn.Startup> . Cuando un complemento de VSTO se deshabilita parcialmente, aparece en la lista **Complementos de aplicación inactivos** de la aplicación, y esta cambia el valor de la entrada del Registro **LoadBehavior** del complemento de VSTO para indicar que no está cargado. Para obtener más información sobre la **LoadBehavior** entrada del registro, consulte [entradas del registro para complementos VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## <a name="troubleshooting-installation-errors-by-using-the-event-viewer"></a>Solucionar errores de instalación con el Visor de eventos  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] escribe mensajes en el Visor de eventos de Windows para todas las excepciones que se producen cuando se instalan o desinstalan soluciones de Office. Puede utilizar estos mensajes para resolver problemas de implementación y de instalación.  
  
## <a name="troubleshooting-startup-errors-by-using-a-log-file-and-error-messages"></a>Solucionar errores de inicio mediante un archivo de registro y mensajes de error  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] puede escribir en un archivo de registro todos los errores que se producen durante el inicio o mostrar cada error en un cuadro de mensaje. Estas opciones están desactivadas de forma predeterminada. Para activarlas, puede crear variables de entorno.  
  
 Si desea mostrar cada error en un cuadro de mensaje, cree una variable de entorno denominada `VSTO_SUPPRESSDISPLAYALERTS` y establézcala en 0 (cero). Para suprimir los mensajes, puede eliminar la variable de entorno o establecerla en 1 (uno).  
  
 Si desea escribir los errores en un archivo de registro, cree una variable de entorno denominada `VSTO_LOGALERTS` y establézcala en 1 (uno). [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] crea el archivo de registro en la carpeta que contiene el manifiesto de implementación del complemento de VSTO o en la carpeta que contiene el documento o libro asociado con la personalización. Si eso no es posible, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] crea el archivo de registro en la carpeta temporal local %TEMP%. Para complementos de VSTO de nivel de aplicación, el nombre predeterminado es *nombre de complemento*.vsto.log. Para los proyectos de nivel de documento, el nombre del archivo de registro es *nombre de documento*.*extensión*.log, por ejemplo, ExcelWorkbook1.xlsx.log. Para detener el registro de errores, elimine la variable de entorno o establézcala en 0 (cero).  
  
## <a name="see-also"></a>Vea también  
 [Compilar soluciones de Office](../vsto/building-office-solutions.md)   
 [Cómo: volver a habilitar un complemento de VSTO que se ha deshabilitado](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)  
  
  