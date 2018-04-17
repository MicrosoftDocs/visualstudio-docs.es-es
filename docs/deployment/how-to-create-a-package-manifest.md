---
title: 'Cómo: crear un manifiesto del paquete | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: d36d6c1d4589fa24e4c3e7c53e041d07f359092b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-package-manifest"></a>Cómo: Crear un manifiesto de paquete
Para implementar los requisitos previos para la aplicación, puede usar un paquete de arranque. Un paquete de arranque contiene un archivo de manifiesto de producto único pero un manifiesto del paquete para cada configuración regional. Funcionalidad compartida por versiones localizadas diferentes debe incluirse en el manifiesto del producto.  
  
 Para obtener más información sobre los manifiestos de paquete, consulte [Cómo: crear un manifiesto de producto](../deployment/how-to-create-a-product-manifest.md).  
  
## <a name="creating-the-package-manifest"></a>Crear el manifiesto del paquete  
  
#### <a name="to-create-the-package-manifest"></a>Para crear el manifiesto del paquete  
  
1.  Cree un directorio para el paquete del programa previo. En este ejemplo se utiliza C:\package.  
  
2.  Cree un subdirectorio con el nombre de la configuración regional, por ejemplo, en para inglés.  
  
3.  En Visual Studio, cree un archivo XML que se denomina `package.xml`y guárdelo en la carpeta C:\package\en.  
  
4.  Agregue el código XML para mostrar el nombre del paquete del programa previo, la referencia cultural para este manifiesto del paquete localizado y el contrato de licencia opcional. El siguiente código XML utiliza las variables `DisplayName` y `Culture`, que se definen en un elemento de una versión posterior.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  Agregue el código XML para obtener una lista de todos los archivos que están en el directorio de configuración regional. El siguiente XML utiliza un archivo que se denomina eula.txt al que se aplica a la **en** configuración regional.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  Agregue el código XML para definir cadenas localizables para el paquete del programa previo. El siguiente código XML agrega las cadenas de error para la configuración regional en.  
  
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
  
7.  Copie la carpeta C:\package en el directorio de programa previo de Visual Studio. Para Visual Studio 2010, este es el directorio de SDKs\Windows\v7.0A\Bootstrapper\Packages \Program.  
  
## <a name="example"></a>Ejemplo  
 El manifiesto del paquete contiene información de configuración regional, como mensajes de error y los términos de licencia de software, paquetes de idioma.  
  
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