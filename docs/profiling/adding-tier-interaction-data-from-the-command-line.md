---
title: Agregar datos de interacción de capas desde la línea de comandos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50e6af91a542c105704a7237d5cd1dcbf8efa2a7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015815"
---
# <a name="add-tier-interaction-data-from-the-command-line"></a>Agregar datos de interacción de capas desde la línea de comandos

La generación de perfiles de interacción de capas proporciona información adicional sobre los tiempos de ejecución de llamadas sincrónicas a [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] en funciones de aplicaciones de varias capas que se comunican con una o más bases de datos.

**Windows 8 y Windows Server 2012**

Para recopilar datos de interacción de capas de aplicaciones de escritorio de Windows 8 o aplicaciones de Windows Server 2012, debe usar el método de instrumentación. No se admite la recopilación de datos de interacción de capas en aplicaciones para UWP.

**Ediciones de Visual Studio**

La generación de perfiles de interacción de capas se puede recopilar con cualquier edición de Visual Studio. Sin embargo, los datos de generación de perfiles de interacción de capas solo se pueden ver en Visual Studio Enterprise.

**Recopilación de datos de TIP en un equipo remoto**

Para recopilar datos de interacción de capas en un equipo remoto, debe copiar el archivo **vs_profiler\_**_\<plataforma>_**\_**_\<lenguaje>_**.exe** de la carpeta _%VSInstallDir%_**\Team Tools\Performance Tools\Setups** de un equipo de Visual Studio en el equipo remoto e instalarlo. Las herramientas de generación de perfiles no se pueden usar en el paquete de descarga de [Depuración remota](../debugger/remote-debugging.md) .

**Informes TIP**

Los datos de interacción de capas solo se pueden ver en Visual Studio Enterprise. Los informes de interacción de capas basados en archivos no están disponibles en [VSPerfReport](../profiling/vsperfreport.md) .

## <a name="add-tier-interaction-data-with-vsperfcmd"></a>Agregar datos de interacción de capas con VSPerfCmd

La herramienta de línea de comandos VSPerfASPNETCmd le permite tener acceso a la funcionalidad completa disponible en las herramientas de generación de perfiles. Para agregar la interacción de capas a los datos de generación de perfiles recopilados mediante VSPerfCmd, debe usar la utilidad **VSPerfCLREnv** para establecer y quitar las variables de entorno que activan los datos de interacción de capas. Las opciones que especifique y los procedimientos necesarios para recopilar datos dependen del tipo de aplicación con que esté generando perfiles.

## <a name="profile-stand-alone-applications"></a>Generación de perfiles de aplicaciones independientes

Para agregar datos de interacción de capas a una aplicación que no se ejecuta por otro proceso, como una aplicación de escritorio de Windows que realiza llamadas sincrónicas [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] a una base de datos de SQL Server, utilice la opción **VSPerfClrEnv /InteractionOn** para establecer las variables de entorno y la opción **VSPerfClrEnv /InteractionOff** para quitarlas.

En el ejemplo siguiente, se generan perfiles para una aplicación de escritorio de Windows mediante el método de instrumentación y se recopilan datos de interacción de capas.

### <a name="profile-a-windows-desktop-application-example"></a>Ejemplo de generación de perfiles para una aplicación de escritorio de Windows

1. Abra una ventana del símbolo del sistema con privilegios de administrador. Haga clic en **Inicio**, seleccione **Todos los programas** y, a continuación, seleccione **Accesorios**. Haga clic con el botón derecho en **Símbolo del sistema** y, a continuación, haga clic en **Ejecutar como administrador**.

2. Inicialice la generación de perfiles de .NET y las variables de entorno de TIP. Escriba los siguientes comandos:

    ```cmd
    vsperfclrenv /traceon
    vsperfclrenv /interactionon
    ```

3. Inicie el generador de perfiles. Escriba el comando siguiente:

    ```cmd
    vsperfcmd /start:trace /output:Desktop_tip.vsp 
    ```

4. Inicie la aplicación con VSPerfCmd. Escriba el comando siguiente:

    ```cmd
    vsperfcmd /launch:DesktopApp.exe
    ```

5. Ejecute la aplicación para recopilar datos de generación de perfiles y, a continuación, ciérrela de la forma habitual.

6. Borre las variables del entorno de TIP. Escriba el comando siguiente:

    ```cmd
    vsperfclrenv /off
    ```

Para obtener más información, vea [Generación de perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md).

## <a name="profile-services"></a>Servicios de generación de perfiles

Para generar perfiles para servicios, incluidas las aplicaciones [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], utilice la opción **VSPerfClrEnv /GlobalInteractionOn** para establecer las variables de entorno y la opción **VSPerfClrEnv /GlobalInteractionOff** para quitarlas.

Cuando genera perfiles para servicios, incluidas las aplicaciones web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], a menudo será necesario reiniciar el equipo para activar la generación de perfiles.

En el ejemplo siguiente, se generan perfiles para un servicio de Windows mediante el método de instrumentación y se recopilan datos de interacción de capas.

### <a name="profile-a-windows-service-example"></a>Ejemplo de generación de perfiles para un servicio de Windows

1. Si es necesario, instale el servicio.

2. Abra una ventana del símbolo del sistema con privilegios de administrador. Haga clic en **Inicio**, seleccione **Todos los programas** y, a continuación, seleccione **Accesorios**. Haga clic con el botón derecho en **Símbolo del sistema** y, a continuación, haga clic en **Ejecutar como administrador**.

3. Inicialice las variables de entorno de generación de perfiles .NET. Escriba el comando siguiente:

    ```cmd
    vsperfclrenv /globaltraceon
    ```

4. Inicialice las variables de entorno de TIP. Escriba el comando siguiente:

    ```cmd
    vsperfclrenv /globalinteractionon
    ```

5. Reinicie el equipo para registrar las variables de entorno.

6. Abra una ventana del símbolo del sistema con privilegios de administrador.

7. Inicie el generador de perfiles. Escriba el comando siguiente:

    ```cmd
    vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession 
    ```

8. Si es necesario, inicie el servicio.

9. Adjunte el generador de perfiles al servicio. Escriba el comando siguiente:

    ```cmd
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession 
    ```

10. Ejecute el servicio y recopile datos de generación de perfiles.

11. Detenga el generador de perfiles. Escriba el comando siguiente:

     `vsperfcmd /detach`

12. Borre las variables de entorno de generación de perfiles de .NET y TIP. Escriba el comando siguiente:

    ```cmd
    vsperfclrenv /globaloff
    ```

13. Reinicie el equipo para registrar las variables de entorno borradas.

Para obtener más información, consulte uno de los temas siguientes:

[Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)

[Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)

## <a name="add-tier-interaction-data-with-vsperfaspnetcmd"></a>Agregar datos de interacción de capas con VSPerfASPNETCmd

La herramienta de línea de comandos VSPerfASPNETCmd le permite generar perfiles fácilmente para aplicaciones web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. En comparación con la herramienta de línea de comandos **VSPerfCmd**, tiene menos opciones, no debe establecerse ninguna variable de entorno y no es necesario reiniciar el equipo. Estas características de VSPerfASPNETCmd hacen que la recopilación de datos de interacción de capas sea extraordinariamente sencilla.

Para agregar la interacción de capas a los datos de generación de perfiles recopilados mediante VSPerfASPNETCmd, agregue la opción **/TIP** de la línea de comandos. Por ejemplo, utilice la siguiente línea de comandos para recopilar datos de interacción de capas para una aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] mediante el método de instrumentación:

```cmd
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp
```

Para obtener más información sobre VSPerfASPNETCmd, vea [Generación rápida de perfiles de sitio web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).