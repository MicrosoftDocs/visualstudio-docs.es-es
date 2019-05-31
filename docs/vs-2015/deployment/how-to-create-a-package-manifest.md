---
title: Procedimiento Crear un manifiesto de paquete | Documentos de Microsoft
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
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c711c50ab484cc88b1d6aff5c8e3018cead69953
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60046020"
---
# <a name="how-to-create-a-package-manifest"></a>Procedimiento Crear un manifiesto del paquete
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para implementar los requisitos previos para la aplicación, puede usar un paquete de arranque. Un paquete de arranque contiene un archivo de manifiesto de producto único, pero un manifiesto del paquete para cada configuración regional. Funcionalidad compartida entre diferentes versiones localizadas debe incluirse en el manifiesto del producto.  
  
 Para obtener más información acerca de los manifiestos de paquete, vea [Cómo: Crear un manifiesto de producto](../deployment/how-to-create-a-product-manifest.md).  
  
## <a name="creating-the-package-manifest"></a>Crear el manifiesto del paquete  
  
#### <a name="to-create-the-package-manifest"></a>Para crear el manifiesto del paquete  
  
1. Cree un directorio para el paquete de programa previo. Este ejemplo utiliza C:\package.  
  
2. Cree un subdirectorio con el nombre de la configuración regional, por ejemplo, en para inglés.  
  
3. En Visual Studio, cree un archivo XML que se denomina `package.xml`y guárdelo en la carpeta C:\package\en.  
  
4. Agregue el código XML para mostrar el nombre del paquete de programa previo, la referencia cultural de este manifiesto del paquete localizado y el contrato de licencia opcional. El siguiente código XML utiliza las variables `DisplayName` y `Culture`, que se definen en un elemento de una versión posterior.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5. Agregue el código XML para mostrar todos los archivos que se encuentran en el directorio específico de la configuración regional. El siguiente código XML utiliza un archivo que se denomina eula.txt que es aplicable la **en** configuración regional.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6. Agregue el código XML para definir cadenas localizables para el paquete de arranque. El siguiente código XML agrega las cadenas de error para la configuración regional en.  
  
    ```  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7. Copie la carpeta C:\package en el directorio de programa previo de Visual Studio. Para Visual Studio 2010, es el directorio de SDKs\Windows\v7.0A\Bootstrapper\Packages \Program Files\Microsoft.  
  
## <a name="example"></a>Ejemplo  
 El manifiesto del paquete contiene información específica de la configuración regional, como los mensajes de error, los términos de licencia de software y paquetes de idioma.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.txt">  
  
  <PackageFiles>  
    <PackageFile Name="eula.txt"/>  
  </PackageFiles>  
  
  <Strings>  
    <String Name="DisplayName">Custom Bootstrapper Package</String>  
    <String Name="Culture">en</String>  
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>  
    <String Name="GeneralFailure">A general error has occurred while   
installing this package.</String>  
  </Strings>  
</Package>  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)
