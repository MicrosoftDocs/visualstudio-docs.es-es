---
title: '&lt;PackageFiles&gt; elemento (arranque) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords: <PackageFiles> element [bootstrapper]
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 25ba72b511782c450b882826a3e3af94a14f6e20
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ltpackagefilesgt-element-bootstrapper"></a>&lt;PackageFiles&gt; elemento (arranque)
El `PackageFiles` contiene el elemento `PackageFile` elementos, que definen los paquetes de instalación que se ejecuta como resultado de la `Command` elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
 El `PackageFiles` elemento tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`CopyAllPackageFiles`|Opcional. Si establece en `false`, el instalador sólo descargará los archivos que se hace referencia desde el `Command` elemento. Si establece en `true`, se descargarán todos los archivos.<br /><br /> Si establece en `IfNotHomesite`, el instalador comportará igual como si `False` si `ComponentsLocation` está establecido en `HomeSite`y en caso contrario, se comportará igual como si `True`. Esta configuración puede ser útil para permitir que los paquetes que son programas previos ejecutar su propio comportamiento en un escenario de HomeSite.<br /><br /> De manera predeterminada, es `true`.|  
  
## <a name="packagefile"></a>PackageFile  
 El `PackageFile` es un elemento secundario de la `PackageFiles` elemento. A `PackageFiles` elemento debe tener al menos un `PackageFile` elemento.  
  
 `PackageFile`tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Name`|Requerido. El nombre del archivo del paquete. Este es el nombre que el `Command` elemento hará referencia cuando define las condiciones en las que se instala un paquete. Este valor también se utiliza como una clave en el `Strings` tabla para recuperar el nombre localizado que herramientas como [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilizará para describir el paquete.|  
|`HomeSite`|Opcional. La ubicación del paquete en el servidor remoto, si no se incluye con el programa de instalación.|  
|`CopyOnBuild`|Opcional. Especifica si el programa previo debe copiar el archivo de paquete en el disco en tiempo de compilación. El valor predeterminado es true.|  
|`PublicKey`|La clave pública cifrada del firmante del certificado del paquete. Requerido si `HomeSite` se usa; en caso contrario, opcional.|  
|`Hash`|Opcional. Un hash SHA1 del archivo del paquete. Esto se utiliza para comprobar la integridad del archivo durante la instalación. Si no se puede calcular el hash idéntico desde el archivo de paquete, no se instalará el paquete.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define paquetes para el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] paquete redistribuible y sus dependencias, como Windows Installer.  
  
```  
<PackageFiles>  
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>  
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetchk.exe"/>  
</PackageFiles>  
```  
  
## <a name="see-also"></a>Vea también  
 [\<Producto > elemento](../deployment/product-element-bootstrapper.md)   
 [\<Paquete > elemento](../deployment/package-element-bootstrapper.md)   
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)