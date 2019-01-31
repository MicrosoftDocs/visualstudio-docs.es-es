---
title: '&lt;fileAssociation&gt; elemento (aplicación ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d506fc7023f01d305fee95c52a32f2ea3dafddaf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984514"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;fileAssociation&gt; elemento (aplicación ClickOnce)
Identifica una extensión de archivo que se asociará con la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El elemento `fileAssociation` es opcional. El elemento tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`extension`|Obligatorio. La extensión de archivo que se asociará con la aplicación.|  
|`description`|Obligatorio. Una descripción del tipo de archivo para su uso por el shell.|  
|`progid`|Obligatorio. Un nombre que identifica el tipo de archivo.|  
|`defaultIcon`|Obligatorio. Especifica el icono que se utiliza para los archivos con esta extensión. El archivo de icono debe especificarse utilizando la [ \<archivo > elemento](../deployment/file-element-clickonce-application.md) dentro de la [ \<ensamblado > elemento](../deployment/assembly-element-clickonce-application.md) que contiene este elemento.|  
  
## <a name="remarks"></a>Comentarios  
 Este elemento debe incluir una referencia de espacio de nombres XML para "urn: schemas-microsoft-v1". Si el `<fileAssociation>` se usa el elemento, debe ir detrás del `<application>` elemento en su elemento primario [ \<ensamblado > elemento](../deployment/assembly-element-clickonce-application.md).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] no se sobrescribirá las asociaciones de archivo existentes. Sin embargo, una aplicación ClickOnce puede reemplazar la extensión de archivo para el usuario actual. Después de desinstala la aplicación ClickOnce, ClickOnce elimina la asociación de archivo para el usuario y la asociación de cada equipo nuevo está activa.  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo de código ilustra `fileAssociation` elementos en una aplicación de manifiesto para una aplicación de editor de texto implementada mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Este ejemplo de código también incluye el [ \<archivo > elemento](../deployment/file-element-clickonce-application.md) requerido por la `defaultIcon` atributo.  
  
```xml  
<file name="text.ico" size="4286">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>  
  </hash>  
</file>  
<file name="writing.ico" size="9662">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>  
  </hash>  
</file>  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />  
```  
  
## <a name="see-also"></a>Vea también  
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)