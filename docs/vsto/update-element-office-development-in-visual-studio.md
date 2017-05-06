---
title: "Elemento &lt;update&gt; (desarrollo de Office en Visual Studio)"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "update (elemento)"
  - "elemento <update>"
  - "manifiestos de aplicación [desarrollo de Office en Visual Studio], elemento <update>"
ms.assetid: bdd5dbf7-ddda-4ef6-9db5-1fb4405261a0
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Elemento &lt;update&gt; (desarrollo de Office en Visual Studio)
  El elemento `update` especifica el intervalo en el que la solución comprobará las actualizaciones.  
  
## Sintaxis  
  
```  
<update  
  enabled>  
  <expiration  
    maximumAge  
    unit  
  />  
</update>  
```  
  
## Elementos y atributos  
 Se requiere el elemento `update`, que se encuentra en el espacio de nombres `vstav3`.  
  
 El elemento `update` presenta los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`enabled`|Obligatorio.  Establezca enabled en uno de los valores siguientes:<br /><br /> -   **true** para comprobar las actualizaciones.<br />-   **false** para evitar la comprobación de las actualizaciones.|  
  
 El elemento `update` tiene los siguientes elementos secundarios.  
  
### expiration  
 Se requiere el elemento `expiration`, que se encuentra en el espacio de nombres `vstav3`.  Este elemento especifica el intervalo en el que la solución comprueba las actualizaciones.  
  
 El elemento `expiration` presenta los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`maximumAge`|-   Obligatorio.  Establézcalo como igual a un entero.|  
|`unit`|Obligatorio.  Establezca `unit` en uno de los valores siguientes:<br /><br /> -   **hours**<br />-   **days**<br />-   **weeks**|  
  
## Ejemplo de comprobar siempre las actualizaciones  
  
### Descripción  
 En el ejemplo de código siguiente se muestra un elemento `update` establecido de modo que siempre busque actualizaciones en soluciones de Office.  
  
### Código  
  
```  
<vstav3:update enabled="true" />  
```  
  
## Ejemplo de establecer un intervalo de actualización predeterminado  
  
### Descripción  
 En el ejemplo de código siguiente se muestra un elemento `update` de un manifiesto de aplicación para soluciones de Office.  Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Código  
  
```  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## Vea también  
 [Implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  