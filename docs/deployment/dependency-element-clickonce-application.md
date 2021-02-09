---
title: '&lt;Dependency &gt; (elemento, aplicación ClickOnce) | Microsoft Docs'
description: El elemento de dependencia identifica una dependencia de plataforma o ensamblado necesaria para la aplicación.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
- manifests [ClickOnce], dependency element
- <dependency> element [ClickOnce application manifest]
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1e716c0e9ebe88a8007296f1dad870424a0def0b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881118"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;Dependency &gt; (elemento, aplicación ClickOnce)
Identifica una dependencia de plataforma o ensamblado necesaria para la aplicación.

## <a name="syntax"></a>Sintaxis

```xml

      <dependency>
   <dependentOS
      supportURL
      description
   >
      <osVersionInfo>
         <os
            majorVersion
            minorVersion
            buildNumber
            servicePackMajor
            servicePackMinor
            productType
            suiteType
         />
      </osVersionInfo>
   </dependentOS>
   <dependentAssembly
      dependencyType
      allowDelayedBinding
      group
      codeBase
      size
   >
      <assemblyIdentity
         name
         version
         processorArchitecture
         language
      >
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

      </assemblyIdentity>
   </dependentAssembly>
</dependency>
```

## <a name="elements-and-attributes"></a>Elementos y atributos
 El elemento `dependency` es obligatorio. Puede haber varias instancias de `dependency` en el mismo manifiesto de aplicación.

 El `dependency` elemento no tiene atributos y contiene los siguientes elementos secundarios.

### <a name="dependentos"></a>dependentOS
 Opcional. Contiene el `osVersionInfo` elemento. Los `dependentOS` `dependentAssembly` elementos y se excluyen mutuamente: uno u otro debe existir para un `dependency` elemento, pero no para ambos.

 `dependentOS` admite los siguientes atributos.

|Atributo|Descripción|
|---------------|-----------------|
|`supportUrl`|Opcional. Especifica una dirección URL de soporte técnico para la plataforma dependiente. Esta dirección URL se muestra al usuario si se encuentra la plataforma necesaria.|
|`description`|Opcional. Describe, en formato legible, el sistema operativo descrito por el `dependentOS` elemento.|

### <a name="osversioninfo"></a>osVersionInfo
 Necesario. Este elemento es un elemento secundario del elemento `dependentOS` y contiene el elemento `os` . Este elemento no tiene atributos.

### <a name="os"></a>os
 Necesario. Este elemento es un elemento secundario del elemento `osVersionInfo` . Este elemento tiene los atributos siguientes.

|Atributo|Descripción|
|---------------|-----------------|
|`majorVersion`|Necesario. Especifica el número de versión principal del sistema operativo.|
|`minorVersion`|Necesario. Especifica el número de versión secundaria del sistema operativo.|
|`buildNumber`|Necesario. Especifica el número de compilación del sistema operativo.|
|`servicePackMajor`|Necesario. Especifica el número principal Service Pack del sistema operativo.|
|`servicePackMinor`|Opcional. Especifica el número secundario Service Pack del sistema operativo.|
|`productType`|Opcional. Identifica el valor de tipo de producto. Valores válidos son `server`, `workstation` y `domainController`. Por ejemplo, para Windows 2000 Professional, este valor de atributo es `workstation` .|
|`suiteType`|Opcional. Identifica un conjunto de productos disponible en el sistema o el tipo de configuración del sistema. Los valores válidos son `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted` y `terminal`. Por ejemplo, para Windows 2000 Professional, este valor de atributo es `professional` .|

### <a name="dependentassembly"></a>dependentAssembly
 Opcional. Contiene el `assemblyIdentity` elemento. Los `dependentOS` `dependentAssembly` elementos y se excluyen mutuamente: uno u otro debe existir para un `dependency` elemento, pero no para ambos.

 `dependentAssembly` tiene los siguientes atributos.

| Atributo | Descripción |
|-----------------------| - |
| `dependencyType` | Necesario. Especifica el tipo de dependencia. Los valores válidos son `preprequisite` y `install`. Un `install` ensamblado se instala como parte de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. Un `prerequisite` ensamblado debe estar presente en la caché de ensamblados global (GAC) para poder [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalar la aplicación. |
| `allowDelayedBinding` | Necesario. Especifica si el ensamblado se puede cargar mediante programación en tiempo de ejecución. |
| `group` | Opcional. Si el `dependencyType` atributo está establecido en `install` , designa un grupo de ensamblados con nombre que solo se instala a petición. Para obtener más información, vea [Tutorial: Descarga de ensamblados a petición con la API de implementación ClickOnce mediante el diseñador](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Si se establece en `framework` y el `dependencyType` atributo se establece en `prerequisite` , designa el ensamblado como parte del .NET Framework. La caché de ensamblado global (GAC) no se comprueba para este ensamblado al instalar en .NET Framework 4 y versiones posteriores. |
| `codeBase` | Obligatorio cuando el `dependencyType` atributo está establecido en `install` . Ruta de acceso al ensamblado dependiente. Puede ser una ruta de acceso absoluta o una ruta de acceso relativa a la base de código del manifiesto. Esta ruta de acceso debe ser un URI válido para que el manifiesto del ensamblado sea válido. |
| `size` | Obligatorio cuando el `dependencyType` atributo está establecido en `install` . Tamaño del ensamblado dependiente, en bytes. |

### <a name="assemblyidentity"></a>assemblyIdentity
 Necesario. Este elemento es un elemento secundario del elemento `dependentAssembly` y tiene los atributos siguientes.

|Atributo|Descripción|
|---------------|-----------------|
|`name`|Necesario. Identifica el nombre de la aplicación.|
|`version`|Necesario. Especifica el número de versión de la aplicación en el formato siguiente: `major.minor.build.revision`|
|`publicKeyToken`|Opcional. Especifica una cadena hexadecimal de 16 caracteres que representa los últimos 8 bytes del `SHA-1` valor hash de la clave pública con la que se firma la aplicación o el ensamblado. La clave pública que se usa para firmar el catálogo debe ser de 2048 bits o más.|
|`processorArchitecture`|Opcional. Especifica el procesador. Los valores válidos son `x86` para Windows de 32 bits y `I64` para windows de 64 bits.|
|`language`|Opcional. Identifica los códigos de idioma de dos partes, como EN-US, del ensamblado.|

### <a name="hash"></a>hash
 El `hash` elemento es un elemento secundario opcional del `assemblyIdentity` elemento. El elemento `hash` no tiene atributos.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utiliza un hash algorítmico de todos los archivos de una aplicación como una comprobación de seguridad, para asegurarse de que ninguno de los archivos se cambió después de la implementación. Si `hash` no se incluye el elemento, no se realizará esta comprobación. Por lo tanto, `hash` no se recomienda omitir el elemento.

### <a name="dsigtransforms"></a>dsig:Transforms
 El `dsig:Transforms` elemento es un elemento secundario necesario del `hash` elemento. El elemento `dsig:Transforms` no tiene atributos.

### <a name="dsigtransform"></a>dsig: transformación
 El `dsig:Transform` elemento es un elemento secundario necesario del `dsig:Transforms` elemento. El elemento `dsig:Transform` tiene los atributos siguientes:

| Atributo | Descripción |
|-------------| - |
| `Algorithm` | Algoritmo usado para calcular el Resumen de este archivo. Actualmente, el único valor utilizado por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es `urn:schemas-microsoft-com:HashTransforms.Identity` . |

### <a name="dsigdigestmethod"></a>dsig:DigestMethod
 El `dsig:DigestMethod` elemento es un elemento secundario necesario del `hash` elemento. El elemento `dsig:DigestMethod` tiene los atributos siguientes:

| Atributo | Descripción |
|-------------| - |
| `Algorithm` | Algoritmo usado para calcular el Resumen de este archivo. Actualmente, el único valor utilizado por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es `http://www.w3.org/2000/09/xmldsig#sha1` . |

### <a name="dsigdigestvalue"></a>dsig:DigestValue
 El `dsig:DigestValue` elemento es un elemento secundario necesario del `hash` elemento. El elemento `dsig:DigestValue` no tiene atributos. Su valor de texto es el hash calculado para el archivo especificado.

## <a name="remarks"></a>Notas
 Todos los ensamblados utilizados por la aplicación deben tener un `dependency` elemento correspondiente. Los ensamblados dependientes no incluyen ensamblados que deben preinstalarse en la caché global de ensamblados como ensamblados de plataforma.

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestran `dependency` los elementos de un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de aplicación. Este ejemplo de código forma parte de un ejemplo mayor proporcionado para el tema de [manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md) .

```xml
<dependency>
  <dependentOS>
    <osVersionInfo>
      <os
        majorVersion="4"
        minorVersion="10"
        buildNumber="0"
        servicePackMajor="0" />
    </osVersionInfo>
  </dependentOS>
</dependency>
<dependency>
  <dependentAssembly
    dependencyType="preRequisite"
    allowDelayedBinding="true">
    <assemblyIdentity
      name="Microsoft.Windows.CommonLanguageRuntime"
      version="4.0.20506.0" />
  </dependentAssembly>
</dependency>

<dependency>
  <dependentAssembly
    dependencyType="install"
    allowDelayedBinding="true"
    codebase="MyApplication.exe"
    size="4096">
    <assemblyIdentity
      name="MyApplication"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="x86" />
    <hash>
      <dsig:Transforms>
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
      </dsig:Transforms>
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
      <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>
    </hash>
  </dependentAssembly>
</dependency>
```

## <a name="see-also"></a>Vea también
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)
- [Elemento \<dependency>](../deployment/dependency-element-clickonce-deployment.md)