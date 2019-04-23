---
title: Manifiesto de aplicación ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application manifests [ClickOnce]
- ClickOnce, application manifests
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be9bfe19b92740d6be6c91802d193bf2fc401847
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59653664"
---
# <a name="clickonce-application-manifest"></a>Manifiesto de aplicación ClickOnce
Un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de aplicación es un archivo XML que describe una aplicación que se implementa mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiestos de aplicación tienen los siguientes elementos y atributos.

| Elemento | Descripción | Atributos |
| - | - | - |
| [\<assembly> Element](../deployment/assembly-element-clickonce-application.md) | Obligatorio. Elemento de nivel superior. | `manifestVersion` |
| [\<assemblyIdentity> Element](../deployment/assemblyidentity-element-clickonce-application.md) | Obligatorio. Identifica el ensamblado principal de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. | `name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language` |
| [\<trustInfo> Element](../deployment/trustinfo-element-clickonce-application.md) | Identifica los requisitos de seguridad de la aplicación. | Ninguna |
| [\<entryPoint> Element](../deployment/entrypoint-element-clickonce-application.md) | Obligatorio. Identifica el punto de entrada de código de aplicación. | `name` |
| [\<dependency> Element](../deployment/dependency-element-clickonce-application.md) | Obligatorio. Identifica cada dependencia necesaria para que se ejecute la aplicación. Identifica opcionalmente los ensamblados que se tienen que preinstalar. | Ninguna |
| [Elemento \<file>](../deployment/file-element-clickonce-application.md) | Opcional. Identifica cada archivo nonassembly utilizado por la aplicación. Puede incluir datos de aislamiento del modelo de objetos componentes (COM) asociados al archivo. | `name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType` |
| [\<fileAssociation> Element](../deployment/fileassociation-element-clickonce-application.md) | Opcional. Identifica una extensión de archivo que se asociará con la aplicación. | `extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon` |

## <a name="remarks"></a>Comentarios
 El [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] archivo de manifiesto de aplicación identifica una aplicación implementada mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Para obtener más información sobre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vea [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md).

## <a name="file-location"></a>Ubicación del archivo
 Un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de aplicación es específico para una única versión de una implementación. Por este motivo, deben almacenarse por separado de los manifiestos de implementación. La convención común es colocarlos en un subdirectorio con el nombre de la versión asociada.

 El manifiesto de aplicación siempre debe estar firmado antes de la implementación. Si cambia un manifiesto de aplicación manualmente, debe usar *mage.exe* para volver a firmar el manifiesto de aplicación, puede actualizar el manifiesto de implementación y, a continuación, volver a firmar el manifiesto de implementación. Para obtener más información, vea [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="file-name-syntax"></a>Sintaxis de los nombres de archivo
 El nombre de un archivo de manifiesto de aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] debe ser el nombre completo y la extensión de la aplicación según se identifica en el elemento `assemblyIdentity`, seguido por la extensión *.manifest*. Por ejemplo, un manifiesto de aplicación que hace referencia a la *Example.exe* aplicación utilizaría la siguiente sintaxis de nombre de archivo.

 `example.exe.manifest`

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra un manifiesto de aplicación para un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación.

```xml
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
...
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>
```

## <a name="see-also"></a>Vea también
- [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)