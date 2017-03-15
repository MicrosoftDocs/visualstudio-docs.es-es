---
title: "C&#243;mo: Crear y ejecutar una instalaci&#243;n desatendida de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instalación de Visual Studio, desatendida"
  - "instalación desatendida, Visual Studio"
ms.assetid: 3867b5dc-ed34-4ee2-be32-a42e7e320517
caps.latest.revision: 44
caps.handback.revision: 32
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# C&#243;mo: Crear y ejecutar una instalaci&#243;n desatendida de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede ejecutar la aplicación de instalación de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] como instalación desatendida \(es decir, silenciosa personalizada\) en una intranet en lugar de usar otros medios como, por ejemplo, un DVD. En este tema, se muestra cómo preparar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para este tipo de instalación desde un recurso compartido de red.  
  
## Crear una imagen de red  
 Primero, cree una imagen de red de los discos de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
#### Para crear una imagen de red  
  
1.  Cree una carpeta en el servidor \(por ejemplo,  *Unidad*:\\IDEinstall\\\).  
  
2.  Realice uno de estos pasos:  
  
    -   Descargue el arranque para web y ejecute *Producto*.exe \/Layout *Unidad*:\\IDEinstall\\.  
  
         O  
  
    -   Copie el contenido de los medios para Visual Studio en la carpeta IDEinstall. Después de copiar el contenido, todavía deberá descargar software de terceros que desee instalar.  
  
3.  Comparta la carpeta IDEinstall en la red y defina la configuración de seguridad adecuada.  
  
     La ruta de acceso de red de la aplicación de instalación de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se parece a \\\\*NombreServidor*\\IDEinstall\\*Producto*.exe.  
  
    > [!NOTE]
    >  En la instalación puede producirse un error si la combinación de ruta de acceso y nombre de archivo supera los 260 caracteres. La longitud máxima de una ruta de acceso en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] es de 221 caracteres.  El nombre de la ruta de acceso local no debe tener más de 70 caracteres y el nombre de la ruta de acceso de red no debe superar los 39 caracteres.  
  
     La instalación también puede producir un error si los nombres de carpeta de la ruta de acceso incluyen espacios incrustados \(por ejemplo, «\\\\*NombreServidor*\\IDE install» o «\\\\*NombreServidor*\\Visual Studio\\\)».  
  
## Implementar Visual Studio en modo desatendido  
 Para implementar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en modo desatendido, debe modificar el archivo AdminDeployment.xml. Para ello, primero debe crear el archivo AdminDeployment.xml con el parámetro de línea de comandos `/CreateAdminFile <ubicación del archivo>`. Luego, puede usar este archivo para situar una implementación de Visual Studio en la red o extraerla en una instalación si coloca ese archivo en el directorio *Unidad*:\\IDEinstall\\packages. El archivo AdminDeployment.xml no es único para un sistema operativo, una arquitectura, una edición de Visual Studio o un lenguaje del sistema operativo.  
  
> [!CAUTION]
>  A veces, los elementos que aparecen seleccionados en el archivo AdminDeployment.xml no se instalan. Para resolver este problema, coloque los elementos marcados como “Selected\="yes"” al **final** del archivo AdminDeployment.xml.  
>   
>  Si no desea instalar las dependencias opcionales de un elemento, debe seleccionar primero el elemento primario y, a continuación, cancelar la selección de las dependencias opcionales después del elemento primario, tal como se muestra en la siguiente captura de pantalla:  
>   
>  ![Elementos de la instalación al final del archivo AdminDeployment.xml](../install/media/vs2015_install_endoffileadmindeploy.png "vs2015\_Install\_EndOfFileAdminDeploy")  
>   
>  Otra manera de hacer esto es simplemente omitir los elementos secundarios opcionales de un elemento primario. En otras palabras, no incluya elementos “Selected\=”no””. Sin embargo, aún deberá colocar todos los elementos “Selected\=”yes”” al final del archivo AdminDeployment.xml.  
  
> [!IMPORTANT]
>  Durante la instalación, el equipo se puede reiniciar una o más veces automáticamente. Después de que se reinicie, debe iniciar sesión con la misma cuenta de usuario con la que inició sesión para efectuar la instalación antes de reiniciar el equipo. Puede evitar los reinicios automáticos si instala los componentes de requisito previo antes de ejecutar una instalación desatendida. Para obtener más información, vea la sección titulada "Evitar el reinicio durante la configuración" en la [Guía del administrador de Visual Studio](../install/visual-studio-administrator-guide.md).  
  
 El esquema del archivo AdminDeployment contiene los siguientes elementos:  
  
|Elemento|Atributo|Valores|Descripción|  
|--------------|--------------|-------------|-----------------|  
|BundleCustomizations|TargetDir|*Ruta de acceso*|Tiene el mismo comportamiento que reemplazar la ruta de acceso en la interfaz de usuario de la aplicación de instalación. Este elemento se omite si Visual Studio ya está instalado.|  
|BundleCustomizations|NoWeb|yes&#124;default|Si el valor de este elemento es yes, la aplicación de instalación nunca intenta ir a la web durante la instalación.|  
|SelectableItemCustomization|Hidden|Yes&#124;No|Si el valor de este elemento es Yes, oculta un elemento seleccionable en el árbol de personalización.|  
|SelectableItemCustomization|Seleccionado|Yes&#124;No|Activa o desactiva un elemento seleccionable en el árbol de personalización.|  
|BundleCustomizations|Fuente|Ruta de acceso|Ubicación de la fuente que el usuario desea usar.  Esta fuente se usa para posteriores operaciones de modificación en la máquina \(“Default” de forma predeterminada\).|  
|BundleCustomizations|SuppressRefreshPrompt|yes&#124;default|Impide que se solicite al usuario que actualice la configuración si hay disponible una más reciente.|  
|BundleCustomizations|NoRefresh|yes&#124;default|No actualizará la configuración si hay disponible una versión más reciente.|  
|BundleCustomizations|NoCacheOnlyMode|yes&#124;default|Impide que se rellene automáticamente la memoria caché del paquete.|  
  
> [!WARNING]
>  La aplicación de instalación respetará el estado seleccionado de un elemento SelectableItem incluso si está oculto. Por ejemplo, si desea instalar siempre un elemento seleccionable, márquelo como oculto y seleccionado.  
  
#### Para crear una instalación desatendida de Visual Studio  
  
1.  En el archivo *Unidad*:\\IDEinstall\\AdminDeployment.xml, cambie el valor del atributo NoWeb del elemento BundleCustomizations de “default” a “yes” tal como se muestra en el siguiente ejemplo:  
  
     Cambiar `<BundleCustomizations TargetDir="default" NoWeb="default"/>` a `<BundleCustomizations TargetDir="default" NoWeb="yes"/>`  
  
2.  Cambie el atributo SelectableItemCustomization según sea necesario para los componentes opcionales y guarde el archivo.  
  
## Ejecutar una instalación desatendida  
 Para ejecutar la instalación desatendida, puede ejecutar automáticamente la aplicación de instalación de Visual Studio en los equipos cliente o puede permitir que los usuarios ejecuten la aplicación ellos mismos con los valores que usted defina.  
  
#### Para ejecutar una instalación desatendida en un equipo cliente  
  
-   Abra el menú **Inicio**, elija **Ejecutar** y escriba `\\ServerName\IDEinstall\vs_Product.exe /adminfile PathOfTheAdmindeployment.xmlFile`*AdditionalParametersAsNeeded*  
  
     Por ejemplo, puede especificar la siguiente línea de comandos: `\\server1\IDEinstall\vs_ultimate.exe /adminfile \\server1\ IDEinstall\AdminDeployment.xml /quiet /norestart`  
  
#### Para permitir que los clientes instalen manualmente Visual Studio con valores predefinidos  
  
1.  Copie el archivo personalizado AdminDeployment.xml en un recurso compartido de red que sea de solo lectura \(por ejemplo, \\\\*NombreServidor*\\IDEinstall\\packages\\AdminDeployment.xml\).  
  
2.  Permita a los usuarios instalar desde ese recurso compartido.  
  
## Mantener una instalación  
 Si abre **Panel de control** y vuelve a ejecutar la aplicación de instalación, puede modificar las características de Visual Studio, desinstalar lenguajes de programación y reparar o desinstalar Visual Studio.  
  
> [!NOTE]
>  Debe tener credenciales administrativas en el equipo local para poder usar el modo de mantenimiento.  
  
#### Para mantener una instalación en un equipo cliente  
  
-   Abra el **Panel de control** y elija **Programas y características**.  
  
-   Elija [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y, después, elija **Cambiar**.  
  
#### Para cambiar los valores de AdminDeployment en un equipo cliente una vez instalado Visual Studio  
  
1.  Actualice AdminDeployment.xml cuando sea necesario.  
  
2.  Abra el menú **Iniciar** y, a continuación, elija **Ejecutar**.  
  
3.  Escriba el siguiente texto:  
  
     `\\ServerName\IDEinstall\vs_Product.exe /AdminFile PathToAdmindeployment.xmlFile` AdditionalParametersAsNeeded  
  
     Por ejemplo, puede especificar la siguiente línea de comandos: `\\server1\IDEinstall\vs_ultimate.exe /adminfile \\server1\IDEinstall\AdminDeployment.xml /quiet /norestart`  
  
 Repair es el parámetro predeterminado cuando Visual Studio está instalado. Si repara Visual Studio con \/AdminFile actualizado, los valores actuales de la implementación de administración se reemplazarán por los que invoque el archivo AdminDeployment.xml actualizado.  
  
## Registrar el producto  
 Una vez completada la instalación, puede registrar la copia de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] desde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
#### Para registrarlo  
  
1.  Abra el menú **Ayuda** y, a continuación, elija **Registrar producto**.  
  
2.  Escriba la clave del producto.  
  
## Vea también  
 [Instalar Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)