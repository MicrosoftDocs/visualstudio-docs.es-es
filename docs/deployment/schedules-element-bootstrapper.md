---
title: "&lt;Schedules&gt; (Elemento, Arranque) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<Schedules> (elemento) [arranque]"
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 5
---
# &lt;Schedules&gt; (Elemento, Arranque)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El elemento `Schedules` contiene elementos `Schedule`, que definen el momento específico en el que los comandos definidos por el elemento `Command` deben ejecutarse.  
  
## Sintaxis  
  
```  
<Schedules>  
    <Schedule  
        Name  
    >  
        <BuildList />  
        <BeforePackage />  
        <AfterPackage />  
    </Schedule>  
</Schedules>  
```  
  
## Elementos y atributos  
 El elemento `Schedules` es un elemento secundario del elemento `Product`.  Cada elemento `Product` puede tener al menos un elemento `Schedules`.  El elemento `Schedules` no tiene atributos.  
  
## Schedule  
 El elemento `Schedule` es un elemento secundario del elemento `Schedules`.  Un elemento `Schedules` debe tener al menos un elemento `Schedule`.  
  
 `Schedule` tiene el atributo siguiente.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Name`|Obligatorio.  Nombre del elemento de programación.  Corresponde a la propiedad `ScheduleName` del elemento `Command`.  Cuando `Command` hace referencia a la programación con nombre, sólo se ejecutará en el momento indicado por dicho elemento `Schedule`.  Los programas también se pueden asociar a elementos `FailIf` y `BypassIf`, que restringen estas comprobaciones condicionales a la ejecución de la programación especificada.  Para obtener más información, vea [\<Commands\> \(Elemento\)](../deployment/commands-element-bootstrapper.md).|  
  
 Un elemento `Schedule` determinado puede tener exactamente uno de los elementos secundarios siguientes.  
  
## BuildList  
 El elemento `BuildList` indica al instalador que ejecute un comando inmediatamente después de que se inicie la aplicación de arranque.  
  
## BeforePackage  
 El elemento `BeforePackage` indica al instalador que ejecute un comando antes de que se instale el paquete especificado.  
  
## AfterPackage  
 El elemento `AfterPackage` indica al instalador que ejecute un comando después de que se instale el paquete especificado.  
  
## Vea también  
 [\<Product\> \(Elemento\)](../deployment/product-element-bootstrapper.md)   
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)