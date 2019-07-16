---
title: '&lt;dependencia&gt; elemento (implementación ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f191b11dfce5b3877d0a31e260e092000a556a5a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187782"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;dependencia&gt; elemento (implementación ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifica la versión de la aplicación que desea instalar y la ubicación del manifiesto de aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      <dependency>   
   <dependentAssembly  
      preRequisite  
      visible  
      dependencyType  
      codeBase  
      size  
   >   
      <assemblyIdentity   
         name   
         version   
         publicKeyToken   
         processorArchitecture   
         language  
         type  
      />   
      <hash>  
         <dsig:Transforms>  
            <dsig:Transform  
                Algorithm  
            />  
         </dsig:Transforms>  
         <dsig:DigestMethod />  
         <dsig:DigestValue>  
         </dsig:DigestValue>  
      </hash>  
  
   </dependentAssembly>   
</dependency>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El `dependency` elemento es necesario. No tiene atributos. Un manifiesto de implementación puede tener varios `dependency` elementos.  
  
 El `dependency` elemento normalmente expresa las dependencias de la aplicación principal en los ensamblados contenidos dentro de un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación. Si su aplicación Main.exe utiliza un ensamblado denominado DotNetAssembly.dll, dicho ensamblado debe estar incluido en una sección de dependencia. Dependencia, sin embargo, también puede expresar otros tipos de dependencias, como las dependencias de una versión específica de common language runtime, en un ensamblado en la caché de ensamblados global (GAC) o en un objeto COM. Porque es una tecnología de implementación "no-touch" [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] no se iniciará la descarga e instalación de estos tipos de dependencias, pero ¿evita que la aplicación se ejecute si no existen una o varias de las dependencias especificadas.  
  
## <a name="dependentassembly"></a>dependentAssembly  
 Necesario. Este elemento contiene el `assemblyIdentity` elemento. En la tabla siguiente se muestra los atributos del `dependentAssembly` admite.  
  
|Atributo|DESCRIPCIÓN|  
|---------------|-----------------|  
|`preRequisite`|Opcional. Especifica que este ensamblado debe existir en la GAC. Los valores válidos son `true` y `false`. Si `true`y el ensamblado especificado no existe en la GAC, no se puede ejecutar la aplicación.|  
|`visible`|Opcional. Identifica la identidad de aplicación de nivel superior, incluidas sus dependencias. Utilizado internamente por [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] para administrar el almacenamiento de aplicaciones y activación.|  
|`dependencyType`|Necesario. La relación entre esta dependencia y la aplicación. Los valores válidos son:<br /><br /> -   `install`. Componente representa una instalación independiente de la aplicación actual.<br />-   `preRequisite`. Componente es necesario para la aplicación actual.|  
|`codebase`|Opcional. La ruta de acceso completa al manifiesto de aplicación.|  
|`size`|Opcional. El tamaño del manifiesto de aplicación, en bytes.|  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 Necesario. Este elemento es un elemento secundario del elemento `dependentAssembly` . El contenido de `assemblyIdentity` debe ser el mismo como se describe en el [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifiesto de aplicación. En la tabla siguiente se muestra los atributos de la `assemblyIdentity` elemento.  
  
|Atributo|DESCRIPCIÓN|  
|---------------|-----------------|  
|`Name`|Necesario. Identifica el nombre de la aplicación.|  
|`Version`|Necesario. Especifica el número de versión de la aplicación, en el formato siguiente: `major.minor.build.revision`|  
|`publicKeyToken`|Necesario. Especifica una cadena hexadecimal de 16 caracteres que representa los últimos 8 bytes del hash SHA-1 de la clave pública con la que se firma la aplicación o el ensamblado. La clave pública utilizada para iniciar sesión debe ser 2048 bits o superior.|  
|`processorArchitecture`|Necesario. Especifica el microprocesador. Los valores válidos son `x86` para Windows de 32 bits y `IA64` para Windows de 64 bits.|  
|`Language`|Opcional. Identifica los códigos de idioma de dos partes del ensamblado. Por ejemplo, EN-US, lo que significa para inglés (Estados Unidos). El valor predeterminado es `neutral`. Este elemento está en el `asmv2` espacio de nombres.|  
|`type`|Opcional. Por razones de compatibilidad con Windows side-by-side instalación tecnología. El único valor permitido es `win32`.|  
  
## <a name="hash"></a>hash  
 El `hash` elemento es un elemento secundario opcional de la `file` elemento. El elemento `hash` no tiene atributos.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] utiliza un valor hash algorítmico de todos los archivos en una aplicación como una comprobación de seguridad para asegurarse de que ninguno de los archivos se han modificado después de la implementación. Si el `hash` elemento no se incluye, no se realizará esta comprobación. Por lo tanto, si se omite el `hash` elemento no se recomienda.  
  
## <a name="dsigtransforms"></a>dsig:Transforms  
 El `dsig:Transforms` elemento es un elemento secundario necesario de la `hash` elemento. El elemento `dsig:Transforms` no tiene atributos.  
  
## <a name="dsigtransform"></a>dsig: Transform  
 El `dsig:Transform` elemento es un elemento secundario necesario de la `dsig:Transforms` elemento. En la tabla siguiente se muestra los atributos de la `dsig:Transform` elemento.  
  
|Atributo|DESCRIPCIÓN|  
|---------------|-----------------|  
|`Algorithm`|El algoritmo utilizado para calcular la síntesis de este archivo. Actualmente el único valor utilizado por [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] es `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 El `dsig:DigestMethod` elemento es un elemento secundario necesario de la `hash` elemento. En la tabla siguiente se muestra los atributos de la `dsig:DigestMethod` elemento.  
  
|Atributo|DESCRIPCIÓN|  
|---------------|-----------------|  
|`Algorithm`|El algoritmo utilizado para calcular la síntesis de este archivo. Actualmente el único valor utilizado por [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] es `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## <a name="dsigdigestvalue"></a>dsig:DigestValue  
 El `dsig:DigestValue` elemento es un elemento secundario necesario de la `hash` elemento. El elemento `dsig:DigestValue` no tiene atributos. Su valor de texto es el hash calculado para el archivo especificado.  
  
## <a name="remarks"></a>Comentarios  
 Manifiestos de implementación suelen tienen un único `assemblyIdentity` elemento que identifica el nombre y la versión del manifiesto de aplicación.  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo de código muestra un `dependency` elemento en un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifiesto de implementación.  
  
```  
<!-- Identify the assembly dependencies -->  
<dependency>  
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">  
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se especifica una dependencia en un ensamblado ya está instalado en la GAC.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se especifica una dependencia en una versión específica de common language runtime.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se especifica una dependencia del sistema operativo.  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## <a name="see-also"></a>Vea también  
 [Manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<dependency> Element](../deployment/dependency-element-clickonce-application.md)
