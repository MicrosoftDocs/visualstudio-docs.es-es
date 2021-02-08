---
title: Manifiesto de implementación de ClickOnce | Microsoft Docs
description: Obtenga información sobre un manifiesto de implementación, un archivo XML que describe una implementación ClickOnce, incluida la versión actual de la aplicación ClickOnce que se va a implementar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce, deployment manifests
- deployment manifests [ClickOnce]
ms.assetid: 8457e615-e3b6-4990-8dcf-11bc590e4e9b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c3e8737a29fed109e82240a74569011be60a586c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840865"
---
# <a name="clickonce-deployment-manifest"></a>Manifiesto de implementación de ClickOnce
Un manifiesto de implementación es un archivo XML que describe una implementación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], incluida la identificación de la versión de la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] actual que se va a implementar.

 Los manifiestos de implementación tienen los siguientes elementos y atributos.

| Elemento | Descripción | Atributos |
| - | - | - |
| [Elemento \<assembly>](../deployment/assembly-element-clickonce-deployment.md) | Necesario. Elemento de nivel superior. | `manifestVersion` |
| [Elemento \<assemblyIdentity>](../deployment/assemblyidentity-element-clickonce-deployment.md) | Necesario. Identifica el manifiesto de aplicación para esta aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. | `name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `culture` |
| [Elemento \<description>](../deployment/description-element-clickonce-deployment.md) | Necesario. Identifica la información de la aplicación utilizada para crear una presencia de shell y el elemento **Agregar o quitar programas** en el Panel de control. | `publisher`<br /><br /> `product`<br /><br /> `supportUrl` |
| [Elemento \<deployment>](../deployment/deployment-element-clickonce-deployment.md) | Opcional. Identifica los atributos utilizados para la implementación de actualizaciones y la exposición del sistema. | `install`<br /><br /> `minimumRequiredVersion`<br /><br /> `mapFileExtensions`<br /><br /> `disallowUrlActivation`<br /><br /> `trustUrlParameters` |
| [Elemento \<compatibleFrameworks>](../deployment/compatibleframeworks-element-clickonce-deployment.md) | Necesario. Identifica las versiones de .NET Framework en las que se puede instalar y ejecutar esta aplicación. | `SupportUrl` |
| [Elemento \<dependency>](../deployment/dependency-element-clickonce-deployment.md) | Necesario. Identifica la versión de la aplicación que se va a instalar para la implementación y la ubicación del manifiesto de aplicación. | `preRequisite`<br /><br /> `visible`<br /><br /> `dependencyType`<br /><br /> `codebase`<br /><br /> `size` |
| [Elemento \<publisherIdentity>](../deployment/publisheridentity-element-clickonce-deployment.md) | Requerido para los manifiestos firmados. Contiene información sobre el editor que firmó este manifiesto de implementación. | `Name`<br /><br /> `issuerKeyHash` |
| [Elemento \<Signature>](../deployment/signature-element-clickonce-deployment.md) | Opcional. Contiene la información necesaria para firmar digitalmente este manifiesto de implementación. | None |
| [Elemento \<customErrorReporting>](../deployment/customerrorreporting-element-clickonce-deployment.md) | Opcional. Especifica un URI que se va a mostrar cuando se produce un error. | Identificador URI |

## <a name="remarks"></a>Notas
 El archivo de manifiesto de implementación identifica una implementación de aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], incluida la versión actual y otras configuraciones de implementación. Hace referencia al manifiesto de aplicación, que describe la versión actual de la aplicación y todos los archivos contenidos en la implementación.

 Para obtener más información, consulta [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).

## <a name="file-location"></a>Ubicación del archivo
 El archivo de manifiesto de implementación hace referencia al manifiesto de aplicación correcto para la versión actual de la aplicación. Al crear una nueva versión de una implementación de aplicación disponible, debe actualizar el manifiesto de implementación para que haga referencia al nuevo manifiesto de aplicación.

 El archivo de manifiesto de implementación debe tener un nombre seguro y también puede contener certificados para la validación del editor.

## <a name="file-name-syntax"></a>Sintaxis de los nombres de archivo
 El nombre de un archivo de manifiesto de implementación debe terminar con la extensión *.application*.

## <a name="examples"></a>Ejemplos
 El ejemplo de código siguiente muestra un manifiesto de implementación.

```xml
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <assemblyIdentity
    name="My Application Deployment.app"
    version="1.0.0.0"
    publicKeyToken="43cb1e8e7a352766"
    language="neutral"
    processorArchitecture="x86"
    xmlns="urn:schemas-microsoft-com:asm.v1" />
  <description
    asmv2:publisher="My Company Name"
    asmv2:product="My Application"
    xmlns="urn:schemas-microsoft-com:asm.v1" />
  <deployment install="true">
    <subscription>
      <update>
        <expiration maximumAge="0" unit="days" />
      </update>
    </subscription>
    <deploymentProvider codebase="\\myServer\sampleDeployment\MyApplicationDeployment.application" />
  </deployment>
  <compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">
    <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.20506" />
    <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.20506" />
  </compatibleFrameworks>
  <dependency>
    <dependentAssembly
      dependencyType="install"
      codebase="1.0.0.0\My Application Deployment.exe.manifest"
      size="6756">
      <assemblyIdentity
        name="My Application Deployment.exe"
        version="1.0.0.0"
        publicKeyToken="43cb1e8e7a352766"
        language="neutral"
        processorArchitecture="x86"
        type="win32" />
      <hash>
        <dsig:Transforms>
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
        </dsig:Transforms>
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
        <dsig:DigestValue>E506x9FwNauks7UjQywmzgtd3FE=</dsig:DigestValue>
      </hash>
    </dependentAssembly>
  </dependency>
<publisherIdentity name="CN=DOMAIN\MyUsername" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">
...
</Signature></asmv1:assembly>
```

## <a name="see-also"></a>Vea también
- [Publicación de aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)