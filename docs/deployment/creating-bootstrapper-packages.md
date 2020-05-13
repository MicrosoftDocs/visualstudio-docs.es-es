---
title: Crear paquetes de programa previo
ms.date: 05/02/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f84f91ebedd47df8c0804adee35dcbec18d8551
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301012"
---
# <a name="create-bootstrapper-packages"></a>Crear paquetes de programa previo
El programa de instalación es un instalador genérico que se puede configurar para detectar e instalar componentes redistribuibles como archivos de Windows Installer (*.msi*) y programas ejecutables. El instalador también se conoce como programa previo. Se programa mediante un conjunto de manifiestos XML que especifican los metadatos que administrarán la instalación del componente.  Cada componente redistribuible, o requisito previo, que aparece en el cuadro de diálogo **Requisitos previos** para ClickOnce es un paquete de arranque. Un paquete de programa previo es un grupo de directorios y archivos que contienen archivos de manifiesto que describen cómo se debe instalar el requisito previo.

El programa previo detecta primero si los requisitos previos están ya instalados. Si no lo están, el programa previo muestra el contrato de licencia. Después de que el usuario acepta los contratos de licencia, comienza la instalación de los requisitos previos. Si se detectan todos los requisitos previos, el programa previo inicia el instalador de la aplicación.

## <a name="create-custom-bootstrapper-packages"></a>Crear paquetes de arranque personalizados
Puede generar los manifiestos de arranque mediante el Editor XML en Visual Studio. Para ver un ejemplo de creación de un paquete de arranque, consulte [Tutorial: Crear un programa](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md)de arranque personalizado con un mensaje de privacidad .

Para crear un paquete de arranque, debe crear un manifiesto de producto y, para cada versión localizada de un componente, también un manifiesto de paquete.

* El manifiesto del producto, *product.xml*, contiene los metadatos independientes del idioma del paquete. Contiene los metadatos comunes a todas las versiones localizadas del componente redistribuible.  Para crear este archivo, consulte [Cómo: crear un manifiesto de producto](../deployment/how-to-create-a-product-manifest.md).

* El manifiesto del paquete, *package.xml*, contiene metadatos específicos del idioma; normalmente contiene mensajes de error localizados. Un componente debe tener al menos un manifiesto del paquete por cada versión localizada de ese componente. Para crear este archivo, consulte [Cómo: crear un manifiesto](../deployment/how-to-create-a-package-manifest.md)de paquete .

Una vez creados estos archivos, coloque el archivo del manifiesto del producto en una carpeta con el nombre del programa previo personalizado. El archivo del manifiesto del paquete va en una carpeta con el nombre de la configuración regional. Por ejemplo, si el archivo del manifiesto del paquete es para la redistribución en inglés, coloque el archivo en una carpeta llamada en. Repita este proceso para cada configuración regional, como ja para japonés y de para alemán. El paquete del programa previo personalizado final podría tener la siguiente estructura de carpetas.

```
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

A continuación, copie los archivos redistribuibles en la ubicación de la carpeta de arranque. Para obtener más información, consulte [Cómo: crear un paquete](../deployment/how-to-create-a-localized-bootstrapper-package.md)de arranque localizado.

```
*\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper*
```

o, para versiones anteriores de Visual Studio

```
*\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

or

```
*\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

También puede encontrar la ubicación de la carpeta de arranque en el valor Ruta de **acceso** en la siguiente clave del Registro:

```
*HKLM\Software\Microsoft\GenericBootstrapper*
```

En los sistemas de 64 bits, use la siguiente clave del Registro:

```
*HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper*
```

Cada componente redistribuible aparece en su propia subcarpeta, en el directorio de los paquetes. El manifiesto del producto y los archivos redistribuibles deben colocarse en esta subcarpeta. Las versiones localizadas de los manifiestos de componentes y paquetes deben colocarse en subcarpetas denominadas según el nombre de la referencia cultural.

Después de copiar estos archivos en la carpeta de arranque, el paquete de arranque aparece automáticamente en el cuadro de diálogo **Requisitos previos** de Visual Studio. Si el paquete de arranque personalizado no aparece, cierre y vuelva a abrir el cuadro de diálogo **Requisitos previos.** Para obtener más información, consulte cuadro de [diálogo Requisitos previos](../ide/reference/prerequisites-dialog-box.md).

La tabla siguiente muestra las propiedades que el programa previo rellena automáticamente.

|Propiedad|Descripción|
|--------------|-----------------|
|ApplicationName|Nombre de la aplicación.|
|ProcessorArchitecture|El procesador y los bits por palabra de la plataforma de destino de un ejecutable. Los valores son los siguientes:<br /><br /> -   Intel<br />-   IA64<br />-   AMD64|
|[Version9x](/windows/desktop/Msi/version9x)|Número de versión de los sistemas operativos Microsoft Windows 95, Windows 98 o Windows ME. La sintaxis de la versión es Principal.Secundaria.ServicePack.|
|[VersionNT](/windows/desktop/Msi/versionnt)|Número de versión de los sistemas operativos Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 o Windows 7. La sintaxis de la versión es Principal.Secundaria.ServicePack.|
|[VersionMSI](/windows/desktop/Msi/versionmsi)|La versión del ensamblado de Windows Installer (msi.dll) que se ejecutará durante la instalación.|
|[AdminUser](/windows/desktop/Msi/adminuser)|Esta propiedad se establece si el usuario tiene privilegios administrativos. Los valores son true o false.|
|InstallMode|El modo de instalación indica desde dónde debe instalarse el componente. Los valores son los siguientes:<br /><br /> -   HomeSite: los requisitos previos se instalan desde el sitio web del proveedor.<br />-   SpecificSite: los requisitos previos se instalan desde la ubicación que seleccione.<br />-   SameSite: los requisitos previos se instalan desde la misma ubicación que la aplicación.|

## <a name="separate-redistributables-from-application-installations"></a>Separe los redistribuibles de las instalaciones de aplicaciones
Puede evitar que los archivos redistribuibles se implementen en proyectos de instalación. Para ello, cree una lista de redistribuibles en la carpeta RedistList de su directorio de .NET Framework:

`%ProgramFiles%\Microsoft.NET\RedistList`

La lista redistribuible es un archivo XML que debe asignar un nombre con el siguiente formato: * \<Nombre de la empresa>.\< Nombre de componente>. RedistList.xml*. Así, por ejemplo, si el componente se denomina DataWidgets creado por Acme, utilice *Acme.DataWidgets.RedistList.xml*. El siguiente podría ser un ejemplo del contenido de la lista de redistribuibles:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<FileList Redist="Acme.DataWidgets" >
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />
</FileList>
```

## <a name="see-also"></a>Consulte también
- [Cómo: Instalar requisitos previos mediante una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Cuadro de diálogo Requisitos previos](../ide/reference/prerequisites-dialog-box.md)
- [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)
- [Usar el programa previo de Visual Studio 2005 para poner en marcha su instalación](https://msdn.microsoft.com/magazine/cc163899.aspx)
