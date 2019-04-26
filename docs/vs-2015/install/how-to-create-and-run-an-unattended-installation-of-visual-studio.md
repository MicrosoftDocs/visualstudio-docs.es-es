---
title: 'Procedimiento: Creación y ejecución de una instalación desatendida | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- installing Visual Studio, unattended
- unattended installation, Visual Studio
ms.assetid: 3867b5dc-ed34-4ee2-be32-a42e7e320517
caps.latest.revision: 44
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 26e059d4fdc8eadd422924dd6bbda6f7c945ccfb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433051"
---
# <a name="how-to-create-and-run-an-unattended-installation-of-visual-studio"></a>Cómo: Crear y ejecutar una instalación desatendida de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede ejecutar la aplicación de instalación de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] como instalación desatendida (es decir, silenciosa personalizada) en una intranet en lugar de usar otros medios como, por ejemplo, un DVD. En este tema se describe cómo preparar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para este tipo de instalación desde un recurso compartido de red.

## <a name="creating-a-network-image"></a>Crear una imagen de red
 Primero, cree una imagen de red de los discos de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

#### <a name="to-create-a-network-image"></a>Para crear una imagen de red

1. Cree una carpeta en el servidor (por ejemplo, *Unidad*:\IDEinstall\\).

2. Descargue el instalador desde [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) y, luego, ejecute *Product*.exe /Layout *Unidad*:\IDEinstall\.

3. Comparta la carpeta IDEinstall en la red y, luego, defina la configuración de seguridad adecuada.

     La ruta de acceso de red de la aplicación de instalación de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se parece a \\\\*ServerName*\IDEinstall\\*Product*.exe.

    > [!NOTE]
    > En la instalación puede producirse un error si la combinación de ruta de acceso y nombre de archivo supera los 260 caracteres. La longitud máxima de una ruta de acceso en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] es de 221 caracteres.  El nombre de la ruta de acceso local no debe tener más de 70 caracteres y el nombre de la ruta de acceso de red no debe superar los 39 caracteres.

     La instalación también puede producir un error si los nombres de carpeta de la ruta de acceso incluyen espacios insertados (por ejemplo, "\\\\*ServerName*\IDE install" o \\\\*ServerName*\Visual Studio\\).

## <a name="deploying-visual-studio-in-unattended-mode"></a>Implementar Visual Studio en modo desatendido
 Para implementar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en modo desatendido, debe modificar el archivo AdminDeployment.xml. Para ello, primero debe crear el archivo AdminDeployment.xml con el parámetro de línea de comandos `/CreateAdminFile` *\<ubicación del archivo>*. Luego, puede usar este archivo para situar una implementación de Visual Studio en la red o extraerla en una instalación si coloca ese archivo en el directorio *Unidad*:\IDEinstall\packages. El archivo AdminDeployment.xml no es único para un sistema operativo, una arquitectura, una edición de Visual Studio o un lenguaje del sistema operativo.

> [!CAUTION]
> A veces, los elementos que aparecen seleccionados en el archivo AdminDeployment.xml no se instalan. Para resolver este problema, coloque los elementos marcados como “Selected="yes"” al **final** del archivo AdminDeployment.xml.
>
> Si no desea instalar las dependencias opcionales de un elemento, debe seleccionar primero el elemento primario y, a continuación, cancelar la selección de las dependencias opcionales después del elemento primario, tal como se muestra en la siguiente captura de pantalla:
>
> ![Elementos de instalación al final del archivo AdminDeployment.xml](../install/media/vs2015-install-endoffileadmindeploy.PNG "vs2015_Install_EndOfFileAdminDeploy")
>
> Otra manera de hacer esto es simplemente omitir los elementos secundarios opcionales de un elemento primario. En otras palabras, no incluya elementos “Selected=”no””. Sin embargo, aún deberá colocar todos los elementos “Selected=”yes”” al final del archivo AdminDeployment.xml.

> [!IMPORTANT]
> Durante la instalación, el equipo se puede reiniciar una o más veces automáticamente. Después de que se reinicie, debe iniciar sesión con la misma cuenta de usuario con la que inició sesión para efectuar la instalación antes de reiniciar el equipo. Puede evitar los reinicios automáticos si instala los componentes de requisito previo antes de ejecutar una instalación desatendida. Para obtener más información, vea la sección titulada "Evitar el reinicio durante la configuración" en la [Visual Studio Administrator Guide](../install/visual-studio-administrator-guide.md).

 El esquema del archivo AdminDeployment contiene los siguientes elementos:

|Elemento|Atributo|Valores|Descripción|
|-------------|---------------|------------|-----------------|
|BundleCustomizations|TargetDir|*Ruta de acceso*|Tiene el mismo comportamiento que reemplazar la ruta de acceso en la interfaz de usuario de la aplicación de instalación. Este elemento se omite si Visual Studio ya está instalado.|
|BundleCustomizations|NoWeb|Sí&#124;valor predeterminado|Si el valor de este elemento es yes, la aplicación de instalación nunca intenta ir a la web durante la instalación.|
|SelectableItemCustomization|Hidden|Sí&#124;No|Si el valor de este elemento es Yes, oculta un elemento seleccionable en el árbol de personalización.|
|SelectableItemCustomization|Seleccionado|Sí&#124;No|Activa o desactiva un elemento seleccionable en el árbol de personalización.|
|BundleCustomizations|Fuente|Ruta de acceso|Ubicación de la fuente que el usuario desea usar.  Esta fuente se usa para posteriores operaciones de modificación en la máquina (“Default” de forma predeterminada).|
|BundleCustomizations|SuppressRefreshPrompt|Sí&#124;valor predeterminado|Impide que se solicite al usuario que actualice la configuración si hay disponible una más reciente.|
|BundleCustomizations|NoRefresh|Sí&#124;valor predeterminado|No actualizará la configuración si hay disponible una versión más reciente.|
|BundleCustomizations|NoCacheOnlyMode|Sí&#124;valor predeterminado|Impide que se rellene automáticamente la memoria caché del paquete.|

> [!WARNING]
> La aplicación de instalación respetará el estado seleccionado de un elemento SelectableItem incluso si está oculto. Por ejemplo, si desea instalar siempre un elemento seleccionable, márquelo como oculto y seleccionado.

#### <a name="to-create-an-unattended-installation-of-visual-studio"></a>Para crear una instalación desatendida de Visual Studio

1. En el archivo *Unidad*:\IDEinstall\AdminDeployment.xml, cambie el valor del atributo NoWeb del elemento BundleCustomizations de “default” a “yes” tal como se muestra en el siguiente ejemplo:

     Cambiar `<BundleCustomizations TargetDir="default" NoWeb="default"/>` a `<BundleCustomizations TargetDir="default" NoWeb="yes"/>`

2. Cambie el atributo SelectableItemCustomization según sea necesario para los componentes opcionales y guarde el archivo.

## <a name="running-unattended-setup"></a>Ejecutar una instalación desatendida
 Para ejecutar la instalación desatendida, puede ejecutar automáticamente la aplicación de instalación de Visual Studio en los equipos cliente o puede permitir que los usuarios ejecuten la aplicación ellos mismos con los valores que usted defina.

#### <a name="to-run-an-unattended-installation-on-a-client-computer"></a>Para ejecutar una instalación desatendida en un equipo cliente

- Abra el menú **Iniciar**, elija **Ejecutar** y, luego, escriba \\\\*ServerName*\IDEinstall\vs_*Product*.exe /adminfile *PathOfTheAdmindeployment.xmlFile*<em>AdditionalParametersAsNeeded</em>.

   Por ejemplo, puede especificar la siguiente línea de comandos: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\ IDEinstall\AdminDeployment.xml /quiet /norestart`

#### <a name="to-enable-clients-to-manually-install-visual-studio-with-pre-defined-settings"></a>Para permitir que los clientes instalen manualmente Visual Studio con valores predefinidos

1. Copie el archivo personalizado AdminDeployment.xml en un recurso compartido de red que sea de solo lectura (por ejemplo, \\\\*ServerName*\IDEinstall\packages\AdminDeployment.xml).

2. Permita a los usuarios instalar desde ese recurso compartido.

## <a name="maintaining-an-installation"></a>Mantener una instalación
 Si abre **Panel de control** y vuelve a ejecutar la aplicación de instalación, puede modificar las características de Visual Studio, desinstalar lenguajes de programación y reparar o desinstalar Visual Studio.

> [!NOTE]
> Debe tener credenciales administrativas en el equipo local para poder usar el modo de mantenimiento.

#### <a name="to-maintain-an-installation-on-a-client-computer"></a>Para mantener una instalación en un equipo cliente

- Abra el **Panel de control**y elija **Programas y características**.

- Elija [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]y, después, elija **Cambiar**.

#### <a name="to-change-admindeployment-settings-on-a-client-computer-after-visual-studio-has-been-installed"></a>Para cambiar los valores de AdminDeployment en un equipo cliente una vez instalado Visual Studio

1. Actualice AdminDeployment.xml cuando sea necesario.

2. Abra el menú **Iniciar** y, a continuación, elija **Ejecutar**.

3. Escriba el siguiente texto: \\\\*ServerName*\IDEinstall\vs_*Product*.exe /AdminFile PathToAdmindeployment.xml.

    AdditionalParametersAsNeeded

    Por ejemplo, puede especificar la siguiente línea de comandos: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\IDEinstall\AdminDeployment.xml /quiet /norestart`

   Repair es el parámetro predeterminado cuando Visual Studio está instalado. Si repara Visual Studio con /AdminFile actualizado, los valores actuales de la implementación de administración se reemplazarán por los que invoque el archivo AdminDeployment.xml actualizado.

## <a name="updating-an-installation"></a>Actualización de una instalación
 Microsoft ha lanzado varias actualizaciones para Visual Studio 2015. En esta sección se explica cómo actualizar la imagen de instalación desatendida de Visual Studio 2015 para que incluya las actualizaciones.

#### <a name="to-update-an-unattended-installation-of-visual-studio"></a>Para actualizar una instalación desatendida de Visual Studio, siga estos pasos:

1. Busque el archivo Product.exe en la imagen de red existente, haga clic en él con el botón derecho y, luego, haga clic en **Propiedades**.

2. Haga clic en la pestaña **Detalles** y tome nota de la propiedad **Versión del producto**.

    ![Ejemplo de cuadro de diálogo de propiedades en una instalación desatendida de Visual Studio](../install/media/unattended-install-properties-dialog-box.PNG "Instalación desatendida: cuadro de diálogo Propiedades")

3. ###### <a name="if-the-product-version-is-140247200-or-140247201-follow-these-steps"></a>Si la versión del producto es 14.0.24720.0 o 14.0.24720.1, siga estos pasos:
   1. Ejecute *Product.exe* /Layout *Unidad:* \IDEinstall en una máquina que tenga acceso a Internet. (Por ejemplo, ejecute: `vs_enterprise.exe /Layout d:\IDEinstall`.)

   2. Una vez finalizado /Layout, copie la nueva imagen en una nueva ubicación.

   3. Cree y modifique el archivo AdminDeployment.xml. Para ello, use el parámetro de línea de comandos `/CreateAdminFile`*\<ubicación del archivo>*. (Para más información, consulte la sección "Implementar Visual Studio en modo desatendido" de este artículo).

   4. En la máquina cliente, ejecute el siguiente comando para actualizar la copia de Visual Studio que instaló anteriormente: "\\\\*server1*\IDEinstall_Updated_1\\*Product.exe* /adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart".

        Por ejemplo, ejecute: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`.
5. ###### <a name="for-other-product-version-values-follow-these-steps"></a>Para otros valores de versión del producto, siga estos pasos:
   1. Ejecute *Product.exe* /Layout *Unidad:* \IDEinstall en una máquina que tenga acceso a Internet. (Por ejemplo, ejecute `vs-enterprise.exe /Layout d:\IDEinstall`.)

   2. Una vez finalizado /Layout, copie la nueva imagen en una nueva ubicación. (O bien, puede reemplazar la imagen de red existente).

   3. Cree y modifique el archivo AdminDeployment.xml. Para ello, use el parámetro de línea de comandos `/CreateAdminFile`*\<ubicación del archivo>*. (Para más información, consulte la sección "Implementar Visual Studio en modo desatendido" de este artículo).

   4. Si copia la imagen en una nueva ubicación, debe ejecutar el siguiente comando en la máquina cliente para actualizar la copia de Visual Studio que instaló anteriormente: "\\\\*server1*\IDEinstall_Updated_1\\*Product.exe* /adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart".

        Por ejemplo, ejecute: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`.

   5. Si reemplaza la imagen de red existente, puede ejecutar el comando como se muestra en el paso anterior, o puede hacer lo siguiente:
       1. Abra el **Panel de control**y elija **Programas y características**.

       2. Elija **Visual Studio** y, luego, **Cambiar**.

       3. Después de que Visual Studio se inicie en modo de mantenimiento, haga clic en **Modificar**.

       4. La actualización más reciente debe aparecer en la página de características. Seleccione las otras características que quiere instalar, haga clic en **Siguiente** y, luego, haga clic en **Actualizar** para instalar la actualización y las nuevas características.

## <a name="registering-the-product"></a>Registro del producto
 Una vez completada la instalación, puede registrar la copia de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] desde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

#### <a name="to-register"></a>Para registrarlo

1. Abra el menú **Ayuda** y, a continuación, elija **Registrar producto**.

2. Escriba la clave de producto.

     (Para más información, consulte los temas [Cómo: Encontrar la clave de producto de Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) y [Cómo: aplicar automáticamente las claves de producto durante la implementación de Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md)).

## <a name="see-also"></a>Vea también
 [Instalar Visual Studio](../install/install-visual-studio-2015.md)