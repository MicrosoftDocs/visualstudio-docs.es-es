---
title: Crear paquetes de programa previo
ms.custom: ''
ms.date: 05/02/2018
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], prerequisites
- deploying applications [Visual Studio], custom prerequisites
- prerequisites, custom
- RedistList file
- custom prerequisites
- redistributables list
ms.assetid: ba1a785b-693d-446b-bcae-b88cadee73d1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a16044657b197229253f93fc6aea6130a4522f64
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512189"
---
# <a name="create-bootstrapper-packages"></a>Crear paquetes de programa previo
El programa de instalación es un instalador genérico que se puede configurar para detectar e instalar componentes redistribuibles, como Windows Installer (*.msi*) los archivos y programas ejecutables. El instalador también se conoce como programa previo. Se programa mediante un conjunto de manifiestos XML que especifican los metadatos que administrarán la instalación del componente.  Cada componente redistribuible o requisito previo, que aparece en el **requisitos previos** cuadro de diálogo de ClickOnce es un paquete de programa previo. Un paquete de programa previo es un grupo de directorios y archivos que contienen archivos de manifiesto que describen cómo se debe instalar el requisito previo. 
  
El programa previo detecta primero si los requisitos previos están ya instalados. Si no lo están, el programa previo muestra el contrato de licencia. En segundo lugar, una vez que el usuario final acepte los contratos de licencia, comienza la instalación de los requisitos previos. Si se detectan todos los requisitos previos, el programa previo inicia el instalador de la aplicación.  
  
## <a name="create-custom-bootstrapper-packages"></a>Crear paquetes de programa previo personalizado  
Puede generar los manifiestos de programa previo mediante el Editor XML en Visual Studio. Para ver un ejemplo de cómo crear un paquete de arranque, consulte [Tutorial: crear un arranque personalizado con un aviso de privacidad](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).  
  
Para crear un paquete de arranque, se debe crear un manifiesto de producto y, para cada versión localizada de un componente, un manifiesto del paquete.
  
* El manifiesto del producto, *product.xml*, contiene los metadatos de lenguaje neutro para el paquete. Contiene los metadatos comunes a todas las versiones localizadas del componente redistribuible.  Para crear este archivo, consulte [Cómo: crear un manifiesto de producto](../deployment/how-to-create-a-product-manifest.md).
  
* El manifiesto del paquete, *package.xml*, contiene metadatos específicos del idioma; normalmente contiene mensajes de error localizado. Un componente debe tener al menos un manifiesto del paquete por cada versión localizada de ese componente. Para crear este archivo, consulte [Cómo: crear un manifiesto del paquete](../deployment/how-to-create-a-package-manifest.md).
  
Una vez creados estos archivos, coloque el archivo del manifiesto del producto en una carpeta con el nombre del programa previo personalizado. El archivo del manifiesto del paquete va en una carpeta con el nombre de la configuración regional. Por ejemplo, si el archivo del manifiesto del paquete es para la redistribución en inglés, coloque el archivo en una carpeta llamada en. Repita este proceso para cada configuración regional, como ja para japonés y de para alemán. El paquete del programa previo personalizado final podría tener la siguiente estructura de carpetas.  

    ```xml
    CustomBootstrapperPackage
      product.xml
      CustomBootstrapper.msi
      de
        eula.rtf
        package.xml
      en
        eula.rtf
        package.xml
      ja
        eula.rtf
        package.xml
    ```
  
A continuación, copie los archivos redistribuibles en la ubicación de carpeta de programa previo. Para obtener más información, consulte [Cómo: crear un paquete de arranque localizado](../deployment/how-to-create-a-localized-bootstrapper-package.md).
 
    *\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
    
o  
    
    *\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
  
También puede determinar la ubicación de la carpeta del programa previo con el valor de **Ruta de acceso** en la siguiente clave del Registro:  
  
    *HKLM\Software\Microsoft\GenericBootstrapper\11.0*
  
En los sistemas de 64 bits, utilice la siguiente clave del registro:  
  
    *HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0*
  
Cada componente redistribuible aparece en su propia subcarpeta, en el directorio de los paquetes. El producto en el manifiesto y redistribuible archivos deben colocarse en esta subcarpeta. Las versiones localizadas de los manifiestos de paquete y el componente deben colocarse en subcarpetas con el nombre de referencia cultural.  
  
Después de que estos archivos se copian en la carpeta de programa previo, el paquete de programa previo aparece automáticamente en Visual Studio **requisitos previos** cuadro de diálogo. Si el paquete de programa previo personalizado no aparece, cierre y vuelva a abrir el **requisitos previos** cuadro de diálogo. Para obtener más información, consulte [cuadro de diálogo de requisitos previos](../ide/reference/prerequisites-dialog-box.md).  
  
La tabla siguiente muestra las propiedades que el programa previo rellena automáticamente.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|ApplicationName|El nombre de la aplicación.|  
|ProcessorArchitecture|El procesador y los bits por palabra de la plataforma de destino de un ejecutable. Los valores son los siguientes:<br /><br /> -Intel<br />-IA64<br />-AMD64|  
|[Version9x](/windows/desktop/Msi/version9x)|Número de versión de los sistemas operativos Microsoft Windows 95, Windows 98 o Windows ME. La sintaxis de la versión es Principal.Secundaria.ServicePack.|  
|[VersionNT](/windows/desktop/Msi/versionnt)|Número de versión de los sistemas operativos Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 o Windows 7. La sintaxis de la versión es Principal.Secundaria.ServicePack.|  
|[VersionMSI](/windows/desktop/Msi/versionmsi)|La versión del ensamblado de Windows Installer (msi.dll) para ejecutar durante la instalación.|  
|[AdminUser](/windows/desktop/Msi/adminuser)|Esta propiedad se establece si el usuario tiene privilegios administrativos. Los valores son true o false.|  
|InstallMode|El modo de instalación indica desde dónde debe instalarse el componente. Los valores son los siguientes:<br /><br /> -HomeSite: los requisitos previos se instalan desde el sitio Web del proveedor.<br />-SpecificSite: los requisitos previos se instalan desde la ubicación que seleccione.<br />-SameSite: los requisitos previos se instalan desde la misma ubicación que la aplicación.|  
  
## <a name="separate-redistributables-from-application-installations"></a>Paquetes redistribuibles independientes desde las instalaciones de aplicaciones  
Puede evitar que los archivos redistribuibles se implementen en proyectos de instalación. Para ello, cree una lista de redistribuibles en la carpeta RedistList de su directorio de .NET Framework:  
  
`%ProgramFiles%\Microsoft.NET\RedistList`  
  
La lista de redistribuibles es un archivo XML que el nombre debe seguir el siguiente formato:  *\<nombre de la compañía >.\< Nombre de componente >. RedistList.xml*. Por lo tanto, por ejemplo, si el componente se llama DataWidgets por Acme, use *Acme.DataWidgets.RedistList.xml*. El siguiente podría ser un ejemplo del contenido de la lista de redistribuibles:  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<FileList Redist="Acme.DataWidgets" >  
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />  
</FileList>  
```  
  
## <a name="see-also"></a>Vea también  
 [Cómo: instalar requisitos previos mediante una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Cuadro de diálogo requisitos previos](../ide/reference/prerequisites-dialog-box.md)   
 [Referencia de esquema de paquete y del producto](../deployment/product-and-package-schema-reference.md)   
 [Utilice al programa previo de Visual Studio 2005 para poner en marcha su instalación.](http://go.microsoft.com/fwlink/?LinkId=107537)
