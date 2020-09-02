---
title: '&lt;&gt;elemento fileAssociation (aplicación ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4b31ac34627b244cb61b6fdb5c6ca214675ec045
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150843"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;&gt;elemento fileAssociation (aplicación ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifica una extensión de archivo que se va a asociar a la aplicación.  
  
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
  
## <a name="elements-and-attributes"></a>Atributos y elementos  
 El elemento `fileAssociation` es opcional. El elemento tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`extension`|Necesario. Extensión de archivo que se va a asociar a la aplicación.|  
|`description`|Necesario. Descripción del tipo de archivo que va a usar el shell.|  
|`progid`|Necesario. Nombre que identifica de forma única el tipo de archivo.|  
|`defaultIcon`|Necesario. Especifica el icono que se va a usar para los archivos con esta extensión. El archivo de icono se debe especificar utilizando el [ \<file> elemento](../deployment/file-element-clickonce-application.md) dentro del [ \<assembly> elemento](../deployment/assembly-element-clickonce-application.md) que contiene este elemento.|  
  
## <a name="remarks"></a>Comentarios  
 Este elemento debe incluir una referencia de espacio de nombres XML a "urn: schemas-microsoft-com: ClickOnce. v1". Si `<fileAssociation>` se usa el elemento, debe aparecer después del `<application>` elemento en su [ \<assembly> elemento](../deployment/assembly-element-clickonce-application.md)primario.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] no sobrescribirá las asociaciones de archivo existentes. Sin embargo, una aplicación ClickOnce puede invalidar la extensión de archivo solo para el usuario actual. Una vez desinstalada la aplicación ClickOnce, ClickOnce elimina la Asociación de archivo del usuario y la Asociación por equipo vuelve a estar activa.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestran `fileAssociation` los elementos de un manifiesto de aplicación para una aplicación de editor de texto implementada mediante [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . En este ejemplo de código también se incluye el [ \<file> elemento](../deployment/file-element-clickonce-application.md) requerido por el `defaultIcon` atributo.  
  
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
  
## <a name="see-also"></a>Consulte también  
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)
