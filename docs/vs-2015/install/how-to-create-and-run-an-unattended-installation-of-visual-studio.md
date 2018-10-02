---
title: 'Cómo: crear y ejecutar una instalación desatendida de Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing Visual Studio, unattended
- unattended installation, Visual Studio
ms.assetid: 3867b5dc-ed34-4ee2-be32-a42e7e320517
caps.latest.revision: 44
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 3604c43dc3a406c303b3b056fe3b155efe182e77
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579986"
---
# <a name="how-to-create-and-run-an-unattended-installation-of-visual-studio"></a>Cómo: Crear y ejecutar una instalación desatendida de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede ejecutar la aplicación de instalación de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] como instalación desatendida (es decir, silenciosa personalizada) en una intranet en lugar de usar otros medios como, por ejemplo, un DVD. En este tema se describe cómo preparar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para este tipo de instalación desde un recurso compartido de red.  
  
## <a name="creating-a-network-image"></a>Crear una imagen de red  
 Primero, cree una imagen de red de los discos de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
#### <a name="to-create-a-network-image"></a>Para crear una imagen de red  
  
1.  Cree una carpeta en el servidor (por ejemplo, *unidad*: \IDEinstall\\).  
  
2.  Descargar el instalador desde [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015)y, a continuación, ejecute *producto*.exe/Layout *unidad*: \IDEinstall\  
  
3.  Comparta la carpeta IDEinstall en la red y, a continuación, establezca la configuración de seguridad adecuada.  
  
     La ruta de acceso de red de la aplicación de instalación para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] es similar a \\ \\ *ServerName*\IDEinstall\\*producto*.exe.  
  
    > [!NOTE]
    >  En la instalación puede producirse un error si la combinación de ruta de acceso y nombre de archivo supera los 260 caracteres. La longitud máxima de una ruta de acceso en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] es de 221 caracteres.  El nombre de la ruta de acceso local no debe tener más de 70 caracteres y el nombre de la ruta de acceso de red no debe superar los 39 caracteres.  
  
     Instalación también puede producir un error si los nombres de carpeta en la ruta de acceso incluyen espacios incrustados (por ejemplo, "\\\\*ServerName*\IDE install" o \\ \\ *ServerName*\Visual studio\\).  
  
## <a name="deploying-visual-studio-in-unattended-mode"></a>Implementar Visual Studio en modo desatendido  
 Para implementar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en modo desatendido, debe modificar el archivo AdminDeployment.xml. Para ello, primero debe crear el archivo AdminDeployment.xml utilizando el `/CreateAdminFile`  *\<ubicación del archivo >* parámetro de línea de comandos. Luego, puede usar este archivo para situar una implementación de Visual Studio en la red o extraerla en una instalación si coloca ese archivo en el directorio *Unidad*:\IDEinstall\packages. El archivo AdminDeployment.xml no es único para un sistema operativo, una arquitectura, una edición de Visual Studio o un lenguaje del sistema operativo.  
  
> [!CAUTION]
>  A veces, los elementos que aparecen seleccionados en el archivo AdminDeployment.xml no se instalan. Para resolver este problema, coloque los elementos marcados como “Selected="yes"” al **final** del archivo AdminDeployment.xml.  
>   
>  Si no desea instalar las dependencias opcionales de un elemento, debe seleccionar primero el elemento primario y, a continuación, cancelar la selección de las dependencias opcionales después del elemento primario, tal como se muestra en la siguiente captura de pantalla:  
>   
>  ![Elementos de la instalación al final del archivo AdminDeployment.xml](../install/media/vs2015-install-endoffileadmindeploy.PNG "vs2015_Install_EndOfFileAdminDeploy")  
>   
>  Otra manera de hacer esto es simplemente omitir los elementos secundarios opcionales de un elemento primario. En otras palabras, no incluya elementos “Selected=”no””. Sin embargo, aún deberá colocar todos los elementos “Selected=”yes”” al final del archivo AdminDeployment.xml.  
  
> [!IMPORTANT]
>  Durante la instalación, el equipo se puede reiniciar una o más veces automáticamente. Después de que se reinicie, debe iniciar sesión con la misma cuenta de usuario con la que inició sesión para efectuar la instalación antes de reiniciar el equipo. Puede evitar los reinicios automáticos si instala los componentes de requisito previo antes de ejecutar una instalación desatendida. Para obtener más información, vea la sección titulada "Evitar reiniciar durante la instalación" en el [Guía del Administrador de Visual Studio](../install/visual-studio-administrator-guide.md).  
  
 El esquema del archivo AdminDeployment contiene los siguientes elementos:  
  
|Elemento|Atributo|Valores|Descripción|  
|-------------|---------------|------------|-----------------|  
|BundleCustomizations|TargetDir|*Path*|Tiene el mismo comportamiento que reemplazar la ruta de acceso en la interfaz de usuario de la aplicación de instalación. Este elemento se omite si Visual Studio ya está instalado.|  
|BundleCustomizations|NoWeb|Sí&#124;predeterminada|Si el valor de este elemento es yes, la aplicación de instalación nunca intenta ir a la web durante la instalación.|  
|SelectableItemCustomization|Hidden|Sí&#124;n|Si el valor de este elemento es Yes, oculta un elemento seleccionable en el árbol de personalización.|  
|SelectableItemCustomization|Seleccionado|Sí&#124;n|Activa o desactiva un elemento seleccionable en el árbol de personalización.|  
|BundleCustomizations|Fuente|Ruta de acceso|Ubicación de la fuente que el usuario desea usar.  Esta fuente se usa para posteriores operaciones de modificación en la máquina (“Default” de forma predeterminada).|  
|BundleCustomizations|SuppressRefreshPrompt|Sí&#124;predeterminada|Impide que se solicite al usuario que actualice la configuración si hay disponible una más reciente.|  
|BundleCustomizations|NoRefresh|Sí&#124;predeterminada|No actualizará la configuración si hay disponible una versión más reciente.|  
|BundleCustomizations|NoCacheOnlyMode|Sí&#124;predeterminada|Impide que se rellene automáticamente la memoria caché del paquete.|  
  
> [!WARNING]
>  La aplicación de instalación respetará el estado seleccionado de un elemento SelectableItem incluso si está oculto. Por ejemplo, si desea instalar siempre un elemento seleccionable, márquelo como oculto y seleccionado.  
  
#### <a name="to-create-an-unattended-installation-of-visual-studio"></a>Para crear una instalación desatendida de Visual Studio  
  
1.  En el archivo *Unidad*:\IDEinstall\AdminDeployment.xml, cambie el valor del atributo NoWeb del elemento BundleCustomizations de “default” a “yes” tal como se muestra en el siguiente ejemplo:  
  
     Cambiar `<BundleCustomizations TargetDir="default" NoWeb="default"/>` a `<BundleCustomizations TargetDir="default" NoWeb="yes"/>`  
  
2.  Cambie el atributo SelectableItemCustomization según sea necesario para los componentes opcionales y guarde el archivo.  
  
## <a name="running-unattended-setup"></a>Ejecutar una instalación desatendida  
 Para ejecutar la instalación desatendida, puede ejecutar automáticamente la aplicación de instalación de Visual Studio en los equipos cliente o puede permitir que los usuarios ejecuten la aplicación ellos mismos con los valores que usted defina.  
  
#### <a name="to-run-an-unattended-installation-on-a-client-computer"></a>Para ejecutar una instalación desatendida en un equipo cliente  
  
-   Abra el **iniciar** menú, elija **ejecutar**y, a continuación, escriba \\ \\ *ServerName*\IDEinstall\vs_*producto*.exe /adminfile *PathOfTheAdmindeployment.xmlFile**AdditionalParametersAsNeeded*  
  
     Por ejemplo, puede especificar la siguiente línea de comandos: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\ IDEinstall\AdminDeployment.xml /quiet /norestart`  
  
#### <a name="to-enable-clients-to-manually-install-visual-studio-with-pre-defined-settings"></a>Para permitir que los clientes instalen manualmente Visual Studio con valores predefinidos  
  
1.  Copie el archivo personalizado AdminDeployment.xml en un recurso compartido de red que es de solo lectura (por ejemplo, \\ \\ *ServerName*\IDEinstall\packages\AdminDeployment.xml).  
  
2.  Permita a los usuarios instalar desde ese recurso compartido.  
  
## <a name="maintaining-an-installation"></a>Mantener una instalación  
 Si abre **Panel de control** y vuelve a ejecutar la aplicación de instalación, puede modificar las características de Visual Studio, desinstalar lenguajes de programación y reparar o desinstalar Visual Studio.  
  
> [!NOTE]
>  Debe tener credenciales administrativas en el equipo local para poder usar el modo de mantenimiento.  
  
#### <a name="to-maintain-an-installation-on-a-client-computer"></a>Para mantener una instalación en un equipo cliente  
  
-   Abra el **Panel de control**y elija **Programas y características**.  
  
-   Elija [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]y, a continuación, elija **cambio**.  
  
#### <a name="to-change-admindeployment-settings-on-a-client-computer-after-visual-studio-has-been-installed"></a>Para cambiar los valores de AdminDeployment en un equipo cliente una vez instalado Visual Studio  
  
1.  Actualice AdminDeployment.xml cuando sea necesario.  
  
2.  Abra el menú **Iniciar** y, a continuación, elija **Ejecutar**.  
  
3.  Escriba el siguiente texto: \\ \\ *ServerName*\IDEinstall\vs_*producto*.exe /AdminFile PathToAdmindeployment.xml archivo  
  
     AdditionalParametersAsNeeded  
  
     Por ejemplo, puede especificar la siguiente línea de comandos: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\IDEinstall\AdminDeployment.xml /quiet /norestart`  
  
 Repair es el parámetro predeterminado cuando Visual Studio está instalado. Si repara Visual Studio con /AdminFile actualizado, se invalidará la configuración de implementación de administración actual con los que invoca el archivo AdminDeployment.xml actualizado.  
  
## <a name="updating-an-installation"></a>Actualizar una instalación  
 Microsoft ha lanzado varias actualizaciones a Visual Studio 2015. Esta sección explica cómo actualizar la imagen de instalación desatendida de Visual Studio 2015 para que incluya las actualizaciones.  
  
#### <a name="to-update-an-unattended-installation-of-visual-studio"></a>Para actualizar una instalación desatendida de Visual Studio  
  
1.  Busque el archivo de Product.exe en la imagen de red existente, haga clic en él y, a continuación, haga clic en **propiedades**.  
  
2.  Haga clic en el **detalles** pestaña y, a continuación, tome nota de la **versión del producto** propiedad.  
  
     ![Ejemplo de cuadro de diálogo de propiedades en una instalación desatendida de Visual Studio](../install/media/unattended-install-properties-dialog-box.PNG "instalación desatendida: cuadro de diálogo Propiedades")  
  
3.  ###### <a name="if-the-product-version-is-140247200-or-140247201-follow-these-steps"></a>Si la versión del producto es 14.0.24720.0 o 14.0.24720.1, siga estos pasos:  
4.  1.  Ejecute *Product.exe* /Layout *unidad:* \IDEinstall en un equipo que tenga acceso a Internet. (Por ejemplo, ejecute: `vs_enterprise.exe /Layout d:\IDEinstall`.)  
  
    2.  Una vez completada la/Layout, copie la nueva imagen a una nueva ubicación.  
  
    3.  Crear y modificar el archivo AdminDeployment.xml. Para ello, use el `/CreateAdminFile`  *\<ubicación del archivo >* parámetro de línea de comandos. (Para obtener más información, consulte la sección "Deploying Visual Studio en modo desatendido" de este artículo).  
  
    4.  En el equipo cliente, ejecute el siguiente comando para actualizar la copia de Visual Studio que instaló anteriormente: "\\\\*server1*\IDEinstall_Updated_1\\*Product.exe*  /adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart ".  
  
         Por ejemplo, ejecute: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`  
5.  ###### <a name="for-other-product-version-values-follow-these-steps"></a>Para otros valores de versión del producto, siga estos pasos:  
6.  1.  Ejecute *Product.exe* /Layout *unidad:* \IDEinstall en un equipo que tenga acceso a Internet. (Por ejemplo, ejecute `vs-enterprise.exe /Layout d:\IDEinstall`.)  
  
    2.  Una vez completada la/Layout, copie la nueva imagen a una nueva ubicación. (O bien, puede reemplazar la imagen de red existente en su lugar).  
  
    3.  Crear y, a continuación, modifique el archivo AdminDeployment.xml. Para ello, use el `/CreateAdminFile`  *\<ubicación del archivo >* parámetro de línea de comandos. (Para obtener más información, consulte la sección "Deploying Visual Studio en modo desatendido" de este artículo).  
  
    4.  Si copia la imagen a una nueva ubicación, debe ejecutar el comando siguiente en el equipo cliente para actualizar la copia de Visual Studio que instaló anteriormente: "\\\\*server1*\IDEinstall_Updated_1\\ *Product.exe* /adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart ".  
  
         Por ejemplo, ejecute: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`  
  
    5.  Si reemplaza la imagen de red existente, puede ejecutar el comando como se muestra en el paso anterior, o puede hacer lo siguiente:  
  
    6.  1.  Abra el **Panel de control**y elija **Programas y características**.  
  
        2.  Elija **Visual Studio**y, a continuación, elija **cambio**.  
  
        3.  Después de que Visual Studio se inicia en modo de mantenimiento, haga clic en **modificar**.  
  
        4.  La actualización más reciente debe aparecer en la página de características. Seleccione las otras características que desea instalar, haga clic en **siguiente**y, a continuación, haga clic en **actualizar** para instalar la actualización y las nuevas características.  
  
## <a name="registering-the-product"></a>Registrar el producto  
 Una vez completada la instalación, puede registrar la copia de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] desde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
#### <a name="to-register"></a>Para registrarlo  
  
1.  Abra el menú **Ayuda** y, a continuación, elija **Registrar producto**.  
  
2.  Escriba la clave de producto.  
  
     (Para obtener más información, consulte el [Cómo: buscar la clave de producto de Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) y [Cómo: aplicar automáticamente las claves de producto durante la implementación de Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md) temas.)  
  
## <a name="see-also"></a>Vea también  
 [Instalar Visual Studio](../install/install-visual-studio-2015.md)