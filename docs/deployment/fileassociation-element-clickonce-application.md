---
title: '&lt;fileAssociation&gt; elemento (aplicación ClickOnce) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 4da80f852526afa4692b7ecd6eefea3cc3c3de7e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;fileAssociation&gt; elemento (aplicación ClickOnce)
Identifica una extensión de archivo que se asociará a la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El elemento `fileAssociation` es opcional. El elemento tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`extension`|Requerido. La extensión de archivo que desee asociar a la aplicación.|  
|`description`|Requerido. Una descripción del tipo de archivo para su uso por el shell.|  
|`progid`|Requerido. Un nombre que identifica de forma única el tipo de archivo.|  
|`defaultIcon`|Requerido. Especifica el icono que se usará para los archivos con esta extensión. El archivo de icono debe especificarse utilizando la [ \<archivo > elemento](../deployment/file-element-clickonce-application.md) dentro de la [ \<ensamblado > elemento](../deployment/assembly-element-clickonce-application.md) que contiene este elemento.|  
  
## <a name="remarks"></a>Comentarios  
 Este elemento debe incluir una referencia al espacio de nombres XML para "urn: schemas-microsoft-v1". Si el `<fileAssociation>` se utiliza el elemento, que debe venir después de la `<application>` elemento de su elemento primario [ \<ensamblado > elemento](../deployment/assembly-element-clickonce-application.md).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] no se sobrescribirá las asociaciones de archivo existente. Sin embargo, una aplicación ClickOnce puede reemplazar la extensión de archivo para el usuario actual. Después de desinstala la aplicación ClickOnce, ClickOnce elimina la asociación de archivo para el usuario y la asociación de cada equipo está activa de nuevo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra `fileAssociation` manifiesto de elementos en una aplicación para una aplicación de editor de texto implementada con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Este ejemplo de código también incluye el [ \<archivo > elemento](../deployment/file-element-clickonce-application.md) requiere el `defaultIcon` atributo.  
  
```  
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