---
title: Agregar datos de interacción de capas desde la línea de comandos | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
ms.assetid: 5a35647f-03f2-4555-8eeb-fda7e0080e67
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3912e823a6e6ee32488fcda94616aef414d3d22
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775308"
---
# <a name="adding-tier-interaction-data-from-the-command-line"></a>Agregar datos de interacción de capas desde la línea de comandos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La generación de perfiles de interacción de capas proporciona información adicional sobre los tiempos de ejecución de llamadas sincrónicas a [!INCLUDE[vstecado](../includes/vstecado-md.md)] en funciones de aplicaciones de varias capas que se comunican con una o más bases de datos.  
  
 **Windows 8 y Windows Server 2012**  
  
 Para recopilar datos de interacción de capas de aplicaciones de escritorio de Windows 8 o aplicaciones de Windows Server 2012, debe usar el método de instrumentación. No se admite la recopilación de datos de interacción de capas en aplicaciones de la Tienda Windows.  
  
 **Ediciones de Visual Studio**  
  
 La generación de perfiles de interacción de capas se puede recopilar usando [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] o [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Sin embargo, los datos de generación de perfiles de interacción de capas solo se pueden ver en [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] y [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
 **Recopilación de datos de TIP en un equipo remoto**  
  
 Para recopilar datos de interacción de capas en un equipo remoto, debe copiar el **vs\_profiler\_**_\<plataforma >_ **\_**  _\<Lenguaje >_**.exe** de archivos desde el _% VSInstallDir %_**\Team Tools\Performance Tools\Setups**carpeta de Visual Studio del equipo en el equipo remoto e instalarlo. Las herramientas de generación de perfiles no se pueden usar en el paquete de descarga de [Herramientas remotas para Visual Studio](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) .  
  
 **Informes TIP**  
  
 Los datos de interacción de capas solo se pueden ver en el IDE de [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]. Los informes de interacción de capas basados en archivos a través de [VSPerfReport](../profiling/vsperfreport.md) no están disponibles.  
  
## <a name="adding-tier-interaction-data-with-vsperfcmd"></a>Agregar datos de interacción de capas con VSPerfCmd  
 La herramienta de línea de comandos VSPerfASPNETCmd le permite tener acceso a la funcionalidad completa disponible en las herramientas de generación de perfiles. Para agregar la interacción de capas a los datos de generación de perfiles recopilados mediante VSPerfCmd, debe usar la utilidad **VSPerfCLREnv** para establecer y quitar las variables de entorno que activan los datos de interacción de capas. Las opciones que especifique y los procedimientos necesarios para recopilar datos dependen del tipo de aplicación con que esté generando perfiles.  
  
### <a name="profiling-stand-alone-applications"></a>Generar perfiles para aplicaciones independientes  
 Para agregar datos de interacción de capas a una aplicación que no se ejecuta por otro proceso, como una aplicación de escritorio de Windows que realiza llamadas sincrónicas [!INCLUDE[vstecado](../includes/vstecado-md.md)] a una base de datos de SQL Server, utilice la opción **VSPerfClrEnv /InteractionOn** para establecer las variables de entorno y la opción **VSPerfClrEnv /InteractionOff** para quitarlas.  
  
 En el ejemplo siguiente, se generan perfiles para una aplicación de escritorio de Windows mediante el método de instrumentación y se recopilan datos de interacción de capas.  
  
##### <a name="profiling-a-windows-desktop-application-example"></a>Ejemplo de generación de perfiles para una aplicación de escritorio de Windows  
  
1. Abra una ventana del símbolo del sistema con privilegios de administrador. Haga clic en **Inicio**, seleccione **Todos los programas** y, a continuación, seleccione **Accesorios**. Haga clic con el botón derecho en **Símbolo del sistema** y, a continuación, haga clic en **Ejecutar como administrador**.  
  
2. Inicialice la generación de perfiles de .NET y las variables de entorno de TIP. Escriba los siguientes comandos:  
  
   ```  
   vsperfclrenv /traceon  
   vsperfclrenv /interactionon  
   ```  
  
3. Inicie el generador de perfiles. Escriba el comando siguiente:  
  
   ```  
   vsperfcmd /start:trace /output:Desktop_tip.vsp   
   ```  
  
4. Inicie la aplicación con VSPerfCmd. Escriba el comando siguiente:  
  
   ```  
   vsperfcmd /launch:DesktopApp.exe  
   ```  
  
5. Ejecute la aplicación para recopilar datos de generación de perfiles y, a continuación, ciérrela de la forma habitual.  
  
6. Borre las variables del entorno de TIP. Escriba el comando siguiente:  
  
   ```  
   vsperfclrenv /off  
   ```  
  
   Para obtener más información, consulte [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md).  
  
### <a name="profiling-services"></a>Generar perfiles para servicios  
 Para generar perfiles para servicios, incluidas las aplicaciones [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], utilice la opción **VSPerfClrEnv /GlobalInteractionOn** para establecer las variables de entorno y la opción **VSPerfClrEnv /GlobalInteractionOff** para quitarlas.  
  
 Cuando genera perfiles para servicios, incluidas las aplicaciones web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], a menudo será necesario reiniciar el equipo para activar la generación de perfiles.  
  
 En el ejemplo siguiente, se generan perfiles para un servicio de Windows mediante el método de instrumentación y se recopilan datos de interacción de capas.  
  
##### <a name="profiling-a-windows-service-example"></a>Un ejemplo de generación de perfiles para un servicio de Windows  
  
1. Si es necesario, instale el servicio.  
  
2. Abra una ventana del símbolo del sistema con privilegios de administrador. Haga clic en **Inicio**, seleccione **Todos los programas** y, a continuación, seleccione **Accesorios**. Haga clic con el botón derecho en **Símbolo del sistema** y, a continuación, haga clic en **Ejecutar como administrador**.  
  
3. Inicialice las variables de entorno de generación de perfiles .NET. Escriba el comando siguiente:  
  
   ```  
   vsperfclrenv /globaltraceon  
   ```  
  
4. Inicialice las variables de entorno de TIP. Escriba el comando siguiente  
  
   ```  
   vsperfclrenv /globalinteractionon  
   ```  
  
5. Reinicie el equipo para registrar las variables de entorno.  
  
6. Abra una ventana del símbolo del sistema con privilegios de administrador.  
  
7. Inicie el generador de perfiles. Escriba el comando siguiente:  
  
   ```  
   vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession   
   ```  
  
8. Si es necesario, inicie el servicio.  
  
9. Adjunte el generador de perfiles al servicio. Escriba el comando siguiente:  
  
    ```  
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
10. Ejecute el servicio y recopile datos de generación de perfiles.  
  
11. Detenga el generador de perfiles. Escriba el comando siguiente:  
  
     `vsperfcmd /detach`  
  
12. Borre las variables de entorno de generación de perfiles de .NET y TIP. Escriba el comando siguiente:  
  
    ```  
    vsperfclrenv /globaloff  
    ```  
  
13. Reinicie el equipo para registrar las variables de entorno borradas.  
  
    Para obtener más información, consulte uno de los temas siguientes:  
  
    [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)  
  
    [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)  
  
## <a name="adding-tier-interaction-data-with-vsperfaspnetcmd"></a>Agregar datos de interacción de capas con VSPerfASPNETCmd  
 La herramienta de línea de comandos VSPerfASPNETCmd le permite generar perfiles fácilmente para aplicaciones web de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. En comparación con la herramienta de línea de comandos **VSPerfCmd**, tiene menos opciones, no debe establecerse ninguna variable de entorno y no es necesario reiniciar el equipo. Estas características de VSPerfASPNETCmd hacen que la recopilación de datos de interacción de capas sea extraordinariamente sencilla.  
  
 Para agregar la interacción de capas a los datos de generación de perfiles recopilados mediante VSPerfASPNETCmd, agregue la opción **/TIP** de la línea de comandos. Por ejemplo, utilice la siguiente línea de comandos para recopilar datos de interacción de capas para una aplicación web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] mediante el método de instrumentación:  
  
```  
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp  
```  
  
 Para obtener más información sobre VSPerfASPNETCmd, consulte [Generación rápida de perfiles de sitio web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).



