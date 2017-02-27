---
title: "C&#243;mo: Establecer los permisos de generaci&#243;n de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "generación de perfiles, establecimiento de permisos"
  - "seguridad [Visual Studio ALM], establecimiento de permisos"
  - "permisos [Visual Studio ALM], generación de perfiles"
  - "herramientas de generación de perfiles, establecimiento de permisos de perfiles"
  - "herramientas de rendimiento, establecimiento de permisos de perfiles"
ms.assetid: 69f27896-8f46-4ef3-bfb7-726d95304f3a
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# C&#243;mo: Establecer los permisos de generaci&#243;n de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tema se describe cómo el administrador de un equipo concede los permisos de seguridad necesarios para generar perfiles a un usuario o grupo que no tiene permisos de administrador en ese equipo.  
  
 Un principio de seguridad básico dice que las aplicaciones deben ejecutarse con los permisos que necesitan y ninguno más.  Este principio también se aplica a los usuarios.  Si los usuarios gozan de plena eficacia cuando inician sesión como miembros del grupo Usuarios en lugar del grupo Administradores, no se les deben conceder permisos de administrador.  En el primer procedimiento, "Crear una cuenta de usuario con permisos de Usuario" se describe cómo crear una cuenta de usuario para un miembro del grupo Usuarios.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Los miembros del grupo Usuarios necesitarán tener acceso a las carpetas y los archivos del disco que se comparten con otros miembros del equipo.  En el segundo procedimiento, "Conceder acceso a los archivos compartidos del proyecto", se describe cómo conceder dicho acceso.  
  
 Los miembros del grupo Usuarios pueden ejecutar las herramientas de generación de perfiles si un administrador les concede acceso al controlador de software para las herramientas de generación de perfiles.  En el último procedimiento, "Conceder acceso al controlador de generación de perfiles", se describe cómo conceder acceso a ese controlador.  
  
> [!NOTE]
>  Se necesitan permisos de administrador para poder seguir los pasos de estos procedimientos.  
  
### Crear una cuenta de usuario con permisos de Usuario  
  
1.  Haga clic con el botón secundario del mouse en **Mi PC** y, a continuación, haga clic en **Administrar**.  
  
     Se abrirá la ventana **Administración de equipos**.  
  
2.  Expanda **Usuarios y grupos locales**.  
  
3.  Haga clic con el botón secundario del mouse en la carpeta **Usuarios** y, a continuación, haga clic en **Usuario nuevo**.  
  
     Aparecerá el cuadro de diálogo **Usuario nuevo**.  
  
4.  Rellene los campos de este cuadro de diálogo con la información correspondiente a la cuenta de usuario que va a crear.  Especifique una contraseña.  Opcionalmente, active la casilla que exige al usuario cambiar la contraseña la siguiente vez que inicie sesión.  
  
5.  Haga clic en **Crear** y después en **Cerrar**.  
  
     El nuevo usuario aparecerá en el grupo Usuarios, un grupo que no tiene permisos de Administrador.  
  
### Conceder acceso a los archivos compartidos del proyecto  
  
1.  En el Explorador de Windows \(o Explorador de archivos\), busque la raíz del árbol de carpetas de los archivos de proyecto utilizados por este usuario y compartidos con el equipo del proyecto.  
  
     La ruta de acceso de esta carpeta será similar a la siguiente:  
  
    ```  
    D:\ourProject  
    ```  
  
2.  Haga clic con el botón secundario del mouse en la carpeta y, a continuación, haga clic en **Propiedades**.  
  
     El cuadro de diálogo de **\<Nombre de carpeta\> Propiedades** aparece.  
  
3.  Haga clic en la ficha **Seguridad**.  
  
4.  Haga clic en el nombre de la cuenta del usuario en el cuadro **Nombres de grupos o usuarios**.  
  
5.  En el cuadro de **Permisos para \<nombre de usuario\>** , active la casilla para **Control total**.  
  
6.  Haga clic en **Aceptar**.  
  
     De esta forma se conceden permisos al usuario para el árbol de carpetas compartidas que comienza por la carpeta seleccionada en el paso 5.  
  
### Conceder acceso al controlador de generación de perfiles  
  
1.  Abra un símbolo del sistema como administrador.  
  
2.  Cambie al directorio:  
  
    ```  
    <drive>:\Program Files\Microsoft Visual Studio 10\Team Tools\Performance Tools  
    ```  
  
3.  Ejecute el siguiente comando:  
  
    ```  
    vsperfcmd /admin:driver,start /admin:service,start  
    ```  
  
     Este comando instala e inicia el controlador correspondiente a las herramientas de generación de perfiles.  
  
     Este comando inicia el controlador y el servicio de generación de perfiles de manera que los usuarios sin permisos de administrador puedan utilizar las características de generación de perfiles disponibles en su espacio de proceso de usuario.  Sólo un administrador puede ejecutar el comando; se produce un error con los usuarios que no tienen permisos administrativos.  
  
     Tenga en cuenta que los efectos de este paso se deshacen al reiniciar el equipo, a menos que también lleve a cabo el último paso del procedimiento.  
  
4.  Ejecute el comando para permitir el acceso a la funcionalidad del controlador de generación de perfiles por parte de un usuario o grupo que no tiene acceso de administrador al equipo:  
  
    ```  
    vsperfcmd /admin:security,allow,<right[,right],<user name|group name>  
    ```  
  
     Este comando concede \<el acceso\> de la cuenta de nombre de usuario\> o \<del nombre de grupo a las herramientas de generación de perfiles.  \<La opción correcta\> determina la funcionalidad que el usuario puede tener acceso.  \<La opción correcta\> puede ser uno o más de los siguientes valores:  
  
    -   FullAccess: permite el acceso a todos los métodos de generación de perfiles, incluyendo la recolección de datos de rendimiento de los servicios, el muestreo y la generación de perfiles entre sesiones.  
  
    -   SampleProfiling: permite al acceso a los métodos de generación de perfiles de muestreo.  
  
    -   CrossSession: permite al acceso a la generación de perfiles entre sesiones que se requiere para los servicios de generación de perfiles.  
  
5.  \(Opcional\) Para conservar los resultados de cualquiera de los pasos anteriores después de reiniciar el equipo, ejecute el comando siguiente:  
  
    ```  
    vsperfcmd /admin:driver,autostart,on  
    ```  
  
 Después de iniciar sesión, los usuarios especificados podrán utilizar las herramientas de generación de perfiles aunque no tengan permisos de administrador.  
  
## Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles y seguridad en Windows Vista](../profiling/profiling-and-windows-vista-security.md)