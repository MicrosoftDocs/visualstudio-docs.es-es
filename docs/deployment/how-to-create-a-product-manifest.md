---
title: "C&#243;mo: Crear un manifiesto de producto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "dependencias, paquete de arranque personalizado"
  - "requisitos previos, paquete de arranque personalizado"
  - "archivos del producto [ClickOnce]"
  - "archivos de producto [Windows Installer]"
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# C&#243;mo: Crear un manifiesto de producto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para implementar los requisitos previos de su aplicación, puede crear un paquete de arranque.  Un paquete de arranque contiene un archivo de manifiesto de producto único pero un manifiesto de paquete para cada configuración regional.  El manifiesto del paquete contiene aspectos específicos de la localización de su paquete.  Esto incluye cadenas, contratos de licencia de usuario final y paquetes de idioma.  
  
 Para obtener más información sobre los manifiestos de producto, vea [Cómo: Crear un manifiesto de paquete](../deployment/how-to-create-a-package-manifest.md).  
  
## Crear el manifiesto del producto  
  
#### Para crear el manifiesto del producto  
  
1.  Cree un directorio para el paquete de arranque.  En este ejemplo se utiliza C:\\package.  
  
2.  En Visual Studio, cree un nuevo archivo XML llamado `product.xml` y guárdelo en la carpeta C:\\package.  
  
3.  Agregue el siguiente XML para describir el espacio de nombres XML y el código de producto para el paquete.  Reemplace el código del producto por un identificador único del paquete.  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  Agregue XML para especificar que el paquete tiene una dependencia.  En este ejemplo se utiliza una dependencia en Microsoft Windows Installer 3.1.  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  Agregue XML para hacer una lista de todos los archivos que están en el paquete de arranque.  En este ejemplo se utiliza el nombre de archivo empaquetado CorePackage.msi.  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  Copie o mueva el archivo CorePackage.msi a la carpeta C:\\package.  
  
7.  Agregue XML para instalar el paquete utilizando los comandos de arranque.  El arranque agrega automáticamente la marca **\/qn** al archivo .msi, que se instalará silenciosamente.  Si el archivo es un .exe, el arranque lo ejecuta utilizando el shell.  El siguiente XML no muestra ningún argumento a CorePackage.msi, pero puede colocar el argumento de la línea de comandos en el atributo Arguments.  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  Agregue el siguiente XML para comprobar si se instala este paquete de arranque.  Reemplace el código de producto por el GUID del componente redistribuible.  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Agregue XML para cambiar el comportamiento de arranque que depende de si ya hay un componente de arranque instalado.  Si el componente está instalado, el paquete de arranque no se ejecuta.  El siguiente XML comprueba si el usuario actual es un administrador porque este componente requiere privilegios de administrador.  
  
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
  
10. Agregue XML para establecer los códigos de salida si la instalación es correcta y es necesario reiniciar.  El siguiente XML muestra los códigos de salida Fail y FailReboot, que indican que el arranque no seguirá instalando los paquetes.  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Agregue el siguiente XML para finalizar la sección para los comandos de arranque.  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. Mueva la carpeta C:\\package al directorio de arranque de Visual Studio.  Para Visual Studio 2010, es \\Archivos de programa\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages.  
  
## Ejemplo  
 El manifiesto del producto contiene las instrucciones de instalación de los requisitos previos personalizados.  
  
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
  
## Vea también  
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)