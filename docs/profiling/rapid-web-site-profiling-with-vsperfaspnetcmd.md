---
title: Generación rápida de perfiles de sitio web con VSPerfASPNETCmd | Microsoft Docs
description: Obtenga más información sobre cómo la herramienta de línea de comandos VSPerfASPNETCmd le permite generar perfiles fácilmente para aplicaciones web de ASP.NET.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a08604b95f49f55a5fea254447046d305d8feff9
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720428"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Generación rápida de perfiles de sitio web con VSPerfASPNETCmd

La herramienta de línea de comandos **VSPerfASPNETCmd** le permite generar perfiles fácilmente para aplicaciones web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. En comparación con la herramienta de línea de comandos [VSPerfCmd](../profiling/vsperfcmd.md), tiene menos opciones, no debe establecerse ninguna variable de entorno y no es necesario reiniciar el equipo. **VSPerfASPNETCmd** es el método preferido para la generación de perfiles con el generador de perfiles independiente. Para obtener más información, vea [Cómo: Instalar el generador de perfiles independiente](../profiling/how-to-install-the-stand-alone-profiler.md).

> [!NOTE]
> Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Vea [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 En algunos escenarios, como la recopilación de datos de simultaneidad o la pausa y reanudación de la generación de perfiles, **VSPerfCmd** es el método preferido de generación de perfiles.

> [!NOTE]
> Para obtener la ruta de acceso a las herramientas de generación de perfiles, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana Símbolo del sistema o agregarla al propio comando.

## <a name="profile-an-aspnet-application"></a>Generar perfiles de una aplicación ASP.NET

Para generar perfiles de una aplicación web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], escriba uno de los comandos descritos en las siguientes secciones. El sitio web se inicia y el generador de perfiles empieza a recopilar datos. Ejecute su aplicación y después cierre el explorador. Para detener la generación de perfiles, presione la tecla **Entrar** en la ventana de símbolo del sistema.

> [!NOTE]
> De forma predeterminada, el símbolo del sistema no se devuelve valores después de un comando **vsperfaspnetcmd**. Puede usar la opción **/nowait** para forzar el símbolo del sistema a devolver valores. Vea [Usar la opción /NoWait](#use-the-nowait-option).

## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Para recopilar estadísticas de aplicación mediante el método de muestreo
 El muestreo es el método predeterminado de generación de perfiles de la herramienta **VSPerfASPNETCmd** y no tiene que especificarse en la línea de comandos. La siguiente línea de comandos recopila estadísticas de aplicación de la aplicación web especificada:

 **vsperfaspnetcmd**  *websiteUrl*

 Un ejemplo de una *websiteUrl* hospedada en un servidor local podría ser *http://localhost/MySite/default.aspx*. Un ejemplo de sitio externo es *http://www.contoso.com* . Para más información, consulte las direcciones URL de ejemplo en [Para generar perfiles de un sitio web sin tener que abrir un proyecto en Visual Studio](how-to-collect-performance-data-for-a-web-site.md#to-profile-a-web-site-without-opening-a-project-in-visual-studio).

## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Para recopilar datos de intervalos mediante el método de instrumentación

Use la siguiente línea de comandos para recopilar datos detallados de intervalos de una aplicación web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilada dinámicamente:

**vsperfaspnetcmd /trace**  *websiteUrl*

Si quiere generar perfiles de archivos .*dll* compilados de forma estática en la aplicación web, debe instrumentar los archivos mediante el uso de la herramienta de línea de comandos [VSInstr](../profiling/vsinstr.md). El comando vsperfaspnetcmd /trace incluirá datos de los archivos instrumentados.

## <a name="to-collect-net-memory-data"></a>Para recopilar datos de memoria de .NET

La opción **/Memory** recopila datos acerca de la asignación de objetos de memoria de .NET y puede recopilar datos sobre la duración de dichos objetos. La recopilación de datos de asignación es el modo predeterminado de la opción de datos **/Memory** y no tiene que especificarse en la línea de comandos.

 **vsperfaspnetcmd /memory** *websiteUrl*

 Utilice el parámetro **Lifetime** para recopilar datos de duración del objeto además a los datos de asignación:

 **vsperfaspnetcmd /memory:lifetime** *websiteUrl*

 También puede utilizar la opción **/Trace** para incluir información de tiempo detallada con los datos de memoria de .NET:

 **vsperfaspnetcmd /memory**[**:lifetime**] **/trace**`websiteUrl`

## <a name="to-collect-tier-interaction-data"></a>Para recopilar datos de interacción de capas

> [!WARNING]
> Los datos de generación de perfiles de interacción de capas (TIP) se pueden recopilar con cualquier edición de Visual Studio. Sin embargo, los datos de generación de perfiles de interacción de capas solo se pueden ver en Visual Studio Enterprise.
>
> Para recopilar datos de TIP en Windows 8 o Windows Server 2012, debe usar la opción de instrumentación (**/trace**).

Para recopilar datos de interacción de capas con datos de muestreo:

**vsperfaspnetcmd /tip** `websiteUrl`

Para recopilar datos de interacción de capas con datos de instrumentación:

**vsperfaspnetcmd /trace /tip** *websiteUrl*

Para recopilar datos de interacción de capas con datos de memoria de .NET:

**vsperfaspnetcmd /memory**[**:lifetime**] **/tip**_websiteUrl_

## <a name="use-the-nowait-option"></a>Usar la opción /NoWait

De forma predeterminada, el símbolo del sistema no se devuelve valores después de un comando **vsperfaspnetcmd**. Puede usar la siguiente opción de sintaxis para forzar el símbolo del sistema a devolver valores. Después, puede realizar otras operaciones en la ventana de símbolo del sistema. Para finalizar la generación de perfiles, use la opción **/shutdown** en un comando **vsperfaspnetcmd** separado.

Para iniciar la generación de perfiles:

**vsperfaspnetcmd** [*/Options*] **/nowait**_websiteUrl_

Para finalizar la generación de perfiles:

**vsperfaspnetcmd /shutdown** *websiteUrl*

## <a name="additional-options"></a>Opciones adicionales

Puede agregar cualquiera de las siguientes opciones para los comandos enumerados anteriormente en esta sección, excepto el comando **vsperfaspnetcmd /shutdown**.

|Opción|Descripción|
|------------|-----------------|
|**/Output:** `VspFile`|De forma predeterminada, el archivo de datos de generación de perfiles (.*vsp*) se crea en el directorio actual con el nombre de archivo **PerformanceReport.vsp**. Utilice la opción /output para cambiar la ubicación, el nombre de archivo o ambos.|
|**/PackSymbols:Off**|De forma predeterminada, VsPerfASPNETCmd inserta símbolos (nombres de función y parámetro, etc.) en el archivo .*vsp*. Incrustar los símbolos puede hacer que el archivo de datos de generación de perfiles sea muy grande. Si va a acceder a los archivos .*pdb* que contienen los símbolos al analizar los datos, use la opción /packsymbols:off para deshabilitar la inserción de los símbolos.|
