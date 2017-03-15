---
title: "C&#243;mo: Depurar una aplicaci&#243;n de confianza parcial | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurar [Visual Studio], aplicaciones de confianza parcial"
  - "aplicaciones de confianza parcial"
  - "seguridad [Visual Studio], aplicaciones de confianza parcial"
ms.assetid: 9d30ad92-28ce-4b21-91d8-698474cddf64
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Depurar una aplicaci&#243;n de confianza parcial
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se aplica a Windows y aplicaciones de consola.  
  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md) facilita la implementación de aplicaciones de confianza parcial que aprovechan la [Code Access Security](../Topic/Code%20Access%20Security.md) para limitar el acceso a los recursos de un equipo.  
  
 La depuración de una aplicación de confianza parcial puede ser difícil porque estas aplicaciones tienen permisos de seguridad diferentes, por tanto, se comportan de manera diferente según la ubicación desde la que se instalen.  Si una aplicación de confianza parcial se instala desde Internet, tendrá pocos permisos.  Si se instala desde una intranet local, tendrá más permisos; si se instala desde el equipo local, tendrá todos los permisos.  También puede haber zonas personalizadas con permisos personalizados.  Tal vez sea necesario depurar una aplicación de confianza parcial si se cumple alguna de estas condiciones o todas ellas.  Afortunadamente, Visual Studio también facilita esta tarea.  
  
 Antes de iniciar una sesión de depuración en Visual Studio, puede elegir la zona desde la cual simulará que se instaló la aplicación.  Cuando se inicie la depuración, la aplicación tendrá los permisos correspondientes a una aplicación de confianza parcial instalada desde esa zona.  Esto permite ver el comportamiento de la aplicación tal como lo verá un usuario que la descarga desde esa zona.  
  
 Si la aplicación intenta realizar una acción para la cual no tiene permiso, se inicia una excepción.  En ese momento, el Asistente de excepciones de Visual Studio ofrece la opción de agregar un permiso adicional, lo que permite reiniciar la sesión de depuración con permisos suficientes para evitar el problema.  
  
 Después, es posible regresar y ver los permisos agregados durante la depuración.  Si hubo que agregar un permiso durante la depuración, posiblemente haya que agregar una solicitud de consentimiento del usuario en esa parte del código.  
  
> [!NOTE]
>  Los visualizadores del depurador requieren más privilegios de los permitidos por una aplicación de confianza parcial.  Los visualizadores no se cargarán cuando la ejecución se detenga en código con confianza parcial.  Para depurar con un visualizador, debe ejecutar el código con plena confianza.  
  
### Para elegir una zona para la aplicación de confianza parcial  
  
1.  En el menú **Proyecto**, elija **Propiedades de** *Projectname*.  
  
2.  En las páginas de propiedades de *Projectname*, haga clic en la página **Seguridad**.  
  
3.  Seleccione **Habilitar configuración de seguridad de ClickOnce**.  
  
4.  En **Zona desde la que se instalará la aplicación**, haga clic en el cuadro de lista desplegable y elija la zona desde la que desea simular la instalación de la aplicación.  
  
     La cuadrícula **Permisos necesarios para la aplicación** muestra todos los permisos disponibles.  La marca de verificación indica los permisos concedidos a la aplicación.  
  
5.  Si la zona elegida es **\(Personalizado\)**, seleccione la configuración personalizada correcta en la columna **Configuración** de la cuadrícula **Permisos**.  
  
6.  Haga clic en **Aceptar** para cerrar las páginas de propiedades.  
  
### Para agregar un permiso adicional cuando se produce una excepción de seguridad  
  
1.  El cuadro de diálogo **Asistente de excepciones** aparece con un mensaje que indica que no se controló la excepción SecurityException.  
  
2.  En el cuadro de diálogo **Asistente de excepciones**, en **Acciones**, haga clic en **Agregar permisos al proyecto**.  
  
3.  Aparecerá el cuadro de diálogo **Reiniciar depuración**.  
  
    -   Si desea reiniciar la sesión de depuración con el nuevo permiso, haga clic en **Sí**.  
  
    -   Si no desea reiniciar todavía, haga clic en **No**.  
  
### Para ver permisos adicionales agregados durante la depuración  
  
1.  En el menú **Proyecto**, elija **Propiedades de** *Projectname*.  
  
2.  En las páginas de propiedades de *Projectname*, haga clic en la página **Seguridad**.  
  
3.  Examine la cuadrícula **Permisos necesarios para la aplicación**.  Todos los permisos adicionales agregados presentan dos iconos en la columna **Incluido**: la marca de verificación normal que muestran todos los permisos incluidos y otro icono con forma de globo y la letra "i" en su interior.  
  
4.  Utilice la barra de desplazamiento vertical para ver la cuadrícula completa **Permisos necesarios para la aplicación**.  
  
## Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)