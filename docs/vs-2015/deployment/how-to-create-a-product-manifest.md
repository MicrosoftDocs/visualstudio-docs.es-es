---
title: 'Cómo: crear un manifiesto de producto | Microsoft Docs'
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
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 73e2c3f2c9736fd762a9e763827ed641ea5069f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153828"
---
# <a name="how-to-create-a-product-manifest"></a>Cómo: Crear un manifiesto de producto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para implementar los requisitos previos de la aplicación, puede crear un paquete de programa previo. Un paquete de programa previo contiene un solo archivo de manifiesto de producto, pero un manifiesto de paquete para cada configuración regional. El manifiesto del paquete contiene aspectos específicos de la localización del paquete. Esto incluye las cadenas, los contratos de licencia para el usuario final y los paquetes de idioma.  
  
 Para obtener más información acerca de los manifiestos de producto, consulte [Cómo: crear un manifiesto de paquete](../deployment/how-to-create-a-package-manifest.md).  
  
## <a name="creating-the-product-manifest"></a>Crear el manifiesto del producto  
  
#### <a name="to-create-the-product-manifest"></a>Para crear el manifiesto del producto  
  
1. Cree un directorio para el paquete de programa previo. En este ejemplo se usa C:\package.  
  
2. En Visual Studio, cree un nuevo archivo XML denominado `product.xml` y guárdelo en la carpeta C:\package.  
  
3. Agregue el siguiente código XML para describir el espacio de nombres XML y el código de producto del paquete. Reemplace el código de producto por un identificador único para el paquete.  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4. Agregue XML para especificar que el paquete tiene una dependencia. En este ejemplo se usa una dependencia en Microsoft Windows Installer 3,1.  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5. Agregue XML para enumerar todos los archivos que se encuentran en el paquete de programa previo. En este ejemplo se usa el nombre de archivo del paquete CorePackage.msi.  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6. Copie o mueva el archivo de CorePackage.msi a la carpeta C:\package.  
  
7. Agregue XML para instalar el paquete mediante los comandos de arranque. El programa previo agrega automáticamente la marca **/QN** al archivo. msi, que se instalará de forma silenciosa. Si el archivo es un archivo. exe, el programa previo ejecuta el archivo. exe mediante el shell. El siguiente XML no muestra ningún argumento para CorePackage.msi, pero puede colocar el argumento de la línea de comandos en el atributo arguments.  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8. Agregue el siguiente código XML para comprobar si este paquete de arranque está instalado. Reemplace el código de producto por el GUID para el componente redistribuible.  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Agregue XML para cambiar el comportamiento del programa previo en función de si el componente de arranque ya está instalado. Si el componente está instalado, el paquete de arranque no se ejecuta. El siguiente XML comprueba si el usuario actual es un administrador porque este componente requiere privilegios administrativos.  
  
    ```  
    <InstallConditions>  
        <BypassIf   
           Property="IsMsiInstalled"   
           Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
            Compare="ValueNotEqualTo" Value="True"  
            String="NotAnAdmin"/>  
    </InstallConditions>  
    ```  
  
10. Agregue XML para establecer códigos de salida si la instalación se realiza correctamente y si es necesario reiniciar. En el siguiente código XML se muestran los códigos de salida FAIL y FailReboot, que indican que el programa previo no seguirá instalando los paquetes.  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Agregue el siguiente código XML para finalizar la sección para los comandos del programa previo.  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. Mueva la carpeta C:\package al directorio de arranque de Visual Studio. Para Visual Studio 2010, este es el directorio \Archivos de Programa\microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.  
  
## <a name="example"></a>Ejemplo  
 El manifiesto del producto contiene instrucciones de instalación para los requisitos previos personalizados.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Product  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  ProductCode="Custom.Bootstrapper.Package">  
  
  <RelatedProducts>  
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
  </RelatedProducts>  
  
  <PackageFiles>  
    <PackageFile Name="CorePackage.msi"/>  
  </PackageFiles>  
  
  <InstallChecks>  
    <MsiProductCheck Product="IsMsiInstalled"   
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
  </InstallChecks>  
  
  <Commands>  
    <Command PackageFile="CorePackage.msi" Arguments="">  
  
      <InstallConditions>  
        <BypassIf Property="IsMsiInstalled"  
          Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
          Compare="ValueNotEqualTo" Value="True"  
         String="NotAnAdmin"/>  
      </InstallConditions>  
  
      <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
      </ExitCodes>  
    </Command>  
  </Commands>  
</Product>  
```  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)
