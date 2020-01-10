---
title: Creando paquetes de programa previo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 47
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: daf72a4466cd0f02eb6ef3a357276ed690fd26bf
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75845521"
---
# <a name="creating-bootstrapper-packages"></a>Crear paquetes de arranque
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El programa de instalación es un instalador genérico que se puede configurar para detectar e instalar componentes redistribuibles, como archivos de Windows Installer (.msi) y programas ejecutables. El instalador también se conoce como programa previo. Se programa mediante un conjunto de manifiestos XML que especifican los metadatos que administrarán la instalación del componente.  
  
 El programa previo detecta primero si los requisitos previos están ya instalados. Si no lo están, el programa previo muestra el contrato de licencia. Después de que el usuario acepta los contratos de licencia, comienza la instalación de los requisitos previos. Si se detectan todos los requisitos previos, el programa previo inicia el instalador de la aplicación.  
  
## <a name="creating-custom-packages"></a>Crear paquetes personalizados  
 Puede generar los manifiestos con el editor XML de Visual Studio. Para obtener más información, vea [How to: Create a Package Manifest](../deployment/how-to-create-a-package-manifest.md) y [How to: Create a Product Manifest](../deployment/how-to-create-a-product-manifest.md). Para obtener un ejemplo de cómo crear un paquete de programa previo, vea [Walkthrough: Creating a Custom Bootstrapper to Show a Privacy Prompt](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).  
  
 Para crear un paquete de programa previo, debe suministrar el redistribuible en forma de archivo EXE o MSI al generador de manifiestos de programa previo. Después, el generador de manifiestos de programa previo crea los siguientes archivos:  
  
- El manifiesto del producto, product.xml, que contiene los metadatos del paquete que son independientes del idioma. Contiene los metadatos comunes a todas las versiones localizadas del componente redistribuible.  
  
- El manifiesto del paquete, package.xml, que contiene los metadatos específicos del idioma; normalmente, contiene mensajes de error localizados. Un componente debe tener al menos un manifiesto del paquete por cada versión localizada de ese componente.  
  
  Una vez creados estos archivos, coloque el archivo del manifiesto del producto en una carpeta con el nombre del programa previo personalizado. El archivo del manifiesto del paquete va en una carpeta con el nombre de la configuración regional. Por ejemplo, si el archivo del manifiesto del paquete es para la redistribución en inglés, coloque el archivo en una carpeta llamada en. Repita este proceso para cada configuración regional, como ja para japonés y de para alemán. El paquete del programa previo personalizado final podría tener la siguiente estructura de carpetas.  
  
  `CustomBootstrapperPackage`  
  
  `product.xml`  
  
  `CustomBootstrapper.msi`  
  
  `de`  
  
  `eula.rtf`  
  
  `package.xml`  
  
  `en`  
  
  `eula.rtf`  
  
  `package.xml`  
  
  `ja`  
  
  `eula.rtf`  
  
  `package.xml`  
  
  Por último, copie los archivos redistribuibles en la ubicación de la carpeta del programa previo. Para obtener más información, consulta [How to: Create a Localized Bootstrapper Package](../deployment/how-to-create-a-localized-bootstrapper-package.md).  
  
```  
\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 o  
  
```  
\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 También puede determinar la ubicación de la carpeta del programa previo con el valor de **Ruta de acceso** en la siguiente clave del Registro:  
  
```  
HKLM\Software\Microsoft\GenericBootstrapper\11.0  
```  
  
 En los sistemas de 64 bits, use la siguiente clave del Registro:  
  
```  
HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0  
```  
  
 Cada componente redistribuible aparece en su propia subcarpeta, en el directorio de los paquetes. Los archivos de manifiesto del producto y de los redistribuibles se colocan en esta subcarpeta. Las versiones localizadas de los manifiestos de componentes y de paquetes se colocan en subcarpetas con el nombre de la referencia cultural.  
  
 Una vez copiados estos archivos en la carpeta del programa previo, el paquete del programa previo aparece automáticamente en el cuadro de diálogo de requisitos previos de Visual Studio. Si el paquete del programa previo personalizado no aparece, cierre y vuelva a abrir el cuadro de diálogo Requisitos previos. Para obtener más información, consulta [Cuadro de diálogo Requisitos previos](../ide/reference/prerequisites-dialog-box.md).  
  
 La tabla siguiente muestra las propiedades que el programa previo rellena automáticamente.  
  
|La propiedad|Descripción|  
|--------------|-----------------|  
|ApplicationName|El nombre de la aplicación.|  
|ProcessorArchitecture|El procesador y los bits por palabra de la plataforma de destino de un ejecutable. Los valores son los siguientes:<br /><br /> -   Intel<br />-   IA64<br />-   AMD64|  
|[Version9x](https://msdn.microsoft.com/library/aa372490\(v=vs.140\).aspx)|Número de versión de los sistemas operativos Microsoft Windows 95, Windows 98 o Windows ME. La sintaxis de la versión es Principal.Secundaria.ServicePack.|  
|[VersionNT](/windows/desktop/Msi/versionnt)|Número de versión de los sistemas operativos Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 o Windows 7. La sintaxis de la versión es Principal.Secundaria.ServicePack.|  
|[VersionMSI](https://msdn.microsoft.com/library/aa372493\(v=vs.140\).aspx)|La versión del ensamblado de Windows Installer (msi.dll) que se ejecuta durante la instalación.|  
|[AdminUser](https://msdn.microsoft.com/library/aa367545\(v=vs.140\).aspx)|Esta propiedad se establece si el usuario tiene privilegios administrativos. Los valores son true o false.|  
|InstallMode|El modo de instalación indica desde dónde debe instalarse el componente. Los valores son los siguientes:<br /><br /> -   HomeSite: los requisitos previos se instalan desde el sitio web del proveedor.<br />-   SpecificSite: los requisitos previos se instalan desde la ubicación que seleccione.<br />-   SameSite: los requisitos previos se instalan desde la misma ubicación que la aplicación.|  
  
## <a name="separating-redistributables-from-application-installations"></a>Separar los redistribuibles de las instalaciones de las aplicaciones  
 Puede evitar que los archivos redistribuibles se implementen en proyectos de instalación. Para ello, cree una lista de redistribuibles en la carpeta RedistList de su directorio de .NET Framework:  
  
 `%ProgramFiles%\Microsoft.NET\RedistList`  
  
 La lista de redistribuibles es un archivo XML cuyo nombre debe seguir el formato siguiente: *Nombre de la compañía*.*Nombre del componente*.RedistList.xml. Por ejemplo, si el componente se llama Datawidgets y ha sido creado por Acme, use Acme.DataWidgets.RedistList.xml. El siguiente podría ser un ejemplo del contenido de la lista de redistribuibles:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<FileList Redist="Acme.DataWidgets" >  
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />  
</FileList>  
```  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Instalar requisitos previos mediante una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Cuadro de diálogo Requisitos previos](../ide/reference/prerequisites-dialog-box.md)   
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)   
 [Usar el programa previo de Visual Studio 2005 para poner en marcha su instalación](https://msdn.microsoft.com/magazine/cc163899.aspx)
