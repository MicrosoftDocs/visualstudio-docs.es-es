---
title: Cómo crear un manifiesto de paquete | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc3a1263136fe4c50b2c7020e1557a7a693691b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382528"
---
# <a name="how-to-create-a-package-manifest"></a>Cómo: Crear un manifiesto de paquete
Para implementar los requisitos previos de la aplicación, puede usar un paquete de programa previo. Un paquete de programa previo contiene un solo archivo de manifiesto de producto, pero un manifiesto de paquete para cada configuración regional. La funcionalidad compartida entre diferentes versiones localizadas debe incluirse en el manifiesto del producto.

 Para obtener más información acerca de los manifiestos de producto, consulte [Cómo: crear un manifiesto de producto](../deployment/how-to-create-a-product-manifest.md).

## <a name="create-the-package-manifest"></a>Crear el manifiesto del paquete

#### <a name="to-create-the-package-manifest"></a>Para crear el manifiesto del paquete

1. Cree un directorio para el paquete de programa previo. En este ejemplo se usa *C:\package*.

2. Cree un subdirectorio con el nombre de la configuración regional, como *en* para inglés.

3. En Visual Studio, cree un archivo XML denominado *package.xml*y guárdelo en la carpeta *C:\package\en* .

4. Agregue XML para mostrar el nombre del paquete de programa previo, la referencia cultural para este manifiesto de paquete localizado y el contrato de licencia opcional. En el código XML siguiente se usan las variables `DisplayName` y `Culture` , que se definen en un elemento posterior.

    ```xml
    <Package
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
        Name="DisplayName"
        Culture="Culture"
        LicenseAgreement="eula.txt">
    ```

5. Agregue XML para enumerar todos los archivos que se encuentran en el directorio específico de la configuración regional. En el código XML siguiente se usa un archivo denominado *eula.txt* que es aplicable a la configuración regional **en** .

    ```xml
    <PackageFiles>
      <PackageFile Name="eula.txt"/>
    </PackageFiles>
    ```

6. Agregue XML para definir cadenas localizables para el paquete de programa previo. El siguiente XML agrega cadenas de error para la configuración regional **en** .

    ```xml
      <Strings>
        <String Name="DisplayName">Custom Bootstrapper Package</String>
        <String Name="CultureName">en</String>
        <String Name="NotAnAdmin">You must be an administrator to install
    this package.</String>
        <String Name="GeneralFailure">A general error has occurred while
    installing this package.</String>
    </Strings>
    ```

7. Copie la carpeta *C:\package* en el directorio de arranque de Visual Studio. Para Visual Studio 2010, este es el directorio *\Archivos de Programa\microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* .

## <a name="example"></a>Ejemplo
 El manifiesto del paquete contiene información específica de la configuración regional, como los mensajes de error, los términos de licencia de software y los paquetes de idioma.

```xml
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
- [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)