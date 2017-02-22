---
title: "Limitaciones de la depuraci&#243;n de script | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "asignación de puntos de interrupción ASPX, limitaciones"
  - "asignación de puntos de interrupción, limitaciones"
  - "depuración de secuencias de comandos, limitaciones"
ms.assetid: 280eead5-693c-47af-967f-dfe9d23f84db
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Limitaciones de la depuraci&#243;n de script
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] admite la depuración de script en el cliente, sujeta a las limitaciones descritas en este tema.  
  
## Limitaciones de la asignación de puntos de interrupción con script de cliente  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permite establecer un punto de interrupción en un archivo ASPX o HTML de servidor que se transforma en un archivo de cliente en tiempo de ejecución.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] asigna el punto de interrupción del archivo de servidor a un punto de interrupción correspondiente en el archivo de cliente, sujeto a las siguientes limitaciones:  
  
-   Los puntos de interrupción se deben establecer dentro de bloques `<script>`.  No se pueden asignar puntos de interrupción en script en línea o en bloques `<% %>`.  
  
-   La dirección URL del explorador de la página debe contener el nombre de página.  Por ejemplo, http:\/\/microsoft.com\/default.apsx.  La asignación de puntos de interrupción no puede reconocer una redirección de una dirección como http:\/\/microsoft.com a la página predeterminada.  
  
-   El punto de interrupción se debe establecer en la página especificada en la dirección URL del explorador, no en un archivo de control de ASPX \(ascx\), la página maestra u otro archivo que incluya dicha página.  No se pueden asignar puntos de interrupción establecidos en páginas incluidas.  
  
-   No se pueden asignar puntos de interrupción establecidos en bloques `<script defer=true>`.  
  
-   Para los puntos de interrupción establecidos en bloques `<script id="">`, la asignación de puntos de interrupción omite el atributo `id`.  
  
## Asignación de puntos de interrupción y líneas duplicadas  
 Para buscar la ubicación correspondiente en el script de cliente y de servidor, el algoritmo de asignación de puntos de interrupción examina el código en cada línea.  El algoritmo supone que cada línea es única.  Si dos o más líneas contienen el mismo código, y establece un punto de interrupción en una de dichas líneas duplicadas, el algoritmo de asignación de puntos de interrupción podría seleccionar el duplicado equivocado en el archivo de cliente.  Para evitarlo, agregue un comentario a la línea en la que ha establecido el punto de interrupción.  Por ejemplo:  
  
```  
i++ ;  
i ++; // I added a comment, so this line is now unique  
i ++;  
```