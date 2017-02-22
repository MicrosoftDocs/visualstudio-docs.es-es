---
title: "&lt;fileAssociation&gt; (Elemento) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "<fileAssociation> (elemento) [manifiesto de aplicación ClickOnce]"
  - "manifiestos [ClickOnce], fileAssociation (elemento)"
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;fileAssociation&gt; (Elemento)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica una extensión de archivo que se va a asociar a la aplicación.  
  
## Sintaxis  
  
```  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## Elementos y atributos  
 El elemento `fileAssociation` es opcional.  El elemento tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`extension`|Obligatorio.  Extensión de archivo que se va a asociar a la aplicación.|  
|`description`|Obligatorio.  Descripción del tipo de archivo que va a utilizar el shell.|  
|`progid`|Obligatorio.  Nombre que identifica inequívocamente el tipo de archivo.|  
|`defaultIcon`|Obligatorio.  Especifica el icono que se va a utilizar en los archivos que tienen esta extensión.  El archivo de icono debe especificarse utilizando [Elemento \<file\>](../deployment/file-element-clickonce-application.md) dentro del objeto [Elemento \<assembly\>](../deployment/assembly-element-clickonce-application.md) que contiene este elemento.|  
  
## Comentarios  
 Este elemento debe incluir una referencia del espacio de nombres XML en "urn:schemas\-microsoft\-com:clickonce.v1".  Si se utiliza el elemento `<fileAssociation>`, debe ir detrás del elemento `<application>` en su objeto [Elemento \<assembly\>](../deployment/assembly-element-clickonce-application.md) primario.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] no sobrescribirá las asociaciones de archivo existentes.  Sin embargo, una aplicación ClickOnce puede invalidar la extensión de archivo sólo del usuario actual.  Después de desinstalar la aplicación ClickOnce, dicho programa elimina la asociación de archivo para el usuario y la asociación por equipo está activa de nuevo.  
  
## Ejemplo  
 En el ejemplo de código siguiente se ilustran los elementos `fileAssociation` de un manifiesto de aplicación en una aplicación de editor de texto implementada con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  En este ejemplo de código también se incluye el elemento [Elemento \<file\>](../deployment/file-element-clickonce-application.md) requerido por el atributo `defaultIcon`.  
  
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
  
## Vea también  
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)