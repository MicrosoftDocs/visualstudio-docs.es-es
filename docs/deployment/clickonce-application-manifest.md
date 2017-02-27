---
title: "Manifiesto de aplicaci&#243;n ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "manifiestos de aplicación [ClickOnce]"
  - "ClickOnce, manifiestos de aplicación"
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# Manifiesto de aplicaci&#243;n ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un manifiesto de aplicación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es un archivo XML que describe una aplicación que se implementa mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 los manifiestos de aplicación de[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tiene los elementos y los atributos siguientes.  
  
|Elemento|Descripción|Atributos|  
|--------------|-----------------|---------------|  
|[Elemento \<assembly\>](../deployment/assembly-element-clickonce-application.md)|Obligatorio.  Elemento de nivel superior.|`manifestVersion`|  
|[Elemento \<assemblyIdentity\>](../deployment/assemblyidentity-element-clickonce-application.md)|Obligatorio.  Identifica el ensamblado primario de la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[\<trustInfo\> \(elemento\)](../deployment/trustinfo-element-clickonce-application.md)|Identifica los requisitos de seguridad de la aplicación.|None|  
|[\<entryPoint\> \(Elemento\)](../deployment/entrypoint-element-clickonce-application.md)|Obligatorio.  Identifica el punto de entrada del código de aplicación.|`name`|  
|[Elemento \<dependency\>](../deployment/dependency-element-clickonce-application.md)|Obligatorio.  Identifica cada dependencia necesaria para que se ejecute la aplicación.  Identifica opcionalmente ensamblados que necesitan preinstalarse.|None|  
|[Elemento \<file\>](../deployment/file-element-clickonce-application.md)|Opcional.  Identifica cada archivo nonassembly utilizado por la aplicación.  Puede incluir los datos de aislamiento Componente Modelo de objetos \(COM\) asociados al archivo.|`name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType`|  
|[\<fileAssociation\> \(Elemento\)](../deployment/fileassociation-element-clickonce-application.md)|Opcional.  Identifica una extensión de archivo que se va a asociar a la aplicación.|`extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon`|  
  
## Comentarios  
 El archivo de manifiesto de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] identifica una aplicación implementada mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Para obtener más información sobre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vea [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md).  
  
## Ubicación del archivo  
 Un manifiesto de aplicación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es específico de una única versión de una implementación.  Por esta razón, deben estar almacenados por separado de los manifiestos de implementación.  La convención común consiste en colocar los manifiestos en un subdirectorio con el nombre de la versión asociada.  
  
 El manifiesto de aplicación siempre se debe firmar antes de la implementación.  Si cambia un manifiesto de aplicación manualmente, debe utilizar mage.exe para firmar de nuevo el manifiesto de aplicación, actualizar el manifiesto de implementación y, a continuación, firmar de nuevo el manifiesto de implementación.  Para obtener más información, vea [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## Sintaxis de los nombres de archivo  
 El nombre de un archivo de manifiesto de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] debe ser el nombre completo y la extensión de aplicación según se identifica en el elemento de `assemblyIdentity` , seguido de la extensión .manifest.  Por ejemplo, un manifiesto de aplicación que hace referencia a la aplicación Example.exe utilizaría la sintaxis de nombre de archivo siguiente.  
  
 `example.exe.manifest`  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra el manifiesto de aplicación de una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd" manifestVersion="1.0" xmlns:asmv3="urn:schemas-microsoft-com:asm.v3" xmlns:dsig="http://www.w3.org/2000/09/xmldsig#" xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2" xmlns="urn:schemas-microsoft-com:asm.v2" xmlns:asmv1="urn:schemas-microsoft-com:asm.v1" xmlns:asmv2="urn:schemas-microsoft-com:asm.v2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
  <asmv1:assemblyIdentity name="My Application Deployment.exe" version="1.0.0.0" publicKeyToken="43cb1e8e7a352766" language="neutral" processorArchitecture="x86" type="win32" />  
  <application />  
  <entryPoint>  
    <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
  <trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet Unrestricted="true" ID="Custom" SameSite="site" />  
        <defaultAssemblyRequest permissionSetReference="Custom" />  
      </applicationRequestMinimum>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <!--  
          UAC Manifest Options  
          If you want to change the Windows User Account Control level replace the   
          requestedExecutionLevel node with one of the following.  
  
        <requestedExecutionLevel  level="asInvoker" uiAccess="false" />  
        <requestedExecutionLevel  level="requireAdministrator" uiAccess="false" />  
        <requestedExecutionLevel  level="highestAvailable" uiAccess="false" />  
  
         If you want to utilize File and Registry Virtualization for backward   
         compatibility then delete the requestedExecutionLevel node.  
    -->  
        <requestedExecutionLevel level="asInvoker" uiAccess="false" />  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
  <dependency>  
    <dependentOS>  
      <osVersionInfo>  
        <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
      </osVersionInfo>  
    </dependentOS>  
  </dependency>  
  <dependency>  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
      <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.20506.0" />  
    </dependentAssembly>  
  </dependency>  
  <dependency>  
    <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="4096">  
      <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
<publisherIdentity name="CN=DOMAINCONTROLLER\UserMe" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">  
…  
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>  
```  
  
## Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)