---
title: '&lt;&gt;Elemento PackageFiles (arranque) | Microsoft Docs'
description: Obtenga información sobre el elemento PackageFiles, que contiene elementos PackageFile que definen los paquetes de instalación que se ejecutan como resultado del elemento Command.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <PackageFiles> element [bootstrapper]
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0fbf76fec604819d7944a7b54fa4b2421e37c111
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925369"
---
# <a name="ltpackagefilesgt-element-bootstrapper"></a>&lt;&gt;Elemento PackageFiles (arranque)
El `PackageFiles` elemento contiene `PackageFile` elementos, que definen los paquetes de instalación que se ejecutan como resultado del `Command` elemento.

## <a name="syntax"></a>Sintaxis

```xml
<PackageFiles
    CopyAllPackageFiles
>
    <PackageFile
        Name
        HomeSite
        CopyOnBuild
        PublicKey
        Hash
    />
</PackageFiles>
```

## <a name="elements-and-attributes"></a>Elementos y atributos
 El elemento `PackageFiles` tiene el siguiente atributo.

|Atributo|Descripción|
|---------------|-----------------|
|`CopyAllPackageFiles`|Opcional. Si se establece en `false` , el instalador solo descargará los archivos a los que se hace referencia desde el `Command` elemento. Si se establece en `true` , se descargarán todos los archivos.<br /><br /> Si se establece en `IfNotHomesite` , el instalador se comportará igual que si `False` `ComponentsLocation` está establecido en `HomeSite` y, de lo contrario, se comportará igual que si `True` . Esta configuración puede ser útil para permitir que los paquetes que se programas previosn a sí mismos ejecuten su propio comportamiento en un escenario de HomeSite.<br /><br /> De manera predeterminada, es `true`.|

## <a name="packagefile"></a>PackageFile
 El `PackageFile` elemento es un elemento secundario del `PackageFiles` elemento. Un `PackageFiles` elemento debe tener al menos un `PackageFile` elemento.

 `PackageFile` tiene los siguientes atributos.

| Atributo | Descripción |
|---------------| - |
| `Name` | Necesario. Nombre del archivo de paquete. Este es el nombre al que `Command` hace referencia el elemento cuando define las condiciones en las que se instala un paquete. Este valor también se utiliza como una clave en la `Strings` tabla para recuperar el nombre localizado que herramientas como [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usará para describir el paquete. |
| `HomeSite` | Opcional. La ubicación del paquete en el servidor remoto, si no se incluye con el instalador. |
| `CopyOnBuild` | Opcional. Especifica si el programa previo debe copiar el archivo de paquete en el disco en el momento de la compilación. El valor predeterminado es true. |
| `PublicKey` | La clave pública cifrada del firmante del certificado del paquete. Es obligatorio si `HomeSite` se usa; en caso contrario, es opcional. |
| `Hash` | Opcional. Un hash SHA1 del archivo de paquete. Se utiliza para comprobar la integridad del archivo en el momento de la instalación. Si no se puede calcular el hash idéntico a partir del archivo de paquete, el paquete no se instalará. |

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se definen los paquetes para el paquete redistribuible de .NET Framework y sus dependencias, como el Windows Installer.

```xml
<PackageFiles>
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>
    <PackageFile Name="dotnetchk.exe"/>
</PackageFiles>
```

## <a name="see-also"></a>Vea también
- [Elemento \<Product>](../deployment/product-element-bootstrapper.md)
- [Elemento \<Package>](../deployment/package-element-bootstrapper.md)
- [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)