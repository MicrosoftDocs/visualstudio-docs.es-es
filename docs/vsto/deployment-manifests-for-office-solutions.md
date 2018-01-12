---
title: "Manifiestos de implementación para soluciones de Office | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], deployment manifests
- deployment manifests [Office development in Visual Studio]
- manifests [Office development in Visual Studio], deployment
- Office development in Visual Studio, deployment manifests
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0cbee926a2f9590526b11c1fb1ad70cfa2013011
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="deployment-manifests-for-office-solutions"></a>Manifiestos de implementación para soluciones de Office
  Un manifiesto de implementación es un archivo XML que describe la configuración de implementación de una solución de Office e identifica la versión actual de la aplicación.  
  
 El desarrollo de Office en Visual Studio usa el [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] esquema del manifiesto de implementación definido en el [manifiesto de implementación de ClickOnce](/visualstudio/deployment/clickonce-deployment-manifest) referencia.  
  
## <a name="remarks"></a>Comentarios  
 El archivo de manifiesto de implementación para soluciones de Office identifica la versión actual y otras configuraciones de implementación. Hace referencia el manifiesto de aplicación, que describe la versión actual de la solución y todos los archivos que se encuentran en la solución.  
  
## <a name="file-name-syntax"></a>Sintaxis de los nombres de archivo  
 El nombre de un archivo de manifiesto de implementación debe terminar con la extensión de VSTO. Aunque es un estándar [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] difiere de la extensión de manifiesto de implementación, para permitir que Visual Studio Tools para Office runtime controlar el archivo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra un manifiesto de implementación para un proyecto de Visual Studio Tools para soluciones de Office.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly   
  xsi:schemaLocation=  
    "urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"   
  manifestVersion="1.0"   
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"   
  xmlns:dsig="http://www.w3.org/2000/09/xmldsig#"   
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"   
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"   
  xmlns="urn:schemas-microsoft-com:asm.v2"   
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"   
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"   
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"   
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <assemblyIdentity   
    name="ContosoOfficeSolutions.vsto"   
    version="1.0.0.0"   
    publicKeyToken="25d0f3ca94156f1f"   
    language="neutral"   
    processorArchitecture="msil"   
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <description   
    asmv2:publisher="Microsoft"   
    asmv2:product="ContosoOfficeSolutions"   
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <deployment install="false" mapFileExtensions="true" />  
  <dependency>  
    <dependentAssembly   
      dependencyType="install"   
      codebase="ContosoOfficeSolutions.dll.manifest"   
      size="13545">  
      <assemblyIdentity   
        name="ContosoOfficeSolutions.dll"   
        version="1.0.0.0"   
        publicKeyToken="25d0f3ca94156f1f"   
        language="neutral"   
        processorArchitecture="msil"   
        type="win32" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm=  
            "urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm=  
          "http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>PoY</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
  <publisherIdentity name="name" issuerKeyHash="003" />  
<Signature   
  Id="StrongNameSignature"   
  xmlns="http://www.w3.org/2000/09/xmldsig#">    
  <SignedInfo>  
    <CanonicalizationMethod Algorithm=  
      "http://www.w3.org/2001/10/xml-exc-c14n#" />  
  <SignatureMethod Algorithm=  
    "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
    <Reference URI="">  
      <Transforms>  
        <Transform Algorithm=  
          "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
        <Transform Algorithm=  
          "http://www.w3.org/2001/10/xml-exc-c14n#" />  
      </Transforms>  
      <DigestMethod Algorithm=  
        "http://www.w3.org/2000/09/xmldsig#sha1" />  
      <DigestValue>5oz</DigestValue>  
    </Reference>  
  </SignedInfo>  
  <SignatureValue>nNG</SignatureValue>  
  <KeyInfo Id="StrongNameKeyInfo">  
    <KeyValue>  
      <RSAKeyValue>  
        <Modulus>ufI</Modulus>  
        <Exponent>AQAB</Exponent>  
      </RSAKeyValue>  
    </KeyValue>  
    <msrel:RelData   
      xmlns:msrel=  
        "http://schemas.microsoft.com/windows/rel/2005/reldata">  
      <r:license   
        xmlns:r="urn:mpeg:mpeg21:2003:01-REL-R-NS"   
        xmlns:as=  
          "http://schemas.microsoft.com/windows/pki/2005/Authenticode">  
        <r:grant>  
          <as:ManifestInformation   
            Hash="099"   
            Description=""   
            Url="">  
            <as:assemblyIdentity   
              name="ContosoOfficeSolutions.vsto"   
              version="1.0.0.0"   
              publicKeyToken="25d0f3ca94156f1f"   
              language="neutral"   
              processorArchitecture="msil"   
              xmlns="urn:schemas-microsoft-com:asm.v1" />  
          </as:ManifestInformation>  
          <as:SignedBy />  
          <as:AuthenticodePublisher>  
            <as:X509SubjectName>CN=DDNET\BAAdmin</as:X509SubjectName>  
          </as:AuthenticodePublisher>  
        </r:grant>  
        <r:issuer>  
          <Signature   
            Id="AuthenticodeSignature"   
            xmlns="http://www.w3.org/2000/09/xmldsig#">  
            <SignedInfo>  
              <CanonicalizationMethod   
                Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#" />  
              <SignatureMethod   
                Algorithm=  
                  "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
              <Reference URI="">  
                <Transforms>  
                  <Transform Algorithm=  
                    "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
                  <Transform Algorithm=  
                    "http://www.w3.org/2001/10/xml-exc-c14n#" />  
                </Transforms>  
                <DigestMethod   
                  Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
                <DigestValue>iAd</DigestValue>  
              </Reference>  
            </SignedInfo>  
            <SignatureValue>HL9</SignatureValue>  
            <KeyInfo>  
              <KeyValue>  
                <RSAKeyValue>  
                  <Modulus>ufI</Modulus>  
                  <Exponent>AQAB</Exponent>  
                </RSAKeyValue>  
              </KeyValue>  
              <X509Data>  
                <X509Certificate>MII</X509Certificate>  
              </X509Data>  
            </KeyInfo>  
          </Signature>  
        </r:issuer>  
      </r:license>  
    </msrel:RelData>  
  </KeyInfo>  
</Signature>  
</asmv1:assembly>  
```  
  
## <a name="see-also"></a>Vea también  
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)  
  
  