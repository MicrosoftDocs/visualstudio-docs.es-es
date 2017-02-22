---
title: "Elemento &lt;dependency&gt; (Implementaci&#243;n ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "<dependency> (elemento) [manifiesto de implementación ClickOnce]"
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;dependency&gt; (Implementaci&#243;n ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica la versión de la aplicación que se instalará, y la ubicación del manifiesto de aplicación.  
  
## Sintaxis  
  
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
  
## Elementos y atributos  
 Se requiere el elemento `dependency`.  No tiene atributos.  Un manifiesto de implementación puede tener varios elementos `dependency`.  
  
 El elemento `dependency` normalmente expresa las dependencias de la aplicación principal en los ensamblados contenidos dentro de una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Si su aplicación Main.exe utiliza un ensamblado denominado DotNetAssembly.dll, dicho ensamblado debe estar incluido en una sección de dependencia.  Sin embargo, la dependencia también puede expresar otros tipos de dependencias, como las dependencias de una versión específica del Common Language Runtime, en un ensamblado en la caché global de ensamblados \(GAC\), o en un objeto COM.  Debido a que se trata de una tecnología de implementación sin contacto, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] no puede iniciar la descarga e instalación de este tipo de dependencias, aunque puede evitar que la aplicación se ejecute si no existe una o varias de las dependencias especificadas.  
  
## dependentAssembly  
 Obligatorio.  Este elemento contiene el elemento `assemblyIdentity`.  En la siguiente tabla se muestran los atributos admitidos por `dependentAssembly`.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`preRequisite`|Opcional.  Especifica que este ensamblado ya debería existir en la GAC.  Los valores válidos son `true` y `false`.  Si es `true`, y el ensamblado especificado no existe en la GAC, la aplicación no se ejecuta.|  
|`visible`|Opcional.  Identifica la identidad de la aplicación de nivel superior, incluida sus dependencias.  Se utiliza internamente por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] para administrar el almacenamiento y la activación de la aplicación.|  
|`dependencyType`|Obligatorio.  La relación entre esta dependencia y la aplicación.  Los valores válidos son:<br /><br /> -   `install`.  El componente representa una instalación independiente respecto a la aplicación actual.<br />-   `preRequisite`.  La aplicación actual requiere el componente.|  
|`codebase`|Opcional.  Ruta de acceso completa al manifiesto de aplicación.|  
|`size`|Opcional.  Tamaño del manifiesto de aplicación en bytes.|  
  
## assemblyIdentity  
 Obligatorio.  Este elemento es secundario del elemento `dependentAssembly`.  El contenido de `assemblyIdentity` debe ser igual al que se describe en el manifiesto de aplicación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  En la siguiente tabla se muestran los atributos del elemento `assemblyIdentity`.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Name`|Obligatorio.  Identifica el nombre de la aplicación.|  
|`Version`|Obligatorio.  Especifica el número de versión de la aplicación, en el siguiente formato: `major.minor.build.revision`|  
|`publicKeyToken`|Obligatorio.  Especifica una cadena hexadecimal de 16 caracteres que representa los últimos 8 bytes del valor hash SHA\-1 de la clave pública bajo la que se firma la aplicación o el ensamblado.  La clave pública que se utiliza para firmar debe ser de 2048 bits o mayor.|  
|`processorArchitecture`|Obligatorio.  Especifica el microprocesador.  Los valores válidos son `x86` para Windows de 32 bits e `IA64` para Windows de 64 bits.|  
|`Language`|Opcional.  Identifica los códigos de idioma en dos partes del ensamblado.  Por ejemplo, EN\-US significa inglés de Estados Unidos.  El valor predeterminado es `neutral`.  Este elemento se encuentra en el espacio de nombres `asmv2`.|  
|`type`|Opcional.  Por razones de compatibilidad con versiones anteriores con la tecnología de instalación en paralelo de Windows.  El único valor permitido es `win32`.|  
  
## hash  
 El elemento `hash` es un elemento secundario opcional del elemento `file`.  El elemento `hash` no tiene atributos.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utiliza un valor hash algorítmico de todos los archivos de una aplicación como comprobación de seguridad para asegurarse de que no se modificó ninguno de los archivos después de la implementación.  Si el elemento `hash` no está incluido, no se realizará esta comprobación. En consecuencia, no se recomienda omitir el elemento `hash`.  
  
## dsig:Transforms  
 El elemento `dsig:Transforms` es un elemento secundario necesario del elemento `hash`.  El elemento `dsig:Transforms` no tiene atributos.  
  
## dsig:Transform  
 El elemento `dsig:Transform` es un elemento secundario necesario del elemento `dsig:Transforms`.  En la siguiente tabla se muestran los atributos del elemento `dsig:Transform`.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Algorithm`|Algoritmo que se utiliza para calcular la síntesis de este archivo.  En la actualidad, el único valor utilizado por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## dsig:DigestMethod  
 El elemento `dsig:DigestMethod` es un elemento secundario necesario del elemento `hash`.  En la siguiente tabla se muestran los atributos del elemento `dsig:DigestMethod`.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Algorithm`|Algoritmo que se utiliza para calcular la síntesis de este archivo.  En la actualidad, el único valor utilizado por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## dsig:DigestValue  
 El elemento `dsig:DigestValue` es un elemento secundario necesario del elemento `hash`.  El elemento `dsig:DigestValue` no tiene atributos.  Su valor de texto es el valor hash calculado para el archivo especificado.  
  
## Comentarios  
 Generalmente, los manifiestos de implementación tienen un único elemento `assemblyIdentity` que identifica el nombre y la versión del manifiesto de aplicación.  
  
## Ejemplo  
 En el siguiente ejemplo de código se muestra un elemento `dependency` en un manifiesto de implementación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
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
  
## Ejemplo  
 En el siguiente ejemplo de código se especifica una dependencia de un ensamblado ya instalado en la GAC.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## Ejemplo  
 En el siguiente ejemplo de código se especifica una dependencia de una versión concreta del Common Language Runtime.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## Ejemplo  
 En el siguiente ejemplo de código se especifica una dependencia del sistema operativo.  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## Vea también  
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Elemento \<dependency\>](../deployment/dependency-element-clickonce-application.md)