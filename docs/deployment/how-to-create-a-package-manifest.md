---
title: "C&#243;mo: Crear un manifiesto de paquete | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
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
  - "dependencias, paquetes de arranque personalizados"
  - "archivos del paquete [ClickOnce]"
  - "archivos de paquete [Windows Installer]"
  - "requisitos previos, paquete de arranque personalizado"
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Crear un manifiesto de paquete
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para implementar los requisitos previos de su aplicación, puede usar un paquete de arranque.  Un paquete de arranque contiene un archivo de manifiesto de producto único pero un manifiesto de paquete para cada configuración regional.  La funcionalidad compartida por versiones localizadas diferentes debe incluirse en el manifiesto del producto.  
  
 Para obtener más información sobre los manifiestos de los paquetes, vea [Cómo: Crear un manifiesto de producto](../deployment/how-to-create-a-product-manifest.md).  
  
## Crear el manifiesto del paquete  
  
#### Para crear el manifiesto del paquete  
  
1.  Cree un directorio para el paquete de arranque.  En este ejemplo se utiliza C:\\package.  
  
2.  Cree un subdirectorio con el nombre de la configuración regional, por ejemplo, en para inglés.  
  
3.  En Visual Studio, cree un archivo XML denominado `package.xml` y guárdelo en la carpeta C:\\package\\en.  
  
4.  Agregue XML para enumerar el nombre del paquete de arranque, la referencia cultural para este manifiesto del paquete localizado y el contrato de licencia opcional.  El siguiente XML utiliza las variables `DisplayName` y `Culture`, que se definen en un elemento posterior.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  Agregue XML para hacer una lista de todos los archivos que están en el directorio específico de la configuración regional.  El siguiente XML utiliza un archivo que se denomina eula.txt al que se aplica la configuración regional **en**.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  Agregue XML para definir las cadenas traducibles del paquete de arranque.  El siguiente XML agrega las cadenas de error para la configuración regional en.  
  
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
  
7.  Copie la carpeta C:\\package en el directorio de arranque de Visual Studio.  Para Visual Studio 2010, es \\Archivos de programa\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages.  
  
## Ejemplo  
 El manifiesto del paquete contiene la información específica de la configuración regional, como los mensajes de error, las condiciones de licencia del software y los paquetes de idioma.  
  
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
  
## Vea también  
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)