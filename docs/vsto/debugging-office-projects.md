---
title: Depurar proyectos de Office
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8b48335ccaa8bd21cf9f6e108d043ecf706903bb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441880"
---
# <a name="debug-office-projects"></a>Depurar proyectos de Office
  Puede depurar proyectos de Office con las mismas herramientas de Microsoft [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] que usa para otros proyectos de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Las características del depurador[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , como la capacidad para insertar puntos de interrupción y ver variables en la ventana **Variables locales** , también están disponibles cuando se depuran proyectos de Office. Para obtener más información acerca de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] las herramientas de depuración, consulte [depurar en Visual Studio](../debugger/debugging-in-visual-studio.md).

> [!TIP]
> Para simplificar la depuración, cierre todas las instancias abiertas de la aplicación de Office antes de compilarla y depurarla.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

> [!NOTE]
> ¿Está interesado en desarrollar soluciones que amplían la experiencia de Office a través de [varias plataformas](https://dev.office.com/add-in-availability)? Visite el nuevo [modelo de complementos de Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Complementos de Office tienen una superficie pequeña en comparación con las soluciones y complementos VSTO, y puede crearlas con prácticamente cualquier tecnología, como HTML5, CSS3, JavaScript y XML de programación web.

## <a name="start-and-stop-the-debugger"></a>Iniciar y detener el depurador
 Puede comenzar a depurar un proyecto de Office tal y como inicia la depuración de otros [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proyectos; por ejemplo, puede presionar la **F5** clave. Al iniciar la depuración de un proyecto de complemento VSTO, se inicia un nuevo proceso para la aplicación de Office de destino y se carga el complemento de VSTO.

 Al iniciar la depuración de un proyecto de nivel de documento, el documento o libro se abre en un nuevo proceso de Word o Excel.

 Cuando se detiene el depurador, este finaliza el proceso de aplicación repentinamente o, si lo tiene configurado para desasociarse, el depurador se desasocia. También se cierran sin previo aviso todos los documentos que estuvieran abiertos en el proceso de aplicación de Office finalizado y se pierden los cambios no guardados. Esto puede incluir todos los documentos o libros que estén abiertos mientras se ejecuta el depurador.

 Normalmente, antes de detener el depurador es mejor desasociarlo del proceso para poder salir de la aplicación de Office de la forma normal. También puede desasociarlo antes del proceso si desea seguir trabajando con un documento u hoja de cálculo abiertos después de detener al depurador.

 Si está depurando una personalización de nivel de documento para Word, detener el depurador y hacer que Word se cierre repentinamente una y otra vez puede dañar la plantilla Normal. Si esto ocurre, puede eliminar la plantilla Normal dañada y ésta se volverá a crear automáticamente la próxima vez que abra Word. Sin embargo, las macros que se hayan almacenado en la plantilla Normal no se volverán a crear.

### <a name="debug-office-2013-vsto-add-ins-by-using-either-office-2013-or-office-2016"></a>Depurar complementos de VSTO de Office 2013 con Office 2013 u Office 2016
 Si usa Visual Studio 2015 y tiene ambas versiones de Office instalado side-by-side, Visual Studio inicia Office 2016. Si usa Visual Studio 2013, Visual Studio inicia Office 2013.

 Si desea depurar el complemento de VSTO empleando una versión diferente de Office (2013 o 2016), abra el **Diseñador de proyectos**y, en la ficha **Depurar** , elija el botón de opción **Iniciar programa externo** . A continuación, busque la ubicación del ejecutable de la aplicación de Office apropiada.

## <a name="f10-and-f11-behavior"></a>Comportamiento de F10 y F11
 Al iniciar la depuración de un proyecto de Office, **F10** y **F11** no tiene el mismo comportamiento que al comenzar la depuración de otros proyectos de Visual Basic o C#. En los proyectos de Visual Basic o C#, el depurador se detiene en la función principal; en los proyectos de Office, Visual Studio no tiene control sobre la función principal de la aplicación de Office. Sin embargo, durante la depuración, **F10** y **F11** tiene las mismas funciones que en los proyectos de Visual Basic y C#.

## <a name="display-exceptions"></a>Mostrar excepciones
 Debido al modo en que el código administrado interactúa con el código no administrado, Visual Studio no muestra los errores que producen las aplicaciones de Microsoft Office. Por ejemplo, si un complemento VSTO creado mediante el uso de herramientas de desarrollo de Office en Visual Studio produce una excepción, la aplicación de Microsoft Office continúa sin mostrar ningún error. Para ver estos errores, configure el depurador para que se interrumpa al aparecer excepciones de Common Language Runtime. Para obtener más información, consulte [administrar excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md).

 Si configura el depurador para que se detenga al aparecer excepciones de Common Language Runtime, el depurador se interrumpirá con todas las excepciones, tanto las que se han controlado como algunas excepciones de primera oportunidad del tiempo de ejecución, que podrían no ser pertinentes para el proyecto. En todos los proyectos aparecen errores relacionados con msosec no encontrado, pero son seguros omitir. Las excepciones de msosec no afectarán a la solución.

 También puede utilizar instrucciones **Try...Catch** en torno a sus métodos para detectar excepciones.

 De forma predeterminada, Visual Studio tampoco muestra errores de depuración de Just-In-Time para proyectos de Office. Sin embargo, puede habilitar esta característica para ver los errores que se produzcan. Para obtener más información, consulte [en Visual Studio la depuración Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md).

## <a name="command-line-arguments"></a>Argumentos de la línea de comandos
 Si el **acción de inicio** en el **depurar** página de propiedad se establece en **Iniciar proyecto**, Visual Studio no utiliza argumentos de línea de comandos al depurar el proyecto, incluso si tiene Especifica los argumentos de línea de comandos como opciones de inicio. Si desea utilizar argumentos de línea de comandos al iniciar la depuración, debe seleccionar un **acción de inicio** distinto **Iniciar proyecto**.

## <a name="source-control"></a>Control de código fuente
 Las propiedades de depuración no se comparten entre varios usuarios cuando se trabaja con control de código fuente. Los proyectos de Visual Basic y C# almacenan las propiedades de depuración en un archivo específico de cada usuario (*NombredeProyecto*.vbproj.user o *NombredeProyecto*.csproj.user), y este archivo no está bajo control de código fuente. Si hay más de una persona depurando, cada una debe introducir manualmente las propiedades de depuración.

## <a name="debug-cached-datasets-in-a-document-level-project"></a>Depurar conjuntos de datos en caché en un proyecto de nivel de documento
 Cada vez que se compila un proyecto, el conjunto de datos se vacía y se vuelve a crear. Si desea depurar un conjunto de datos en caché, debe abrir el documento fuera de Visual Studio y, a continuación, asociar el depurador.

## <a name="debug-word-document-projects-based-on-the-word-97-2003-document-doc-format"></a>Depurar proyectos de documento de Word basados en el documento de Word 97-2003 (* .doc) formato
 Para depurar un proyecto de documento de Word basado en el documento de Word 97-2003 (*/*.doc *) formato, debe agregar la carpeta del proyecto a la lista de carpetas de confianza. Para obtener más información sobre cómo hacerlo, consulte [conceder confianza a los documentos](../vsto/granting-trust-to-documents.md).

## <a name="debug-disabled-add-ins"></a>Complementos de depuración deshabilitada
 Las aplicaciones de Microsoft Office pueden deshabilitar los complementos de VSTO que se comporten de forma inesperada. La aplicación de Microsoft Office deshabilita los complementos de VSTO para evitar que se cargue código problemático cada vez que se inicie la aplicación. Sin embargo, esto también puede producir un comportamiento inesperado durante la depuración típica. Para obtener información acerca de cómo volver a habilitar los complementos de VSTO, consulte [Cómo: Volver a habilitar un complemento de VSTO que se ha deshabilitado](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md).

 Las aplicaciones de Microsoft Office usan dos tipos de deshabilitación para los complementos de VSTO: deshabilitación total y deshabilitación parcial.

### <a name="hard-disabling"></a>La deshabilitación
 Deshabilitación total puede producirse cuando un complemento VSTO hace que la aplicación se cierre inesperadamente. También puede ocurrir en el equipo de desarrollo si detiene el depurador mientras se está ejecutando el controlador de eventos <xref:Microsoft.Office.Tools.AddIn.Startup> en el complemento de VSTO. Cuando un complemento de VSTO se deshabilita totalmente, aparece en el **elementos deshabilitados** lista en la aplicación.

 Si una aplicación de Office de disco dura deshabilita un complemento VSTO creado mediante el uso de herramientas de desarrollo de Office en Visual Studio, la aplicación deshabilita únicamente el complemento VSTO que produjo el error. Los demás complementos de VSTO creados con las herramientas de desarrollo de Office en Visual Studio para esa aplicación de Office continuarán cargándose.

### <a name="soft-disabling"></a>La deshabilitación parcial
 La deshabilitación parcial puede producirse cuando un complemento de VSTO genera un error que no hace que la aplicación se cierre inesperadamente. Por ejemplo, una aplicación podría deshabilitar parcialmente un complemento de VSTO si produce una excepción no controlada mientras se ejecuta el controlador de eventos <xref:Microsoft.Office.Tools.AddIn.Startup> . Cuando un complemento de VSTO se deshabilita parcialmente, aparece en el **complementos de aplicación inactivos** lista en la aplicación y la aplicación cambia el valor de la **LoadBehavior** entrada del registro para el complemento de VSTO para indicar que no está cargado. Para obtener más información sobre la **LoadBehavior** entrada del registro, consulte [entradas del registro para complementos VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

## <a name="troubleshoot-installation-errors-by-using-the-event-viewer"></a>Solucionar errores de instalación mediante el Visor de eventos
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] escribe mensajes en el Visor de eventos de Windows para todas las excepciones que se producen cuando se instalan o desinstalan soluciones de Office. Puede utilizar estos mensajes para resolver problemas de implementación y de instalación.

## <a name="troubleshoot-startup-errors-by-using-a-log-file-and-error-messages"></a>Solución de problemas de errores de inicio mediante el uso de un mensajes de error y de archivo de registro
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] puede escribir en un archivo de registro todos los errores que se producen durante el inicio o mostrar cada error en un cuadro de mensaje. Estas opciones están desactivadas de forma predeterminada. Puede activar las opciones mediante la creación de variables de entorno.

 Si desea mostrar cada error en un cuadro de mensaje, cree una variable de entorno denominada `VSTO_SUPPRESSDISPLAYALERTS` y establézcala en 0 (cero). Para suprimir los mensajes, puede eliminar la variable de entorno o establecerla en 1 (uno).

 Si desea escribir los errores en un archivo de registro, cree una variable de entorno denominada `VSTO_LOGALERTS` y establézcala en 1 (uno). [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] crea el archivo de registro en la carpeta que contiene el manifiesto de implementación del complemento de VSTO o en la carpeta que contiene el documento o libro asociado con la personalización. Si se produce un error, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] crea el archivo de registro local *% TEMP %* carpeta. Para complementos de VSTO de nivel de aplicación, el nombre predeterminado es *nombre de complemento*.vsto.log. Para los proyectos de nivel de documento, el nombre del archivo de registro es *nombre de documento*.*extensión*.log, por ejemplo, ExcelWorkbook1.xlsx.log. Para detener el registro de errores, elimine la variable de entorno o establézcala en 0 (cero).

## <a name="see-also"></a>Vea también

- [Compilar soluciones de Office](../vsto/building-office-solutions.md)
- [Cómo: Volver a habilitar un complemento de VSTO que se ha deshabilitado](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)
- [Programar complementos VSTO](../vsto/programming-vsto-add-ins.md)