---
title: "Elemento &lt;dependency&gt; (Aplicaci&#243;n ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#osVersionInfo"
  - "urn:schemas-microsoft-com:asm.v2#os"
  - "http://www.w3.org/2000/09/xmldsig#Transform"
  - "urn:schemas-microsoft-com:asm.v2#dependency"
  - "http://www.w3.org/2000/09/xmldsig#DigestValue"
  - "urn:schemas-microsoft-com:asm.v2#assemblyIdentity"
  - "http://www.w3.org/2000/09/xmldsig#DigestMethod"
  - "http://www.w3.org/2000/09/xmldsig#Transforms"
  - "urn:schemas-microsoft-com:asm.v2#hash"
  - "urn:schemas-microsoft-com:asm.v2#dependentAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<dependency> (elemento) [manifiesto de aplicación ClickOnce]"
  - "manifiestos [ClickOnce], dependency (elemento)"
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
caps.latest.revision: 34
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 34
---
# Elemento &lt;dependency&gt; (Aplicaci&#243;n ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica una plataforma o dependencia de ensamblado requerida para la aplicación.  
  
## Sintaxis  
  
```  
  
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
  
## Elementos y atributos  
 Se requiere el elemento `dependency`.  Puede haber varias instancias de `dependency` en el mismo manifiesto de aplicación.  
  
 El elemento `dependency` no contiene atributos y contiene los siguientes elementos secundarios.  
  
### dependentOS  
 Opcional.  Contiene el elemento `osVersionInfo`.  Los elementos `dependentOS` y `dependentAssembly` se excluyen mutuamente: uno de los dos debe existir para un elemento `dependency`, pero no ambos.  
  
 `dependentOS` admite los siguientes atributos.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`supportUrl`|Opcional.  Especifica una dirección URL de soporte para la plataforma dependiente.  La dirección URL se muestra al usuario si se encuentra la plataforma necesaria.|  
|`description`|Opcional.  Describe, de forma legible para el usuario, el sistema operativo descrito por el elemento `dependentOS`.|  
  
### osVersionInfo  
 Obligatorio.  Este elemento es un elemento secundario del elemento `dependentOS` y contiene el elemento `os`.  Este elemento no tiene ningún atributo.  
  
### os  
 Obligatorio.  Este elemento es secundario del elemento `osVersionInfo`.  Este elemento presenta los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`majorVersion`|Obligatorio.  Especifica el número de versión principal del sistema operativo.|  
|`minorVersion`|Obligatorio.  Especifica el número de versión secundario del sistema operativo.|  
|`buildNumber`|Obligatorio.  Especifica el número de compilación del sistema operativo.|  
|`servicePackMajor`|Obligatorio.  Especifica el número principal del Service Pack del sistema operativo.|  
|`servicePackMinor`|Opcional.  Especifica el número secundario del Service Pack del sistema operativo.|  
|`productType`|Opcional.  Identifica el valor del tipo de producto.  Los valores válidos son `server`, `workstation` y `domainController`.  Por ejemplo, para Windows 2000 Professional, este valor de atributo es `workstation`.|  
|`suiteType`|Opcional.  Identifica un conjunto de productos disponible en el sistema o el tipo de configuración del sistema.  Los valores válidos son `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted` y `terminal`.  Por ejemplo, para Windows 2000 Professional, este valor de atributo es `professional`.|  
  
### dependentAssembly  
 Opcional.  Contiene el elemento `assemblyIdentity`.  Los elementos `dependentOS` y `dependentAssembly` se excluyen mutuamente: uno de los dos debe existir para un elemento `dependency`, pero no ambos.  
  
 `dependentAssembly` tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`dependencyType`|Obligatorio.  Especifica el tipo de dependencia.  Los valores válidos son `preprequisite` e `install`.  Se instala un ensamblado `install` como parte de la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Debe haber un ensamblado `prerequisite` en la memoria caché global de ensamblados \(GAC\) para que la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pueda realizar la instalación.|  
|`allowDelayedBinding`|Obligatorio.  Especifica si el ensamblado se puede cargar mediante programación en tiempo de ejecución.|  
|`group`|Opcional.  Si el atributo `dependencyType` está establecido en `install`, designa un grupo de ensamblados con nombre que solo se instala a petición.  Para obtener más información, vea [Tutorial: Descargar ensamblados a petición con la API de implementación de ClickOnce mediante el diseñador](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Si está establecido en `framework` y el atributo `dependencyType` está establecido en `prerequisite`, designa el ensamblado como parte de .NET Framework.  Este ensamblado no se comprueba en la memoria caché global de ensamblados \(GAC\) si la instalación se realiza en [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] y versiones posteriores.|  
|`codeBase`|Se requiere cuando el atributo `dependencyType` está establecido en `install`.  Ruta de acceso al ensamblado dependiente.  Puede ser una ruta de acceso absoluta o una ruta de acceso relativa a la base del código del manifiesto.  Esta ruta de acceso debe ser un Identificador uniforme de recursos URI válido para que el manifiesto del ensamblado sea válido.|  
|`size`|Se requiere cuando el atributo `dependencyType` está establecido en `install`.  El tamaño del ensamblado dependiente, en bytes.|  
  
### assemblyIdentity  
 Obligatorio.  Es un elemento secundario del elemento `dependentAssembly` y tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`name`|Obligatorio.  Identifica el nombre de la aplicación.|  
|`version`|Obligatorio.  Especifica el número de versión de la aplicación en el formato siguiente: `major.minor.build.revision`|  
|`publicKeyToken`|Opcional.  Especifica una cadena hexadecimal de 16 caracteres que representa los últimos 8 bytes del valor hash `SHA-1` de la clave pública bajo la que se firma la aplicación o el ensamblado.  La clave pública utilizada para firmar el catálogo debe tener 2048 bits o más.|  
|`processorArchitecture`|Opcional.  Especifica el procesador.  Los valores válidos son `x86` para Windows de 32 bits e `I64` para Windows de 64 bits.|  
|`language`|Opcional.  Identifica los códigos de idioma de dos partes del ensamblado \(por ejemplo, EN\-US\).|  
  
### hash  
 El elemento `hash` es un elemento secundario opcional del elemento `assemblyIdentity`.  El elemento `hash` no tiene atributos.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utiliza un valor hash algorítmico de todos los archivos de una aplicación como comprobación de seguridad para asegurarse de que no se modificó ninguno de los archivos después de la implementación.  Si el elemento `hash` no está incluido, no se realizará esta comprobación. En consecuencia, no se recomienda omitir el elemento `hash`.  
  
### dsig:Transforms  
 El elemento `dsig:Transforms` es un elemento secundario necesario del elemento `hash`.  El elemento `dsig:Transforms` no tiene atributos.  
  
### dsig:Transform  
 El elemento `dsig:Transform` es un elemento secundario necesario del elemento `dsig:Transforms`.  El elemento `dsig:Transform` presenta los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Algorithm`|Algoritmo que se utiliza para calcular la síntesis de este archivo.  En la actualidad, el único valor utilizado por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
### dsig:DigestMethod  
 El elemento `dsig:DigestMethod` es un elemento secundario necesario del elemento `hash`.  El elemento `dsig:DigestMethod` presenta los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Algorithm`|Algoritmo que se utiliza para calcular la síntesis de este archivo.  En la actualidad, el único valor utilizado por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
### dsig:DigestValue  
 El elemento `dsig:DigestValue` es un elemento secundario necesario del elemento `hash`.  El elemento `dsig:DigestValue` no tiene atributos.  Su valor de texto es el valor hash calculado para el archivo especificado.  
  
## Comentarios  
 Todos los ensamblados que utiliza la aplicación deben tener un elemento `dependency` correspondiente.  Los ensamblados dependientes no incluyen ensamblados que se deban preinstalar en la caché global de ensamblados como ensamblados de plataforma.  
  
## Ejemplo  
 En el siguiente ejemplo de código se muestran elementos `dependency` en un manifiesto de aplicación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Este ejemplo de código forma parte de un ejemplo más extenso que aparece en el tema [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md).  
  
```  
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
  
## Vea también  
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Elemento \<dependency\>](../deployment/dependency-element-clickonce-deployment.md)