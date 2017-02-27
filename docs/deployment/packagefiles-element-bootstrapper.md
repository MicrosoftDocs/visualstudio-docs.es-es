---
title: "&lt;PackageFiles&gt; (Elemento, Arranque) | Microsoft Docs"
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
  - "<PackageFiles> (elemento) [arranque]"
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# &lt;PackageFiles&gt; (Elemento, Arranque)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El elemento `PackageFiles` contiene elementos `PackageFile` que definen los paquetes de instalación ejecutados como resultado del elemento `Command`.  
  
## Sintaxis  
  
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
  
## Elementos y atributos  
 El elemento `PackageFiles` tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`CopyAllPackageFiles`|Opcional.  Si se establece en `false`, el instalador sólo descargará los archivos a los que se hace referencia en el elemento `Command`.  Si se establece en `true`, se descargarán todos los archivos.<br /><br /> Si se establece en `IfNotHomesite`, el instalador se comportará como si se hubiera establecido en `False` si `ComponentsLocation` se ha establecido en `HomeSite`; de lo contrario, se comportará como si se hubiera establecido en `True`.  Este valor puede ser útil para permitir que los propios paquetes de arranque ejecuten su propio comportamiento en un escenario de HomeSite.<br /><br /> El valor predeterminado es `true`.|  
  
## PackageFile  
 El elemento `PackageFile` es un elemento secundario del elemento `PackageFiles`.  Un elemento `PackageFiles` debe tener al menos un elemento `PackageFile`.  
  
 `PackageFile` tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Name`|Obligatorio.  Nombre del archivo de paquete.  Se trata del nombre al que el elemento `Command` hace referencia cuando define las condiciones de instalación de un paquete.  Este valor también se utiliza como clave en la tabla `Strings` para recuperar el nombre encontrado que herramientas como [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilizarán para describir el paquete.|  
|`HomeSite`|Opcional.  Ubicación del paquete en el servidor remoto, si no está incluido con el instalador.|  
|`CopyOnBuild`|Opcional.  Especifica si el arranque debe copiar el archivo de paquete en el disco en tiempo de compilación.  El valor predeterminado es true.|  
|`PublicKey`|Clave pública cifrada del firmante del certificado del paquete.  Requerido si se utiliza `HomeSite`; en caso contrario, es opcional.|  
|`Hash`|Opcional.  Un hash SHA1 del archivo de paquete.  Esto se utiliza para comprobar la integridad del archivo en el momento de la instalación.  Si el hash idéntico no se puede calcular a partir del archivo empaquetado, no se instalará el paquete.|  
  
## Ejemplo  
 En el siguiente ejemplo de código se definen paquetes para el paquete redistribuible de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] y sus dependencias, como Windows Installer.  
  
```  
<PackageFiles>  
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>  
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetchk.exe"/>  
</PackageFiles>  
```  
  
## Vea también  
 [\<Product\> \(Elemento\)](../deployment/product-element-bootstrapper.md)   
 [\<Package\> \(Elemento\)](../deployment/package-element-bootstrapper.md)   
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)