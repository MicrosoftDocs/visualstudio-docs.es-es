---
title: '&lt;Dependency &gt; (elemento, implementación ClickOnce) | Microsoft Docs'
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
- <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84e26a2d7dae70e0029817d4e6bb6e70dd53bce4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62928949"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;Dependency &gt; (elemento, implementación ClickOnce)
Identifica la versión de la aplicación que se va a instalar y la ubicación del manifiesto de aplicación.

## <a name="syntax"></a>Sintaxis

```xml

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
 El elemento `dependency` es obligatorio. No tiene atributos. Un manifiesto de implementación puede tener varios `dependency` elementos.

 `dependency`Normalmente, el elemento expresa las dependencias de la aplicación principal en los ensamblados contenidos en una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. Si la aplicación Main.exe consume un ensamblado denominado DotNetAssembly.dll, ese ensamblado debe aparecer en una sección de dependencia. Sin embargo, la dependencia también puede expresar otros tipos de dependencias, como las dependencias de una versión específica del Common Language Runtime, en un ensamblado de la caché de ensamblados global (GAC) o en un objeto COM. Dado que se trata de una tecnología de implementación no táctil, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] no puede iniciar la descarga e instalación de estos tipos de dependencias, pero impide que la aplicación se ejecute si una o varias de las dependencias especificadas no existen.

## <a name="dependentassembly"></a>dependentAssembly
 Necesario. Este elemento contiene el `assemblyIdentity` elemento. En la tabla siguiente se muestran los atributos que `dependentAssembly` admite.

| Atributo | Descripción |
|------------------| - |
| `preRequisite` | Opcional. Especifica que este ensamblado ya debe existir en la GAC. Los valores válidos son `true` y `false`. Si `true` , y el ensamblado especificado no existe en la GAC, la aplicación no se puede ejecutar. |
| `visible` | Opcional. Identifica la identidad de aplicación de nivel superior, incluidas sus dependencias. Lo utiliza internamente [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] para administrar el almacenamiento y la activación de la aplicación. |
| `dependencyType` | Necesario. La relación entre esta dependencia y la aplicación. Los valores válidos son:<br /><br /> -   `install`. El componente representa una instalación independiente de la aplicación actual.<br />-   `preRequisite`. El componente es necesario para la aplicación actual. |
| `codebase` | Opcional. Ruta de acceso completa al manifiesto de aplicación. |
| `size` | Opcional. Tamaño del manifiesto de aplicación, en bytes. |

## <a name="assemblyidentity"></a>assemblyIdentity
 Necesario. Este elemento es un elemento secundario del elemento `dependentAssembly` . El contenido de `assemblyIdentity` debe ser el mismo que se describe en el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de aplicación. En la tabla siguiente se muestran los atributos del `assemblyIdentity` elemento.

|Atributo|Descripción|
|---------------|-----------------|
|`Name`|Necesario. Identifica el nombre de la aplicación.|
|`Version`|Necesario. Especifica el número de versión de la aplicación en el formato siguiente: `major.minor.build.revision`|
|`publicKeyToken`|Necesario. Especifica una cadena hexadecimal de 16 caracteres que representa los últimos 8 bytes del hash SHA-1 de la clave pública con la que se firma la aplicación o el ensamblado. La clave pública que se usa para firmar debe ser de 2048 bits o superior.|
|`processorArchitecture`|Necesario. Especifica el microprocesador. Los valores válidos son `x86` para Windows de 32 bits y `IA64` para windows de 64 bits.|
|`Language`|Opcional. Identifica los códigos de idioma de dos partes del ensamblado. Por ejemplo, EN-US, lo que significa inglés (EE. UU.). El valor predeterminado es `neutral`. Este elemento está en el `asmv2` espacio de nombres.|
|`type`|Opcional. Para la compatibilidad con versiones anteriores con la tecnología de instalación en paralelo de Windows. El único valor permitido es `win32` .|

## <a name="hash"></a>hash
 El `hash` elemento es un elemento secundario opcional del `file` elemento. El elemento `hash` no tiene atributos.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utiliza un hash algorítmico de todos los archivos de una aplicación como una comprobación de seguridad para asegurarse de que ninguno de los archivos se cambió después de la implementación. Si `hash` no se incluye el elemento, no se realizará esta comprobación. Por lo tanto, `hash` no se recomienda omitir el elemento.

## <a name="dsigtransforms"></a>dsig:Transforms
 El `dsig:Transforms` elemento es un elemento secundario necesario del `hash` elemento. El elemento `dsig:Transforms` no tiene atributos.

## <a name="dsigtransform"></a>dsig: transformación
 El `dsig:Transform` elemento es un elemento secundario necesario del `dsig:Transforms` elemento. En la tabla siguiente se muestran los atributos del `dsig:Transform` elemento.

| Atributo | Descripción |
|-------------| - |
| `Algorithm` | Algoritmo usado para calcular el Resumen de este archivo. Actualmente, el único valor utilizado por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es `urn:schemas-microsoft-com:HashTransforms.Identity` . |

## <a name="dsigdigestmethod"></a>dsig:DigestMethod
 El `dsig:DigestMethod` elemento es un elemento secundario necesario del `hash` elemento. En la tabla siguiente se muestran los atributos del `dsig:DigestMethod` elemento.

| Atributo | Descripción |
|-------------| - |
| `Algorithm` | Algoritmo usado para calcular el Resumen de este archivo. Actualmente, el único valor utilizado por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es `http://www.w3.org/2000/09/xmldsig#sha1` . |

## <a name="dsigdigestvalue"></a>dsig:DigestValue
 El `dsig:DigestValue` elemento es un elemento secundario necesario del `hash` elemento. El elemento `dsig:DigestValue` no tiene atributos. Su valor de texto es el hash calculado para el archivo especificado.

## <a name="remarks"></a>Comentarios
 Los manifiestos de implementación suelen tener un único `assemblyIdentity` elemento que identifica el nombre y la versión del manifiesto de aplicación.

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra un `dependency` elemento en un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de implementación.

```xml
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
 En el ejemplo de código siguiente se especifica una dependencia de un ensamblado que ya está instalado en la GAC.

```xml
<dependency>
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />
  </dependentAssembly>
</dependency>
```

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se especifica una dependencia en una versión específica de la Common Language Runtime.

```xml
<dependency>
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />
  </dependentAssembly>
</dependency>
```

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se especifica una dependencia del sistema operativo.

```xml
<dependency>
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">
      <osVersionInfo>
         <os majorVersion="4" minorVersion="10" />
      </osVersionInfo>
   </dependentOS>
</dependency>
```

## <a name="see-also"></a>Consulte también
- [Manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [\<dependency> Element](../deployment/dependency-element-clickonce-application.md)